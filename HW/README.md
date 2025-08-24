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

## 🧩 Schematic Highlights (as-built)

### 1) MCU — STM32H723ZGT6
![MCU](docs/images/MCU.jpg)
- **Device**: STM32H723ZGT6 
- **Connections**: Debug UART, **ST-Link Mini** (SWD), boot-mode pins, GPIO banks **PA/PB/PC/PD/PE/PF/PG**, external clock **TCXO 12 MHz**, reset circuit  
- **Purpose**: Central control with dedicated debug/boot paths and ample I/O for peripherals

### 2) SDRAM — IS42S16320F-7BL
![SDRAM](docs/images/SDRAM.jpg)
- **Device**: IS42S16320F-7BL  
- **Interface**: **FMC** — DQ0–DQ15, A0–A12, BA0–BA1, **SDNWE/SDNCAS/SDNRAS/SDNE0/SDCKE0/SDCLK**, NBL0/NBL1  
- **Purpose**: External memory to expand capacity for image buffering and lightweight AI execution

### 3) Power
![Power](docs/images/POWER.jpg)
- **Key ICs**: **INA219BxD** (current/voltage monitor), **TPS562201** (buck converter)  
- **Rails**: From **+12 V** input to **+5 V / +3.3 V / +2.8 V / +1.8 V**  
- **Purpose**: Stable multi-rail supply with inline power telemetry for easier power management

### 4) Camera — OV5640
![Camera](docs/images/CAM.jpg)
- **Sensor**: **OV5640**  
- **Interface**: **DCMI** (D0–D7, HSYNC, VSYNC, PIXCLK) + **I²C4** (SCL, SDA)  
- **Power & Control**: **+1.8 V / +2.8 V / +3.3 V** rails, LED control (**Camera_LED**, **FLASH**, **FLASH_PWM**)  
- **Use Case**: Capturing images for tasks like **counting SMD components inside a box**

### 5) FDCAN
![FDCAN](docs/images/FDCAN.jpg)
- **Transceiver**: **MCP2562FD**  
- **Connections**: MCU **FDCAN_Tx3 / FDCAN_Rx3** ↔ bus **CANH/CANL**; includes **120 Ω** termination  
- **Purpose**: Robust CAN communication to external modules/systems

### 6) Temperature — AS6221 ×2
![Temp](docs/images/TEMP.jpg)
- **Sensors**: **AS6221** ×2  
- **Interface**: **I²C2** (SCL, SDA)  
- **Purpose**: Dual-point temperature monitoring (e.g., motor driver and board ambient)

### 7) Motor Driver — A4988
![Motor](docs/images/Motor.jpg)
- **Driver**: **A4988**  
- **Signals**: **STEP, DIR, ENABLE, MS1, MS2, MS3**; outputs **1A/1B/2A/2B**  
- **Purpose**: Stepper control with microstepping configuration for camera positioning

### 8) microSD — SDMMC2
![SD](docs/images/SDCARD.jpg)
- **Interface**: **SDMMC2** — D0–D3, CMD, CLK, INT  
- **Purpose**: Removable storage for images and logs

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
