# StairsLight

Stair lighting control system with traveling wave effect

Individual stairs lighting control system 
Stair lighting control system with traveling wave effect.
Designed for installation on stairs with several spans. At the beginning and end of each span, an ultrasonic sensor is installed to detect a person. Each step is equipped with individual lighting, which is controlled by a relay connected to the controller
After the sensor is triggered, a traveling wave effect is created - turning on the lighting of each step in turn, moving away from you.

## Traveling wave algorithm

When passing the first sensor (at the bottom or at the top of the stairs), a wave of activation of the corresponding flight begins in the direction of movement (up or down).
If a person continues to stand at the beginning of the stairs, the already lit flight continues to burn
If a person passes by the sensor - after a specified time (10 seconds by default), the steps start to turn off in the same direction as they were turned on before. Thus, after passing the sensor, in any case, there will be at least 10 seconds to pass the illuminated stairs.
If a person managed to reach the intermediate sensor before the first flight goes out, the first flight continues be lighten and the second flight starts to turn on. 
If you reach the upper sensor while the second flight is on, nothing happens. 
If both flights had time to go out and the upper sensor triggered, it is assumed that a person came up from the second floor and goes down, respectively, there are switching waves from top to bottom.
If a person is opposite the middle sensor, and both flights go out, it is not clear where he came from. So begins the simultaneous wave of the first flight from top to bottom and the second flight bottom to top.

## System operation example
[Top sensor triggered](https://github.com/Brabn/StairsLight/blob/main/Photo/Top%20sensor%20triggered.3gp)

[Bottom sensor triggered](https://github.com/Brabn/StairsLight/blob/main/Photo/Bottom%20than%20middle%20sensor%20triggered.3gp)

[Top than middle sensors triggered](https://github.com/Brabn/StairsLight/blob/main/Photo/Top%20than%20middle%20sensor%20triggered.3gp)

[Bottom than middle sensors triggered](https://github.com/Brabn/StairsLight/blob/main/Photo/Bottom%20than%20middle%20sensor%20triggered.3gp)


## Main system parameters:

* The maximum load switched by each relay channel:
  - for alternating current –  10A 250VAC
  - for direct current –       10A, 30VDC
  - Relay control voltage – 5V
  - Relay supply voltage – 12V
* Relay channels – 37 pcs.
* Relay type – Optocoupler  
* Stairs flights	– 3 (17+10+10 stairs)
* Ultrasonic sensor - HC-SR04
  - Angle of view – 15°
  - Detection range – 2..450 cm
  - Precision – 0.3 cm
 
## Wiring diagram

![Stairs Ligts wiring diagram](https://github.com/Brabn/StairsLight/blob/main/Wiring_diagram/StairsLights.Wiring_diagram.jpg)


## Components:
* Arduino MEGA controller
* 8-channel relay 10A 30VAC 250VDC – 5 pcs.
* Ultrasonic sensor HC-SR04 – 4 pcs.

## Optionally, it is possible to implement:
* Adding physical switches in addition to sensors;
* Differ channels grouping and flights amount;
* inclusion of checkerboard, tracks, rhythm, etc;
* Additional effects (checkmate lighting);
* Relay control via i2c -  appropriate scaling of the number of channels;
* Eexternal control (Bluetooth, radio channel, remote control);
* Web interface for control and changing parameters;
* Connecting to an existing smart home system;
