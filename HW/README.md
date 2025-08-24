# Eye-Mass Hardware Design

## 🔎 Overview
The **Eye-Mass Board** is a custom embedded platform designed for **camera-based vision tasks and AI experimentation**.  
It integrates an OV5640 camera, external SDRAM, motor driver, and multiple debug/monitoring features.

---

## 📸 PCB Overview
| Top View | Bottom View |
|----------|-------------|
| ![Top](docs/images/eye-mass-F.png) | ![Bottom](docs/images/eye-mass-B.png) |

---

## 📑 Design Resources

- **Schematics**: [eye-mass.pdf](eye-mass.pdf) (PDF for quick view)
    
---

## 🔧 Key Hardware Notes
- **EDA Tool**: KiCad 7.0  
- **PCB Stackup**: 6-layer, impedance-controlled for high-speed (DCMI, FDCAN)  
- **Memory**: External SDRAM for real-time image buffering + AI workloads  
- **Camera**: OV5640 with DCMI interface for capturing and analysis  
- **Motor Driver**: Enables camera positioning to capture full target area  
- **Debugging**: LEDs + USART interface  
- **Monitoring**: Temperature and current/voltage sensing  

---

## 🧩 Schematic Highlights

**Power & Regulation**
![POWER](docs/images/POWER.jpg)
- Input regulation and rails distribution
- Decoupling strategy near MCU/SDRAM and camera

**SDRAM Interface**
![SDRAM](docs/images/SDRAM.jpg)
- External SDRAM for high-resolution frame buffers & lightweight AI
- Address/data bus, clocking, and timing-critical routing considerations

**Camera (OV5640) Interface**
![Camera](docs/images/CAM.jpg)
- DCMI data lines + PCLK/VSYNC/HSYNC, I²C control
- MCLK generation and connector/pinout

**Motor Driver**
![Motor](docs/images/Motor.jpg)
- Motor driver power path & control signals
- Enables camera positioning to capture the full scene

**Telemetry (Temp / Current / Voltage)**
![Telemetry](docs/images/TEMP.jpg)
- Temperature sensing for motor driver & board
- Power monitoring for bring-up/debug safety

**Communications (FDCAN)**
![FDCAN](docs/images/FDCAN.jpg)
- FDCAN interface to external systems
- USART for debug logging & firmware bring-up

---

## ✅ Progress
- [x] Schematics completed  
- [x] PCB prototype (Rev. A) fabricated  
- [x] SDRAM bring-up (partial validation ongoing)  
- [ ] Camera interface bring-up (OV5640)  
- [x] Motor driver test & positioning control  
- [x] Communication tests (FDCAN / USART)  

---

## 📂 Folder Layout
