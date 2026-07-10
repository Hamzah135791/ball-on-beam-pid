# Ball-on-Beam PID Control System  
  
A dual-loop PID control system for stabilizing a ball on a beam using Arduino, featuring cascade control architecture with system identification and data analysis tools.  
  
## Overview  
  
This project implements a ball-on-beam balance system using a DC motor, quadrature encoder, and ultrasonic sensors. The control system uses a dual-loop PID architecture where an outer loop controls ball position and an inner loop controls motor angle [1](#2-0) .  
  
## Hardware Components  
  
| Component | Description |  
|-----------|-------------|  
| **DC Motor** | Actuator for beam angle control |  
| **Quadrature Encoder** | Provides position feedback (ENCA/ENCB) [2](#2-1)  |  
| **HC-SR04 Ultrasonic Sensors** | Ball position and reference distance measurement [3](#2-2)  |  
| **L298N Motor Driver** | H-Bridge for motor control via PWM [4](#2-3)  |  
  
## Software Architecture  
  
### Firmware (PID.ino)  
  
The main control loop implements:  
  
- **Dual-Loop PID Control**: Outer loop calculates required beam angle, inner loop controls motor position [1](#2-0)   
- **Anti-windup**: Integral term capped at ±100 to prevent saturation [5](#2-4)   
- **Dead Zone Compensation**: Minimum PWM of 60 to overcome static friction [6](#2-5)   
- **Sensor Filtering**: Invalid ultrasonic readings filtered out [7](#2-6)   
  
### Key Functions  
  
- `readEncoder()`: ISR for quadrature decoding [8](#2-7)   
- `getFilteredBallReading()`: Filters sensor timeouts [7](#2-6)   
- `setMotor(dir, pwmVal)`: Low-level motor control [9](#2-8)   
  
## Data Analysis Tools  
  
### MATLAB System Identification  
  
`kodeballandbeam.m` performs transfer function estimation from experimental data:  
  
- Loads CSV data via file dialog [10](#2-9)   
- Estimates 2-pole transfer function using `tfest` [11](#2-10)   
- Compares against underdamped (ζ=0.3), critically damped (ζ=1.0), and overdamped (ζ=2.0) responses [12](#2-11)   
- Calculates step response metrics (rise time, overshoot, settling time) [13](#2-12)   
  
### Python Data Visualization  
  
`Check_the_Graph.ipynb` processes experimental data:  
  
- Converts TXT data to CSV format [14](#2-13)   
- Uses columns: `milis` (timestamp), `posisi_target` (setpoint), `posisi_bola` (ball position) [15](#2-14)   
  
## Data Format  
  
Experimental data files contain:  
- `milis`: Timestamp in milliseconds  
- `posisi_target`: Desired ball position (setpoint)  
- `posisi_bola`: Measured ball position  
  
  
## Hardware Setup  
  
Wiring diagram and 3D design files are available in the repository [17](#2-16) .