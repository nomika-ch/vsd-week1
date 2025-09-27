# Day 1: Introduction to Verilog RTL Design and Synthesis

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

---

## 3. Lab: Simulating a 2-to-1 Multiplexer

Let’s simulate a simple **2-to-1 multiplexer** using iverilog!

###  Step 1: Clone the Workshop Repository

```shell
git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git
cd sky130RTLDesignAndSynthesisWorkshop/verilog_files
```

###  Step 2: Install Required Tools

```shell
sudo apt install iverilog
sudo apt install gtkwave
```
###  Step 3: Simulate the Design

Compile the design and testbench:

```shell
iverilog good_mux.v tb_good_mux.v
```

Run the simulation:

```shell
./a.out
```

View the waveform:

```shell
gtkwave tb_good_mux.vcd
```

<img width="1278" height="625" alt="wavef_good_mux" src="https://github.com/user-attachments/assets/ba469203-cf83-4244-ac5b-67037da2d026" />

--

## 4. Verilog Code Analysis

**The code for the multiplexer (`good_mux.v`):**

```verilog
module good_mux (input i0, input i1, input sel, output reg y);
always @ (*)
begin
    if(sel)
        y <= i1;
    else 
        y <= i0;
end
endmodule
```

###  **How It Works**

- **Inputs:** `i0`, `i1` (data), `sel` (select line)
- **Output:** `y` (registered output)
- **Logic:** If `sel` is 1, `y` gets `i1`; if `sel` is 0, `y` gets `i0`.

---

## 5. Introduction to Yosys & Gate Libraries

###  What is Yosys?

**Yosys** is a powerful open-source synthesis tool for digital hardware. It takes your Verilog code and converts it into a gate-level netlist—a hardware blueprint.

#### Yosys Features

- **Synthesis:** Converts HDL to a logic circuit
- **Optimization:** Improves speed or area
- **Technology Mapping:** Matches logic to actual hardware cells
- **Verification:** Checks correctness
- **Extensibility:** Supports custom flows

###  Why Do Libraries Have Different Gate "Flavors"?

A `.lib` file contains many versions of each gate (like AND, OR, NOT) with different properties:

- **Performance:** Faster gates for critical paths, slower for power savings
- **Power:** Some gates use less energy
- **Area:** Smaller gates for compact chips
- **Drive Strength:** Stronger gates to drive more load
- **Signal Integrity:** Specialized gates for noise/performance
- **Mapping:** Synthesis tools pick the best flavor for your needs

---

## 6. Synthesis Lab with Yosys

Let’s synthesize the `good_mux` design using Yosys!

###  Step-by-Step Yosys Flow

1. **Start Yosys**
    ```shell
    yosys
    ```

2. **Read the liberty library**
    ```shell
    read_liberty -lib /address/to/your/sky130/file/sky130_fd_sc_hd__tt_025C_1v80.lib
    ```

3. **Read the Verilog code**
    ```shell
    read_verilog /home/vsduser/VLSI/sky130RTLDesignAndSynthesisWorkshop/verilog_files/good_mux.v
    ```

4. **Synthesize the design**
    ```shell
    synth -top good_mux
    ```

5. **Technology mapping**
    ```shell
    abc -liberty /address/to/your/sky130/file/sky130_fd_sc_hd__tt_025C_1v80.lib
    ```

6. **Visualize the gate-level netlist**
    ```shell
    show
    ```

    <img width="680" height="248" alt="synth_good_mux" src="https://github.com/user-attachments/assets/14474a0b-6176-4a7d-bfa9-47a0e8332440" />

<img width="1055" height="525" alt="synthezied_good_mux" src="https://github.com/user-attachments/assets/22bbd32a-40d9-47e8-b821-62dfd9b5440b" />
