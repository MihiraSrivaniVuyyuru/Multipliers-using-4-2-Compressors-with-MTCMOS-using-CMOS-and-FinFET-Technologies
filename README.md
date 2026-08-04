# Multipliers-using-4-2-Compressors-with-MTCMOS-using-CMOS-and-FinFET-Technologies
Design and verification of array multipliers built using 4:2 compressors, implemented in **CMOS (45nm)** and **FinFET (18nm)** technologies with **MTCMOS** (Multi-Threshold CMOS) applied for leakage power reduction. All schematics, symbols, testbenches, and waveforms are captured in **Cadence Virtuoso**.

## Overview

This repository documents the bottom-up design flow for building compressor-based multipliers — starting from basic logic gates and going up through half adders, full adders, XOR-based compressors, and 2:1 muxes, before integrating them into a complete multiplier. The same design hierarchy is implemented twice: once in standard CMOS and once in FinFET, to compare performance and power characteristics across technologies. MTCMOS sleep-transistor techniques are layered onto the multiplier stage to cut static leakage power.

## Status

| Module | CMOS (45nm) | FinFET (18nm) |
|---|---|---|
| Logic Gates | ✅ Done | ✅ Done |
| Half Adder | ✅ Done | ✅ Done |
| Full Adder | ✅ Done | ✅ Done |
| 2:1 Mux | ✅ Done | ✅ Done |
| XOR Compressor (4:2) | ✅ Done | ✅ Done |
| 4×4 Multiplier (+ MTCMOS) | ✅ Done | ✅ Done |
| 8×8 Multiplier (+ MTCMOS) | 🚧 In progress | 🚧 In progress |

## Tools & Technology

- **EDA Tool:** Cadence Virtuoso
- **CMOS process node:** 45nm
- **FinFET process node:** 18nm
- **Simulator:** Spectre (schematic-level simulation)
- **Low-power technique:** MTCMOS (sleep-transistor-based power gating)

## Repository Structure

```
├── 1_01_CMOS/
│   ├── Logic_Gates/
│   │   ├── AND/
│   │   ├── Inverter/
│   │   ├── OR/
│   │   ├── XOR/
│   ├── 2_Half_adder/
│   ├── 3_Full_adder/
│   └── 4_Mux_2x1/
│   ├── 5_Compressor_XOR/
│   ├── 6_Multiplier_4X4/
│   │   ├── MTCMOS/
│
├── 02_FinFET/
│   ├── 1_Logic_Gates/
│   │   ├── AND/
│   │   ├── Inverter/
│   │   ├── OR/
│   │   ├── XOR/
│   ├── 2_Half_Adder/
│   ├── 3_Full_Adder/
│   └── 4_Mux_2x1/
│   ├── 5_Compressor_XOR/
│   ├── 6_Multiplier_4X4/
│   │   ├── MTCMOS/
│
└── README.md
```

> Every leaf module (Logic_Gates, Half_adder, Full_adder, Compressor_XOR, Mux_2x1, Multiplier_4X4) follows the same four-file documentation pattern: **Schematic**, **Symbol**, **Test(bench)**, and **Waveform** screenshots, so each block's design and verification can be reviewed independently.

## Design Hierarchy

The multiplier is built bottom-up:

1. **Logic_Gates** — Basic CMOS/FinFET logic gates used as building blocks.
2. **Half_adder / Full_adder** — Adder cells used inside the compressor and partial-product summation stages.
3. **Compressor_XOR** — 4:2 compressor built primarily around XOR-based logic, used to reduce partial-product rows faster than a plain adder tree.
4. **Mux_2x1** — Multiplexers used for control/selection paths within the design.
5. **Multiplier_4X4** — The 4×4 array multiplier integrating the above blocks, with a dedicated **MTCMOS** subfolder containing the power-gated (sleep-transistor) version of the design for leakage reduction analysis.

**8×8 Multiplier (in progress):** extends the same 4:2 compressor + MTCMOS methodology to a larger 8×8 array, in both CMOS and FinFET, following the identical documentation pattern once complete.

## MTCMOS Technique

MTCMOS inserts high-threshold-voltage (high-Vt) sleep transistors in series with the low-Vt logic block, allowing the circuit to be power-gated (cut off from supply) during idle/sleep states. This significantly reduces subthreshold leakage current while preserving the speed advantage of low-Vt devices during active operation. It is applied at the multiplier level in this repository, since that is where leakage impact is most significant given the transistor count.

## Documentation Convention

For each module folder, the four screenshots represent:
- **Schematic.png** — Transistor-level circuit implementation
- **Symbol.png** — Block symbol used for hierarchical instantiation
- **Test.png** — Testbench setup used for simulation
- **Waveform1.png / Waveform2.png** — Simulation output waveforms (functional/timing verification where applicable)

## Authors

This design is developed as part of an academic project by:

Vuyyuru Mihira Srivani
R Naga Sai Harish
S Pranav Sai
