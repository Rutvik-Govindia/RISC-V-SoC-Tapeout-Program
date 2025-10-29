## Inception of Open-Source EDA, OpenLANE, and Sky130 PDK

* **Open-Source EDA (Electronic Design Automation):**
    * Refers to **free and publicly available software tools** (e.g., Yosys, Magic, OpenSTA) used for designing and verifying complex integrated circuits (ICs).
    * **Goal:** To lower the high barrier to entry for chip design by replacing expensive, proprietary software.
* **Sky130 PDK (Process Design Kit):** 
    * A set of design files, models, and rules necessary to manufacture an IC using the **SkyWater 130nm process**.
    * Made **open-source** through the Google-SkyWater collaboration, allowing designers to create manufacturable chips without an NDA.
* **OpenLANE:**
    * A fully automated, **end-to-end flow** that converts a high-level chip description (**RTL**) into a final manufacturing file (**GDSII**).
    * It acts as an **orchestrator**, seamlessly integrating various open-source EDA tools (synthesis, placement, routing) to produce a tape-out-ready layout.

---

## How to Talk to Computers

### 2. Introduction to QFN-48 Package, Chip, Pads, Core, Die, and IPs

| Term | Description |
| :--- | :--- |
| **Die** | The actual piece of processed **silicon** containing the integrated circuit. |
| **Chip** | The entire assembly, typically referring to the **Die + Package**. |
| **QFN-48 Package** | A **Quad Flat No-Lead** surface-mount package used to physically and electrically connect the die to a Printed Circuit Board (**PCB**), featuring **48** connection pads. |
| **Pads** | The small metallic connection points on the edge of the die or package that serve as the **input/output (I/O) interfaces** for the chip. |
| **Core** | The central processing unit (**CPU**) within the chip, responsible for executing instructions (e.g., the RISC-V core). |
| **IPs (Intellectual Property)** | **Reusable blocks of pre-designed circuitry** (e.g., memory controllers, communication interfaces) that are integrated with the core to build a complete **System-on-Chip (SoC)**. |

### 3. Introduction to RISC-V

* **Open Standard ISA:** RISC-V is a **free and open Instruction Set Architecture**. Its specifications can be used, implemented, and extended by anyone without paying licensing fees.
* **Reduced Instruction Set:** It follows the **RISC** (Reduced Instruction Set Computer) principle, using a smaller, simpler set of instructions.
* **Modularity:** It has a small, standard base instruction set with optional extensions, allowing for the creation of highly **customized and efficient processors** (from microcontrollers to high-performance cores).

### 4. From Software Applications to Hardware

* **Compilation:** High-level code (e.g., C++) is translated into a sequence of **binary instructions (machine code)**.
* **ISA (Instruction Set Architecture):** These binary instructions are understood by the processor's ISA, defining the set of operations the CPU can perform.
* **Physical Representation:** The binary **0s and 1s** are represented by **low (Ground)** and **high (Voltage)** electrical signals in the silicon.
* **Digital Logic:** Transistors, connected to form **logic gates**, manipulate these voltage levels (the 0s and 1s) to perform the instructions (arithmetic, logic, etc.).

***

## SoC Design & OpenLANE

## 5- Introduction to all components of open-source digital ASIC design

This section introduces the foundational elements of designing an **Application-Specific Integrated Circuit (ASIC)** using **open-source tools** and **workflows**.

* **ASIC vs. FPGA:** It defines an ASIC as a custom-designed chip for a specific task, contrasting it with a general-purpose chip like an FPGA (Field-Programmable Gate Array).
* **The Design Source (RTL):** The design always starts with the **Register Transfer Level (RTL)** code, typically written in a Hardware Description Language (HDL) like **Verilog** or SystemVerilog, which describes the circuit's functionality.
* **Open-Source EDA Tools:** A key component is the suite of **Electronic Design Automation (EDA)** software used for implementation. Unlike traditional proprietary tools, these are freely available and modifiable. Important examples include:
    * **Yosys:** Used for **Logic Synthesis**.
    * **OpenROAD tools (e.g., OpenSTA):** Used for physical design and timing analysis.
* **Open-Source PDKs (Process Design Kits):** These are technology files provided by a foundry (chip manufacturer) that contain all the necessary data (libraries, design rules, etc.) to design a chip for a specific manufacturing process. **SkyWater 130nm (SKY130)** is the most famous open-source PDK.
* **IP Cores:** Pre-designed, reusable blocks of logic (**Intellectual Property**) that are integrated into the final chip.

---

## 6- Simplified RTL2GDS flow

This is the general, step-by-step process of converting the design's functional description (**RTL**) into the final manufacturing file (**GDSII**), which is sent to the foundry. The "simplified" flow focuses on the main, sequential stages:

1.  **Logic Synthesis (RTL to Netlist):** The HDL code (**RTL**) is translated into a **gate-level netlist**, which is a description of the circuit using basic logic gates (like AND, OR, flip-flops) from the standard cell library of the target technology.
2.  **Floorplanning and Power Planning:** Defines the chip's overall size and shape (**die size**), reserves space for large blocks (**macros**), and designs the power distribution network (**power grid**) to deliver stable voltage to all components.
3.  **Placement:** All the standard cells from the netlist are physically placed onto the chip's core area, aiming to minimize the length of interconnecting wires.
4.  **Clock Tree Synthesis (CTS):** The clock signal is distributed to all sequential elements (like flip-flops) in a carefully balanced structure (**clock tree**) to ensure the signal arrives at all points simultaneously, minimizing **clock skew**.
5.  **Routing:** The final step where all the placed cells and blocks are electrically connected by drawing metal wires (**interconnects**) across the different metal layers.
6.  **Signoff and GDSII:** A final stage involving checks like **Static Timing Analysis (STA)** to ensure performance, and **Design Rule Check (DRC)** and **Layout Versus Schematic (LVS)** to ensure manufacturability and functional correctness. The final, verified layout is saved in the **GDSII** format.

---

## 7- Introduction to OpenLANE and Strive chipsets

This point focuses on the specific open-source infrastructure and a key result of its application.

* **OpenLANE (Open-Source Digital ASIC Implementation Flow):** This is a highly automated and tape-out-hardened flow that unifies and manages a collection of open-source EDA tools (like Yosys, OpenROAD, etc.) into a cohesive design process. Its main purpose is to automate the entire RTL-to-GDSII flow, making digital ASIC design more accessible.
    * **Main Use Cases:** Hardening an individual block (**macro**) or integrating multiple components into a full **System-on-a-Chip (SoC)**.
    * **Key Advantage:** It abstracts the complexity of individual tools, allowing designers to configure the entire flow using a single set of settings.
* **Strive Chipsets (or striVe SoCs):** This refers to a family of **RISC-V based System-on-a-Chip (SoC)** designs that were successfully **"taped out"** (sent for fabrication) using the **OpenLANE** flow. The striVe chips serve as a critical proof point, demonstrating that a completely open-source toolchain (OpenLANE) is robust enough to produce a functional, manufacturable chip.

---

## 8- Introduction to OpenLANE detailed ASIC design flow

This section dives into the **specific, granular steps** within the OpenLANE framework, expanding on the simplified RTL2GDS flow.

The OpenLANE flow is a sequence of stages, including but not limited to:

* **Synthesis:** (as in Simplified Flow) Uses **Yosys** to create the gate-level netlist and **OpenSTA** for timing analysis.
* **Floorplanning:** (as in Simplified Flow) Defines the die area and places I/O pads.
* **I/O Placement:** Specific placement of the pins that connect the chip to the outside world.
* **Pre-Place Optimization:** Initial optimization of the netlist before placing the cells.
* **Global Placement and Detailed Placement:** (as in Simplified Flow) The process of arranging standard cells.
* **Clock Tree Synthesis (CTS):** (as in Simplified Flow) Building the clock network.
* **Routing:** (as in Simplified Flow) Includes Global and Detailed Routing.
* **Post-Route Optimization:** Final timing and power optimization after routing is complete.
* **Spef Extraction:** Generating the Standard Parasitic Exchange Format (SPEF) file, which captures the accurate resistance and capacitance of the placed and routed wires for final analysis.
* **GDSII Generation and Signoff Checks (DRC/LVS):** Creating the final file and performing all necessary physical and electrical verification checks to ensure the chip is ready for manufacturing.

This detailed flow showcases OpenLANE's ability to automate and integrate all the complex, interdependent stages required for a production-ready ASIC design.

***
