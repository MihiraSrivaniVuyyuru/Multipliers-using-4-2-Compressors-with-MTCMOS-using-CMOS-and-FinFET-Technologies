# Half Adder — FinFET (18nm)

FinFET implementation of a half adder, designed and simulated in **Cadence Virtuoso** at the **18nm** process node. The half adder is the first arithmetic building block in this repository, combining the basic logic gates into a functional 1-bit adder cell used in the Full Adder, the XOR-based 4:2 Compressor, and ultimately the multiplier.

## Design

A half adder combines two inputs (A, B) into a Sum and Carry output using two logic gates:
- **Sum = A ⊕ B** — implemented using the FinFET XOR gate.
- **Carry = A · B** — implemented using the FinFET AND gate (NAND + inverter).

Both sub-gates are instantiated from the `Logic_Gates` module and connected at the schematic level to form the half adder cell. The FinFET devices' multi-gate structure gives tighter channel control and lower leakage than the planar CMOS version, which is particularly relevant at the 18nm node.

## Truth Table

| A | B | Sum | Carry |
|---|---|---|---|
| 0 | 0 | 0 | 0 |
| 0 | 1 | 1 | 0 |
| 1 | 0 | 1 | 0 |
| 1 | 1 | 0 | 1 |

## Files in this Module

| File | Description |
|---|---|
| `Schematic.png` | Transistor-level FinFET schematic (XOR + AND gates) |
| `Symbol.png` | Block symbol used for hierarchical instantiation in higher-level modules |
| `Test.png` | Testbench setup used for functional simulation |
| `Waveform.png` | Simulated input/output waveforms verifying Sum and Carry outputs |

## Tool & Technology

- **EDA Tool:** Cadence Virtuoso
- **Simulator:** Spectre
- **Process:** FinFET 18nm

## Usage in This Repository

This half adder is part of the `Half_Adder` module under `02_FinFET/`, and is used as a building block within the Full Adder and the XOR-based 4:2 Compressor stages of the 4×4/8×8 multiplier with MTCMOS. It mirrors the CMOS half adder in the `01_CMOS/` tree, enabling a direct technology comparison.

## Authors

This design is developed as part of an academic project by:

- **Vuyyuru Mihira Srivani**
- **R Naga Sai Harish**
- **S Pranav Sai**
