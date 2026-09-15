# Analog_AC-DC_Converter
# LTspice Full-Wave AC-DC Converter Simulation

This project contains the schematic and simulation files for a **Full-Wave AC-DC Converter** designed using [LTspice](https://analog.com). The circuit converts an alternating current (AC) input voltage into a steady direct current (DC) output voltage using a **two-diode configuration** and a **smoothing capacitor**.

---

## 🛠️ Circuit Topology
This converter utilizes a **Center-Tapped Full-Wave Rectifier** configuration, which requires exactly two diodes to achieve full-wave rectification.

### Core Components
* **Center-Tapped Transformer / Dual Sources:** Provides two equal AC voltage signals that are 180 degrees out of phase with respect to the center tap (ground).
* **Two Diodes ($D_1$ and $D_2$):** Act as directional switches. 
  * $D_1$ conducts during the positive half-cycle of the primary input.
  * $D_2$ conducts during the negative half-cycle of the primary input.
  * Together, they route both halves of the AC wave in the same direction toward the load.
* **Smoothing Capacitor ($C$):** Connected in parallel with the load. It charges up to the peak voltage during the conduction phases and slowly discharges into the load when the rectified voltage drops, drastically reducing output ripple.
* **Load Resistor ($R$):** Simulates the device or circuit drawing power from the DC output.

---

## 📈 Circuit Operation & Waveform Behavior

### 1. Rectification Stage (Without Capacitor)
If the capacitor is removed, the two diodes convert the sinusoidal AC input ($V_{peak} \sin(\omega t)$) into a **pulsating DC signal**. Both the positive and negative halves of the AC cycle are flipped upright. 
* **Peak Output Voltage:** $V_{out(peak)} = V_{peak} - V_d$ *(where $V_d$ is the ~0.7V forward voltage drop of the diode)*.

### 2. Smoothing Stage (With Capacitor)
When the capacitor is added, it acts as a low-pass filter:
* **Charging:** As the rectified voltage rises toward its peak, the diodes turn on and quickly charge the capacitor to $V_{out(peak)}$.
* **Discharging:** As the input voltage drops past its peak, the diodes become reverse-biased and turn off. The capacitor steps in to supply current to the load resistor ($R$). Because it discharges slowly, it prevents the output voltage from dropping to zero.
* **The Result:** A smooth, stable DC output voltage with a small, manageable **Ripple Voltage ($V_{ripple}$)**.

---

## 🚀 How to Run the Simulation
1. Download and install **LTspice**.
2. Clone this repository to your machine.
3. Open the `.asc` schematic file in LTspice.
4. Click the **Run** icon (the running man) to execute the transient analysis (`.tran`).
5. Use the voltage probe to click on:
   * The **AC inputs** to see the dual-phase sine waves.
   * The **Output node** (across the capacitor/resistor) to observe the smooth DC output and measure the ripple voltage.
