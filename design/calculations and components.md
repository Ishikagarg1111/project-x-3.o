Task 4 — Challenge B: Grip Force Calculation and Component Justification

### Assumptions

For my self-aligning gripper, I have considered a 50 mm cube as the object to be picked up.

Since the actual mass and surface friction are not given, I have assumed the following values:

- Mass of cube = 100 g = 0.1 kg
- Acceleration due to gravity = 9.81 m/s²
- Coefficient of friction between rubber pads and cube = 0.5
- Number of gripping fingers = 2
- Factor of safety = 2
- Distance from finger pivot to contact point = 30 mm

These values are approximate and will need to be checked during testing.

## Grip Force Calculation
Weight = Mass × Gravity
Weight of cube = 0.1 × 9.81= 0.981 N
The gripper will hold the cube using two fingers. I have assumed that both fingers apply equal force and that friction prevents the cube from slipping.
For two fingers:
Total friction force = 2 × μ × F
Where:
- μ = Coefficient of friction
- F = Normal gripping force applied by each finger
- 
For the cube to remain in place:
2 × μ × F ≥ W
Substituting the values:
2 × 0.5 × F ≥ 0.981
F ≥ 0.981 N
Therefore, each finger needs to apply at least 0.981 N of normal force.

To make the grip more reliable, I have considered a factor of safety of 2.
Required force per finger = 0.981 × 2
Required gripping force = 1.962 N per finger

### Actuator Torque Calculation

I have considered an MG90S servo motor to operate both fingers through a linkage mechanism.
For an approximate torque calculation, I have assumed an effective lever arm of 30 mm.
Torque = Force × Distance
Torque required per finger:
T = 1.962 × 0.03
T = 0.0589 N·m
For two fingers, the ideal total torque is:
T = 2 × 0.0589
T = 0.1178 N·m
Converting into kg·cm:
T = 0.1178 / 0.0981
T ≈ 1.20 kg·cm
This is an ideal estimate. The actual servo torque requirement will depend on the linkage geometry, mechanical losses and finger positions.

## Component Justification

*MG90S Servo Motor*
I have selected an MG90S servo because it is compact, lightweight and can control the opening and closing of the gripper.
A typical MG90S servo is advertised with a stall torque of around 2 kg·cm at 6 V, although the exact value depends on the manufacturer.
My ideal calculation gives a torque requirement of approximately 1.20 kg·cm.
This suggests that the MG90S may be suitable, but I still need to check the actual linkage geometry and usable operating torque.
Stall torque should not be treated as the torque available for continuous operation.

*Two Adaptive Fingers*
I have chosen two adaptive fingers because they can adjust to the shape and position of the object.
This should help the gripper make better contact with a cube that is not perfectly centred.

*Rubber Pads*
I will use rubber pads on the inner surfaces of the fingers to increase friction.
This will help prevent the cube from slipping and reduce the gripping force needed.

*Linkage Mechanism*
I have considered a simple linkage mechanism so that one servo can operate both fingers.
This reduces the number of actuators and keeps the gripper relatively compact.

*Mounting Plate*
The mounting plate will support the servo and finger mechanism. I will keep it rigid enough to prevent unwanted movement while gripping the cube.
