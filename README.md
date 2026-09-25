# Pick-Place-Arm

# 🤖 Joystick Controlled Robotic Arm

A simple **4-axis robotic arm** controlled using **two joystick modules and an Arduino**. The project allows the user to control the base, shoulder, elbow, and gripper using joystick movements.

The system also includes **smooth servo movement**, **joystick dead-zone control** and **automatic return-to-center** for the base, shoulder and elbow.

## ✨ Features

* 🎮 Dual joystick control.
* 🔄 Base rotation control.
* 💪 Shoulder movement control.
* 🦾 Elbow movement control.
* ✋ Gripper open/close control.
* 🎯 Joystick dead-zone to prevent unwanted movement.
* ⚙️ Smooth servo movement.
* 🔙 Base, shoulder and elbow return to their original position when the joystick is released.
* 🛡️ Gripper debounce protection.
* 📟 Serial Monitor status messages.

## 🧩 Components Required

| Component                   |    Quantity |
| --------------------------- | ----------  |
| Arduino Board               |           1 |
| Servo Motor                 |           4 |
| Joystick Module             |           2 |
| Robotic Arm Mechanism       |           1 |
| Jumper Wires                | As required |


## 🔌 Pin Connections

### Servo Motors

| Servo          | Arduino Pin | Function           |
| -------------- | ----------- | ------------------ |
| Base Servo     | D2          | Base rotation      |
| Shoulder Servo | D3          | Shoulder movement  |
| Elbow Servo    | D5          | Elbow movement     |
| Gripper Servo  | D6          | Gripper open/close |

### Joystick 1

| Joystick 1 | Arduino Pin | Function |
| ---------- | ----------- | -------- |
| VRx        | A0          | Base     |
| VRy        | A1          | Shoulder |

### Joystick 2

| Joystick 2 | Arduino Pin | Function |
| ---------- | ----------- | -------- |
| VRx        | A2          | Gripper  |
| VRy        | A3          | Elbow    |

## 🎮 Control System

### Joystick 1

* **Left / Right** → Base rotation
* **Up / Down** → Shoulder movement

### Joystick 2

* **Up / Down** → Elbow movement
* **Left** → Open gripper
* **Right** → Close gripper

### Automatic Return

When the joystick is released:

* Base → returns to **90°**
* Shoulder → returns to **90°**
* Elbow → returns to **90°**

The gripper stays in its last selected position.

## ⚙️ Servo Positions

| Movement                  | Position |
| ------------------------- | -------: |
| Base Initial Position     |      90° |
| Shoulder Initial Position |      90° |
| Elbow Initial Position    |      90° |
| Gripper Open              |       0° |
| Gripper Closed            |      90° |

> **Note:** Servo angles may need to be adjusted depending on your robotic arm's mechanical design.

## 🧠 How It Works

The Arduino continuously reads the two joystick modules.

text
Joystick 1
   │
   ├── X → Base Servo
   └── Y → Shoulder Servo

Joystick 2
   │
   ├── X → Gripper Servo
   └── Y → Elbow Servo


The joystick values are converted into servo movements.

A **dead zone** is used around the joystick center so that small fluctuations do not move the servos.

cpp
const int DEAD_ZONE = 80;


The servo movement is performed gradually instead of jumping directly to the target angle.

cpp
moveServoSmooth(...)


This helps provide smoother robotic-arm movement.

## 🛠️ Software

* **Arduino IDE**
* **Arduino Servo Library**
* Arduino-compatible board

## 🚀 How to Upload

1. Install **Arduino IDE**.
2. Connect the Arduino board to your computer.
3. Connect the servos and joystick modules according to the pin table.
4. Open the `.ino` file.
5. Select your Arduino board.
6. Select the correct COM port.
7. Click **Upload**.
8. Open the **Serial Monitor** at **9600 baud**.

## 🖥️ Serial Monitor

After startup, the Arduino displays:

text
=================================
ROBOT ARM CONTROLS:
Joy1 LEFT/RIGHT -> Base
Joy1 UP/DOWN    -> Shoulder
Joy2 UP/DOWN    -> Elbow
Joy2 LEFT/RIGHT -> GRIPPER
  LEFT  = OPEN
  RIGHT = CLOSE
=================================

When the gripper is operated:

>>> GRIPPER OPEN <<<


or


>>> GRIPPER CLOSED <<<


🔋 Power Supply

The robotic arm can be powered using a 5V USB power bank.

Connect the power bank output to the Arduino through the USB cable.
The servo motors can be powered from the 5V power bank supply.
Connect the GND of the Arduino and servo power supply together.
Use a power bank capable of supplying sufficient current for the Arduino and all servo motors.
Avoid powering multiple high-load servos directly from the Arduino 5V pin.
Power Connection
             🔋 5V USB Power Bank
                    │
              ┌─────┴─────┐
              │           │
          Arduino       Servos
          5V/GND       5V/GND
              │           │
              └─────┬─────┘
                    │
              Common GND

Recommended: Use a good-quality 5V power bank with sufficient current capacity, especially when all four servos are operating simultaneously.

## 📁 Suggested GitHub Structure


Joystick-Robotic-Arm/
│
├── Joystick-Robotic-Arm.ino
├── README.md
├── circuit/
│   └── circuit-diagram.png
├── images/
│   └── robotic-arm.jpg
└── video/
    └── demo.mp4


## 🔮 Future Improvements

Possible upgrades for the project:

* Add more robotic-arm joints
* Add Bluetooth or Wi-Fi control
* Add an automatic pick-and-place mode
* Add object detection using a camera
* Add preset arm positions
* Add potentiometer/encoder-based position feedback
* Add an emergency-stop button
* Add inverse kinematics for automatic movement

## 📌 Project Summary

This project demonstrates how **joysticks, Arduino, and servo motors** can be combined to create a manually controlled robotic arm. The design is suitable for **robotics learning, STEM demonstrations, school projects, and competition prototypes**.

---

### 👨‍💻 Project

**Joystick Controlled Robotic Arm**

**Controller:** Arduino
**Actuators:** Servo Motors
**Input:** Dual Joystick Modules
**Control:** Manual Joystick-Based Movement
