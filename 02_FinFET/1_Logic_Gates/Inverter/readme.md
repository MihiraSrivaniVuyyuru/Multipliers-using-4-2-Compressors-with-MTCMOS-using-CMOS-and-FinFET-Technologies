# Inverter (NOT Gate) — FinFET (18nm)

FinFET implementation of an inverter (NOT gate), designed and simulated in **Cadence Virtuoso** at the **18nm** process node. This is the most fundamental logic gate in the repository and forms the base building block for the NAND/NOR-based derivations of the AND and OR gates, as well as restoring/buffering stages used throughout the higher-level modules.

## Design

A standard FinFET inverter consists of a single P-FinFET and a single N-FinFET:
- **P-FinFET (pull-up):** Source tied to VDD, conducts when input is low, pulling the output high.
- **N-FinFET (pull-down):** Source tied to GND, conducts when input is high, pulling the output low.
- The two devices are never on simultaneously in steady state, giving the inverter its characteristic low static power consumption. FinFET's multi-gate structure gives tighter channel control and lower leakage than the planar CMOS version, which is particularly relevant at the 18nm node.

## Truth Table

| A | Y = A' |
|---|---|
| 0 | 1 |
| 1 | 0 |

## Files in this Module

| File | Description |
|---|---|
| `Schematic.png` | Transistor-level FinFET schematic (single P-FinFET + N-FinFET pair) |
| `Symbol.png` | Block symbol used for hierarchical instantiation in higher-level modules |
| `Test.png` | Testbench setup used for functional simulation |
| `Waveform.png` | Simulated input/output waveforms verifying inverter operation |

## Tool & Technology

- **EDA Tool:** Cadence Virtuoso
- **Simulator:** Spectre
- **Process:** FinFET 18nm

## Usage in This Repository

This inverter is part of the `Logic_Gates` module under `02_FinFET/`. It is used directly as a standalone gate and also as the output stage for the AND (NAND + inverter) and OR (NOR + inverter) gates, as well as within the Half Adder, Full Adder, XOR-based 4:2 Compressor, and multiplier designs. It mirrors the CMOS inverter in the `01_CMOS/` tree, enabling a direct technology comparison.

## Authors

This design is developed as part of an academic project by:

- **Vuyyuru Mihira Srivani**
- **R Naga Sai Harish**
- **S Pranav Sai**
