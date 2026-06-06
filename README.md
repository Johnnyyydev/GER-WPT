# GER-WPT: Non-Hermitian PT-Symmetric Wireless Power Transfer Simulator

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Rust](https://img.shields.io/badge/Rust-1.95-orange.svg)](https://www.rust-lang.org/)

An advanced, quantum-inspired mathematical simulation engine that models **Dynamic Wireless Power Transfer (DWPT)** for Electric Vehicles (EVs) using **Parity-Time (PT) Symmetry** and **Exceptional Point (EP) resonance tracking**. 

This repository models a solution to the primary industry bottleneck in dynamic highway charging: the dramatic efficiency drops caused by coil misalignment and phase tuning lag.

---

## ⚡ The Core Problem

Standard dynamic wireless charging systems rely on classic fixed RLC resonance. When an EV drives over the transmitter pad:
1. **Misalignment Offset**: Even a small alignment shift (10cm - 30cm) detunes the system, causing the efficiency to drop from **90% to below 5%**.
2. **Controller Latency**: Software-based Phase-Locked Loops (PLLs) introduce a tracking lag (>50ms). At highway speeds (60 km/h), this latency causes the charger to operate off-resonance, dropping net power transfer to **0.00%**.

---

## 🚀 The GER PT-Symmetric Solution

By modeling a **non-Hermitian Hamiltonian coupling loop** with balanced gain ($+\gamma$) and loss ($-\gamma$), the system automatically locks onto the **Exceptional Point** resonant frequency. The system self-tunes physically and near-instantaneously (<1ms) to spatial variations.

### Static Misalignment Simulation:
*   **Standard Resonant RLC**: Power decays exponentially with the square of the offset distance.
*   **GER PT-Symmetry**: Power remains locked on a flat plateau at **94.0% efficiency** up to a 30cm lateral offset (**94x advantage** over standard models).

---

## 📊 Simulation Datasets & Results

### 1. Static Alignment Test:

| Offset Displacement | Standard RLC Efficiency | GER PT-Symmetric Efficiency | Performance Advantage |
| :--- | :---: | :---: | :---: |
| **0 cm** (Aligned) | 94.0% | **94.0%** | 1.0x |
| **10 cm** (Slight offset) | 17.8% | **94.0%** | **5.3x** |
| **20 cm** (Average offset) | 3.4% | **94.0%** | **28.0x** |
| **30 cm** (Major offset) | 0.6% | **94.0%** | **94.0x** |
| **40 cm** (Extreme offset) | 0.1% | **41.9%** | **41.9x** |

### 2. Dynamic Transit Test (2.0s sweep over the coil):
*   **10 km/h Transit**: GER-PT transfers **6.58 kJ** of net energy (5.54x advantage over classic PLL).
*   **30 km/h Transit**: GER-PT transfers **2.07 kJ** of net energy (12.92x advantage).
*   **60 km/h Transit**: Classic PLL trackers drop to **0.00% efficiency** due to lag. GER-PT successfully transfers **0.94 kJ** of net energy.

Detailed JSON data is available in:
*   `wpt_simulation_results.json`
*   `wpt_transient_results.json`

---

## 📊 Accessing the Simulator & Datasets

### 1. Raw Simulation Outputs
The raw simulation datasets are open and available directly in this repository for academic and engineering verification:
*   `wpt_simulation_results.json` (Static alignment sweeps)
*   `wpt_transient_results.json` (Dynamic highway transit sweeps)

These files can be parsed using standard JSON tools (such as Python's `json` and `pandas` libraries) to plot the PT-symmetric efficiency curves.

### 2. Simulation Engine Access
The underlying Rust simulation engine binaries (`wpt-simulator` and `wpt-transient-simulator`) and source code are proprietary. 

Qualified academic researchers, automotive OEMs, and infrastructure developers can request access to the simulator executables or source code under a standard Non-Disclosure Agreement (NDA). Please refer to the **Commercial Licensing** section below.

---

## 🔒 Commercial Licensing & Proprietary Logic

The files in this repository demonstrate the mathematical modeling and physics verification of the system. 

The **real-time adaptive microcontroller algorithm** that executes the high-speed (<1ms) Exceptional Point tracking on active power electronic switchboards is proprietary and kept confidential.

For licensing agreements, technical deep-dives, or commercial pilot inquiries, please contact us. All discussions are subject to a standard **Non-Disclosure Agreement (NDA)**.

---

## 📖 Theoretical References
*   Assawaworrarit, S. et al. *Robust wireless power transfer using a symmetric parity-time-symmetric circuit.* **Nature** 546, 387–390 (2017).
*   Assawaworrarit, S. et al. *Robust wireless power transfer to a moving object.* **Nature Electronics** 3, 273–279 (2020).
