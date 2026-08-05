# AND Gate — FinFET (18nm)

FinFET implementation of a 2-input AND gate, designed and simulated in **Cadence Virtuoso** at the **18nm** process node. This gate is one of the basic logic building blocks used across the higher-level modules (adders, compressors, multiplexers, and the compressor-based multiplier) in this repository.

## Design

As in the CMOS version, the AND function is realized as a NAND gate followed by an inverter, but built using FinFET (multi-gate, non-planar) devices instead of planar MOSFETs:
- **NAND stage:** P-FinFETs in parallel, N-FinFETs in series — pull-up network conducts if either input is low, pull-down network conducts only if both inputs are high.
- **Inverter stage:** Restores the correct AND logic at the output and drives the following stage.
- FinFET devices offer better short-channel control (reduced leakage, improved sub-threshold slope) compared to the planar CMOS devices used in the 45nm version, which becomes especially relevant at the 18nm node.

## Truth Table

| A | B | Y = A·B |
|---|---|---|
| 0 | 0 | 0 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 1 |

## Files in this Module

| File | Description |
|---|---|
| `Schematic.png` | Transistor-level FinFET schematic (NAND + inverter) |
| `Symbol.png` | Block symbol used for hierarchical instantiation in higher-level modules |
| `Test.png` | Testbench setup used for functional simulation |
| `Waveform.png` | Simulated input/output waveforms verifying AND gate operation |

## Tool & Technology

- **EDA Tool:** Cadence Virtuoso
- **Simulator:** Spectre
- **Process:** FinFET 18nm

## Usage in This Repository

This AND gate is part of the `Logic_Gates` module under `02_FinFET/`, and feeds into the design of higher-level blocks (Half Adder, Full Adder, XOR-based 4:2 Compressor) used in the 4×4/8×8 multiplier with MTCMOS. It mirrors the CMOS AND gate in the `01_CMOS/` tree, enabling a direct technology comparison.

## Authors

This design is developed as part of an academic project by:

- **Vuyyuru Mihira Srivani**
- **R Naga Sai Harish**
- **S Pranav Sai**
