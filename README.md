
# Optimized Power Supply & Battery Management System (ICS)

## Overview

This project is an optimized, high-efficiency **Power Management and Multi-Cell Battery Protection System** designed for Industrial Control Systems (ICS) and embedded hardware architectures. The system integrates a **5V Step-Down Switching Regulator**, an **Integrated Li-Ion/LiPo Charger Power Management IC (PMIC)**, and a dedicated **Multi-Cell Battery Monitor & Protection IC** to deliver reliable power regulation, fault protection, and uninterrupted system operation.

---

## Technical Specifications & Architecture

### 1. Buck DC-DC Voltage Regulator (`U1`: LM2596S-5)

* **Function:** High-efficiency step-down DC-DC conversion supplying a stable 5V system rail.
* **Key Components:**
* **Inductor (`L1`):** $33\,\mu\text{H}$ power inductor optimized for switching output ripple filtering.
* **Catch Diode (`D1`):** SS54 Schottky diode for efficient freewheeling action.
* **Capacitors (`C1`, `C2`):** $680\,\mu\text{F}$ input bulk capacitor and $220\,\mu\text{F}$ output smoothing capacitor.



### 2. Power Management & Charger IC (`U2`: IP2326)

* **Function:** Integrated power-path management and lithium battery charging controller.
* **Key Features:**
* **Power Inductor (`L2`):** $2.2\,\mu\text{H}$ low-DCR inductor for high-efficiency charge buck/boost stages.
* **Decoupling/Filter Network:** Output and input ceramic filter capacitors (`C3`, `C5`, `C6` — $10\,\mu\text{F}$ / $22\,\mu\text{F}$).
* **Thermal Monitoring:** External NTC thermistor interface (`TH1` - $100\text{k}\Omega$) for battery over-temperature protection.
* **Status Indication:** Integrated LED indicator (`LED3` / KPT-1608EC) for charging status output.



### 3. Multi-Cell Battery Protection & Monitoring (`U3`: BQ7791500PWR)

* **Function:** Advanced hardware protection for multi-cell Lithium-ion/LiFePO4 battery packs.
* **Key Features:**
* **Cell Balancing & Sensing:** Multi-channel cell tap connections (`VC0`–`VC5`) paired with filter RC networks (`R10`–`R12`, `C10`–`C13`).
* **Charge/Discharge Protection MOSFETs:** Dual high-side/low-side N-channel MOSFET switching control (`Qchg1` & `Qdis1` - IRLR7843TRPBF) driven by high-voltage gate circuitry.
* **Current Sensing:** Low-resistance high-precision current sense resistor (`RCS1` - CRA2512 series) for overcurrent and short-circuit protection.
* **Thermal Sensing:** Onboard NTC thermistor input (`TH3` - $10\text{k}\Omega$) for cell-level temperature monitoring.



### 4. Input/Output Interfaces & Protection

* **Connectors:**
* `J1`: DC Barrel Jack input ($54\text{-}00133$).
* `J2`: Screw terminal output header ($1\times2$).
* `J3`: Multi-pin screw terminal block for battery pack tap/connection interfaces (`B+`, `B-`, `PACK+`, `PACK-`).


* **Overcurrent Protection:** Inline board-level input/output protection fuse (`F1`).
* **Tactile Control Switches:** Push buttons (`S1`, `S2`, `S3`, `S4` - EVP-BB1AAB000) for system control/wake function.
* **Status Indicators:** Diagnostics LEDs (`LED1`, `LED2` - KP-1608SGC) with current-limiting resistors (`R17`, `R22`).

---

## PCB Design & Layout Details

* **Board Type:** 2-Layer High-Density Interconnect PCB.
* **Top Layer:** Signal routing, IC power pads, switching nodes (`LX`, `SW`), and ground copper pouring for optimal thermal dissipation.
* **Bottom Layer:** Solid ground plane return paths and secondary trace routing.
* **Thermal Management:** Exposed thermal ground pads with dense via arrays under `U1`, `U2`, and `U3` to sink heat across layers.
* **High-Current Paths:** Widened power traces for input voltage rails, ground pads, and MOSFET drain/source connections to minimize $I^2R$ conduction losses.

---

```text
├── Hardware/
│   ├── Schematic/
│   │   └── Power Circuit.kicad_sch
│   ├── Layout/
│   │   ├── PCB top layer.png
│   │   ├── PCB bottom layer.png
│   │   └── Power Circuit.kicad_pcb
│   └── Gerber/
│       └── Gerber_Files.zip
├── Docs/
│   └── PCB Schematic.png
├── LICENSE
└── README.md

```
