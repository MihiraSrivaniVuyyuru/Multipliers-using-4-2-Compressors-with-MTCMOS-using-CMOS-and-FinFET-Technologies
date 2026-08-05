# Full Adder — CMOS (45nm)

CMOS implementation of a full adder, designed and simulated in **Cadence Virtuoso** at the **45nm** process node. The full adder extends the half adder to handle a carry-in, making it the core 1-bit arithmetic cell used to build the XOR-based 4:2 Compressor and the compressor-based multiplier.

## Design

A full adder combines three inputs (A, B, Cin) into a Sum and Carry-out, built from two half adders and an OR gate:
- **Sum = A ⊕ B ⊕ Cin** — computed by cascading two CMOS half adders (XOR stages).
- **Cout = (A · B) + (Cin · (A ⊕ B))** — computed by combining the carry outputs of both half adders through a CMOS OR gate.

All sub-blocks (XOR, AND, OR gates and the half adder cell) are instantiated from the `Logic_Gates` and `Half_adder` modules and connected at the schematic level to form the full adder.

## Truth Table

| A | B | Cin | Sum | Cout |
|---|---|---|---|---|
| 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 1 | 0 |
| 0 | 1 | 0 | 1 | 0 |
| 0 | 1 | 1 | 0 | 1 |
| 1 | 0 | 0 | 1 | 0 |
| 1 | 0 | 1 | 0 | 1 |
| 1 | 1 | 0 | 0 | 1 |
| 1 | 1 | 1 | 1 | 1 |

## Files in this Module

| File | Description |
|---|---|
| `Schematic.png` | Transistor-level CMOS schematic (two half adders + OR gate) |
| `Symbol.png` | Block symbol used for hierarchical instantiation in higher-level modules |
| `Test.png` | Testbench setup used for functional simulation |
| `Waveform.png` | Simulated input/output waveforms verifying Sum and Carry-out |

## Tool & Technology

- **EDA Tool:** Cadence Virtuoso
- **Simulator:** Spectre
- **Process:** CMOS 45nm

## Usage in This Repository

This full adder is part of the `Full_adder` module under `01_CMOS/`, and is a core component of the XOR-based 4:2 Compressor used in the 4×4/8×8 multiplier with MTCMOS. It mirrors the FinFET full adder in the `02_FinFET/` tree, enabling a direct technology comparison.

## Authors

This design is developed as part of an academic project by:

- **Vuyyuru Mihira Srivani**
- **R Naga Sai Harish**
- **S Pranav Sai**
