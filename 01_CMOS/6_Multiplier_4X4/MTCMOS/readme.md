# 4×4 Multiplier with MTCMOS — CMOS (45nm)

MTCMOS (Multi-Threshold CMOS) version of the 4×4 array multiplier, built on top of the base `Multiplier_4X4` CMOS design in this repository. High-Vt sleep transistors are inserted to power-gate the multiplier during idle states, targeting a reduction in static leakage power while preserving active-mode speed. Designed and simulated in **Cadence Virtuoso** at the **45nm** process node.

## Design

This version reuses the same 4:2 compressor-based multiplier architecture as the base `Multiplier_4X4` module — built from `Logic_Gates`, `Half_adder`/`Full_adder`, `Mux_2x1`, and `Compressor_XOR` cells — with the addition of an MTCMOS sleep-transistor stage:

- **High-Vt sleep transistors** (PMOS header and/or NMOS footer, depending on implementation) are placed in series between the multiplier's low-Vt logic block and the supply rails.
- A **sleep control signal** turns the sleep transistor off during idle periods, cutting the leakage path through the low-Vt logic entirely.
- During active operation, the sleep transistor is on, and the circuit behaves like the standard low-Vt multiplier with minimal added delay.

## Simulation Results — Power Analysis

| Metric | Value |
|---|---|
| Average Power | 2.179 × 10⁻⁶ W |
| Dynamic Power | 2.158 × 10⁻⁶ W |
| Static Power (Vin = 0) | 1.79 × 10⁻⁹ W |
| Static Power (Vin = 1) | 3.9 × 10⁻¹² W |

At Vin = 1 (sleep transistor cutting off the leakage path), static power drops to the pW range — a significant reduction compared to the Vin = 0 case, demonstrating the leakage-suppression benefit of the MTCMOS technique.

## Files in this Module

| File | Description |
|---|---|
| `Schematic.png` | Transistor-level CMOS schematic with MTCMOS sleep transistors added |
| `Symbol.png` | Block symbol used for hierarchical instantiation |
| `Test.png` | Testbench setup used for functional and power simulation |
| `Waveform1.png`, `Waveform2.png` | Functional simulation waveform (product verification) |

## Tool & Technology

- **EDA Tool:** Cadence Virtuoso
- **Simulator:** Spectre
- **Process:** CMOS 45nm
- **Low-power technique:** MTCMOS (sleep-transistor power gating)

## Usage in This Repository

This design is the `MTCMOS` sub-module within `Multiplier_4X4` under `01_CMOS/`, and provides a direct leakage-power comparison against the base (non-MTCMOS) 4×4 multiplier in the same folder.

## Authors

This design is developed as part of an academic project by:

- **Vuyyuru Mihira Srivani**
- **R Naga Sai Harish**
- **S Pranav Sai**
