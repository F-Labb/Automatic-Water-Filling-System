# Automatic-Water-Filling-System
Automated water filling for coffee machine, thermopot, and robotic vacuum cleaner based on the ESP32-C6 and ESPHome. The project uses the Thread protocol (via OpenThread) for smart home integration.

**Main features**

• Three independent channels: separate refill control for the coffee machine, water heater, and vacuum cleaner.

• Smart delays:

Coffee machine and water heater: 3-minute wait before switching on (prevents false alarms/chatter).

Vacuum cleaner: 3-hour wait (ideal for periodic maintenance).

Safety (Timeouts): Automatic forced valve closure after 5-7 minutes if the level sensor is not triggered.

• Master lock: Global autofill_lock switch that instantly closes all valves and prevents them from opening (e.g., when leaving).

• Home Assistant integration: Devices are displayed as valves with corresponding icons and statuses.

**Hardware**

• Controller: ESP32-C6 (Thread support).

• Actuators: MOSFET switches for controlling solenoid valves.

• Sensors: Reed level sensors (connected with INPUT_PULLUP).

**Operating Logic**

1. Event: The sensor signals a low water level.

2. Delay: The system waits a set time (from 3 minutes to 3 hours) to ensure refilling is necessary.
   
3. Check: If the interlock is disabled, the corresponding valve opens.

4. Completion: The valve closes either based on a sensor signal (refilling) or a safety timer (flood prevention).
