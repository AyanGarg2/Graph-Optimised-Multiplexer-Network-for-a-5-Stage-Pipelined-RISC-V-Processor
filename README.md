# Graph-Optimized Multiplexer Network for a 5-Stage Pipelined RISC-V Processor

This repository presents the design, optimization, and formal verification of a 5-stage pipelined RISC-V processor, with a specific focus on graph-based optimization of the datapath multiplexer network. The project demonstrates how systematic modeling and optimization of multiplexer structures can significantly improve area, power, and timing performance, while preserving functional correctness through formal verification.

---

## Project Overview

Modern pipelined processors rely extensively on multiplexers for datapath selection, including forwarding paths, ALU inputs, writeback selection, and program counter control. Poorly optimized multiplexer networks often become critical bottlenecks, negatively impacting delay, area, and power consumption.

In this project:
- A single-cycle RISC-V processor was first designed and verified.
- The design was extended to a 5-stage pipelined architecture with hazard detection and data forwarding.
- The multiplexer network was explicitly modeled as a directed graph.
- Graph-based optimization algorithms were applied to reduce redundant stages and critical-path depth.
- Formal verification using CTL model checking (NuSMV) was used to ensure correctness after optimization.

---

## Key Features

- 5-stage pipelined RISC-V processor (IF, ID, EX, MEM, WB)
- Hazard detection and data forwarding units
- Parameterized 2:1 and 3:1 multiplexer modules
- Explicit graph-based modeling of datapath multiplexers
- Multiplexer network optimization using Python and NetworkX
- Formal verification using CTL properties in NuSMV
- Comprehensive simulation and waveform-based validation

---

## Tools and Technologies Used

- **Verilog HDL** – RTL design
- **Icarus Verilog (iverilog)** – Compilation and simulation
- **GTKWave** – Waveform visualization and debugging
- **Python** – Graph modeling and optimization scripting
- **NetworkX** – Graph analysis and optimization library
- **NuSMV / nuXmv** – CTL-based formal verification

---

## Multiplexer Network Optimization

The multiplexer network is modeled as a directed graph, where:
- Nodes represent data sources and sinks
- Edges represent datapaths passing through multiplexers
- Edge weights correspond to delay, area, or power cost

### Optimization Techniques Applied
- Serial chain merging
- Critical path stage reduction
- Redundant multiplexer elimination
- Early forwarding path restructuring

---

## Optimization Results

| Metric | Before Optimization | After Optimization | Improvement |
|------|--------------------|-------------------|------------|
| Mux stages in critical path | 3 | 1 | 66.7% reduction |
| Total multiplexers | 5 | 2 | 60.0% reduction |
| LUT count | 128 | 64 | 50.0% reduction |
| Power consumption | 3.40 mW | 1.45 mW | 57.4% reduction |
| Critical path delay | 1.00 ns | 0.30 ns | 70.0% reduction |

---

## Formal Verification

To guarantee functional correctness after structural optimization:
- A formal model of the multiplexer network was developed in NuSMV
- A total of **21 CTL properties** were defined and verified, covering:
  - Reachability of all datapaths
  - Mutual exclusivity of multiplexer selections
  - Correct data propagation across pipeline stages
- All CTL properties were successfully verified, ensuring equivalence before and after optimization

---

## Simulation and Validation

- A comprehensive Verilog testbench was developed
- Correct instruction execution, forwarding behavior, and memory operations were verified
- Waveform analysis confirms proper pipeline operation
- No functional regressions were observed after optimization
