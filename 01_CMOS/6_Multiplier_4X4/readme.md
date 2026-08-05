# 4×4 Multiplier (4:2 Compressor Based) — CMOS (45nm)

CMOS implementation of a 4×4 array multiplier built using the XOR–MUX based **4:2 compressor** cells from this repository, designed and simulated in **Cadence Virtuoso** at the **45nm** process node.

## Design

The 4×4 multiplier is constructed bottom-up from the modules in this repository:
- **Logic_Gates** (AND, OR, XOR, Inverter) → partial-product generation and compressor sub-gates
- **Half_adder / Full_adder** → intermediate carry/sum stages
- **Mux_2x1** → carry/cout selection within each compressor
- **Compressor_XOR** → 4:2 compressors used to reduce the partial-product rows

Two 4-bit operands are multiplied to produce an 8-bit product, with partial products reduced through the compressor stage rather than a plain ripple-carry adder tree, reducing the critical path length.

## Simulation Results — Power Analysis

| Metric | Value |
|---|---|
| Average Power | 1.96 × 10⁻⁶ W |
| Dynamic Power | 1.95 × 10⁻⁶ W |
| Static Power (Vin = 0) | 1.75 × 10⁻⁹ W |
| Static Power (Vin = 1) | 1.80 × 10⁻⁹ W |

Static (leakage) power stays in the nW range across both input states, while dynamic power dominates overall consumption.

## Files in this Module

| File | Description |
|---|---|
| `Schematic.png` | Transistor/block-level CMOS schematic of the 4×4 multiplier |
| `Symbol.png` | Block symbol used for hierarchical instantiation |
| `Test.png` | Testbench setup used for functional and power simulation |
| `Waveform1.png`, `Waveform2.png` | Functional simulation waveform (product verification) |
|  | Power/timing-related simulation waveform |

## Tool & Technology

- **EDA Tool:** Cadence Virtuoso
- **Simulator:** Spectre
- **Process:** CMOS 45nm

## Usage in This Repository

This module is `Multiplier_4X4` under `01_CMOS/`, the top-level integration of all lower blocks in the CMOS tree. It mirrors the FinFET 4×4 multiplier in the `02_FinFET/` tree for direct technology comparison, and serves as the base design being extended to the 8×8 multiplier (in progress).

## Authors

This design is developed as part of an academic project by:

- **Vuyyuru Mihira Srivani**
- **R Naga Sai Harish**
- **S Pranav Sai**
