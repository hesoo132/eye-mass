# Eye-Mass Firmware

![MCU](https://img.shields.io/badge/MCU-STM32H723-1f6feb?style=flat-square&logo=stmicroelectronics&logoColor=white)
![Toolchain](https://img.shields.io/badge/Toolchain-STM32CubeIDE-0ea5e9?style=flat-square&logo=eclipseide&logoColor=white)
![Storage](https://img.shields.io/badge/Storage-SDMMC2%20%2B%20FatFs-10b981?style=flat-square)
![Status](https://img.shields.io/badge/Status-WIP-f59e0b?style=flat-square)

Firmware snapshot for the **Eye-Mass** board (**STM32H723ZGTx**).  
This build focuses on **microSD bring-up** and a **1 MiB write/read speed test** via **SDMMC2 + FatFs**, with UART logging and status LEDs.

> Headers for **INA219**, **AS6221**, **OV5640** are included; their runtime code is currently commented out in this test.
>
> SDRAM isn’t used in this build.

---

## 🔎 Overview

- **Clock (this build)**: **HSI → PLL** (see `SystemClock_Config`), MCO1 outputs **HSI**  
- **Storage**: microSD via **SDMMC2**, filesystem via **FatFs**  
- **Logging**: `printf` retargeted to **USART1** (`115200-8-N-1`)  
- **Status LEDs**: **PC11 = OK**, **PC12 = ERR**

**Runtime flow**
1. Initialize clocks/peripherals  
2. Mount SD card → create a one-shot text file `0:/HeBoSuGi.txt`  
3. Run **speed test** on `0:/speed.bin` (1 MiB) using a 4 KiB I/O buffer  
4. Print write/read kB/s to UART, set LED OK/ERR accordingly  
5. Repeat the speed test every **5 s**

---

## 🧭 System Diagram (FW)

```mermaid
flowchart LR
    CPU[STM32H723] -->|printf| UART[USART1 115200]
    CPU -->|FatFs| SD[(microSD via SDMMC2)]
    CPU --> LEDS[LED OK(PC11) / LED ERR(PC12)]
    subgraph Staged (next builds)
      SDRAM[(SDRAM)] & CAM[OV5640 via DCMI]
      PWR[INA219] & TEMP[AS6221 x2]
    end
