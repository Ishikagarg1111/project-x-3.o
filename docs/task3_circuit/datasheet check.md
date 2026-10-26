## Task 3c — Datasheet Check

Selected component: Cytron MDD10A Rev2.0 dual-channel motor driver
I selected the Cytron MDD10A motor driver because the reference L298N-class driver may not be able to handle the motor's stall current safely.

### Current Rating
According to the manufacturer's datasheet, the MDD10A can handle:
- 10 A continuous current per channel
- 30 A peak current per channel for up to 10 seconds
In Appendix A, the stall current of each DC motor is given as 4 A.
Current margin:
10 / 4 = 2.5

This means the motor driver's continuous current rating is 2.5 times the reference motor's stall current.
The L298N-class driver mentioned in the reference sheet has a continuous rating of only 2 A per channel. Since the motor can draw up to 4 A at stall, I decided to use the MDD10A instead.

### Operating Voltage
The MDD10A Rev2.0 supports a motor supply voltage of 5–30 V.
I have selected a 3S LiPo battery, which provides:
- 11.1 V nominal voltage
- 12.6 V when fully charged
Both values are within the motor driver's voltage range, so the selected battery can be used with it.

### Rating That Could Damage the Component
One important thing mentioned in the manufacturer's documentation is that the MDD10A does not have reverse-polarity protection at its motor power input.
If the positive and negative battery wires are connected incorrectly, the driver may get damaged.
To avoid this, I will use a polarised connector, clearly label the positive and negative wires, and check the connections before switching on the robot.
I will also make sure the motors do not exceed the driver's current rating during operation.

### Compatibility With ESP32
The MDD10A accepts 3.3 V logic signals, so it can be controlled directly using the ESP32's GPIO outputs.
It uses one PWM signal and one direction signal for each motor.
This is different from the L298N, which uses two direction inputs for each motor along with a speed-control input.
Therefore, I will connect the MDD10A according to its own pin arrangement rather than using the L298N wiring directly.

*Conclusion*
I chose the Cytron MDD10A because it has a higher current rating than the reference L298N-class driver and supports the voltage of the selected battery.

Its control signals are also compatible with the ESP32. The main precautions are to connect the battery with the correct polarity and keep the motor current within the driver's limits.

Reference: Cytron Technologies — MDD10A Rev2.0 datasheet and user manual.
