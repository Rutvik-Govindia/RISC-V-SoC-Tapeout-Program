# SoC Fundamentals & BabySoC Functional Modelling

## Introduction
A **System-on-Chip (SoC)** is an integrated circuit (IC) that brings together multiple system-level components into a single chip. Instead of having separate chips for CPU, memory, and peripherals, an SoC integrates all these into one unit. This makes SoCs highly efficient in terms of power, cost, and performance, which is why they are widely used in smartphones, IoT devices, automotive electronics, and other embedded systems.  

The **BabySoC** model is a simplified learning framework that introduces the fundamental concepts of SoC design without the complexity of real-world industrial chips. It helps learners build a foundation in functional modelling and system-level integration before moving into RTL design and physical implementation.  

---

## Components of a Typical SoC

1. **CPU (Central Processing Unit)**
   - Acts as the brain of the system.  
   - Executes instructions and coordinates the overall functionality.  
   - Can be general-purpose (e.g., ARM cores) or domain-specific (DSP, GPU).  

2. **Memory**
   - Stores instructions and data for the CPU.  
   - Includes both volatile memory (RAM) and non-volatile memory (ROM, Flash).  
   - Plays a crucial role in determining system performance.  

3. **Peripherals**
   - Interfaces for input/output (I/O) operations.  
   - Examples: UART, SPI, I2C, GPIO, timers, and communication modules.  
   - Allow the SoC to interact with external devices.  

4. **Interconnect (Bus or Network-on-Chip)**
   - Provides communication between CPU, memory, and peripherals.  
   - Ensures efficient data transfer and synchronization across components.  

---

## Why BabySoC?

Designing a complete industrial SoC is complex and requires deep expertise across digital design, verification, and physical implementation. **BabySoC simplifies this learning process** by providing:  

- A minimal set of components (CPU, memory, basic I/O).  
- Focus on **conceptual understanding** rather than hardware complexity.  
- A structured way to practice **functional modelling** before diving into detailed RTL coding.  
- An educational stepping stone toward advanced design flows like synthesis, floorplanning, and chip fabrication.  

---

## Role of Functional Modelling

Before RTL (Register Transfer Level) and physical design, it is essential to validate the **system’s intended functionality**. Functional modelling provides this early verification by:  

- Simulating the behavior of the SoC components at a high level.  
- Allowing students to test how CPU, memory, and peripherals interact.  
- Identifying logical or integration errors early in the design flow.  
- Serving as a **reference model** for later RTL development.  

By using tools like **Icarus Verilog** for simulation and **GTKWave** for waveform visualization, functional modelling enables a hands-on approach to exploring how different blocks of an SoC communicate and function together.  

---

## Conclusion

The **BabySoC framework** bridges the gap between theory and practice in SoC design. It introduces the essential building blocks of an SoC (CPU, memory, peripherals, interconnect) while keeping the complexity manageable for learners. Through functional modelling, we gain insights into system behavior and prepare for the next stages of RTL design and physical implementation.  

This approach ensures that learners build a **solid foundation** in SoC design, enabling them to transition smoothly into advanced VLSI design flows.