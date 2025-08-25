# 📷 STM32H723ZGT6 – Vision & Control Firmware

## 🔎 Overview
This firmware is developed for the **STM32H723ZGT6** based embedded platform.  
The system is designed to capture images of **SMD components inside a box** and perform counting with camera + AI (WIP).  
It integrates **external SDRAM, motor driver, SD card logging, temperature/current sensors, and FDCAN communication**.

---

## ⚙️ Features

- ✅ **SD Card (SDMMC2)**  
  - File creation & logging tested successfully  
  - Stores captured data and sensor logs

- ✅ **SDRAM (IS42S16320F-6BLI)**  
  - JEDEC init sequence implemented  
  - Full memory write/read test completed

- ✅ **Motor Control (A4988)**  
  - Supports speed & distance control  
  - Verified positioning logic for camera movement

- ✅ **Temperature Sensor (AS6221)**  
  - I²C2 interface  
  - Accurate ambient + board temp reading

- ✅ **Current/Voltage Monitor (INA219B)**  
  - I²C3 interface  
  - Real-time bus voltage & shunt current measurement

- ✅ **FDCAN Communication**  
  - I²C4 interface 
  - Protocol layer implemented  
  - Verified with external CAN nodes

- ⏳ **Camera (OV5640 + DCMI DMA)**  
  - Basic bring-up in progress  
  - SDRAM frame buffer prepared  
  - AI-based SMD counting pipeline: **Planned**

---

## 📂 Folder Layout
