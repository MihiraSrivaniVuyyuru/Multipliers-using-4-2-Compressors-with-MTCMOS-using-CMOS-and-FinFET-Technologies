# 2:1 Multiplexer — CMOS (45nm)

CMOS implementation of a 2:1 multiplexer, designed and simulated in **Cadence Virtuoso** at the **45nm** process node. The mux is used for selection/control paths within the higher-level modules in this repository.

## Design

A 2:1 mux selects between two data inputs (I0, I1) based on a select line (S):
- **Y = S' · I0 + S · I1**
- Implemented at the transistor level using pass-transistor logic (complementary NMOS/PMOS pass gates) gated by S and its complement, with an inverter generating S' from S.
- The pass-transistor approach keeps the design compact and fast compared to a fully static gate-level (AND-OR-NOT) implementation.

## Truth Table

| S | I0 | I1 | Y |
|---|---|---|---|
| 0 | 0 | X | 0 |
| 0 | 1 | X | 1 |
| 1 | X | 0 | 0 |
| 1 | X | 1 | 1 |

*(Y = I0 when S = 0, Y = I1 when S = 1)*

## Files in this Module

| File | Description |
|---|---|
| `Schematic.png` | Transistor-level CMOS schematic (pass-transistor mux + inverter) |
| `Symbol.png` | Block symbol used for hierarchical instantiation in higher-level modules |
| `Test.png` | Testbench setup used for functional simulation |
| `Waveform.png` | Simulated input/output waveforms verifying mux selection |

## Tool & Technology

- **EDA Tool:** Cadence Virtuoso
- **Simulator:** Spectre
- **Process:** CMOS 45nm

## Usage in This Repository

This 2:1 mux is part of the `Mux_2x1` module under `01_CMOS/`, and is used for selection/control paths supporting the multiplier design. It mirrors the FinFET 2:1 mux in the `02_FinFET/` tree, enabling a direct technology comparison.

## Authors

This design is developed as part of an academic project by:

- **Vuyyuru Mihira Srivani**
- **R Naga Sai Harish**
- **S Pranav Sai**
