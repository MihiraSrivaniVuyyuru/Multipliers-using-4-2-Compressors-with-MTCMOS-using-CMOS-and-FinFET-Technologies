# 4:2 Compressor (XOR–MUX Based) — FinFET (18nm)

FinFET implementation of a 4:2 compressor, designed and simulated in **Cadence Virtuoso** at the **18nm** process node. Instead of the conventional two-full-adder cascade, this compressor is built using **XOR gates for the Sum path** and **2:1 multiplexers for the Carry paths**, which reduces transistor count and critical-path delay — making it well suited for the partial-product reduction stage of the multiplier.

## Design

**Inputs:** X1, X2, X3, X4, Cin, Win
**Outputs:** Sum, Carry (`carry`), Cout (`ccout`)

- **Sum generation (XOR chain):** The four primary inputs are combined through a cascade of `Logic_Gates` XOR cells — X1⊕X2 and X3⊕X4 are computed first, the two intermediate XOR outputs are combined with `Win`, and the result is XOR-ed with `Cin` to produce the final **Sum**.
- **Carry generation (MUX-based):** Rather than deriving the carry outputs through additional AND/OR logic (as in a full-adder-based compressor), each carry output is produced by a `Mux_2x1` cell, with the select line driven by an intermediate XOR output. This lets the carry bit pass through whichever input is correct for that XOR condition, at a fraction of the transistor cost of a gate-level carry network.
  - **Mux 1** selects between `X3` and `X1` (select driven by the X1⊕X2 XOR stage) to produce `Cout (ccout)`.
  - **Mux 2** selects between `Cin` and `X4` (select driven by `Win`) to produce `Carry`.

This XOR + MUX structure is a well-known low-power/low-transistor-count technique for 4:2 compressors used in high-speed multiplier partial-product reduction trees. Built from FinFET (multi-gate, non-planar) devices, the design benefits from tighter short-channel control and lower leakage than the planar CMOS version, which is particularly relevant at the 18nm node.

## Files in this Module

| File | Description |
|---|---|
| `Schematic.png` | Transistor-level FinFET schematic: XOR chain (Sum path) + two 2:1 muxes (Carry/Cout paths) |
| `Symbol.png` | Block symbol used for hierarchical instantiation in higher-level modules |
| `Test.png` | Testbench setup used for functional simulation |
| `Waveform1.png` | Simulated input/output waveforms verifying Sum, Carry, and Cout |

## Tool & Technology

- **EDA Tool:** Cadence Virtuoso
- **Simulator:** Spectre
- **Process:** FinFET 18nm

## Building Blocks Used

- `Logic_Gates` → XOR gates (Sum generation, mux select lines)
- `Mux_2x1` → Carry and Cout generation

## Usage in This Repository

This compressor is part of the `Compressor_XOR` module under `02_FinFET/`, and is the core reduction cell used in the 4×4/8×8 multiplier with MTCMOS. It mirrors the CMOS compressor in the `01_CMOS/` tree, enabling a direct technology comparison.

## Authors

This design is developed as part of an academic project by:

- **Vuyyuru Mihira Srivani**
- **R Naga Sai Harish**
- **S Pranav Sai**
