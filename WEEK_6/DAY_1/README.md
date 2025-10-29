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
