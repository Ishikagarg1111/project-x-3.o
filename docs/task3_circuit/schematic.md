## Task 3a — Circuit Design and Wiring

### Components Used
For the circuit, I have selected the following components:
- ESP32-WROOM-32 DevKit
- Cytron MDD10A dual-channel motor driver
- Two 12 V, 100 RPM DC gearmotors
- Four MG996R servos for the arm
- One MG90S servo for the gripper
- 3S LiPo battery (11.1 V, 2200 mAh)
- 6 V, 20 A buck converter for the servos
- 5 V, 3 A buck converter for the ESP32
- Main kill-switch, fuse, wires and capacitors

### Power Connections
I have chosen a 3S LiPo battery to power the robot. It provides 11.1 V normally and 12.6 V when fully charged.
The battery is connected to a main kill-switch and fuse. After that, the power is divided into three parts.
1. The motor driver gets power directly from the battery and controls the two DC motors.
2. A 6 V buck converter supplies power to all five servos.
3. A separate 5 V buck converter supplies power to the ESP32.

I have kept the ESP32 and servo power supplies separate because the servos can draw a large amount of current when they start moving or lift an object.
If they use the ESP32's power supply, the voltage might drop and cause the controller to restart.

All the components share a common ground so that the control signals work correctly.

### Why I Did Not Power the Servos from the ESP32's 5 V Pin
I have used a separate 6 V buck converter for the servos instead of powering them through the ESP32's 5 V pin.
Servos draw a large amount of current, especially when they start moving or lift a load. 
The ESP32's 5 V pin and its power supply path are not designed to handle the combined current of five servos.
If I power the servos through the controller, the high current demand could cause voltage drops, reset the ESP32 or overload its power connections.
So, I have provided a separate power supply for the servos and connected their ground to the ESP32's ground so that the control signals work properly.

### Control Connections
The ESP32 sends PWM and direction signals to the motor driver. These signals control the speed and direction of the left and right motors.
The servo control connections are:
Component| ESP32 GPIO
Base servo| GPIO 13
Shoulder servo| GPIO 16
Elbow servo| GPIO 17
Wrist servo| GPIO 18
Gripper servo| GPIO 19
Status LED| GPIO 2
The motor driver needs two control signals for each motor: one for speed (PWM) and one for direction. 
I will use suitable free ESP32 GPIO pins for these connections.
The ESP32 will receive commands wirelessly from the team's designated controller. Only authorised commands should be accepted so that another controller cannot operate the robot.

### Decoupling Capacitors
I will add a bulk capacitor near the motor driver because motors can cause sudden voltage changes when starting or changing direction.
I will also add a capacitor near the servo power connections to help reduce voltage drops when the servos start moving.
Small ceramic capacitors can be used near the logic supply connections to reduce electrical noise.
The capacitor voltage ratings will be chosen according to the supply voltage.

### Wire Selection
For the main battery connections, I have considered 16 AWG stranded copper wire because it can carry relatively high current with less voltage drop.
For the individual motor connections, 18 AWG wire may be suitable, depending on the actual current and wire length.
The final wire sizes will be checked according to the current ratings of the components and connectors.

I have kept the motor, servo and controller power connections separate to make the circuit more reliable. The ESP32 will control the motors and servos, while the motor driver and buck converters will handle their power requirements.

This arrangement should reduce voltage drops and make troubleshooting easier.
