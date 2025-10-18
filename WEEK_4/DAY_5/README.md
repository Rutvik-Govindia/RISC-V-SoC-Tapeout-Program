## Static Behavior Evaluation – CMOS Inverter Robustness – Power Supply Variation

This is how a **CMOS inverter** (the fundamental building block of digital logic) performs and maintains its reliability when the **power supply voltage ($V_{DD}$)** changes. **Static behavior** refers to the circuit's operation when the inputs are held constant, as opposed to dynamic behavior, which considers switching speed and power consumption. **Robustness** here means the circuit's ability to maintain its intended logic function and noise margins despite these variations.

---

## 44-L1 Smart SPICE simulation for power supply variations

This point focuses on the **practical analysis** of the CMOS inverter's robustness using a circuit simulation tool.

* **Smart SPICE** is a commercial or educational version of the widely-used **SPICE** (Simulation Program with Integrated Circuit Emphasis) simulator. These tools are essential for verifying circuit design before fabrication.
* **The Simulation:** This part would involve setting up a simulation of a CMOS inverter circuit. The key technique here would be a **parametric sweep** or **DC sweep** where the power supply voltage ($V_{DD}$) is varied over a range (e.g., from the minimum specified voltage to the maximum).
* **What is analyzed:** The simulation would typically plot the **Voltage Transfer Characteristic (VTC)** of the inverter for different $V_{DD}$ values. From the VTC, one can extract critical static parameters like:
    * **Noise Margins ($NM_L$ and $NM_H$):** How much noise the circuit can tolerate before an incorrect logic level is read.
    * **Trip Voltage ($V_M$):** The input voltage where the output voltage is equal to the input voltage, typically the switching point.
    * The goal is to show **quantitatively** how these parameters degrade or improve as the power supply varies, demonstrating the inverter's robustness.

---

## 45-L2 Advantages and disadvantages using low supply voltage

This point delves into the **design trade-offs** associated with operating a CMOS circuit at a lower power supply voltage ($V_{DD}$). This is a critical topic in modern digital design, especially for portable and low-power applications.

### Advantages of Low Supply Voltage

* **Reduced Power Consumption:** This is the primary driver. Power dissipation in CMOS circuits has a strong quadratic dependence on $V_{DD}$ (for dynamic power: $P_{dynamic} \propto C_{load} \cdot V_{DD}^2 \cdot f$). Cutting $V_{DD}$ dramatically reduces power.
* **Longer Battery Life:** Directly related to reduced power, lower $V_{DD}$ extends the operational time for battery-powered devices.
* **Reduced Heat Dissipation:** Lower power means less heat generated, simplifying thermal management and improving circuit reliability.
* **Improved Manufacturing Yield (in some cases):** Operating at lower voltages can sometimes reduce the stress on thin gate oxides.

### Disadvantages of Low Supply Voltage

* **Slower Operation (Increased Delay):** The speed of a CMOS circuit is inversely proportional to $V_{DD}$ (i.e., $t_d \propto \frac{V_{DD}}{(V_{DD}-V_{T})^2}$), where $V_T$ is the threshold voltage. As $V_{DD}$ approaches $V_T$, the speed drops drastically.
* **Reduced Noise Margins:** A lower $V_{DD}$ means the difference between a high voltage level and a low voltage level is smaller, which directly reduces the **noise margins** and makes the circuit more susceptible to noise and process variation.
* **Increased Subthreshold Leakage Power:** To compensate for the speed loss, the threshold voltage ($V_T$) is often reduced, which leads to an exponential increase in **leakage current** (static power consumption) when the transistor is nominally "off."
* **Sensitivity to Process Variation:** Circuits operating near the threshold voltage are much more sensitive to manufacturing variations in transistor parameters ($V_T$, channel length, etc.), which can lead to larger variations in speed and power across different manufactured chips.

---

## 46-L3 Sky130 Supply Variation Labs

-> ngspice day5_inv_supplyvariation_Wp1_Wn036.spice
<img width="1213" height="671" alt="1 ngspice day_5 supply variation" src="https://github.com/user-attachments/assets/c33640c4-bea8-46f1-a88a-b09270b0f8f1" />

-> Input Voltage vs Output Voltage
<img width="1213" height="678" alt="2 input voltage vs output voltage" src="https://github.com/user-attachments/assets/d6e19330-a40d-4e59-9e2d-f45104492282" />

-> Calculating Gain
<img width="303" height="105" alt="3 Calculating Gain" src="https://github.com/user-attachments/assets/eab88877-c5c0-418f-b192-8d9719ce7df2" />

Subtracting Y values : 1.69 - 0.11 = 1.58

Now

Subtracting X values : 0.78 - 0.97 = -0.19

So;
The ratio of $1.58$ to $-0.19$ is approximately **$-8.32$**.

$$
\text{Ratio} = \frac{1.58}{-0.19} \approx -8.315789...
$$
