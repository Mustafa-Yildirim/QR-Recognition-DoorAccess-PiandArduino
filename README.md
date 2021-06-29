# QR-Recognition-DoorAccess-PiandArduino

We implemented an automatic door system which recognize one’s QR badge
and let’s authorized people in when a sensor detects a movement in allowed distance. 
After a person let in by opening the door, another sensor checks current light value and makes decision to close based on received value.

Design

An ultrasonic sensor, a photoresistor is connected to the Arduino. 
And a camera connected to the Raspberry Pi. 
The Arduino and Raspberry Pi had connected via serial communication I2C protocol.

Execution

When the ultrasonic sensor indicates the presence of a user at the door, 
Arduino communicates with Raspberry Pi to tell that a user is detected which leads to the activation of the Pi camera. 
Then Pi camera scans the QR badge and sends the data to Arduino.
If the badge belongs to one of the authorized users defined in Arduino's memory, Arduino activates the servo motor to open the door. 
When person passed by the door and went inside, ultrasonic sensor will sense nobody present at the door, and photoresistor will sense a light value more than the limit it is set to. That light value indicates door is still open and ultrasonic sensor senses no one, After 2 seconds delay, photoresistor condition will lead servo to close the door.

