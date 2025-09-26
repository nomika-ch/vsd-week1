# vsd-week1
In this repo, all the basic codes and process of simulation, synthesis and analysing the synthesis block is present.

# Week-1 Documentation – VSD RISC-V SoC Tapeout Program

---

## Overview
In **Week-1**, the focus was on understanding **Verilog RTL design and synthesis concepts** using open-source tools (`iverilog`, `gtkwave`, `yosys`) and the **Sky130 PDKs(process design kits)**. The lectures spanned across 5 days, each introducing new concepts followed by practical labs.

---

## Day 1 – Introduction to Verilog RTL Design and Synthesis
- **Topics Covered:**
  - Basics of Verilog RTL design.
  - Introduction to open-source simulator **Icarus Verilog (iverilog)**.
  - Using **GTKWave** for waveform analysis.
  - Introduction to **Yosys** (open-source synthesis tool).
  - Logic synthesis concepts.
  - Introduction to **Sky130 PDKs**.

- **Labs Performed:**
  - Running simulations using `iverilog`.
  - Viewing simulation waveforms in `gtkwave`.
  - Synthesizing simple Verilog designs with `yosys`.
  - Exploring standard cells in the Sky130 PDK.

---

## Day 2 – Timing Libraries, Hierarchical vs Flat Synthesis, and Flop Coding Styles
- **Topics Covered:**
  - Introduction to **timing libraries (.lib files)**.
  - Role of timing libraries in synthesis and simulation.
  - Hierarchical vs flat synthesis approaches.
  - Efficient flip-flop coding styles in Verilog.
  - Importance of correct RTL coding for optimized synthesis.

- **Labs Performed:**
  - Analyzing `.lib` files from Sky130 PDK.
  - Writing Verilog RTL with different flop coding styles.
  - Observing synthesis optimizations in Yosys.

---

## Day 3 – Combinational and Sequential Optimizations
- **Topics Covered:**
  - Introduction to **logic optimizations** in synthesis.
  - **Combinational optimizations**: removing redundant logic.
  - **Sequential optimizations**: optimizing state-holding elements.
  - Handling **unused outputs** during synthesis.

- **Labs Performed:**
  - Running Yosys to optimize combinational logic.
  - Exploring sequential logic optimizations.
  - Identifying and removing unused outputs in synthesized designs.

---

## Day 4 – GLS, Blocking vs Non-Blocking, and Synthesis-Simulation Mismatch
- **Topics Covered:**
  - **GLS (Gate-Level Simulation)** using post-synthesis netlists.
  - Understanding **synthesis-simulation mismatch**.
  - Verilog coding guidelines to avoid mismatches.
  - Differences between **blocking (`=`)** and **non-blocking (`<=`)** assignments.
  - Common issues when using blocking statements in sequential logic.

- **Labs Performed:**
  - Performing GLS using synthesized netlists and iverilog.
  - Observing mismatches between RTL simulation and synthesized design.
  - Practical cases of blocking vs non-blocking usage.

---

## Day 5 – Optimization in Synthesis
- **Topics Covered:**
  - Optimizations with **if-else** and **case** constructs.
  - Handling **incomplete if/case statements**.
  - **Overlapping case conditions** and their impact.
  - Introduction to `for` loops and `generate` constructs in Verilog.
  - Structural and parametric design techniques.

- **Labs Performed:**
  - Demonstrating synthesis impact of incomplete if/case.
  - Observing synthesis mismatch with overlapping cases.
  - Writing Verilog with `for` loops.
  - Using `generate` blocks for repetitive hardware structures.

---

## Final Summary
- Learned fundamentals of **RTL design, simulation, and synthesis** using open-source tools (`iverilog`, `gtkwave`, `yosys`) with **Sky130 PDK**.
- Gained understanding of:
  - Simulation vs synthesis behavior.
  - Importance of **timing libraries**.
  - **Combinational and sequential optimizations**.
  - Correct **Verilog coding styles** to avoid synthesis-simulation mismatch.
  - Advanced coding constructs (`if`, `case`, `for`, `generate`).
- Successfully performed **hands-on labs** for each concept, validating theoretical learning.

---

