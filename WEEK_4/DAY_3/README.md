## Voltage Transfer Characteristics – SPICE Simulations

This section transitions from the mathematical and graphical analysis of the CMOS VTC to its **computer-aided simulation** using **SPICE (Simulation Program with Integrated Circuit Emphasis)**. This is a critical step in verifying theoretical device models against a realistic circuit implementation.

---

## 30-L1 SPICE deck creation for CMOS inverter

* **Focus:** This step details the process of writing the **SPICE netlist**, often called the **SPICE deck**, which is a text file that describes the circuit to the simulation program.
* **Details:** The deck must include several key elements:
    1.  **Model Definitions:** Including the specific **MOSFET models** (e.g., LEVEL 1, LEVEL 3, or BSIM models for modern nodes) for both the NMOS and PMOS transistors. These models contain parameters like $V_t$, $\mu$, $W$, and $L$.
    2.  **Netlist:** Describing the connections of the circuit, which for a CMOS inverter involves:
        * Connecting the PMOS source to $\boldsymbol{V_{DD}}$.
        * Connecting the NMOS source to $\boldsymbol{GND}$ (0V).
        * Connecting the PMOS and NMOS gates to the input node ($\boldsymbol{V_{in}}$).
        * Connecting the PMOS and NMOS drains to the output node ($\boldsymbol{V_{out}}$).
    3.  **Voltage Sources:** Defining the DC power supply ($\boldsymbol{V_{DD}}$) and the input voltage source ($\boldsymbol{V_{in}}$).
* **Outcome:** The creation of a complete, syntax-correct SPICE netlist file that is ready to be run by the simulator.

---

## 31-L2 SPICE simulation for CMOS inverter

* **Focus:** Running the simulation to generate the VTC curve and analyze the results.
* **Details:** This involves setting up the **analysis command** in the SPICE deck:
    1.  **DC Sweep Analysis:** The specific analysis required for a VTC is a **DC sweep**. This command instructs the simulator to:
        * Sweep the **input voltage ($\boldsymbol{V_{in}}$)** from a starting value (e.g., $0\text{V}$) to an ending value (e.g., $V_{DD}$).
        * Do this in defined increments.
    2.  **Output Specification:** The simulator is instructed to calculate and record the voltage at the **output node ($\boldsymbol{V_{out}}$)** for every step of the $\boldsymbol{V_{in}}$ sweep.
* **Outcome:** The SPICE simulator generates a data file that lists pairs of ($\boldsymbol{V_{in}}$, $\boldsymbol{V_{out}}$) values. This data is then used to plot the classic **S-shaped VTC curve**. The simulation results are used to determine practical metrics such as the noise margins ($NM_H$ and $NM_L$), the switching threshold ($V_M$), and the gain in the transition region.
