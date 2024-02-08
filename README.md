# P1 Port - Veitur Iceland smart-meters

This repository holds documentation, configuration examples, provide basic code examples and point to other repositories and documentation

Everything to enable everyone to utilize the P1 Port for Veitur smart meters (Veitur is an Utility company in Iceland)


## General Summary of the P1 Port Capabilities
The P1 port enables passive access to a data stream from the smart meter. The port provides access to multiple electricity measurements, including power, consumption, and power quality data. The P1 port also provides access to data from submeters; in Veitur's case, that can be data from water and heat meters. The availability of the data depends on the installation and setup at each location, so what data is available depends on several factors. As this is still under configuration, this will change until the profile is ready.

Data points and values are referenced by "OBIS Codes," which can be part of the OBIS standard, particularly IEC 62056-61; however, it could also enable access to "non-standard OBIS codes" as IEC 62056-61 allows. This might be true for submeters (Heat and Water) if applicable.

The frequency of data collection from the P1 port depends on several factors. One is the general bandwidth and payload size; the other is how frequently the meter's configuration is set to collect data. Overall, at least a 10-second frequency should be available.

## Hardware
The P1 port is passive. This means that no information can be sent to the port, but the device parsing the data from the P1 port can request data (by setting Pin 2 to High), and the device should control the request frequency using this pin.
The P1 port provides (very limited) power to power a device. It accepts very low inrush/burst current but should handle devices that use around 200mA at 5V. If the device reading the port needs more power, it needs to be self-powered.
TODO: List devices that are known to work.
As a note: Not all self-powered devices will work for Veitur meters, even though they might work as self-powered on other smart meters.
Generally, the best solution is to have a simple device that only parses and forwards the captured data to a management or data collection system, such as Home Assistant or other data collection systems.

## Software
Home Assistant using ESPHome on a supported device works to view electricity usage. Has not been proven to work with heat meters.
Other standard software, such as Azure IoT / MQTT brokers, InfluxDB, Grafana, can be set up to create custom solutions and dashboards using a device with firmware or software that can parse and forward data to such systems.

## P1 Port Configuration
Veitur is still working on the final configuration; this might all change.
Note: Serial communication is inverted (the meter has an optocoupler).

- Baud Rate: 9600
- Data Bits: 7
- Parity: None
- Stop Bits: 1

## OBIS Codes on Veitur Smart Meters Explained
To be added...
