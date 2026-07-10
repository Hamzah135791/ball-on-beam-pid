# Ball-on-Beam PID Control System  
  
A dual-loop PID control system for stabilizing a ball on a beam using Arduino, featuring cascade control architecture with system identification and data analysis tools.  
  
## Overview  
  
This project implements a ball-on-beam balance system using a DC motor, quadrature encoder, and ultrasonic sensors. The control system uses a dual-loop PID architecture where an outer loop controls ball position and an inner loop controls motor angle.  
  
## Hardware Components  
  
| Component | Description |  
|-----------|-------------|  
| **DC Motor** | Actuator for beam angle control |  
| **Quadrature Encoder** | Provides position feedback (ENCA/ENCB)  |  
| **HC-SR04 Ultrasonic Sensors** | Ball position and reference distance measurement  |  
| **L298N Motor Driver** | H-Bridge for motor control via PWM  |  
  
## Software Architecture  
  
### Firmware (PID.ino)  
  
The main control loop implements:  
  
- **Dual-Loop PID Control**: Outer loop calculates required beam angle, inner loop controls motor position   
- **Anti-windup**: Integral term capped at ±100 to prevent saturation   
- **Dead Zone Compensation**: Minimum PWM of 60 to overcome static friction   
- **Sensor Filtering**: Invalid ultrasonic readings filtered out   
  
### Key Functions  
  
- `readEncoder()`: ISR for quadrature decoding   
- `getFilteredBallReading()`: Filters sensor timeouts   
- `setMotor(dir, pwmVal)`: Low-level motor control   
  
## Data Analysis Tools  
  
### MATLAB System Identification  
  
`kodeballandbeam.m` performs transfer function estimation from experimental data:  
  
- Loads CSV data via file dialog   
- Estimates 2-pole transfer function using `tfest   
- Compares against underdamped (ζ=0.3), critically damped (ζ=1.0), and overdamped (ζ=2.0) responses   
- Calculates step response metrics (rise time, overshoot, settling time)   
  
### Python Data Visualization  
  
`Check_the_Graph.ipynb` processes experimental data:  
  
- Converts TXT data to CSV format   
- Uses columns: `milis` (timestamp), `posisi_target` (setpoint), `posisi_bola` (ball position)   
  
## Data Format  
  
Experimental data files contain:  
- `milis`: Timestamp in milliseconds  
- `posisi_target`: Desired ball position (setpoint)  
- `posisi_bola`: Measured ball position  
  
  
## Hardware Setup  
  
Wiring diagram and 3D design files are available in the repository .
