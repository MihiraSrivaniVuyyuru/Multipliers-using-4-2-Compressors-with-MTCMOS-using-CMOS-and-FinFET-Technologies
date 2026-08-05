# XOR Gate — CMOS (45nm)

CMOS implementation of a 2-input XOR gate, designed and simulated in **Cadence Virtuoso** at the **45nm** process node. This gate is one of the basic logic building blocks used across the higher-level modules (adders, the 4:2 compressor, and the compressor-based multiplier) in this repository.

## Design

A common transistor-level realization combines complementary pull-up/pull-down networks driven by both true and complemented inputs (A, A', B, B') so the output goes high only when exactly one input is high:
- **Pull-up network:** Conducts for input combinations where A ≠ B.
- **Pull-down network:** Conducts for input combinations where A = B.
- This structure avoids cascading NAND/NOR/inverter stages, giving a more compact and faster XOR compared to a gate-level (multi-stage) implementation — important here since XOR gates form the core of the 4:2 compressor and are heavily replicated in the multiplier.

## Truth Table

| A | B | Y = A⊕B |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

## Files in this Module

| File | Description |
|---|---|
| `Schematic.png` | Transistor-level CMOS schematic |
| `Symbol.png` | Block symbol used for hierarchical instantiation in higher-level modules |
| `Test.png` | Testbench setup used for functional simulation |
| `Waveform.png` | Simulated input/output waveforms verifying XOR gate operation |

## Tool & Technology

- **EDA Tool:** Cadence Virtuoso
- **Simulator:** Spectre
- **Process:** CMOS 45nm

## Usage in This Repository

This XOR gate is part of the `Logic_Gates` module under `01_CMOS/`, and is a core component of the Half Adder, Full Adder, and the XOR-based 4:2 Compressor used in the 4×4/8×8 multiplier with MTCMOS. It mirrors the FinFET XOR gate in the `02_FinFET/` tree, enabling a direct technology comparison.

## Authors

This design is developed as part of an academic project by:

- **Vuyyuru Mihira Srivani**
- **R Naga Sai Harish**
- **S Pranav Sai**
