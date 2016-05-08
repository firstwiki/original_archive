# Line following (FLL)

## From FIRSTwiki

Jump to: navigation, search

In LEGO Mindstorms based robots designed to compete in the FIRST LEGO League competition, line-following is a common technique. The robot uses a [light sensor](/index.php?title=Light_sensor&action=edit "Light sensor") to follow a line as part of navigation to objectives in the game. Various techniques and algorithms are available. Some utilize one light sensor, some two.

[[edit](/index.php?title=Line_following_%28FLL%29&action=edit&section=1 "Edit
section: Algorithms")]

## Algorithms

[[edit](/index.php?title=Line_following_%28FLL%29&action=edit&section=2 "Edit
section: One Light Sensor")]

### One Light Sensor

- Using a single light sensor, the robot turns in one direction (does not spin on its axis, but turns while moving forward) until it can no longer see the line, then turns in the opposite direction until it can see the line. This method is generally inefficient and slow, but is usually accurate.

[[edit](/index.php?title=Line_following_%28FLL%29&action=edit&section=3 "Edit
section: Two Light Sensors")]

### Two Light Sensors

- The robot turns until in one direction until one light sensor detects the line, then turns in the other direction until the other light sensor sees the line. This method is slightly more efficient and slightly less accurate than the single light sensor method.
- The robot moves straight forward until one of the light sensors detects the line. It then turns until neither light sensor detects the line and proceeds forward. This method is the most efficient and is only slightly less accurate than the single light sensor method.
