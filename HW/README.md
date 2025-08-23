# Eye-Mass Hardware Design

This directory contains the complete hardware design resources for the **Eye-Mass Board**.

---

## 📂 Contents

### schematic/
- **eye-mass.sch**: KiCad schematic source file
- **eye-mass.pdf**: Exported schematic in PDF format (recommended for quick viewing)
- **block_diagram.png**: High-level hardware block diagram

### pcb/
- **eye-mass.kicad_pcb**: KiCad PCB layout file
- **eye-mass-gerber.zip**: Gerber files for PCB manufacturing
- **bom.csv**: Bill of Materials (BOM), including part numbers and suppliers
- **3d_render_top.png / 3d_render_bottom.png**: 3D renderings of the PCB

### lib/
- **footprints.pretty/**: Custom KiCad footprints
- **symbols/**: Custom schematic symbols

---

## 🛠 Design Notes
- **Toolchain**: Designed with *KiCad 7.0*
- **PCB Stackup**: 6-layer, impedance controlled for high-speed signals (DCMI, FDCAN)
- **Power Domains**: Separated rails for MCU, SDRAM, and motor driver
- **Debugging**: LEDs and USART for system bring-up
- **Expansion**: SDRAM for AI workloads, motor driver for camera positioning

---

## 📑 Recommended Viewing
1. Open `schematic/eye-mass.pdf` for a quick overview of the circuit design.  
2. View `pcb/3d_render_top.png` and `pcb/3d_render_bottom.png` for the PCB layout.  
3. Refer to `bom.csv` for component list and sourcing.
