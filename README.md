# Ball Throwing Robot using VEX 🤖⚾

This project implements a **ball throwing / mobile robot** using the **VEX Robotics Kit**, programmed in **ROBOTC**.  
The robot is controlled using a **VEX joystick controller**, enabling real-time motor control for movement and actuation.

The repository contains multiple ROBOTC scripts demonstrating **different drive control mappings** using joystick channels.

---

## 🧰 Software Requirements

- **ROBOTC**
  - Used to program VEX Cortex-based robots
  - Required for compiling and uploading code to the robot

> Ensure ROBOTC is properly licensed and configured for VEX hardware.

---

## 🔩 Hardware Requirements

- **VEX Robotics Kit**
- **VEX Cortex Microcontroller**
- **VEX 393 Motors**
- **VEX Joystick Controller**
- Motor Controller Modules (MC29)
- Power Distribution and Batteries
- Mechanical setup for **ball throwing mechanism**

---

## 🎮 Controller Reference

Joystick channels used in the project:
- `Ch1` – Right joystick (X-axis)
- `Ch2` – Right joystick (Y-axis)
- `Ch3` – Left joystick (Y-axis)
- `Ch4` – Left joystick (X-axis)

---

## 📂 Code Overview

### 🔹 Script 1: Holonomic / Mixed Drive Control

This script combines multiple joystick channels to control four motors, allowing **complex movement patterns**.

```c
#pragma config(Motor,  port5,  LeftFrontMotor,  tmotorVex393_MC29, openLoop, reversed)
#pragma config(Motor,  port7,  LeftBackMotor,   tmotorVex393_MC29, openLoop, reversed)
#pragma config(Motor,  port4,  RightBackMotor,  tmotorVex393_MC29, openLoop, reversed)
#pragma config(Motor,  port6,  RightFrontMotor, tmotorVex393_MC29, openLoop, reversed)

task main()
{
	while(1 == 1)
	{
		motor[LeftFrontMotor]  = vexRT[Ch2] + vexRT[Ch1] + vexRT[Ch4];
		motor[LeftBackMotor]   = vexRT[Ch2] - vexRT[Ch1] + vexRT[Ch4];
		motor[RightBackMotor]  = (-vexRT[Ch2]) + vexRT[Ch1] + vexRT[Ch4];
		motor[RightFrontMotor] = (-vexRT[Ch2]) - vexRT[Ch1] + vexRT[Ch4];
	}
}
```
Features:

-Multi-axis joystick mixing
-Smooth directional control
-Suitable for omnidirectional or experimental drive setups

###🔹 Script 2: Independent Motor Control
This script maps individual joystick channels directly to motors, useful for testing or simple drive configurations.

```c
#pragma config(Motor,  port5, bottom_right, tmotorVex393_MC29, openLoop)
#pragma config(Motor,  port6, bottom_left,  tmotorVex393_MC29, openLoop)
#pragma config(Motor,  port7, top_right,    tmotorVex393_MC29, openLoop)
#pragma config(Motor,  port8, top_left,     tmotorVex393_MC29, openLoop)

task main()
{
	while(1 == 1)
	{
		motor[bottom_right] = vexRT[Ch2];
		motor[top_right]    = vexRT[Ch1];
		motor[bottom_left]  = vexRT[Ch3];
		motor[top_left]     = vexRT[Ch4];
	}
}
```
Features:

-One joystick channel per motor
-Ideal for debugging and motor testing
-Simple and intuitive control logic

##▶️ How to Run

- Open ROBOTC
- Create a new ROBOTC project
- Copy any script into the editor
- Configure motors using the ROBOTC Motor Configuration Wizard
- Connect VEX Cortex via USB
- Compile and download the program
- Power on the robot and use the joystick controller

## 🎥 Reference Video
A demonstration of the VEX controller interface and joystick usage can be found here:
Video_link for reference to interface controller and joystick: https://youtu.be/4xXx3QsU78w

## 🛠️ Troubleshooting

-Ensure motor ports match physical wiring
-Verify joystick is paired with the Cortex
-Check motor direction (reversed) if movement is inverted
-Confirm ROBOTC platform type is set to VEX Cortex

## 📜 License
This project is intended for educational and academic use.
You may modify and extend the code as needed.

## 👤 Author
- Shakthibala
- Robotics | Embedded Systems | VEX Robotics | Control Systems

---

If you want next, I can:
- Add **block diagrams** (drive + throwing mechanism)
- Convert this to a **portfolio-ready project**
- Explain **why joystick mixing works mathematically**
- Clean up and **optimize the control logic**

Just tell me 👍

