## SPICE Simulation and Velocity Saturation

This overarching theme indicates a study of how **velocity saturation** impacts transistor behavior, both in theoretical models and when simulated using **SPICE (Simulation Program with Integrated Circuit Emphasis)**, a widely used electronic circuit simulator. Velocity saturation is a phenomenon in short-channel **MOSFETs** where, as the electric field across the channel increases, the carrier (electron or hole) drift velocity no longer increases proportionally, but instead reaches a maximum or "saturates." This limits the drain current.

---

## 18-L1 SPICE simulation for lower nodes

* **Focus:** This section likely covers how to set up and run a **SPICE simulation** for transistors built using **"lower nodes"** (i.e., smaller, more advanced technology nodes like 45 nm, 28 nm, or smaller).
* **Details:** In these modern, smaller transistors, **short-channel effects** like velocity saturation become dominant and *must* be accurately modeled.
* **Key Topics:** It would detail the specific **MOSFET model** (e.g., BSIM) used in SPICE for these nodes and how the simulation results (like $\boldsymbol{I_D}$ vs. $\boldsymbol{V_{GS}}$ or $\boldsymbol{I_D}$ vs. $\boldsymbol{V_{DS}}$ curves) are affected by the small geometry and the inherent velocity saturation phenomenon.

---

## 19-L2 Drain current vs gate voltage for long and short channel device

* **Focus:** A fundamental comparison of the **current-voltage (I-V) characteristics**—specifically **drain current ($\boldsymbol{I_D}$) vs. gate voltage ($\boldsymbol{V_{GS}}$)**—between a classical **long-channel** MOSFET and a modern **short-channel** MOSFET.
* **Details:**
    * **Long-Channel:** The $I_D-V_{GS}$ curve follows the ideal square-law model, where $I_D$ is proportional to $(V_{GS} - V_t)^2$ (in saturation). Velocity saturation is negligible.
    * **Short-Channel:** The curve deviates significantly. Due to velocity saturation, the **drain current increases more linearly** with the gate voltage, rather than quadratically. This is a key signature of velocity saturation and is a major topic in device scaling.

---

## 20-L3 Velocity saturation at lower and higher electric fields

* **Focus:** An in-depth look at the **physics** of carrier velocity within the channel as a function of the **lateral electric field ($\boldsymbol{E_{lat}}$)**.
* **Details:**
    * **Lower Electric Fields:** The carrier drift velocity ($\boldsymbol{v_d}$) is **linearly** proportional to the electric field ($v_d = \mu E_{lat}$, where $\mu$ is the mobility). This is known as the **constant mobility region** (or Ohmic region).
    * **Higher Electric Fields:** As the field increases (e.g., in a short channel device), the velocity starts to **saturate** and approaches a maximum limit, $\boldsymbol{v_{sat}}$. The section would likely cover the mathematical models describing this transition, such as the **empirical mobility model** that accounts for velocity saturation.

---

## 21-L4 Velocity saturation drain current model

* **Focus:** Discussing the **mathematical models** used to accurately predict the **drain current** in a short-channel transistor *with* the effect of velocity saturation.
* **Details:** The standard long-channel drain current equations are no longer valid. This section would introduce:
    * **The Velocity Saturation Factor:** A modification to the effective mobility in the drain current equation to account for $v_{sat}$.
    * **The $I_D$ Equation:** The resulting equation shows that in saturation, the drain current becomes approximately **proportional to $(V_{GS} - V_t)$** (linear dependence) rather than $(V_{GS} - V_t)^2$ (quadratic dependence). This change is crucial for modern circuit design, especially for analog circuits.

These topics form a comprehensive overview of how one of the most critical **short-channel effects**—velocity saturation—is understood, modeled mathematically, and incorporated into electronic circuit simulation tools like SPICE.

---

## 22-L5 Labs Sky130 Id-Vgs

<img width="1215" height="683" alt="1 ngspice day_2 vds" src="https://github.com/user-attachments/assets/7025632e-95c1-4375-9171-1004b2200149" />

<img width="1215" height="683" alt="2 plot -vdd#branch" src="https://github.com/user-attachments/assets/f7419aa0-4378-45f8-a890-be7a3563154f" />

<img width="1215" height="683" alt="3 ngspice day_2 vgs" src="https://github.com/user-attachments/assets/6af21bed-fe4e-421e-a043-0818b12eab3e" />

<img width="1215" height="683" alt="4 plot -vdd#branch" src="https://github.com/user-attachments/assets/e7bc39ad-51dc-45f7-b356-059ec8b373fe" />

---

## 23-L6 Labs Sky130 Vt

<img width="1215" height="683" alt="3 ngspice day_2 vgs" src="https://github.com/user-attachments/assets/9c636fa3-a6b6-4325-8b5d-bd1e7ad89fd7" />

<img width="1215" height="683" alt="4 plot -vdd#branch" src="https://github.com/user-attachments/assets/2c9a9b24-979f-4e46-8c04-39d4cccdf439" />


---

## CMOS Voltage Transfer Characteristics (VTC)

The **Voltage Transfer Characteristic (VTC)** is a graph that plots the **output voltage ($\boldsymbol{V_{out}}$) versus the input voltage ($\boldsymbol{V_{in}}$)** for a logic gate, such as a **CMOS inverter**. It is the most critical curve for determining a digital circuit's performance metrics like noise margins, switching threshold, and gain.

---

## 24-L1 MOSFET as a switch

* **Focus:** Establishing the foundational concept of how a **MOSFET (Metal-Oxide-Semiconductor Field-Effect Transistor)** operates in digital circuits.
* **Details:** This section explains that in digital design, a MOSFET is primarily used as a **voltage-controlled switch**.
    * **N-MOSFET:** An input voltage ($V_{GS}$) greater than the threshold voltage ($V_t$) turns the switch **ON** (low resistance), connecting the drain to the source. An input voltage of $0\text{V}$ turns it **OFF** (high resistance).
    * **P-MOSFET:** An input voltage ($V_{GS}$) less than $|V_t|$ turns the switch **ON**. An input voltage near the supply voltage ($V_{DD}$) turns it **OFF**.
* **Significance:** This switching action is the basis for all digital logic and the core function of the CMOS inverter.

---

## 25-L2 Introduction to standard MOS voltage current parameters

* **Focus:** Defining the key electrical parameters and operating regions of a MOSFET required to analyze the VTC.
* **Details:** This section reviews:
    * **Threshold Voltage ($\boldsymbol{V_t}$):** The minimum gate-to-source voltage required to turn the transistor ON.
    * **Drain Current ($\boldsymbol{I_D}$):** The current flowing between the drain and source.
    * **Operating Regions:** **Cutoff** (switch OFF), **Triode/Linear** (switch ON, resistive mode), and **Saturation** (switch ON, constant current mode).
    * **Mobility ($\boldsymbol{\mu}$), Aspect Ratio ($\boldsymbol{W/L}$), and Transconductance Parameter ($\boldsymbol{K}$ or $\boldsymbol{k'}$):** Parameters used in the $\boldsymbol{I_D}$ equations for each region.

---

## 26-L3 PMOS/NMOS drain current v/s drain voltage

* **Focus:** Examining the fundamental $\boldsymbol{I_D}$ vs. $\boldsymbol{V_{DS}}$ (Drain Current vs. Drain-Source Voltage) curves for both an **N-MOSFET** and a **P-MOSFET**.
* **Details:** These curves illustrate the different operating regions.
    * For a fixed $\boldsymbol{V_{GS}}$, as $\boldsymbol{V_{DS}}$ increases, $\boldsymbol{I_D}$ initially increases linearly (Triode region) and then flattens out (Saturation region).
    * The **P-MOSFET** curve is typically plotted with a reversed polarity (negative voltages) because its terminal voltages are referenced differently in the CMOS inverter structure. This section establishes the load curves necessary for plotting the VTC.

---

## 27- L4 Step1 – Convert PMOS gate-source-voltage to Vin

* **Focus:** The first step in mathematically or graphically deriving the CMOS inverter VTC.
* **Details:** In a CMOS inverter, the input voltage ($\boldsymbol{V_{in}}$) is applied simultaneously to the **gate** of the N-MOSFET and the **gate** of the P-MOSFET. The $\boldsymbol{I_D}$ equations for the P-MOSFET use the **gate-to-source voltage ($\boldsymbol{V_{GSP}}$)**.
* **Conversion:** The source of the P-MOSFET is connected to the supply voltage ($\boldsymbol{V_{DD}}$). Therefore, the conversion is:
    $$\boldsymbol{V_{GSP} = V_{in} - V_{DD}}$$
* **Purpose:** This step allows the P-MOSFET current equation to be expressed as a function of the circuit's input voltage ($\boldsymbol{V_{in}}$), which is essential for VTC plotting.

---

## 28- L5 Step2 & Step3 – Convert PMOS and NMOS drain-source-voltage to Vout

* **Focus:** The second and third steps, which involve expressing the $\boldsymbol{V_{DS}}$ terms of both transistors in terms of the output voltage ($\boldsymbol{V_{out}}$).
* **Details:** In a CMOS inverter, the drains of the N-MOSFET and P-MOSFET are connected together to form the **output node ($\boldsymbol{V_{out}}$)**.
    * **N-MOSFET $\boldsymbol{V_{DSN}}$:** The source is at ground ($0\text{V}$), so $\boldsymbol{V_{DSN} = V_{out} - 0 = V_{out}}$.
    * **P-MOSFET $\boldsymbol{V_{DSP}}$:** The source is at $\boldsymbol{V_{DD}}$, so $\boldsymbol{V_{DSP} = V_{out} - V_{DD}}$.
* **Purpose:** This step completely transforms both the N-MOSFET and P-MOSFET $\boldsymbol{I_D}$ equations into functions of only the input ($\boldsymbol{V_{in}}$) and output ($\boldsymbol{V_{out}}$) voltages.

---

## 29-L6 Step4 – Merge PMOS – NMOS load curves and plot VTC

* **Focus:** The final and most critical step—combining the transistor equations to generate the final VTC curve.
* **Details:** The core principle of the CMOS inverter analysis is that the drain currents must be equal ($\boldsymbol{I_{DP} = I_{DN}}$) because the PMOS and NMOS are stacked in series between $\boldsymbol{V_{DD}}$ and ground, with the output as the connecting point.
* **Process:**
    1.  Equate the $\boldsymbol{I_D}$ equations (expressed in terms of $V_{in}$ and $V_{out}$) for the NMOS and PMOS for every operating region combination (e.g., PMOS in Triode, NMOS in Saturation).
    2.  For a given $\boldsymbol{V_{in}}$, solve the resulting transcendental equation for $\boldsymbol{V_{out}}$.
    3.  Plot the resulting $\boldsymbol{V_{out}}$ against the corresponding $\boldsymbol{V_{in}}$ to obtain the characteristic **steeply sloping S-shaped VTC curve**.
