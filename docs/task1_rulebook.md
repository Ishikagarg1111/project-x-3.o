## Task 1 — Quick Rulebook Check

**1. Size and Reach**
- Starting dimensions: The robot must fit inside a 300 × 200 × 300 mm (length × breadth × height) box.
- Arm reach: The robotic arm must grasp objects whose centre is 450 mm above the ground.
- Minimum ground clearance: 50 mm.
The robot may extend beyond its starting dimensions after the run begins.

**2. Disconnect**
If the wireless connection between the joystick and the robot is lost:
- Both drive motors must stop immediately.
-  arm motion must cease.
- The gripper must remain in its previous position without releasing the object.
- The robot must remain completely disabled until a new valid command is received from the designated controller.

**3. Power Calculation**
The maximum permitted voltage between any two points is 24 V DC.
A fully charged LiPo cell has a voltage of 4.2 V.

For a 3S LiPo battery:
Maximum voltage = 3 × 4.2 = 12.6 V

For a 6S LiPo battery:
Maximum voltage = 6 × 4.2 = 25.2 V

Conclusion: A fully charged 3S LiPo(v<24) satisfies the voltage requirement, whereas a fully charged 6S LiPo(v>24) exceeds it.
Thus only 3S LiPo battery will comply

**4. Score Calculation**
Given:The robot successfully completes the following obstacles:
Obstacle| Points
The Pickup| 10
The Ascent| 30
The Bridge| 10
The Descent Breakdown| 60
Touchdown| 10
The End| 10
Completion time = 250 seconds
Cube dropped once = 15-point penalty
One wheel leaves the track once = 10-point penalty

The scoring formula is:
Total Score = A + T − P
Where:
- A = Points earned from completed obstacles
- T = Time bonus
- P = Total penalties

A = 10 + 30 + 10 + 60 + 10 + 10=130
T = 300 − Completion time
T = 300 − 250 = 50
P = 15 + 10= 25

Total Score = A + T − P
Total Score = 130 + 50 − 25

`Final Score = 155 points`
