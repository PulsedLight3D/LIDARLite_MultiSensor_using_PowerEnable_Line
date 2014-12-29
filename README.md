# LIDAR-Lite MultiSensor using PowerEnable Line


This sketch demonstrates getting distance from multiple LIDAR-Lite sensors by enabling the Power Enable line of the sensor  to read from, and disabling the others.

## Dependencies
1. Arduino Uno compatible Board
2. Arduino IDE (1.0.5 or newer)
3. USB Cable
5. 2-4 x LIDAR-Lite Sensor
6. The 'Arduino I2C Master Library' from DSS Circuits: http://www.dsscircuits.com/index.php/articles/66-arduino-i2c-master-library

## Installation
1. Download Repository and open with Arduino IDE
2. Install DSS "Arduino I2C Master Library" - Information about installing libraries can be found:  
http://arduino.cc/en/Guide/Libraries


## LIDAR-Lite/Arduino Setup

![Fritizing Diagram](http://pl3d.us/ll-multisensor-update.jpg)

All LIDAR-Lite Sensors| Arduino Pins
:---|:---
5V | 5V
***PWR EN*** | ***Each Sensor connects to a different Digital I/O Pin on the Arduino (ex. 2,3,4,5)***
MODE | _(Unused)_
SCL | SCL (topmost pin on the right hand side of Arduino)
SDA | SDA (second pin from the top on the right hand side of Arduino)
GND | GND

## Usage
1. Open the code with the Arduino IDE
2. Before the "setup()" there are two variables: "sensorPins" Array and "sensorPinsArraySize". Make sure you have entered each of the digital I/O pin numbers into the array (if different than the diagram and sketch) and that you list the size of the array (ex. if you're only using two sensors, make sure the array only has two elements and that the array size is "2").
3. Connect to Arduino and upload code.
4. Open the serial monitor (Make sure baud rate is set to 115200)
5. For each sensor the distance measured in centimeters (cm) will print to the serial monitor separated by a "."

## How it works

The Power Enable line on the LIDAR-Lite sensor allows the unit to be put to sleep (when set LOW) and woken up (when set HIGH). Before taking a reading, this sketch turns off all the units, then enables the one set in "enableDisableSensor(int sensorPin)". Once the unit wakes up we take a reading, then repeat for each sensorPin. 

