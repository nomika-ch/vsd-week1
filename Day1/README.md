# Day 1: Introduction to Verilog RTL Design and Synthesis

---
## Table of Contents
---

##  1. What is a Simulator, Design and Testbench?
### Simulator
A simulator is a software tool (or sometimes hardware + software system) that imitates the behavior of a real system or design so you can study, test, or analyze it without physically building it.
A **simulator** is used to:
- Run your HDL code (RTL design, testbench, etc.)
- Apply test inputs (stimulus)
- Observe outputs (waveforms, logs, dumps)
- Verify correctness before going to synthesis or hardware implementation

A simulator provides a virtual environment to check how a system would behave under different conditions without the cost or risk of using the real system.

Here in this workshop we are using **Icarus Verilog(iverilog)** - this is an open source Verilog simulator

**ModelSim/ Questa / VCS / Xcelium** - these are industry standard simulators

---
### Design
- A design usually refers to the RTL (Register Transfer Level) description of a digital system written in HDL (Hardware Description Language) like Verilog or VHDL.
- It describes how data moves between registers, how logic is implemented, and how the system responds to inputs.
- Design is the actual Verilog code or set of verilog codes which has the intended functionality to meet with the required specifications.

---

### Teshbench
- A testbench is not part of the actual hardware design, but rather a virtual environment you write (in Verilog/SystemVerilog) to test and verify your design.
- A testbench is a verification environment written in HDL to test your design by providing stimulus and checking the response. It ensures your design works as intended before synthesis or hardware implementation.
- Testbench is the setup to apply stimulus(test_vectors) to the design to check its functionality.
  <div align="center">
  <img src="https://github.com/user-attachments/assets/93927b96-df80-4da5-b801-284fc2cc6757" alt="Design & Testbench Overview" width="70%">
</div>
---

### How simulator works
- Simulator looks for the changes on the input signals.
- Upon change to the input the output is evaluated
      - If no change to the input, no change to the output!
- Simulator is looking for change in the values of input!
---

## 2. Getting Started with iverilog

**iverilog** is an open-source simulator for Verilog. Here’s the typical simulation flow:

<div align="center">
  <img src="https://github.com/user-attachments/assets/3ca190fb-cfa4-4abb-b9e1-0151b3c4bdba" alt="iverilog Simulation Flow" width="70%">
</div>

- Both the design and testbench are provided as input to iverilog.
- The simulator produces a `.vcd` file for waveform viewing in GTKWave.
