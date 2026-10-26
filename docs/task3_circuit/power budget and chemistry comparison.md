Task 3b — Electronics BOM, Power Budget and Battery Selection

##  Power Budget
I used the reference current values given in Appendix A to estimate how much current the components will need.
Component| Voltage| Quantity| Typical total current| Maximum total current
DC gearmotors| Battery voltage| 2| 2 A| 8 A
MG996R servos| 6 V| 4| 2 A| 10 A
MG90S servo| 6 V| 1| 0.2 A (assumed)| 0.7 A
ESP32| 5 V| 1| 0.08 A| 0.35 A

The maximum current is calculated by considering the stall current of the motors and servos.

## Chemistry comparison

### Buck Converter Selection

For the four MG996R servos:
4 × 2.5 = 10 A
For the MG90S servo:
0.7 A
Total maximum servo current:
10 + 0.7 = 10.7 A
The assignment asks for at least 1.5 times the maximum current capacity.
Required converter current:
10.7 × 1.5 = 16.05 A
So, I selected a 6 V, 20 A buck converter for the servos.
For the ESP32, the maximum current is 0.35 A.
0.35 × 1.5 = 0.525 A
A 5 V, 3 A buck converter is enough for the ESP32.

### Maximum Battery Current
I assumed both buck converters have an efficiency of 85%.
Current drawn by the two drive motors at stall = 8 A
Current drawn from the battery by the servo converter:
(6 × 10.7) / (0.85 × 11.1) = 6.80 A
Current drawn by the ESP32 converter:
(5 × 0.35) / (0.85 × 11.1) = 0.19 A
Total estimated maximum battery current:
8 + 6.80 + 0.19 = 14.99 A
This is an approximate worst-case value. The actual current may be different because of motor loading and electrical losses.

### Battery Selection and Runtime
I selected a 3S LiPo battery rated at 11.1 V, 2200 mAh and 25C.
Battery capacity = 2200 mAh = 2.2 Ah
Assuming 80% of the capacity is usable:
2.2 × 0.8 = 1.76 Ah
For normal operation, I assumed:
- Each drive motor uses around 1 A.
- Each MG996R servo uses around 0.5 A while moving.
- The MG90S servo uses around 0.2 A.
- The ESP32 uses around 0.08 A.
Taking converter efficiency as 85%, the estimated average battery current is:
2 + (6 × 2.2)/(0.85 × 11.1) + (5 × 0.08)/(0.85 × 11.1)= 3.44 A

Estimated runtime:
(1.76 / 3.44) × 60 = 30.7 minutes

Since one competition run lasts 7 minutes, this battery should provide enough capacity for one run and some additional testing under the assumed conditions.

### Battery Discharge Rating

The selected battery has a 25C discharge rating.
Maximum rated continuous discharge current:
2.2 × 25 = 55 A
The estimated maximum current requirement is about 14.99 A, which is below the battery's rated discharge current.

### Comparison of LiPo and Li-ion Batteries

Factor| LiPo| Li-ion 18650
Energy density| Moderate to high| Generally higher
Discharge current| High-current packs available| Depends on the cell
Weight| Suitable for compact robots| Often better for energy storage
Cost| Depends on pack| Depends on cells and pack
Main advantage| High discharge capability| Longer runtime for similar stored energy

I chose a LiPo battery because the robot needs high current for the motors and servos, especially when starting or lifting objects. A LiPo pack with a suitable discharge rating can handle these short periods of high current.

### Voltage and Safety Check

A 3S LiPo battery has three cells connected in series.
Maximum voltage of one fully charged cell = 4.2 V
Maximum battery voltage:3 × 4.2 = 12.6 V

The competition allows a maximum of 24 V DC, so the battery meets this requirement.
I will use a main kill-switch that disconnects power to the entire robot. It must be rated for the actual current. A suitable fuse will also be included.
The battery will be fixed securely to the chassis using a proper holder or straps so that it cannot fall out if the robot tips over.

Conclusion:
I selected a 3S LiPo battery, separate buck converters for the servos and ESP32, and a higher-current motor driver.
Based on the calculations, the estimated cost is within the budget, and the battery should be sufficient for a 7-minute run.
The final component ratings and prices will need to be checked before building the circuit.
