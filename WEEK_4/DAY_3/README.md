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

---

## 32-L3 Labs Sky130 SPICE simulation for CMOS

-> ngspice day3_inv_vtc_Wp084_Wn036.spice

<img width="1215" height="683" alt="1 ngspice day_3 vtc" src="https://github.com/user-attachments/assets/95ef629e-93e1-431c-a693-4ac093512633" />

-> plot out vs in

<img width="1215" height="683" alt="2 plot out vs in" src="https://github.com/user-attachments/assets/ba3fe415-7653-4bb4-855f-f0792c6da162" />

-> Zoomed plot out vs in

<img width="1212" height="685" alt="3 zoomed plot out vs in" src="https://github.com/user-attachments/assets/379e38d1-7a70-4cf7-8de6-6ae37a78a4df" />

-> Switching Thresold Value

<img width="616" height="417" alt="4 switching thresold value" src="https://github.com/user-attachments/assets/823a73db-f41d-4b20-8a30-12f24d0987ab" />

-> day3_inv_tran_Wp084_Wn036.spice

<img width="1216" height="685" alt="5 ngspice day_3 tran" src="https://github.com/user-attachments/assets/8c6b5f6d-0f78-402a-802c-02a18f65ff63" />

-> plot out vs time in

<img width="1216" height="685" alt="6 plot out vs time in" src="https://github.com/user-attachments/assets/e626dee9-8c3d-4381-be4d-c3a0ebf65651" />

-> Zoomed plot out vs time in to calculate Rise Delay

<img width="1216" height="685" alt="7 zoomed plot out vs time in" src="https://github.com/user-attachments/assets/5bd97ba3-724a-4607-966d-0d4cc0edc79f" />

-> Calculating Rise Delay

<img width="545" height="198" alt="8 Calculating Rise Delay" src="https://github.com/user-attachments/assets/e85c8727-3e26-4544-b1dc-e768e7b3be01" />

Therefore; Rise Delay = 2.48 - 2.15 = 0.33

-> Zoomed plot out vs time in to calculate Fall Delay

<img width="1214" height="683" alt="9 Zoomed plot out vs time in to Calculat Fall Delay" src="https://github.com/user-attachments/assets/3e026ac4-e398-447b-bdc9-f72d61bc9c9d" />

-> Calculating Fall Delay

<img width="332" height="99" alt="10 Calculating Fall Delay" src="https://github.com/user-attachments/assets/0a947cd0-cc8f-4fdd-9853-84b38cc6b8a0" />

Therefore; Fall Delay = 4.33 - 4.05 = 0.28
