# 1:4 DEMUX Using Transmission Gate Logic

A transistor-level 1:4 Demultiplexer designed and verified in CMOS technology, built as part of the Principles of Digital VLSI course (BEC606) at The National Institute of Engineering, Mysuru

## Overview

A 1:4 Demultiplexer (DEMUX) routes a single input signal to one of four output lines based on select-line inputs. This project implements the DEMUX entirely at the **transistor level** using PMOS and NMOS devices arranged as CMOS **transmission gates**, rather than using pre-built logic gate primitives — offering direct insight into switching behavior, signal routing, and CMOS design at the device level. Transmission gate logic is used because it offers a good balance between functionality, speed, and area.

## Objectives

- Design a 1:4 DEMUX circuit using MOSFETs
- Implement the DEMUX using transmission gate logic
- Verify correct signal routing based on select inputs
- Analyze switching behavior of the DEMUX circuit
- Perform pre-layout simulation and waveform verification

## Circuit Description

**Signals**

| Signal | Description |
|---|---|
| `D` (IN) | Input signal |
| `S0`, `S1` | Select lines |
| `Y0`–`Y3` | Output lines |

The transmission gate logic network routes the input signal to exactly one output line at a time, determined by the combination of `S0` and `S1`, while all other outputs remain inactive.

| S1 | S0 | Active Output |
|---|---|---|
| 0 | 0 | Y0 |
| 0 | 1 | Y1 |
| 1 | 0 | Y2 |
| 1 | 1 | Y3 |

## Design Flow

1. **Schematic Design** — Transistor-level CMOS DEMUX cell built using PMOS/NMOS devices in Cadence Virtuoso.

<img width="812" height="556" alt="image" src="https://github.com/user-attachments/assets/86dae5c1-d0fa-4801-bad3-749e1959268f" />

*Transistor-level 1:4 DEMUX cell built using PMOS/NMOS devices*

2. **Test Circuit** — DEMUX cell instantiated with pulse sources on `D`, `S0`, `S1` and a 1.8V supply.

<img width="667" height="460" alt="image" src="https://github.com/user-attachments/assets/b4a3c712-08fe-4698-b44f-8fec4577bca3" />

*Test bench with pulse sources driving the DEMUX cell*

3. **Pre-layout Simulation** — Transient simulation to verify correct output routing.
4. **Physical Layout** — Full transistor-level layout implementation of the DEMUX cell.

<img width="806" height="586" alt="image" src="https://github.com/user-attachments/assets/d8122c63-3c63-438f-8442-ff29968d325d" />

*Transistor-level physical layout of the DEMUX cell*

## Results

<img width="830" height="376" alt="image" src="https://github.com/user-attachments/assets/c2dfe90e-ee03-43ef-8735-f650b8c682b1" />

*Transient response showing D routed to Y0–Y3 as S0/S1 change**

The output waveform confirms correct DEMUX operation across all four select-line combinations:

- **0–10 ns** (S1=0, S0=0): Output `Y0` follows input `D`; Y1–Y3 remain inactive.
- **10–20 ns** (S1=0, S0=1): Output `Y1` follows input `D`; remaining outputs stay low.
- **20–30 ns** (S1=1, S0=0): Output `Y2` follows input `D`; remaining outputs stay low.
- **30–40 ns** (S1=1, S0=1): Output `Y3` follows input `D`; remaining outputs stay low.

This confirms correct switching, selection, and routing behavior of the transmission-gate-based DEMUX design.

## Tools Used

- Cadence Virtuoso (Schematic Capture, Simulation, Layout)

## Conclusion

The 1:4 DEMUX was successfully designed and verified using transmission gate logic at the transistor level in CMOS technology. Pre-layout simulation confirmed functionally correct switching and routing operation, and the design was carried through to a complete physical layout — demonstrating the full schematic-to-layout VLSI design flow and confirming readiness for post-layout analysis.

## Contributors

- Hemanth Gowda K G (4NI23EC035)
- M Niranjan (4NI23EC049)

**Guided by:** Dr. Yajunath K, Assistant Professor, Dept. of ECE, NIE Mysuru
