*“Introduction to Circuit Design and SPICE simulations”*:

---

### **3–L1: Why do we need SPICE simulations?**

**SPICE (Simulation Program with Integrated Circuit Emphasis)** is a powerful tool used to **simulate and analyze electronic circuits** before physically building them.
Here’s why we need SPICE simulations:

1. **Cost and Time Efficiency:**

   * Fabricating ICs or PCBs repeatedly for testing is expensive and time-consuming.
   * SPICE helps analyze circuits virtually, reducing the number of prototypes needed.

2. **Accurate Circuit Behavior Prediction:**

   * SPICE models the real electrical characteristics of components (resistors, capacitors, MOSFETs, BJTs, etc.).
   * It includes effects like parasitic capacitance, leakage, temperature variations, and transistor non-linearity.

3. **Pre-Verification:**

   * Before layout or fabrication, designers verify circuit behavior (gain, delay, power consumption, noise margin, etc.) using SPICE.

4. **Performance Analysis:**

   * Allows **DC**, **AC**, **Transient**, and **Noise** analyses:

     * *DC Analysis:* Finds bias points and operating regions.
     * *AC Analysis:* Studies frequency response.
     * *Transient Analysis:* Observes time-domain behavior.
     * *Noise Analysis:* Checks signal-to-noise ratio and noise impact.

5. **Design Optimization:**

   * Designers can tweak component values or transistor sizes easily and immediately see how performance changes.

---

### **4–L2: Introduction to Basic Element in Circuit Design – NMOS**

**NMOS (N-type Metal-Oxide-Semiconductor)** transistor is a **fundamental building block** in modern digital and analog circuits.

#### **Structure:**

* It consists of:

  * **Source (S)** and **Drain (D)** terminals made of n-type regions.
  * **Gate (G)** made of metal or polysilicon, separated from the substrate by a thin **oxide layer**.
  * **Body (B)** or **Substrate**, typically p-type.

#### **Working Principle:**

* When **V<sub>GS</sub> (Gate-to-Source voltage)** is **greater than the threshold voltage (V<sub>th</sub>)**, an **inversion layer** of electrons forms under the gate.
* This creates a conductive channel between the source and drain.
* The transistor behaves as a **switch**:

  * **OFF:** V<sub>GS</sub> < V<sub>th</sub> → No current flows.
  * **ON:** V<sub>GS</sub> ≥ V<sub>th</sub> → Current flows from Drain → Source.

#### **Current Regions:**

1. **Cut-off Region:** Transistor OFF.
2. **Linear (Triode) Region:** Acts as a resistor (small V<sub>DS</sub>).
3. **Saturation Region:** Acts as a current source (large V<sub>DS</sub>).

#### **Applications:**

* Used in logic gates (CMOS circuits), amplifiers, analog switches, current mirrors, etc.

---

### **5–L3: Strong Inversion and Threshold Voltage**

#### **Threshold Voltage (V<sub>th</sub>):**

It is the **minimum gate-to-source voltage** required to create a **conductive channel** between the source and drain.

* When **V<sub>GS</sub> < V<sub>th</sub>**, the transistor is **OFF** (no channel).
* When **V<sub>GS</sub> ≈ V<sub>th</sub>**, a **weak inversion** occurs — small subthreshold current flows.
* When **V<sub>GS</sub> > V<sub>th</sub>**, the transistor enters **strong inversion** — a large number of electrons form a strong n-channel.

#### **Strong Inversion:**

* The electron concentration at the surface exceeds the substrate hole concentration.
* Drain current (I<sub>D</sub>) depends mainly on V<sub>GS</sub> and V<sub>DS</sub>.
* The transistor behaves like a **controlled current source**:
  [
  I_D = \frac{1}{2} \mu_n C_{ox} \frac{W}{L} (V_{GS} - V_{th})^2
  ]
  where:

  * μₙ = electron mobility
  * Cₒₓ = oxide capacitance per unit area
  * W/L = width/length ratio of MOSFET

#### **Factors Affecting V<sub>th</sub>:**

* Oxide thickness
* Doping concentration
* Substrate bias (body effect)
* Temperature

---

### **6–L4: Threshold Voltage with Positive Substrate Potential**

Normally, the **substrate (body)** is connected to the **lowest potential** in the circuit (for NMOS, it’s ground).
However, when the **substrate potential (V<sub>SB</sub>)** becomes **positive**, the **threshold voltage increases** — this is known as the **Body Effect** or **Substrate Bias Effect**.

#### **Effect Explanation:**

When the substrate is more positive than the source:

* The depletion region under the gate widens.
* More gate voltage is needed to create the inversion layer.
* Hence, **V<sub>th</sub> increases**.

#### **Modified Threshold Voltage Equation:**

[
V_{th} = V_{th0} + \gamma \left( \sqrt{2\phi_F + V_{SB}} - \sqrt{2\phi_F} \right)
]
Where:

* **V<sub>th0</sub>** = threshold voltage at zero substrate bias
* **γ** = body effect coefficient
* **φ<sub>F</sub>** = Fermi potential
* **V<sub>SB</sub>** = substrate-to-source voltage

#### **Practical Implications:**

* Higher V<sub>SB</sub> → higher V<sub>th</sub> → transistor turns ON later.
* Impacts **speed and power** of MOS circuits.
* Designers must consider this in analog and digital design (especially in multi-transistor ICs).



**“NMOS resistive region and saturation region of operation”**

---

### **7–L1: Resistive Region of Operation with Small Drain-Source Voltage**

When an **NMOS transistor** operates with a **small drain-to-source voltage (V<sub>DS</sub>)**, and the **gate-to-source voltage (V<sub>GS</sub>)** is greater than the **threshold voltage (V<sub>th</sub>)**, it behaves like a **variable resistor**.

This mode is called the **Resistive region** or **Linear region** of operation.

#### **Conditions:**

[
V_{GS} > V_{th}
]
[
V_{DS} < (V_{GS} - V_{th})
]

#### **Explanation:**

* The inversion layer (channel) forms between the source and drain.
* Since V<sub>DS</sub> is small, the voltage drop along the channel is small, and the electron concentration is almost uniform.
* The current through the device increases almost linearly with V<sub>DS</sub>.

Thus, the MOSFET behaves like a **voltage-controlled resistor**:

* Increasing V<sub>GS</sub> → channel resistance decreases.
* Decreasing V<sub>GS</sub> → channel resistance increases.

#### **Applications:**

* Used as analog switches, variable resistors, and for modeling the “ON” behavior of MOS transistors in digital circuits.

---

### **8–L2: Drift Current Theory**

In an NMOS transistor, the **current flow** from **drain to source** mainly occurs due to the **drift of charge carriers (electrons)** under the influence of an **electric field**.

#### **Drift Current Concept:**

When an electric field (E) is applied, electrons move with an **average velocity** called the **drift velocity (v<sub>d</sub>)**:
[
v_d = \mu_n E
]
where:

* μₙ = electron mobility
* E = electric field (V<sub>DS</sub>/L)

#### **Drain Current (I<sub>D</sub>) Expression:**

[
I_D = Q_n \cdot v_d \cdot W
]
[
I_D = (Q_n) (\mu_n E) W
]
[
I_D = \mu_n C_{ox} \frac{W}{L} (V_{GS} - V_{th}) V_{DS}
]
for small V<sub>DS</sub>.

Thus, drift current theory explains **how electrons move in the inversion layer**, forming the basis of MOSFET current equations.

---

### **9–L3: Drain Current Model for Linear Region of Operation**

In the **linear (resistive) region**, the MOSFET behaves like a resistor controlled by the gate voltage.

#### **Condition:**

[
V_{DS} < (V_{GS} - V_{th})
]

#### **Current Model:**

From the gradual channel approximation:
[
I_D = \mu_n C_{ox} \frac{W}{L} \left[ (V_{GS} - V_{th})V_{DS} - \frac{V_{DS}^2}{2} \right]
]

#### **Interpretation:**

* The first term ((V_{GS} - V_{th})V_{DS}) → represents a **linear** relationship between current and voltage.
* The second term (-\frac{V_{DS}^2}{2}) → accounts for the **non-linear** channel voltage drop.

When V<sub>DS</sub> is very small, the second term can be ignored:
[
I_D ≈ \mu_n C_{ox} \frac{W}{L} (V_{GS} - V_{th})V_{DS}
]

---

### **10–L4: SPICE Conclusion to Resistive Operation**

SPICE simulations help verify the **linear behavior of the MOSFET** in the resistive region by plotting I<sub>D</sub> vs. V<sub>DS</sub> for different gate voltages (V<sub>GS</sub>).

#### **Observations from SPICE:**

1. For small V<sub>DS</sub>, I<sub>D</sub> increases linearly — confirming **resistive behavior**.
2. The slope (conductance) increases with higher V<sub>GS</sub>.
3. Beyond a certain V<sub>DS</sub>, curves start bending — indicating the transition toward **saturation region**.

#### **SPICE Applications:**

* Verify the transition between linear and saturation regions.
* Extract device parameters (μₙCₒₓ, V<sub>th</sub>).
* Model transistor resistance for analog design.

---

### **11–L5: Pinch-off Region Condition**

**Pinch-off** occurs when the **channel near the drain end** becomes **depleted of mobile electrons**, stopping any further increase in current with higher V<sub>DS</sub>.

#### **Condition for Pinch-off:**

[
V_{DS} = V_{GS} - V_{th}
]

At this point:

* The voltage difference between gate and drain equals the threshold voltage.
* The inversion layer disappears near the drain.
* The channel “pinches off,” and the current becomes **almost constant**.

#### **After Pinch-off:**

* Increasing V<sub>DS</sub> further causes the pinch-off point to move slightly toward the source.
* The drain current **saturates** (reaches I<sub>D(sat)</sub>).
* The MOSFET enters **saturation region** (or **active region**).

---

### **12–L6: Drain Current Model for Saturation Region of Operation**

Once **pinch-off** occurs, the current becomes **independent of V<sub>DS</sub>** and depends mainly on V<sub>GS</sub>.

#### **Condition:**

[
V_{DS} ≥ (V_{GS} - V_{th})
]

#### **Drain Current Equation (Saturation Region):**

[
I_D = \frac{1}{2} \mu_n C_{ox} \frac{W}{L} (V_{GS} - V_{th})^2
]

#### **Explanation:**

* The current is controlled by the **gate voltage** (V<sub>GS</sub>).
* Increasing V<sub>GS</sub> increases inversion charge and hence current.
* The channel is pinched off at the drain but still conducts due to carrier drift from source to pinch-off point.

#### **Including Channel Length Modulation (λ):**

In reality, I<sub>D</sub> slightly increases with V<sub>DS</sub> due to effective shortening of the channel:
[
I_D = \frac{1}{2} \mu_n C_{ox} \frac{W}{L} (V_{GS} - V_{th})^2 (1 + \lambda V_{DS})
]
where λ = channel length modulation parameter.

---

✅ **Summary Table**

| Region                  | Condition                                                                         | Current Equation                                                             | Behavior           |
| :---------------------- | :-------------------------------------------------------------------------------- | :--------------------------------------------------------------------------- | :----------------- |
| **Cut-off**             | V<sub>GS</sub> < V<sub>th</sub>                                                   | I<sub>D</sub> ≈ 0                                                            | OFF                |
| **Linear (Resistive)**  | V<sub>GS</sub> > V<sub>th</sub>, V<sub>DS</sub> < V<sub>GS</sub> - V<sub>th</sub> | μₙCₒₓ(W/L)[(V<sub>GS</sub>-V<sub>th</sub>)V<sub>DS</sub> - ½V<sub>DS</sub>²] | Acts like resistor |
| **Saturation (Active)** | V<sub>DS</sub> ≥ V<sub>GS</sub> - V<sub>th</sub>                                  | ½μₙCₒₓ(W/L)(V<sub>GS</sub> - V<sub>th</sub>)²                                | Current source     |



**“Introduction to SPICE”**

---

### **13–L1: Basic SPICE Setup**

**SPICE (Simulation Program with Integrated Circuit Emphasis)** is a circuit simulator used to analyze and verify electronic circuits before fabrication.

#### **Purpose of SPICE Setup:**

The SPICE setup provides a framework for defining:

* Circuit elements (transistors, resistors, capacitors, etc.)
* Node connections
* Input sources
* Simulation commands and output requirements

#### **Basic SPICE File Structure (Netlist):**

A SPICE file typically has the following format:

```
* Title line - gives a brief description of the circuit

[Component definitions]
[Power sources]
[Models]
[Simulation commands]
[.end]
```

#### **Example:**

```spice
* Simple NMOS Inverter circuit
VDD 1 0 DC 5
Vin 2 0 PULSE(0 5 0 1n 1n 10n 20n)
M1 3 2 0 0 NMOS L=1u W=10u
M2 3 2 1 1 PMOS L=1u W=20u
.tran 1n 100n
.model NMOS NMOS (LEVEL=1 VTO=1 KP=50u)
.model PMOS PMOS (LEVEL=1 VTO=-1 KP=20u)
.end
```

#### **SPICE Setup Steps:**

1. **Create a text file** (`.cir` or `.sp` extension).
2. **Define circuit components and connections** using node numbers.
3. **Add source definitions** (DC, AC, or transient).
4. **Include device models** (for MOSFETs, BJTs, etc.).
5. **Add analysis commands** (like `.dc`, `.ac`, `.tran`, etc.).
6. **End with `.end` command.**

This setup allows SPICE to interpret and simulate the circuit correctly.

---

### **14–L2: Circuit Description in SPICE Syntax**

SPICE uses a specific **syntax and naming convention** to describe circuits. Each component in SPICE has a **prefix letter** and a defined order of node connections.

#### **Basic Syntax Rules:**

Each line defines one element:

```
ElementName Node1 Node2 [Node3 Node4 ...] Value/ModelName
```

#### **Common Component Prefixes:**

| Element        | Prefix | Example           | Description                |
| :------------- | :----- | :---------------- | :------------------------- |
| Resistor       | R      | R1 1 2 10k        | 10kΩ between node 1 and 2  |
| Capacitor      | C      | C1 2 0 10p        | 10pF from node 2 to ground |
| Inductor       | L      | L1 1 3 1u         | 1 µH between node 1 and 3  |
| Voltage Source | V      | V1 1 0 DC 5       | 5V DC supply               |
| Current Source | I      | I1 2 0 DC 1m      | 1 mA source                |
| MOSFET         | M      | M1 D G S B NMOS   | 4-terminal MOS transistor  |
| BJT            | Q      | Q1 C B E QMODEL   | Bipolar transistor         |
| Diode          | D      | D1 2 0 DMODEL     | Diode with model           |
| Subcircuit     | X      | X1 1 2 my_circuit | Custom circuit block       |

#### **Example Circuit Description:**

```spice
* NMOS Common Source Amplifier
VDD 3 0 DC 5
VIN 2 0 SIN(0 0.01 1k)
M1 3 2 0 0 NMOS L=1u W=10u
.model NMOS NMOS (LEVEL=1 VTO=1 KP=50u)
.tran 1u 10m
.end
```

Here:

* Node 3 → connected to VDD
* Node 2 → gate input
* Node 0 → ground
* `.model` defines transistor parameters

#### **SPICE Syntax Rules Summary:**

* Comments start with `*`
* Node 0 always represents **ground**
* Units are implied (e.g., k = 10³, u = 10⁻⁶)
* Commands start with a dot (`.`)
* Names are **case-insensitive**

---

### **15–L3: Define Technology Parameters**

Technology parameters define **device characteristics** based on fabrication process technology (like 180nm, 90nm, etc.).
These are essential to model how real MOSFETs behave in simulation.

#### **Key Parameters in a MOSFET Model:**

| Parameter | Meaning                            | Typical Value |
| :-------- | :--------------------------------- | :------------ |
| VTO       | Threshold voltage                  | 0.7 V         |
| KP        | Transconductance parameter (μₙCₒₓ) | 50 µA/V²      |
| GAMMA     | Body effect coefficient            | 0.4 V½        |
| LAMBDA    | Channel length modulation          | 0.02          |
| PHI       | Surface potential                  | 0.6 V         |
| TOX       | Oxide thickness                    | 10 nm         |
| UO        | Carrier mobility                   | 500 cm²/V·s   |

#### **Defining Technology in SPICE:**

```spice
.model NMOS NMOS (LEVEL=1 VTO=0.7 KP=50u GAMMA=0.4 LAMBDA=0.02 PHI=0.6)
.model PMOS PMOS (LEVEL=1 VTO=-0.7 KP=20u GAMMA=0.4 LAMBDA=0.02 PHI=0.6)
```

* **LEVEL 1:** Basic analytical model for MOSFETs (used in educational setups).
* Higher levels (LEVEL 3, BSIM3, BSIM4) are used in industry for accuracy.

#### **Purpose of Technology Parameters:**

1. Define **physical behavior** of devices (mobility, threshold, etc.).
2. Simulate circuits **close to real silicon behavior**.
3. Allow scaling between **different CMOS technologies** (e.g., 180nm → 45nm).
4. Used in **PVT (Process, Voltage, Temperature)** variation analysis.

#### **SPICE Example with Technology Parameters:**

```spice
* NMOS with defined technology parameters
VDD 1 0 DC 5
VIN 2 0 DC 2
M1 3 2 0 0 NMOS L=1u W=10u
.model NMOS NMOS (LEVEL=1 VTO=0.7 KP=50u GAMMA=0.4 LAMBDA=0.02 PHI=0.6)
.dc VIN 0 5 0.1
.end
```

This setup allows you to **sweep VIN** and observe **I<sub>D</sub>–V<sub>GS</sub>** characteristics based on technology data.

---

✅ **Summary Overview**

| Lesson    | Topic                               | Key Learning                                                               |
| :-------- | :---------------------------------- | :------------------------------------------------------------------------- |
| **13–L1** | Basic SPICE setup                   | Structure of SPICE netlist and setup steps                                 |
| **14–L2** | Circuit description in SPICE syntax | How to define components and connections using SPICE syntax                |
| **15–L3** | Define technology parameters        | How to describe MOSFET and process characteristics for accurate simulation |

---

*### **16–L4:First Spice Simulation**

<img width="1056" height="185" alt="1 gitclone sky130" src="https://github.com/user-attachments/assets/2d6f01c4-c6d0-412f-a554-65f125498b82" />
<img width="1215" height="683" alt="4 plot -vdd#branch" src="https://github.com/user-attachments/assets/ff19c1a7-9f85-476e-a615-6e7d7eb1fb47" />
<img width="1071" height="625" alt="3 ngspice sky130" src="https://github.com/user-attachments/assets/42f514c5-a260-4249-9ec5-96e11fab0ea6" />
<img width="1023" height="468" alt="2 sudo apt install ngspice" src="https://github.com/user-attachments/assets/ae7b0f08-93f1-4cd7-84dd-a50cf518b6a9" />
