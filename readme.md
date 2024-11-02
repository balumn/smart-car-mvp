# Arduino Smart Car

A versatile Arduino-based robotic car with autonomous navigation, path memory, and Bluetooth control capabilities.

## Features

- **Bluetooth Control**: Remote control via Bluetooth connection
- **Autonomous Navigation**: Smart obstacle avoidance using ultrasonic sensor
- **Path Memory**: Can store and replay up to 3 different movement paths
- **Multiple Movement Modes**:
  - Forward/Backward movement
  - 45° and 90° turns in both directions
  - Speed control (Normal/High)
  - Smart autonomous mode
- **Path Recording & Playback**:
  - Record custom movement sequences
  - Automatic return path calculation
  - Memory storage in EEPROM

## Hardware Requirements

- Arduino board (Uno recommended)
- Motor Driver Shield (L293D)
- 4x DC Motors
- Servo Motor
- Ultrasonic Sensor (HC-SR04)
- Bluetooth Module (HC-05/HC-06)
- Power Supply

## Pin Configuration

- **Motors**: 
  - M1: Motor Shield Port 1
  - M2: Motor Shield Port 2
  - M3: Motor Shield Port 3
  - M4: Motor Shield Port 4
- **Ultrasonic Sensor**:
  - TRIG: A0
  - ECHO: A1
- **Servo**: Pin 10
- **Bluetooth**:
  - RX: Pin 0
  - TX: Pin 1

## Control Commands

---------------------------------------------
| Command | Action                          |
|---------|---------------------------------|
| '1'     | Start recording path for Room 1 |
| '2'     | Start recording path for Room 2 |
| '3'     | Start recording path for Room 3 |
| '4'     | Replay path to Room 1           |
| '5'     | Replay path to Room 2           |
| '6'     | Replay path to Room 3           |
| '7'     | Increase turn adjustment        |
| '8'     | Decrease turn adjustment        |
| 'z'     | End path recording              |
| 's'     | Enable smart autonomous mode    |
| 'f'     | Move forward                    |
| 'b'     | Move backward                   |
| 'r'     | Turn right 45°                  |
| 'l'     | Turn left 45°                   |
| 'u'     | Turn right 90°                  |
| 'v'     | Turn left 90°                   |
| 'm'     | Set high speed                  |
| 'n'     | Set normal speed                |
| 'c'     | Clear all stored paths          |
---------------------------------------------

## Libraries Required
```cpp
#include <EEPROM.h>
#include <AFMotor.h>
#include <NewPing.h>
#include <SoftwareSerial.h>
#include <Servo.h>
```

## Setup Instructions

1. Install all required libraries in Arduino IDE
2. Connect hardware components according to pin configuration
3. Upload code to Arduino board
4. Connect to the Bluetooth module using any Bluetooth terminal app
5. Send commands to control the car

## Memory Management

- Room 1 path: EEPROM addresses 1-49
- Room 2 path: EEPROM addresses 51-99
- Room 3 path: EEPROM addresses 101-149
- Turn adjustment value stored at address 200

## Notes

- The car automatically stops if obstacles are detected within 50cm
- Turn angles can be fine-tuned using commands '7' and '8'
- The return path automatically inverts all turns while maintaining forward/backward movements
- Motor speeds are calibrated with slight offsets to compensate for motor differences

## Contributing

Feel free to submit issues and enhancement requests!