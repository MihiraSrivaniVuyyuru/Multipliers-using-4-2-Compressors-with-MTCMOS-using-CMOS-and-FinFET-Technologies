# 4×4 Multiplier (4:2 Compressor Based) — FinFET (18nm)

FinFET implementation of a 4×4 array multiplier built using the XOR–MUX based **4:2 compressor** cells from this repository, designed and simulated in **Cadence Virtuoso** at the **18nm** process node.

## Design

The 4×4 multiplier is constructed bottom-up from the modules in this repository:
- **Logic_Gates** (AND, OR, XOR, Inverter) → partial-product generation and compressor sub-gates
- **Half_Adder / Full_Adder** → intermediate carry/sum stages
- **Mux_2x1** → carry/cout selection within each compressor
- **Compressor_XOR** → 4:2 compressors used to reduce the partial-product rows

Two 4-bit operands are multiplied to produce an 8-bit product, with partial products reduced through the compressor stage rather than a plain ripple-carry adder tree, reducing the critical path length. FinFET's multi-gate structure gives tighter short-channel control than the planar CMOS devices used in the 45nm version, which becomes relevant at the 18nm node.

## Simulation Results — Power Analysis

| Metric | Value |
|---|---|
| Average Power | 7.738 × 10⁻⁶ W |
| Dynamic Power | 7.49 × 10⁻⁶ W |
| Static Power (Vin = 0) | 1.369 × 10⁻⁶ W |
| Static Power (Vin = 1) | 1.29 × 10⁻⁶ W |

## Files in this Module

| File | Description |
|---|---|
| `Schematic.png` | Transistor/block-level FinFET schematic of the 4×4 multiplier |
| `Symbol.png` | Block symbol used for hierarchical instantiation |
| `Test.png` | Testbench setup used for functional and power simulation |
| `Waveform1.png`, `Waveform2.png` | Functional simulation waveform (product verification) |

## Tool & Technology

- **EDA Tool:** Cadence Virtuoso
- **Simulator:** Spectre
- **Process:** FinFET 18nm

## Usage in This Repository

This module is `Multiplier_4X4` under `02_FinFET/`, the top-level integration of all lower blocks in the FinFET tree. It mirrors the CMOS 4×4 multiplier in the `01_CMOS/` tree for direct technology comparison, and serves as the base design being extended to the 8×8 multiplier (in progress).

## Authors

This design is developed as part of an academic project by:

- **Vuyyuru Mihira Srivani**
- **R Naga Sai Harish**
- **S Pranav Sai**
