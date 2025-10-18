## Static behavior evaluation - CMOS inverter robustness - Noise Margin

---

### 39-L1 Introduction to noise margin

This topic introduces the concept of **Noise Margin (NM)**. It defines NM as a measure of a logic circuit's ability to tolerate noise voltages on its inputs without causing the output voltage to move into the indeterminate or incorrect logic region. It explains why a large noise margin is vital for reliable operation in digital systems, especially in noisy environments or when signals travel over long wires.

***

### 40-L2 Noise margin voltage parameters

This section defines the four key voltage points on the **Voltage Transfer Characteristic (VTC)** curve of the inverter that are used to calculate the noise margins:

1.  **$V_{OH}$ (Output High Voltage):** The minimum voltage that the inverter outputs when it's supposed to be a logic '1'. Ideally, this is $V_{DD}$.
2.  **$V_{OL}$ (Output Low Voltage):** The maximum voltage that the inverter outputs when it's supposed to be a logic '0'. Ideally, this is $0\text{ V}$.
3.  **$V_{IH}$ (Input High Voltage):** The minimum input voltage that is recognized by the next gate as a logic '1'. This is the point where the VTC slope is $-1$ in the high-to-low transition.
4.  **$V_{IL}$ (Input Low Voltage):** The maximum input voltage that is recognized by the next gate as a logic '0'. This is the point where the VTC slope is $-1$ in the low-to-high transition.

***

### 41-L3 Noise margin equation and summary

This covers the formal calculation of the two noise margins:

* **High Noise Margin ($NM_H$):** Measures noise tolerance when the input is a logic '0' (output is a logic '1').
    $$\text{NM}_H = V_{OH} - V_{IH}$$
* **Low Noise Margin ($NM_L$):** Measures noise tolerance when the input is a logic '1' (output is a logic '0').
    $$\text{NM}_L = V_{IL} - V_{OL}$$

The topic will also provide a **summary** of noise margin principles, emphasizing that for an optimal and robust design, $NM_H$ should ideally be equal to $NM_L$, which is achieved when the switching threshold ($V_m$) is close to $V_{DD}/2$.

***

### 42-L4 Noise margin variation with respect to PMOS width

This point is a design analysis, investigating how **sizing the pMOS transistor** (by changing its width, $W_p$) affects the noise margins.

* Increasing the **pMOS width** ($W_p$) **increases its driving strength**.
* This shifts the **Switching Threshold ($V_m$)** towards **$0\text{ V}$**.
* This shift generally leads to an **increase in the Low Noise Margin ($NM_L$)** and a **decrease in the High Noise Margin ($NM_H$)**, making the inverter **skewed** towards a logic '1' input.