# katya-emily-project

import random
import datetime

class EnergyConsumptionSimulator:
    def __init__(self, devices):
        self.devices = devices
        self.data = {}

    def simulate_energy_consumption(self, start_time, end_time, interval_minutes):
        current_time = start_time
        while current_time < end_time:
            for device in self.devices:
                if device not in self.data:
                    self.data[device] = []
                consumption = random.uniform(1, 10)  # Simulating random energy consumption
                entry = {"timestamp": current_time, "consumption": consumption}
                self.data[device].append(entry)
            current_time += datetime.timedelta(minutes=interval_minutes)

    def display_energy_consumption(self):
        for device, entries in self.data.items():
            print(f"Energy consumption for {device}:")
            for entry in entries:
                print(f"{entry['timestamp']} - {entry['consumption']} kWh")

# Example usage
devices_to_simulate = ["DeviceA", "DeviceB", "DeviceC"]
simulator = EnergyConsumptionSimulator(devices_to_simulate)

start_time = datetime.datetime(2023, 1, 1, 0, 0)  # January 1, 2023, 00:00
end_time = datetime.datetime(2023, 1, 1, 23, 59)   # January 1, 2023, 23:59
interval_minutes = 60  # Simulating energy consumption every 60 minutes

simulator.simulate_energy_consumption(start_time, end_time, interval_minutes)
simulator.display_energy_consumption()
