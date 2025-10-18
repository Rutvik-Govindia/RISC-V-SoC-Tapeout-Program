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

---

## Static Behavior Evaluation – CMOS Inverter Robustness – Device Variation

It indicates an analysis of how a **CMOS inverter** (a fundamental digital logic gate) performs under **static** (non-switching) conditions. The core focus is on its **robustness**, meaning its ability to maintain correct operation despite **device variations**—the inevitable differences in physical characteristics between individual transistors that arise during the manufacturing process.

---

### 47-L1 Sources of variation – Etching process

This point addresses one of the primary origins of manufacturing variability: the **etching process**.

* **Description:** During semiconductor fabrication, etching is used to define the geometric features of the transistors (like the gate length and width) by selectively removing material. Inconsistencies in this process—such as variations in etch rate, over-etching, or under-etching—lead to deviations in the actual **physical dimensions** of the PMOS and NMOS transistors in the inverter.
* **Impact:** These dimensional variations directly affect the transistor's **drive current** and **threshold voltage** ($V_{th}$), thereby shifting the inverter's **Voltage Transfer Characteristic (VTC)** and potentially degrading critical parameters like **noise margins** and **switching point**.

---

### 48-L2 Sources of variation – Oxide thickness

This point covers the second major source of device variation: the **gate oxide thickness** ($t_{ox}$).

* **Description:** The gate oxide layer (typically silicon dioxide, $\text{SiO}_2$) acts as the insulator between the gate terminal and the channel. Its thickness is crucial as it determines the **gate capacitance** ($C_{ox}$) of the transistor. Slight variations in the deposition or growth process can cause $t_{ox}$ to be non-uniform across the wafer or from batch to batch.
* **Impact:** Since $C_{ox}$ is inversely proportional to $t_{ox}$, variations in oxide thickness cause changes in the transistor's **transconductance** and, most importantly, the **threshold voltage** ($V_{th}$). Thinner oxide often leads to a lower $V_{th}$ and a higher drive current, which again shifts the inverter's **VTC** and impacts its static behavior and robustness.

---

### 49-L3 Smart SPICE simulation for device variations

This section details the **methodology** used to analyze the effects of the variations discussed in L1 and L2.

* **Description:** **SPICE (Simulation Program with Integrated Circuit Emphasis)** is the industry-standard tool for analog and mixed-signal circuit simulation. A **"Smart" SPICE** simulation (likely referring to advanced techniques like **Monte Carlo analysis** or **Corner Analysis**) is used here to model the combined impact of the statistical variations (e.g., in gate length and oxide thickness) on the CMOS inverter's static performance.
* **Objective:** The simulation generates many instances of the inverter, each with slightly different parameters based on the expected manufacturing tolerances. This allows engineers to statistically determine the **yield** and **robustness** of the design by checking how many instances fail to meet the required static specifications (like minimum noise margins).

---

### 50-L4 Conclusion

* **Content:** The conclusion would typically **summarize the key findings** from the SPICE simulations, quantify the degree to which etching and oxide thickness variations impact the CMOS inverter's static performance (e.g., how much the noise margins degrade). It would also likely propose **design-for-manufacturability (DFM)** techniques or **design guidelines** (like using larger devices or specific design rules) necessary to ensure the inverter remains robust and reliable in a real-world manufacturing environment.

---

## 51-L5 Sky130 Device Variation Labs

-> ngspice day5_inv_devicevariation_wp7_wn042.spice
<img width="1212" height="663" alt="4 ngspice day5_inv_devicevariation_wp7_wn042 spice" src="https://github.com/user-attachments/assets/d296ccc8-aa0d-430f-899d-eb1aa17d6fe1" />

-> plot out vs in
<img width="1212" height="663" alt="5 plot out vs in" src="https://github.com/user-attachments/assets/456c3b89-6dc5-47a1-99d3-2730fac76fad" />

-> Zoomed plot out vs in
<img width="1212" height="663" alt="6 Zoomed plot out vs in" src="https://github.com/user-attachments/assets/dc1dad5a-e617-4ace-8f89-38dae0a507c5" />

-> Calculating Switching Thresold
<img width="595" height="135" alt="7 Calculating Switching Thresold" src="https://github.com/user-attachments/assets/b1e03325-6e93-4ec7-8a49-53990f56c007" />
Therefore Swtiching Thresold = 0.98
