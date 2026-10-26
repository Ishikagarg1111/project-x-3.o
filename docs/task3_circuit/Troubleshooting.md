## Task 3d — Troubleshooting

*Selected Fault: The ESP32 resets when the shoulder servo starts moving.*

### Possible Causes
The main reason could be a sudden voltage drop when the shoulder servo starts moving.
The servo draws more current when it starts moving or lifts a load. If the power supply cannot provide enough current, the voltage may drop and cause the ESP32 to restart.
Other possible reasons could be loose connections, an overloaded power supply or electrical noise from the servo.

### First Diagnostic Check
First, measure the voltage at the ESP32's power input using a multimeter while moving the shoulder servo.
If the voltage drops significantly when the servo starts moving, it would indicate a possible power supply problem.
Then also check whether the servo is receiving power from the separate 6 V buck converter instead of the ESP32's 5 V pin.

### How I Would Fix It
I would make sure that the servos are powered through the separate 6 V buck converter, while the ESP32 receives power from its own 5 V converter.
I would also check that both converters can supply enough current and that all components share a common ground.
If needed, I would add a bulk capacitor near the servo power connections to help reduce sudden voltage fluctuations.

### How I Would Confirm the Fix
After making these changes, I would move the shoulder servo repeatedly, including under its expected load.
If the ESP32 no longer resets and its supply voltage remains stable during servo movement, I would consider the problem fixed.

*Conclusion*
The most likely cause of the reset is a voltage drop due to the servo's high current demand.
Using separate power supplies, checking the connections and adding suitable capacitors should help prevent this problem.
