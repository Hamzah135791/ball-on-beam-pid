## 🎬 System Demonstration & Hardware Design

This section provides a comprehensive visual documentation of the Ball and Beam system, including the software/hardware demonstration, initial 3D CAD modeling, and electrical schematics.

---

### 📹 Video Demonstration

You can watch the fully assembled system stabilizing the ball using the tuned PID controller via the link below:

* 🎥 **[Watch the Live Demonstration Video](https://drive.google.com/file/d/1Ny1G3wwNm1VYaLJH1jfdDQXM5qyiEKa6/view?usp=sharing)**

---

### 📐 Mechanical Design (3D CAD Modeling)

The physical structure of the system was planned using 3D modeling software to ensure structural stability and optimal weight distribution for the balancing mechanism.

#### 1. Isometric View (Early Design)
*Initial concept showing the full integration of the beam, balancing rail, and servo/motor mounting base.*
<img width="1478" height="748" alt="Ball and Beam 3D Design - Isometric View" src="https://github.com/user-attachments/assets/a5dd5728-c1d6-4144-8fce-b34f5ab00e28" />

#### 2. Front View
*Front-facing projection detailing the axis of rotation and the alignment of the sensor track.*
<img width="1478" height="748" alt="Ball and Beam 3D Design - Front View" src="https://github.com/user-attachments/assets/41eb0e59-3c82-4302-beae-bd2010ae4a09" />

#### 3. Top View
*Top-down perspective showcasing the rail clearance and positioning of the ball path.*
<img width="1478" height="748" alt="Ball and Beam 3D Design - Top View" src="https://github.com/user-attachments/assets/5d87c3d9-1e96-415d-9b5c-83f509d56073" />

---

### ⚡ Electrical Wiring Diagram

The diagram below outlines the electrical connection interface between the microcontroller, sensor feedback modules (encoder), motor driver, and power supply layout.

<img width="1080" height="720" alt="Ball and Beam Electrical Wiring Schematic" src="https://github.com/user-attachments/assets/ad602c62-e211-4716-b083-f6ef2150b8a7" />

> 📌 **Note:** Ensure all shared ground pins (GND) are tied together across the microcontroller, sensor modules, and motor drivers to prevent signal noise during high-frequency PID control loops.