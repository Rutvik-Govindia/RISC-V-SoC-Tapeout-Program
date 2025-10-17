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

