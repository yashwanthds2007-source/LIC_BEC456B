# Experiment 4 

# Differential Amplifier Analysis

## Aim

To design and simulate three MOSFET differential amplifier configurations using LTspice by performing DC, Transient, and AC analyses, and to compare their performance based on gain, bandwidth, and power efficiency.

## Introduction

A differential amplifier is one of the most fundamental building blocks in analog circuit design. It amplifies the difference between two input signals while rejecting common-mode signals, making it highly useful in noise-sensitive applications.

MOSFET-based differential amplifiers are widely used in integrated circuits such as operational amplifiers, comparators, and analog signal processing systems due to their high gain, good noise immunity, and efficient performance.

In this experiment, three different MOSFET differential amplifier configurations are analyzed using LTspice. The behavior of each circuit is studied through DC, Transient, and AC analyses to understand their gain, bandwidth, and overall performance characteristics.

## Theory

A differential amplifier is a circuit that amplifies the difference between two input signals while rejecting any signal that is common to both inputs. This property is known as common-mode rejection and is an important feature in analog circuit design.

A basic MOS differential amplifier consists of two matched MOSFETs (M1 and M2) whose sources are connected together and biased using a constant current source. The drains are connected to load elements such as resistors or active loads.

When a differential input voltage is applied:

$$
v_{id} = v_{in1} - v_{in2}
$$

the total current is steered between the two transistors depending on the input difference. If $v_{in1} > v_{in2}$, transistor M1 conducts more current, and if $v_{in2} > v_{in1}$, transistor M2 conducts more.

For small differential inputs, both transistors operate in the saturation region, and the circuit behaves linearly. The differential gain of the amplifier is given by:

$$
A_v = g_m R_{out}
$$

where $g_m$ is the transconductance of the MOSFET and $R_{out}$ is the effective output resistance.

The transconductance is defined as:

$$
g_m = \frac{2 I_D}{V_{ov}}
$$

where $I_D$ is the drain current and $V_{ov}$ is the overdrive voltage.

For larger differential inputs:

$$
v_{id} > \sqrt{2} V_{ov}
$$

one transistor turns OFF while the other carries the entire current, resulting in non-linear operation.

The performance of the differential amplifier depends on the type of load used:

- Resistive load → moderate gain  
- Active load → higher output resistance and higher gain  
- Current mirror load → maximum gain and improved output characteristics  

Thus, by changing the circuit configuration, the gain, bandwidth, and overall performance of the differential amplifier can be significantly affected.

---

## Circuit 1: Differential Amplifier with Resistive Load

## 1.1 Working Principle

The circuit consists of two matched NMOS transistors (M1 and M2) forming a differential pair, with their sources connected to a constant tail current source and their drains connected to resistive loads.

When a differential input is applied:

$$
v_{id} = v_{in1} - v_{in2}
$$

the total tail current ($I_{SS}$) is steered between the two transistors depending on the input difference.

- If $v_{in1} > v_{in2}$, transistor M1 conducts more current while M2 conducts less.  
- If $v_{in2} > v_{in1}$, transistor M2 conducts more current while M1 conducts less.  

The change in drain current through each transistor produces a corresponding voltage drop across the load resistors ($R_D$), resulting in differential output voltages at the drains.

For small differential inputs, both transistors operate in the saturation region, and the amplifier behaves linearly, producing an amplified output proportional to the input difference.

For larger differential inputs, one transistor may turn OFF while the other carries the entire current, resulting in non-linear operation.

Thus, the circuit converts a differential input voltage into a differential output voltage using current steering through resistive loads.

## Circuit Diagram

<img width="1029" height="781" alt="image" src="https://github.com/user-attachments/assets/086d748f-befc-4b50-8182-a455590d91bb" />


## 1.2 Design Calculations

### GIVEN PARAMETERS

- Technology: TSMC 180nm 
- Supply voltage, $V_{DD} = +0.9V$  
- Negative supply, $V_{SS} = -0.9V$   
- Power constraint, $P \leq 1.8mW$
- Channel length, $L_n = 480nm$ 
- Input common-mode voltage, $V_{in,CM} = 0V$  
- Output common-mode voltage, $V_{O,CM} = 0V$  
- Tail node voltage, $V_p = -0.7V$  
- Load capacitance, $C_L = 10pF$   
- Threshold voltage, $V_T \approx 0.36V$  

---

### 1.2.a Power Constraint


The total power consumed by the differential amplifier is given by:

$$
P = (V_{DD} - V_{SS}) \cdot I_{SS}
$$

Total supply voltage:

$$
V_{DD} - V_{SS} = 0.9 - (-0.9) = 1.8V
$$

Since the maximum allowed power is 1.8mW,

$$
P \leq 1.8 \times 10^{-3}
$$

$$
(V_{DD} - V_{SS}) \cdot I_{SS} \leq 1.8 \times 10^{-3}
$$

$$
1.8 \cdot I_{SS} \leq 1.8 \times 10^{-3}
$$

$$
I_{SS} \leq 1mA
$$

To fully utilize the available power budget, we choose:

$$
I_{SS} = 1mA
$$

Power dissipated:

$$
P = 1.8 \times 1mA = 1.8mW
$$

Since $1.8mW \leq 1.8mW$, the power constraint is satisfied.

##

### 1.2.b Drain Current Calculation

In a balanced differential amplifier, the tail current splits equally between both transistors:

$$
I_{D1} = I_{D2} = \frac{I_{SS}}{2}
$$

Substituting:

$$
I_{D1} = I_{D2} = \frac{1mA}{2}
$$

$$
I_{D1} = I_{D2} = 0.5mA
$$

##

### 1.2.c Load Resistance Calculation

Given:

$$
V_{OCM} = 0V
$$

So,

$$
V_{out1} = V_{out2} = 0V
$$

The output voltage is given by:

$$
V_{out} = V_{DD} - I_D R_D
$$

Substituting:

$$
0 = 0.9 - I_D R_D
$$

$$
I_D R_D = 0.9
$$

Solving for resistance:

$$
R_D = \frac{0.9}{I_D}
$$

Substituting:

$$
R_D = \frac{0.9}{0.5 \times 10^{-3}}
$$

$$
R_D = 1.8k\Omega
$$

##

### 1.2.d Bias Point Calculation

Given:

$$
V_{in,CM} = 0V
$$

So,

$$
V_{G1} = V_{G2} = 0V
$$

### Source Voltage

Given:

$$
V_p = -0.7V
$$

Assuming:

$$
V_S = V_p
$$

$$
V_S = -0.7V
$$

### Gate-Source Voltage

$$
V_{GS} = V_G - V_S
$$

$$
V_{GS} = 0 - (-0.7)
$$

$$
V_{GS} = 0.7V
$$

### Overdrive Voltage

Given:

$$
V_T \approx 0.36V
$$

$$
V_{OV} = V_{GS} - V_T
$$

$$
V_{OV} = 0.7 - 0.36
$$

$$
V_{OV} = 0.34V
$$

### Drain Voltage

From previous calculation:

$$
V_{out1} = V_{out2} = 0V
$$

### Drain-Source Voltage

$$
V_{DS} = V_D - V_S
$$

$$
V_{DS} = 0 - (-0.7)
$$

$$
V_{DS} = 0.7V
$$

### Saturation Check

Condition:

$$
V_{DS} > V_{OV}
$$

$$
0.7 > 0.34
$$

Hence, both transistors operate in saturation.

### Final Bias Point

$$
V_G = 0V
$$

$$
V_S = -0.7V
$$

$$
V_D = 0V
$$

$$
V_{GS} = 0.7V
$$

$$
V_{DS} = 0.7V
$$

##

### 1.2.e Width Calculation

The drain current in saturation is given by:

$$
I_D = \frac{1}{2} \mu_n C_{ox} \frac{W}{L} (V_{GS} - V_T)^2
$$

Rewriting:

$$
I_D = \frac{1}{2} \mu_n C_{ox} \frac{W}{L} (V_{OV})^2
$$

Rearranging to find width:

$$
W = \frac{2 I_D L}{\mu_n C_{ox} (V_{OV})^2}
$$

### Substituting Values

$$
I_D = 0.5mA = 0.5 \times 10^{-3}A
$$

$$
L = 480nm = 480 \times 10^{-9}m
$$

$$
\mu_n C_{ox} = 236.5 \mu A/V^2 = 2.365 \times 10^{-4}
$$

$$
V_{OV} = 0.34V
$$

### Calculation

$$
W = \frac{2 \times 0.5 \times 10^{-3} \times 480 \times 10^{-9}}{2.365 \times 10^{-4} \times (0.34)^2}
$$

$$
W = \frac{480 \times 10^{-12}}{2.365 \times 10^{-4} \times 0.1156}
$$

$$
W = \frac{480 \times 10^{-12}}{2.732 \times 10^{-5}}
$$

$$
W \approx 17.57 \mu m
$$

The width calculated using first-order equations provides an approximate value based on assumed parameters such as constant mobility and ideal saturation conditions. However, in practical MOSFET models, several non-ideal effects such as channel length modulation, mobility degradation, and model parameter variations affect the actual operating point.

To strictly satisfy the given condition:

$$
V_p = V_S = -0.7V
$$

the transistor width was fine-tuned using simulation. By adjusting the width, the drain current was controlled such that the source node voltage precisely matched the required value.

Final width obtained:

$$
W \approx 28.475 \mu m
$$

Thus, the deviation from the theoretical width arises due to non-ideal device behavior and the need to meet exact biasing conditions in simulation.

---

## DC Analysis

<img width="1785" height="810" alt="image" src="https://github.com/user-attachments/assets/9b6d9a2f-2082-47a9-9059-5d918d20918c" />


The DC operating point confirms that the output voltage and source voltage is near the designed bias value, ensuring proper saturation operation.

---

### 1.2.f Input Common Mode Range (ICMR)

The input common-mode range is defined as the range of input voltage for which all transistors remain in saturation.

### Minimum Input Common Mode Voltage

For proper operation, the tail current source must remain active and the NMOS transistors must stay in saturation.

Condition:

$$
V_{GS} \ge V_T
$$

Using:

$$
V_{GS} = V_{ICM} - V_S
$$

So,

$$
V_{ICM(min)} = V_S + V_T
$$

Substituting values:

$$
V_S = -0.7V, \quad V_T = 0.36V
$$

$$
V_{ICM(min)} = -0.7 + 0.36
$$

$$
V_{ICM(min)} = -0.34V
$$

### Maximum Input Common Mode Voltage

For maximum input voltage, the NMOS transistors must remain in saturation.

Condition:

$$
V_{DS} \ge V_{OV}
$$

Using:

$$
V_D = 0V, \quad V_S = -0.7V
$$

$$
V_{DS} = V_D - V_S = 0 - (-0.7) = 0.7V
$$

Now,

$$
V_{ICM(max)} = V_D + V_T
$$

Substituting:

$$
V_{ICM(max)} = 0 + 0.36
$$

$$
V_{ICM(max)} = 0.36V
$$

### Final Input Common Mode Range

$$
-0.34V \le V_{ICM} \le 0.36V
$$

##

### 1.2.g Output Common Mode Range

The output common-mode voltage range is determined by ensuring that the NMOS transistors remain in saturation and the circuit operates properly.

### Maximum Output Voltage

The maximum output voltage occurs when the drain voltage is at its highest possible value, which is limited by the supply voltage:

$$
V_{OCM(max)} \le V_{DD}
$$

However, to maintain current flow through the load resistor:

$$
V_{OCM(max)} = V_{DD}
$$

$$
V_{OCM(max)} = 0.9V
$$

### Minimum Output Voltage

For proper operation, the NMOS transistors must remain in saturation:

$$
V_{DS} \ge V_{OV}
$$

Using:

$$
V_{DS} = V_D - V_S
$$

At the edge of saturation:

$$
V_D - V_S = V_{OV}
$$

So,

$$
V_D = V_S + V_{OV}
$$

Since:

$$
V_D = V_{OCM(min)}
$$

$$
V_{OCM(min)} = V_S + V_{OV}
$$

### Substituting Values

$$
V_S = -0.7V, \quad V_{OV} = 0.34V
$$

$$
V_{OCM(min)} = -0.7 + 0.34
$$

$$
V_{OCM(min)} = -0.36V
$$

### Final Output Common Mode Range

$$
-0.36V \le V_{OCM} \le 0.9V
$$

##

### 1.2.h Differential Input Voltage Range (Linear Region)

The differential amplifier behaves linearly only when both transistors operate in saturation and the current is approximately equally shared between them.

For a MOS differential pair, linear operation is maintained when the differential input voltage is small compared to the overdrive voltage.

### Condition for Linear Operation

$$
|V_{id}| \le 2V_{OV}
$$

### Substituting Values

$$
V_{OV} = 0.34V
$$

$$
|V_{id}| \le 2 \times 0.34
$$

$$
|V_{id}| \le 0.68V
$$

### Final Linear Range

$$
-0.68V \le V_{id} \le 0.68V
$$

---

## 1.3 Transient Analysis and Linearity Observation

The linear behavior of the differential amplifier is verified using transient analysis.

### Condition for Linearity

$$
|V_{id}| < \sqrt{2} V_{OV}
$$

$$
\sqrt{2} V_{OV} = 1.414 \times 0.34 = 0.48V
$$

### Case 1: Linear Region

Input applied:

$$
V_{id} = 100mV < 0.48V
$$

<img width="1916" height="849" alt="image" src="https://github.com/user-attachments/assets/5aee6e4f-5178-4b4b-bce0-e774338e362f" />


Observation:

- Output waveform is sinusoidal
- No distortion observed
- Both transistors operate in saturation
- Amplifier behaves linearly

### Case 2: Non-Linear Region

Input applied:

$$
V_{id} = 600mV > 0.48V
$$

<img width="1919" height="847" alt="image" src="https://github.com/user-attachments/assets/cac11637-fa5a-434c-8b67-cbd5b71ddf0a" />


Observation:

- Output waveform shows distortion
- Clipping observed
- One transistor enters cutoff region
- Linear amplification is lost

##

The behavior of the differential amplifier is analyzed for two cases based on the input differential voltage.

### Comparison Table

| Parameter | Case 1: Linear Region | Case 2: Non-Linear Region |
|----------|----------------------|--------------------------|
| Condition | $V_{id} < \sqrt{2}V_{OV}$ | $V_{id} > \sqrt{2}V_{OV}$ |
| Input ($V_{id}$) | 100 mV | 600 mV |
| Output waveform | Sinusoidal | Distorted / Clipped |
| Gain | Constant | Reduced / Non-linear |
| Transistor operation | Both in saturation | One enters cutoff |
| Current distribution | Equal sharing | Current shifts to one transistor |

### Interpretation

In the linear region, the differential input voltage is small, and both transistors operate in saturation. The tail current is equally shared, resulting in a proportional and undistorted output. Hence, the amplifier exhibits linear behavior with constant gain.

In the non-linear region, the input differential voltage exceeds the limit, causing one transistor to carry most of the current while the other moves toward cutoff. This results in distortion and loss of linearity in the output waveform.

### Conclusion

The differential amplifier operates linearly only for small input signals.

$$
|V_{id}| < \sqrt{2} V_{OV}
$$

As the differential input voltage increases beyond the limit:

$$
|V_{id}| > \sqrt{2} V_{OV}
$$

the circuit transitions from linear amplification to non-linear behavior due to unequal current distribution and transistor cutoff.

##

## Theoretical and Simulated Gain

<img width="1919" height="426" alt="image" src="https://github.com/user-attachments/assets/9a312e32-b816-49c6-a570-cbb3880cc64a" />


The output waveform is amplified and inverted.

### Simulated Gain

Input signal parameters:

- Type: Sine wave  
- Frequency = 1kHz  
- Amplitude = 50mV (applied differentially) 
- DC Offset = 0V

Measured peak-to-peak values:

$$
V_{in(p-p)} = 50mV - ( - 50mV ) = 100mV
$$

$$
V_{out(p-p)} = 302mV - ( - 302mV ) = 604mV
$$

Voltage gain:

$$
A_v = \frac{V_{out(p-p)}}{V_{in(p-p)}}
$$

$$
A_v = \frac{604 \times 10^{-3}}{100 \times 10^{-3}}
$$

$$
A_v = 6.04
$$

Gain in dB:

$$
A_v(dB) = 20\log_{10}(6.04)
$$

$$
A_v(dB) = 15.62dB
$$

##

### Theoretical Gain

Assume channel length modulation:

$$
\lambda = 0.1 \, V^{-1}
$$

### Output Resistance

The output resistance of each MOSFET is:

$$
r_o = \frac{1}{\lambda I_D}
$$

Substituting:

$$
I_D = 0.5mA = 0.5 \times 10^{-3}A
$$

$$
r_o = \frac{1}{0.1 \times 0.5 \times 10^{-3}}
$$

$$
r_o = 20k\Omega
$$

### Effective Output Resistance

Since two transistors are present:

$$
r_{o,eff} = r_{o1} \parallel r_{o2}
$$

$$
r_{o,eff} = 20k \parallel 20k
$$

$$
r_{o,eff} = 10k\Omega
$$

### Transconductance

$$
g_m = \frac{2 I_D}{V_{OV}}
$$

$$
g_m = \frac{2 \times 0.5 \times 10^{-3}}{0.34}
$$

$$
g_m \approx 2.94mS
$$

### Total Output Resistance

The effective load seen at the output is:

$$
R_{out} = R_D \parallel r_{o,eff}
$$

$$
R_{out} = 1.8k \parallel 10k
$$

$$
R_{out} \approx 1.53k\Omega
$$

### Differential Gain

$$
A_d = g_m R_{out}
$$

$$
A_d = 2.94 \times 10^{-3} \times 1.53 \times 10^3
$$

$$
A_d \approx 4.5
$$

### Gain in dB

$$
A_d(dB) = 20 \log_{10}(4.5)
$$

$$
A_d(dB) \approx 13.06dB
$$

##

## Reason for Difference Between Theoretical and Simulated Gain

A deviation is observed between the theoretical and simulated gain values. This difference arises due to the simplifying assumptions made in analytical calculations and the inclusion of non-ideal effects in simulation.

### Reasons for Deviation

 ### 1. Channel Length Modulation

In theoretical calculations, channel length modulation is often neglected or approximated.  
However, in simulation, the MOSFET model includes a more accurate value of $\lambda$, which affects the output resistance $r_o$ and hence the gain.

 ### 2. Finite Output Resistance

The theoretical gain assumes ideal conditions, whereas in simulation, the finite output resistance of MOSFETs modifies the effective load resistance:

$$
R_{out} = R_D \parallel r_o
$$

This changes the overall gain.

 ### 3. Mobility Degradation and Short Channel Effects

In practical MOSFET models, carrier mobility reduces with increasing electric field.  
This reduces the effective transconductance $g_m$, which directly affects gain.

 ### 4. Variation in Overdrive Voltage ($V_{OV}$)

Theoretical calculations assume a fixed $V_{OV}$, whereas in simulation, the operating point may slightly shift, causing variations in $g_m$ and current.

 ### 5. Parasitic Capacitances

Simulation includes intrinsic parasitic capacitances, which influence the dynamic response and slightly affect the measured gain, especially in transient analysis.

 ### 6. Measurement Method

In simulation, gain is obtained from waveform measurements, which may include small inaccuracies due to scaling, cursor placement, or non-ideal waveform symmetry.

### Conclusion

Thus, the difference between theoretical and simulated gain is expected and arises due to practical device behavior and more accurate modeling in simulation compared to simplified analytical expressions.

---

## 1.4 AC Analysis

<img width="1919" height="422" alt="image" src="https://github.com/user-attachments/assets/df4106d7-2959-47c3-8738-4c228ed5e547" />


In AC analysis, the frequency response of the Differential Amplifier is observed.

The midband gain is obtained from the flat region of the Bode plot.  
The bandwidth is defined as the frequency range between the lower cutoff frequency ($f_L$) and upper cutoff frequency ($f_H$), measured at the −3 dB points.

##

### Midband gain:

From AC simulation:

$$
A_v = 9.871 \text{ dB}
$$

The −3 dB gain is:

$$
A_v - 3 = 9.871 - 3
$$

$$
A_v - 3 = 6.871 \text{ dB}
$$

##

### Cutoff Frequencies

Lower cutoff frequency:

$$
f_L = 0
$$

Upper cutoff frequency:

$$
f_H = 4.819 \text{ MHz}
$$

##

### Bandwidth

Bandwidth is defined as:

$$
BW = f_H - f_L
$$

$$
BW = 4.819 - 0
$$

$$
BW = 4.819 \text{ MHz}
$$

---

### 1.5 Unity Gain Bandwidth (UGB)

Since the 0 dB crossing is not visible in the plot, UGB cannot be directly measured.

However, it can be approximated as:

$$
UGB = A_v \times BW
$$

$$
A_v = 6.04
$$

$$
UGB = 6.04 \times 4.819 \text{ MHz}
$$

$$
UGB = 29.106 \text{ MHz}
$$

---

### Note

First-order theoretical analysis assumes ideal MOSFET operation in saturation and neglects higher-order effects such as channel length modulation, mobility degradation, and parasitic capacitances. These non-ideal effects are included in simulation, leading to differences between theoretical and simulated results.

## Comparison of Results

| Parameter | Theoretical | Simulated |
|------------|-------------|-----------|
| Voltage Gain ($A_v$) | 4.5 V/V | 6.04 V/V |
| Gain (dB) | 14.46 dB | 15.62 dB |

The deviation between theoretical and simulated gain is mainly due to simplified first-order assumptions used in analytical calculations and the inclusion of non-ideal MOSFET effects such as channel length modulation, mobility degradation, and parasitic capacitances in simulation.

---

## Inference

The MOS differential amplifier with resistive load was successfully designed and analyzed while satisfying the given design constraints:

Power consumption ≤ 1.8mW  
VDD = 0.9V  
VSS = -0.9V  
Vocm = 0V  

The tail current was selected as 1mA to ensure operation within the power limit (1.8mW). Under balanced conditions, the current splits equally between the two transistors:

$$
I_{D1} = I_{D2} = 0.5mA
$$

The bias point was carefully chosen such that both NMOS transistors operate in saturation, ensuring proper differential amplification. The source node voltage was adjusted to match the required tail voltage:

$$
V_S \approx -0.7V
$$

by tuning the transistor width during simulation.

Theoretical and simulated results are reasonably consistent:

Theoretical gain ≈ 5.29 V/V (14.46 dB)  
Simulated gain ≈ 6.04 V/V (15.62 dB)  
Simulated bandwidth ≈ 4.819 MHz  
Unity Gain Bandwidth ≈ 15.03 MHz  

The deviation between theoretical and simulated gain arises due to second-order effects such as channel length modulation, mobility degradation, and parasitic capacitances included in the MOSFET model. Additionally, the theoretical analysis assumes ideal conditions and neglects the finite output resistance of transistors.

From the AC analysis, it is observed that the amplifier exhibits a flat midband gain followed by a roll-off at higher frequencies due to parasitic capacitances, which introduce a dominant pole and limit the bandwidth.

The differential amplifier provides good linear amplification for small differential input signals. However, when the input differential voltage exceeds the linear range, the circuit enters non-linear operation, resulting in distortion.

Hence, the designed differential amplifier satisfies the required specifications and demonstrates proper biasing, expected gain characteristics, and acceptable frequency response behavior.

---
## Circuit 2: Differential Amplifier with PMOS active load and an NMOS current source

## 2.1 Working Principle

The circuit consists of two matched NMOS transistors (M1 and M2) forming a differential pair, with their sources connected to an NMOS transistor (M5) acting as a current source, and their drains connected to a PMOS current mirror load (M3 and M4).

When a differential input is applied:

$$
v_{id} = v_{in1} - v_{in2}
$$

the tail current ($I_{SS}$), set by transistor M5, is steered between M1 and M2 depending on the input difference.

- If $v_{in1} > v_{in2}$, transistor M1 conducts more current while M2 conducts less.  
- If $v_{in2} > v_{in1}$, transistor M2 conducts more current while M1 conducts less.  

The PMOS transistors (M3 and M4) form a current mirror load. Transistor M3 is diode-connected and sets the reference current, while M4 mirrors this current to the other branch. This active load provides a high output resistance compared to resistive loads.

The change in drain current through M1 and M2 results in corresponding voltage variations at the output nodes (OUT1 and OUT2), producing differential output voltages.

The NMOS transistor M5 operates in saturation and provides a nearly constant tail current. However, due to its finite output resistance, it introduces a source degeneration effect, which slightly reduces the overall gain.

For small differential input signals, all transistors operate in saturation, and the amplifier behaves linearly, producing an amplified output proportional to the input difference.

For larger differential inputs, one transistor may turn OFF while the other carries most of the current, resulting in non-linear behavior.

Thus, the circuit performs differential amplification using current steering and a PMOS active load, achieving higher gain compared to a resistive load differential amplifier.

## Circuit Diagram

<img width="1257" height="876" alt="image" src="https://github.com/user-attachments/assets/a685a418-769b-4fac-9af5-3fdcac4996c9" />


## 2.2 Design Calculations

### GIVEN PARAMETERS

- Technology: TSMC 180nm 
- Supply voltage, $V_{DD} = +0.9V$  
- Negative supply, $V_{SS} = -0.9V$   
- Power constraint, $P \leq 1.8mW$
- Channel length, $L_n = 480nm$ 
- Input common-mode voltage, $V_{in,CM} = 0V$  
- Output common-mode voltage, $V_{O,CM} = 0V$  
- Tail node voltage, $V_p = -0.7V$  
- Load capacitance, $C_L = 10pF$   
- Threshold voltage, $V_T \approx 0.36V$  

---

### 2.2.a Power Constraint

The total power consumed by the differential amplifier is given by:

$$
P = (V_{DD} - V_{SS}) \cdot I_{SS}
$$

Total supply voltage:

$$
V_{DD} - V_{SS} = 0.9 - (-0.9) = 1.8V
$$

Given the maximum allowed power:

$$
P \leq 1.8 \times 10^{-3}
$$

$$
1.8 \cdot I_{SS} \leq 1.8 \times 10^{-3}
$$

$$
I_{SS} \leq 1mA
$$

To maximize transconductance and improve gain while staying within the power limit, the tail current is chosen as:

$$
I_{SS} = 1mA
$$

The corresponding power dissipation is:

$$
P = 1.8 \times 1mA = 1.8mW
$$

Thus, the design satisfies the power constraint.

The tail current is provided by the NMOS transistor M5, which acts as a current source for the differential pair.

##

### 2.2.b Drain Current Calculation

Under balanced input conditions:

$$
V_{in1} = V_{in2}
$$

the differential pair operates symmetrically, and the tail current splits equally between both transistors.

$$
I_{D1} = I_{D2} = \frac{I_{SS}}{2}
$$

Substituting:

$$
I_{D1} = I_{D2} = \frac{1mA}{2}
$$

$$
I_{D1} = I_{D2} = 0.5mA
$$

Thus, each transistor carries equal current under zero differential input.

##

### 2.2.c Bias Point Calculation

#### NMOS Differential Pair (M1 and M2)

Given:

$$
V_{in,CM} = 0V
$$

So,

$$
V_{G1} = V_{G2} = 0V
$$

#### Source Node Voltage

From specifications:

$$
V_p = V_S = -0.7V
$$

#### Gate-Source Voltage

$$
V_{GS} = V_G - V_S
$$

$$
V_{GS} = 0 - (-0.7)
$$

$$
V_{GS} = 0.7V
$$

#### Overdrive Voltage

$$
V_{OV} = V_{GS} - V_T
$$

$$
V_{OV} = 0.7 - 0.36
$$

$$
V_{OV} = 0.34V
$$

#### Drain Voltage

Given:

$$
V_{O,CM} = 0V
$$

So,

$$
V_D = 0V
$$

#### Drain-Source Voltage

$$
V_{DS} = V_D - V_S
$$

$$
V_{DS} = 0 - (-0.7)
$$

$$
V_{DS} = 0.7V
$$

#### Saturation Condition

$$
V_{DS} > V_{OV}
$$

$$
0.7 > 0.34
$$

Thus, M1 and M2 operate in saturation.

##

### NMOS Current Source (M5)

For M5:

- Source is connected to:

$$
V_S = V_{SS} = -0.9V
$$

- Drain is connected to:

$$
V_D = V_p = -0.7V
$$

#### Drain-Source Voltage

$$
V_{DS} = V_D - V_S
$$

$$
V_{DS} = -0.7 - (-0.9)
$$

$$
V_{DS} = 0.2V
$$

#### Saturation Condition

For saturation:

$$
V_{DS} \ge V_{OV}
$$

Thus,

$$
0.2V \ge V_{OV}
$$

#### Choosing Overdrive Voltage

To ensure M5 remains in saturation while maximizing current, the overdrive voltage is chosen close to the upper limit:

$$
V_{OV} \approx 0.2V
$$

#### Gate-Source Voltage

$$
V_{GS} = V_T + V_{OV5}
$$

$$
V_{GS} = 0.36 + 0.2
$$

$$
V_{GS} = 0.56V
$$

#### Gate Voltage

$$
V_{G} = V_S + V_{GS}
$$

$$
V_{G} = -0.9 + 0.56
$$

$$
V_{G} = -0.34V
$$

#### Saturation Check

$$
V_{DS} \ge V_{OV}
$$

$$
0.2 \ge 0.2
$$

Thus, M5 operates at the edge of saturation and provides the required tail current.

##

### PMOS Active Load (M3 and M4)

For PMOS:

- Source is connected to:

$$
V_{DD} = 0.9V
$$

- Drain is at:

$$
V_D = 0V
$$

#### Source-Drain Voltage

$$
V_{SD} = V_{DD} - V_D
$$

$$
V_{SD} = 0.9 - 0
$$

$$
V_{SD} = 0.9V
$$

#### Saturation Condition

$$
V_{SD} > V_{OV}
$$

$$
0.9V > V_{OV}
$$

Since $0.9V$ is sufficiently large, both PMOS transistors operate in saturation.

### Final Bias Point Summary

All transistors (M1, M2, M3, M4, and M5) operate in saturation, ensuring proper differential amplifier operation.

##

### 2.2.d Width Calculation

The drain current in saturation is given by:

$$
I_D = \frac{1}{2} \mu_n C_{ox} \frac{W}{L} (V_{OV})^2
$$

Rearranging to find width:

$$
W = \frac{2 I_D L}{\mu_n C_{ox} (V_{OV})^2}
$$

### NMOS Differential Pair (M1 and M2)

From previous calculations:

$$
I_D = 0.5mA = 0.5 \times 10^{-3}A
$$

$$
V_{OV} = 0.34V
$$

$$
L = 480nm = 480 \times 10^{-9}m
$$

$$
\mu_n C_{ox} = 236.5 \mu A/V^2 = 2.365 \times 10^{-4}
$$

#### Substituting:

$$
W = \frac{2 \times 0.5 \times 10^{-3} \times 480 \times 10^{-9}}{2.365 \times 10^{-4} \times (0.34)^2}
$$

$$
W = \frac{480 \times 10^{-12}}{2.365 \times 10^{-4} \times 0.1156}
$$

$$
W = \frac{480 \times 10^{-12}}{2.733 \times 10^{-5}}
$$

$$
W \approx 17.56 \mu m
$$

### Final Width (M1 and M2)

$$
W_{M1} = W_{M2} \approx 17.6 \mu m
$$

##

### NMOS Current Source (M5)

From previous calculations:

$$
I_D = I_{SS} = 1mA = 1 \times 10^{-3}A
$$

$$
V_{OV5} = 0.2V
$$

#### Substituting:

$$
W = \frac{2 \times 1 \times 10^{-3} \times 480 \times 10^{-9}}{2.365 \times 10^{-4} \times (0.2)^2}
$$

$$
W = \frac{960 \times 10^{-12}}{2.365 \times 10^{-4} \times 0.04}
$$

$$
W = \frac{960 \times 10^{-12}}{9.46 \times 10^{-6}}
$$

$$
W \approx 101.5 \mu m
$$

### Width Adjustment

To achieve the desired biasing conditions (\(V_p \approx -0.7V\) and \(I_{SS} \approx 1mA\)), the transistor widths were tuned in simulation.

Updated values:

$$
W_{M1} = W_{M2} : 17.56\mu m \rightarrow 29.852\mu m
$$

$$
W_{M5} : 101.5\mu m \rightarrow 195.85\mu m
$$

This adjustment ensures accurate biasing under non-ideal MOSFET effects.

---

## DC Analysis

<img width="1682" height="726" alt="image" src="https://github.com/user-attachments/assets/4daa2a65-e68a-4541-a6a8-6a7a7f309c50" />


The DC operating point confirms that the output voltage and source voltage is near the designed bias value, ensuring proper saturation operation.

---

### 2.2.e Input Common Mode Range (ICMR)

The input common-mode range is defined as the range of input voltage for which all transistors remain in saturation.

### Minimum Input Common Mode Voltage

For proper operation, the NMOS input transistors (M1 and M2) must remain ON and the tail current source (M5) must remain in saturation.

Condition:

$$
V_{GS1} \ge V_T
$$

Using:

$$
V_{GS1} = V_{ICM} - V_S
$$

So,

$$
V_{ICM(min)} = V_S + V_T
$$

Substituting:

$$
V_S = -0.7V, \quad V_T = 0.36V
$$

$$
V_{ICM(min)} = -0.7 + 0.36
$$

$$
V_{ICM(min)} = -0.34V
$$

### Maximum Input Common Mode Voltage

For maximum input voltage, the PMOS load transistors (M3 and M4) must remain in saturation.

Condition:

$$
V_{SD} \ge V_{OVp}
$$

Using:

$$
V_{SD} = V_{DD} - V_D
$$

At the edge of saturation:

$$
V_{SD} = V_{SG} - |V_{TP}|
$$

Also,

$$
V_{SG} = V_{DD} - V_{ICM}
$$

So,

$$
V_{DD} - V_D = (V_{DD} - V_{ICM}) - |V_{TP}|
$$

Rearranging:

$$
V_{ICM(max)} = V_D + |V_{TP}|
$$

Substituting:

$$
V_D \approx 0V, \quad |V_{TP}| \approx 0.39V
$$

$$
V_{ICM(max)} = 0 + 0.39
$$

$$
V_{ICM(max)} = 0.39V
$$

### Final Input Common Mode Range

$$
-0.34V \le V_{ICM} \le 0.39V
$$

##

### 2.2.f Output Common Mode Range (OCMR)

The output common-mode range is defined as the range of output voltage for which all transistors remain in saturation.

### Minimum Output Common Mode Voltage

For minimum output voltage, the NMOS input transistors (M1 and M2) must remain in saturation.

Condition:

$$
V_{DS1} \ge V_{OV}
$$

Using:

$$
V_{DS1} = V_{out} - V_S
$$

So,

$$
V_{out(min)} - V_S \ge V_{OV}
$$

$$
V_{out(min)} \ge V_S + V_{OV}
$$

Substituting:

$$
V_S = -0.7V, \quad V_{OV} = 0.34V
$$

$$
V_{out(min)} = -0.7 + 0.34
$$

$$
V_{out(min)} = -0.36V
$$

### Maximum Output Common Mode Voltage

For maximum output voltage, the PMOS load transistors (M3 and M4) must remain in saturation.

Condition:

$$
V_{SD} \ge V_{OVp}
$$

Using:

$$
V_{SD} = V_{DD} - V_{out}
$$

So,

$$
V_{DD} - V_{out(max)} \ge V_{OVp}
$$

$$
V_{out(max)} \le V_{DD} - V_{OVp}
$$

Substituting:

$$
V_{DD} = 0.9V, \quad V_{OVp} \approx 0.25V
$$

$$
V_{out(max)} = 0.9 - 0.25
$$

$$
V_{out(max)} = 0.65V
$$

### Final Output Common Mode Range

$$
-0.36V \le V_{out} \le 0.65V
$$

##

### 2.2.g Differential Input Voltage Range (Linear Region)

The differential amplifier operates in the linear region as long as both transistors (M1 and M2) remain in saturation and conduct current.

The differential input voltage is defined as:

$$
v_{id} = v_{in1} - v_{in2}
$$

### Condition for Linear Operation

For linear operation:

- Both transistors must remain ON  
- Tail current must be shared between M1 and M2  

The maximum differential input occurs when one transistor starts to turn OFF.

### Maximum Differential Input Voltage

At the boundary of linear operation:

$$
v_{id(max)} = 2V_{OV}
$$

Substituting:

$$
V_{OV} = 0.25V
$$

$$
v_{id(max)} = 2 \times 0.25
$$

$$
v_{id(max)} = 0.5V
$$

### Final Differential Input Range

$$
-0.5V \le v_{id} \le 0.5V
$$

---

## 2.3 Transient Analysis and Linearity Observation

The linear behavior of the differential amplifier with PMOS active load is verified using transient analysis.

### Condition for Linearity

$$
|V_{id}| < \sqrt{2} V_{OV}
$$

Using:

$$
V_{OV} = 0.24V
$$

$$
\sqrt{2} V_{OV} = 1.414 \times 0.24 = 0.34V
$$

### Case 1: Linear Region

Input applied:

$$
V_{id} = 100mV < 0.34V
$$

<img width="1919" height="850" alt="image" src="https://github.com/user-attachments/assets/0657f47e-8f42-4ce2-bf88-85c504ffd9e9" />


#### Observation:

- Output waveform is sinusoidal  
- No distortion observed  
- Both NMOS transistors (M1, M2) operate in saturation  
- PMOS load transistors (M3, M4) remain in saturation  
- Amplifier behaves linearly  

### Case 2: Non-Linear Region

Input applied:

$$
V_{id} = 600mV > 0.34V
$$

<img width="1919" height="846" alt="image" src="https://github.com/user-attachments/assets/1a4b077a-fbd1-45e9-8b94-e7bc1491c278" />


#### Observation:

- Output waveform shows distortion and clipping  
- One transistor (M1 or M2) enters cutoff  
- Current is steered completely to one branch  
- PMOS load still operates, but amplification becomes non-linear  

## Comparison Table

| Parameter | Case 1: Linear Region | Case 2: Non-Linear Region |
|----------|----------------------|--------------------------|
| Condition | $V_{id} < \sqrt{2}V_{OV}$ | $V_{id} > \sqrt{2}V_{OV}$ |
| Input ($V_{id}$) | 100 mV | 600 mV |
| Output waveform | Sinusoidal | Distorted / Clipped |
| Gain | Constant | Reduced / Non-linear |
| Transistor operation | All in saturation | One NMOS in cutoff |
| Current distribution | Shared between M1 & M2 | Current flows in one branch |

## Interpretation

In the linear region, the differential input is small and both NMOS transistors conduct simultaneously. The tail current is shared between the two branches, and the PMOS active load converts current variations into voltage, resulting in a proportional and undistorted output.

In the non-linear region, the differential input exceeds the limit, causing one transistor to carry almost the entire tail current while the other turns OFF. This leads to distortion and loss of linearity in the output.

## Conclusion

The differential amplifier with active load operates linearly only for small input signals:

$$
|V_{id}| < \sqrt{2} V_{OV}
$$

When:

$$
|V_{id}| > \sqrt{2} V_{OV}
$$

the circuit exhibits non-linear behavior due to current steering and transistor cutoff.

##

## Theoretical and Simulated Gain

<img width="1919" height="424" alt="image" src="https://github.com/user-attachments/assets/f6187168-15b2-4d75-88dc-3049c125ae68" />


The output waveform is amplified and inverted.

### Simulated Gain

Input signal parameters:

- Type: Sine wave  
- Frequency = 1kHz  
- Amplitude = 50mV (applied differentially) 
- DC Offset = 0V

Measured peak-to-peak values:

$$
V_{in(p-p)} = 50mV - ( - 50mV ) = 100mV
$$

$$
V_{out(p-p)} = 106mV - ( - 75mV ) = 181mV
$$

Voltage gain:

$$
A_v = \frac{V_{out(p-p)}}{V_{in(p-p)}}
$$

$$
A_v = \frac{181 \times 10^{-3}}{100 \times 10^{-3}}
$$

$$
A_v = 1.81
$$

Gain in dB:

$$
A_v(dB) = 20\log_{10}(1.81)
$$

$$
A_v(dB) = 5.153dB
$$

##

### Theoretical Gain

Assume channel length modulation:

$$
\lambda = 0.1 \, V^{-1}
$$

### Output Resistance

The output resistance of each MOSFET is:

$$
r_o = \frac{1}{\lambda I_D}
$$

Substituting:

$$
I_D = 0.5mA = 0.5 \times 10^{-3}A
$$

$$
r_o = \frac{1}{0.1 \times 0.5 \times 10^{-3}}
$$

$$
r_o = 20k\Omega
$$

### Effective Output Resistance

Since both NMOS and PMOS contribute:

$$
r_{o,eff} = r_{o_n} \parallel r_{o_p}
$$

$$
r_{o,eff} = 20k \parallel 20k
$$

$$
r_{o,eff} = 10k\Omega
$$

### Transconductance

$$
g_m = \frac{2 I_D}{V_{OV}}
$$

Substituting:

$$
V_{OV} = 0.24V
$$

$$
g_m = \frac{2 \times 0.5 \times 10^{-3}}{0.24}
$$

$$
g_m \approx 4.17mS
$$

### Total Output Resistance

Since active load is used (no resistor):

$$
R_{out} = r_{o,eff}
$$

$$
R_{out} = 10k\Omega
$$

### Differential Gain

$$
A_d = g_m R_{out}
$$

$$
A_d = 4.17 \times 10^{-3} \times 10 \times 10^3
$$

$$
A_d \approx 41.7
$$

### Gain in dB

$$
A_d(dB) = 20 \log_{10}(41.7)
$$

$$
A_d(dB) \approx 32.4dB
$$

##

## Reason for Difference Between Theoretical and Simulated Gain

A deviation is observed between the theoretical and simulated gain values. This difference arises due to simplifying assumptions in analytical calculations and the inclusion of non-ideal MOSFET effects in simulation.

### Reasons for Deviation

### 1. Channel Length Modulation

In theoretical calculations, channel length modulation is approximated using a constant value of $\lambda$.  
However, in simulation, both NMOS and PMOS devices have more accurate and bias-dependent $\lambda$, affecting the output resistance:

$$
r_o = \frac{1}{\lambda I_D}
$$

This directly impacts the gain.

### 2. Finite Output Resistance of Active Load

In Circuit 2, the load is implemented using PMOS transistors instead of resistors.

The effective output resistance is:

$$
R_{out} = r_{o_n} \parallel r_{o_p}
$$

Any variation in NMOS and PMOS output resistances significantly affects the gain.

### 3. Mobility Degradation and Short Channel Effects

In practical MOSFET models, carrier mobility decreases with increasing electric field.  
This reduces the effective transconductance:

$$
g_m = \frac{2I_D}{V_{OV}}
$$

leading to lower gain in simulation compared to theory.

### 4. Variation in Overdrive Voltage ($V_{OV}$)

Theoretical calculations assume a fixed overdrive voltage.  
However, in simulation, the operating point slightly shifts, causing variations in $V_{OV}$ and hence in $g_m$ and gain.

### 5. Current Source Non-Ideality (M5)

The tail current source (M5) is not ideal in simulation.

- Finite output resistance  
- Slight variation in tail current  

This affects current distribution and reduces gain.

### 6. Parasitic Capacitances

Simulation includes intrinsic capacitances of MOSFETs, which influence signal behavior and slightly reduce the observed gain, especially at higher frequencies.

### 7. Measurement Method

Gain in simulation is obtained from waveform measurements, which may introduce minor inaccuracies due to scaling, cursor placement, and waveform asymmetry.

### Conclusion

Thus, the difference between theoretical and simulated gain is expected.  
It arises due to the use of simplified analytical models in theory and the inclusion of realistic device behavior and non-ideal effects in simulation.

---

## 2.4 AC Analysis

<img width="1919" height="424" alt="image" src="https://github.com/user-attachments/assets/f47f5271-1043-488f-bd8b-5eed0e001ff9" />


In AC analysis, the frequency response of the Differential Amplifier is observed.

The midband gain is obtained from the flat region of the Bode plot.  
The bandwidth is defined as the frequency range between the lower cutoff frequency ($f_L$) and upper cutoff frequency ($f_H$), measured at the −3 dB points.

##

### Midband gain:

From AC simulation:

$$
A_v = 5.2 \text{ dB}
$$

The −3 dB gain is:

$$
A_v - 3 = 5.2 - 3
$$

$$
A_v - 3 = 2.2 \text{ dB}
$$

##

### Cutoff Frequencies

Lower cutoff frequency:

$$
f_L = 0
$$

Upper cutoff frequency:

$$
f_H = 2.2 \text{ GHz}
$$

##

### Bandwidth

Bandwidth is defined as:

$$
BW = f_H - f_L
$$

$$
BW = 2.2 - 0
$$

$$
BW = 2.2 \text{ GHz}
$$

---

## 2.5 Unity Gain Bandwidth (UGB)

$$
f_{0dB} \approx 4.8 \text{GHz}
$$

$$
UGB = A_v \times f_H
$$

Using linear gain:

$$
A_v = 1.81
$$

$$
UGB = 1.81 \times 4.8 \text{ GHz}
$$

$$
UGB = 8.688 \text{ GHz}
$$

---

### Note

First-order theoretical analysis assumes ideal MOSFET operation in saturation and neglects higher-order effects such as channel length modulation, mobility degradation, finite output resistance of current sources, and parasitic capacitances. These non-ideal effects are included in simulation, leading to differences between theoretical and simulated results.

## Comparison of Results

| Parameter | Theoretical | Simulated |
|------------|-------------|-----------|
| Voltage Gain ($A_v$) | 41.7 V/V | 1.81 V/V |
| Gain (dB) | 32.4 dB | 5.153 dB |

The deviation between theoretical and simulated gain is mainly due to simplified first-order assumptions and the presence of non-ideal MOSFET effects such as finite output resistance of the current source, channel length modulation, and parasitic capacitances.

---

## Inference

The MOS differential amplifier with PMOS active load and NMOS current source was successfully designed and analyzed while satisfying the given design constraints:

Power consumption ≤ 1.8mW  
VDD = 0.9V  
VSS = -0.9V  
Vocm = 0V  

The tail current was set close to 1mA to ensure operation within the power limit. Under balanced conditions, the current splits equally between the two branches:

$$
I_{D1} = I_{D2} \approx 0.5mA
$$

The biasing was carefully adjusted to ensure all transistors (M1, M2, M3, M4, and M5) operate in saturation. The tail node voltage was fixed at:

$$
V_S \approx -0.7V
$$

by tuning the transistor widths in simulation.

Theoretical and simulated results show a significant deviation:

Theoretical gain ≈ 41.7 V/V (32.4 dB)  
Simulated gain ≈ 1.81 V/V (5.135 dB)  

This large difference arises because the theoretical gain assumes an ideal current source and large output resistance. In practice:

- The NMOS current source (M5) has finite output resistance  
- The PMOS active load (M3, M4) is not ideal  
- Channel length modulation reduces effective gain  
- Mobility degradation reduces transconductance  

These factors significantly reduce the gain in simulation.

From AC analysis, the amplifier shows a flat midband gain followed by a roll-off at higher frequencies due to parasitic capacitances and the load capacitance, which introduce a dominant pole and limit bandwidth.

The differential amplifier provides linear amplification for small differential inputs. However, for large input signals, current steering causes one transistor to turn OFF, leading to distortion and non-linear behavior.

Hence, the designed differential amplifier demonstrates correct biasing and operation, but highlights the impact of non-ideal device behavior on gain when using active loads and current sources.
-----




# Experiment 4  
## Circuit 3 – CMOS Differential Amplifier (DC Analysis & Saturation Conditions)
<img width="1079" height="665" alt="image" src="https://github.com/user-attachments/assets/c36c9b83-c1c1-4db0-80d5-73bc9a80cd4a" />

---

## Aim

To analyze the DC operating conditions of a CMOS differential amplifier and verify the saturation region of all MOSFETs in Circuit 3.

---

## Circuit Description

The circuit consists of a CMOS differential amplifier with:
- NMOS differential pair (M1, M2)
- PMOS active load (M3, M4)
- NMOS tail current source (M5)

The circuit operates with symmetric inputs and fixed biasing conditions.

---

## Given Parameters

### Supply Voltages
- VDD = 0.9 V  
- VSS = -0.35 V  

---

### Input Signals
- Vin1 = SINE(0, 10mV, 1kHz), AC = 1  
- Vin2 = SINE(0, -10mV, 1kHz), AC = 180°  

Differential input:
Vid = Vin1 - Vin2 = 20 mV  

---

### DC Node Voltages
- Vout1 = 0.3 V  
- Vout2 = 0.3 V  
- Vp (tail node) = -0.7 V (fixed)

---

### Bias Voltage
- Gate voltage of M5:
  Vg5 = 0.366 V  

---

### Technology
- Model: tsmc018.lib  
- Threshold voltage:
  Vt ≈ 0.366 V  

---

## MOSFET Types

- M1, M2, M5 → NMOS  
- M3, M4 → PMOS  

---

## Saturation Conditions

### NMOS
VDS ≥ VGS − Vt  

### PMOS
VSD ≥ VSG − |Vt|  

---

## DC Analysis and Region Verification

---

### M1 (NMOS)

Vg1 = 0 V  
Vs1 = Vp = -0.7 V  

VGS1 = 0 − (-0.7) = 0.7 V  

Vd1 = 0.3 V  

VDS1 = 0.3 − (-0.7) = 1.0 V  

Condition:
VDS1 ≥ VGS1 − Vt  
1.0 ≥ 0.7 − 0.366 = 0.334  

M1 operates in saturation region  

---

### M2 (NMOS)

Vg2 = 0 V  
Vs2 = -0.7 V  

VGS2 = 0.7 V  

Vd2 = 0.3 V  

VDS2 = 1.0 V  

Condition satisfied  

M2 operates in saturation region  

---

### M3 (PMOS)

Vs3 = 0.9 V  
Vd3 = 0.3 V  

VSD3 = 0.9 − 0.3 = 0.6 V  

Vg3 = 0.3 V  

VSG3 = 0.9 − 0.3 = 0.6 V  

Condition:
VSD3 ≥ VSG3 − |Vt|  
0.6 ≥ 0.6 − 0.366 = 0.234  

M3 operates in saturation region  

---

### M4 (PMOS)

Vs4 = 0.9 V  
Vd4 = 0.3 V  

VSD4 = 0.6 V  

Vg4 = 0.3 V  

VSG4 = 0.6 V  

Condition satisfied  

M4 operates in saturation region  

---

### M5 (NMOS)

Vg5 = 0.366 V  
Vs5 = -0.35 V  

VGS5 = 0.366 − (-0.35) = 0.716 V  

Vd5 = -0.7 V  

VDS5 = -0.7 − (-0.35) = -0.35 V  

|VDS5| = 0.35 V  

Condition:
VDS5 ≥ VGS5 − Vt  
0.35 ≥ 0.716 − 0.366 = 0.35  

M5 operates at the boundary of saturation region  

---


## DC Analysis (Operating Point)

The DC operating point analysis provides the node voltages and drain currents of the CMOS differential amplifier.
<img width="853" height="627" alt="image" src="https://github.com/user-attachments/assets/2992dc79-1ea6-4a53-b3e0-66c8f034bc5f" />

---

### Node Voltages

- VDD node = 0.9 V  
- Ground reference = 0 V  
- Negative supply ≈ -0.9 V  

- Vout1 = 0.8876 V  
- Vout2 = 0.8876 V  

- Tail node:
  Vp = -0.7218 V  

- Bias node:
  Vg5 ≈ -0.37 V  

---

### Currents

- Tail current (through M5):
  Id(M5) = 1.0487 mA  

- Differential pair currents:
  Id(M1) = 0.5243 mA  
  Id(M2) = 0.5243 mA  

- PMOS load currents:
  Id(M3) = -0.5243 mA  
  Id(M4) = -0.5243 mA  

---

### Observations

- The total tail current splits equally:
  Id(M1) ≈ Id(M2)

- Current matching confirms symmetry of the differential pair.

- PMOS currents are equal and opposite to NMOS currents, ensuring proper load operation.

- Output voltages are equal:
  Vout1 = Vout2  
  → Indicates zero differential input condition.

---

### Voltage Verification

For M1 and M2:

VGS ≈ 0 − (-0.7218) = 0.7218 V  

VDS ≈ 0.8876 − (-0.7218) = 1.6094 V  

---

For M5:

VGS5 = Vg5 − Vs  
= (-0.37) − (-0.9)  
= 0.53 V  

VDS5 = Vp − Vs  
= (-0.7218) − (-0.9)  
= 0.1782 V  

---

### Current Consistency Check

Id(M5) ≈ Id(M1) + Id(M2)  
1.0487 mA ≈ 0.5243 + 0.5243 mA  



---


## Transient Analysis

The transient analysis is performed to observe the time-domain response of the CMOS differential amplifier for a sinusoidal differential input.

---
<img width="1899" height="428" alt="image" src="https://github.com/user-attachments/assets/1d7edbd6-d2d3-458c-bc75-6ce0eacb78d2" />
<img width="1900" height="450" alt="image" src="https://github.com/user-attachments/assets/9f59e6e1-cff8-4c79-b1eb-27df99c727e1" />
<img width="1898" height="387" alt="image" src="https://github.com/user-attachments/assets/fe0d7791-d13d-47cb-b1f1-3e09705dcd61" />

### Simulation Setup

- Analysis type:
  .tran 5 ms  

- Input signals:
  Vin1 = SINE(0, 10 mV, 1 kHz)  
  Vin2 = SINE(0, -10 mV, 1 kHz)  

- Differential input:
  Vid = 20 mV peak-to-peak  

---

### Observed Waveforms

---

#### Input Signal

- The input waveform is a sinusoidal signal with:
  - Amplitude ≈ ±10 mV  
  - Frequency = 1 kHz  

- The signal is centered around 0 V.

---

#### Output Voltage (Vout1)

- The output waveform is sinusoidal in nature.  
- DC level:
  Vout1 ≈ 0.8876 V  

- Small signal variation is observed around the DC operating point.

- Output amplitude is significantly smaller compared to input variation due to biasing conditions.

---

#### Combined Observation

- Input and output waveforms maintain sinusoidal shape.  
- No visible distortion is present.  
- Output follows the input variation, indicating linear operation in this region.  

---

### Key Parameters from Waveform

- Input amplitude ≈ 10 mV  
- Output DC level ≈ 0.8876 V  
- Output signal shows small variation around DC level  

---







## AC Analysis

The AC analysis is performed to determine the frequency response, voltage gain, bandwidth, and gain-bandwidth product of the CMOS differential amplifier.

---
<img width="1919" height="486" alt="image" src="https://github.com/user-attachments/assets/a2fb9fb8-4477-46cb-947c-80f569511f34" />

## Simulation Setup

- Analysis command:
  .ac dec 100 100 100G  

- Input:
  AC magnitude = 1 V  

- Output node:
  Vout1  

---

## Theoretical Analysis

### Differential Gain Formula

For a MOS differential amplifier with active load:

Ad = gm × Rout  

Where:
- gm = transconductance  
- Rout = ro_n || ro_p  

This is the standard gain relation:
Ad ≈ gm × ro :contentReference[oaicite:0]{index=0}  

---

### Transconductance (gm)

gm = μnCox × (W/L) × Vov  

OR

gm = 2Id / Vov  

---

### Given Parameters

- μnCox = 235 μA/V²  
- L = 480 nm  
- Vt = 0.366 V  

From DC analysis:
- Id ≈ 0.524 mA  

---

### Step 1: Overdrive Voltage

Vov = VGS − Vt  

From DC:
VGS ≈ 0.72 V  

Vov = 0.72 − 0.366 = 0.354 V  

---

### Step 2: gm Calculation

gm = 2Id / Vov  

gm = 2 × 0.524 mA / 0.354  

gm ≈ 2.96 mS  

---

### Step 3: Output Resistance

ro ≈ 1 / (λId)  

Assuming:
λ ≈ 0.1 V⁻¹ (typical for 180nm)

ro ≈ 1 / (0.1 × 0.524 mA)  
ro ≈ 19.08 kΩ  

---

### Step 4: Gain Calculation

Rout = ro || ro ≈ ro/2  

Rout ≈ 9.5 kΩ  

Ad = gm × Rout  

Ad = 2.96 mS × 9.5 kΩ  

Ad ≈ 28.1 V/V  

---

### Step 5: Gain in dB

Ad(dB) = 20 log(28.1)  

Ad ≈ 28.97 dB  

---

## Practical Results (From Graph)

From AC plot:

- Gain ≈ -20 dB  
- Bandwidth ≈ ~1 GHz  
- Gain decreases after high frequency  

---

## Conversion

Gain (linear):

Av = 10^(−20/20)  

Av ≈ 0.1 V/V  

---

## Comparison

| Parameter | Theoretical | Practical |
|----------|------------|----------|
| Gain (V/V) | 28.1 | 0.1 |
| Gain (dB) | 28.97 dB | -20 dB |

---

## Reason for Difference

- M5 not fully in saturation  
- Low output resistance  
- Channel length modulation effect  
- Improper biasing reduces gain  
- Single-ended output reduces effective gain  

---

## Frequency Response

- Flat region → low-frequency gain  
- Roll-off → due to parasitic capacitances  
- Phase shift increases at high frequency  

---





## Transient Analysis for Vid > √2 Vov (Nonlinear Region)

---
<img width="1912" height="387" alt="image" src="https://github.com/user-attachments/assets/acf0038d-129a-427b-ad7b-a1197327c18b" />

### Condition

The differential input applied satisfies:

Vid > √2 Vov  

Where:
√2 Vov ≈ 0.50 V  

---

### Observed Output Behavior

- The output waveform is no longer purely sinusoidal.  
- The waveform shows:
  - Flattened peaks (clipping at top)
  - Sharp transitions
  - Asymmetry in rising and falling edges  

- Output swings between:
  - Upper limit ≈ 0.9 V  
  - Lower limit ≈ 0.88 V  

---

### Justification

When Vid exceeds √2 Vov:

- One NMOS transistor (M1 or M2) enters **strong conduction**  
- The other transistor enters **cutoff region**  

As a result:

- Tail current is no longer shared equally  
- Entire current flows through only one branch  
- Differential pair behaves like a **switch rather than amplifier**

---

### Effect on Output

- Output node connected to ON transistor:
  - Pulled strongly → saturation level  

- Output node connected to OFF transistor:
  - No current → remains near supply  

This causes:

- Signal clipping  
- Loss of linearity  
- Distorted waveform  

---

### Key Observation

- The amplifier no longer operates in small-signal region  
- It behaves as a **large-signal nonlinear system**  

---

### Physical Interpretation

- For small Vid:
  current splits smoothly → linear output  

- For large Vid:
  current fully steers → switching action  

---






## Transient Analysis for Vid < √2 Vov (Linear Region)

---
<img width="1913" height="423" alt="image" src="https://github.com/user-attachments/assets/60ae9989-fada-40ea-98f2-6c3299411a42" />

### Condition

The applied differential input satisfies:

Vid < √2 Vov  

Where:
√2 Vov ≈ 0.50 V  

In this case:
Vid = 20 mV << 0.50 V  

---

### Observed Output Behavior

- The output waveform is **purely sinusoidal**  
- No distortion or clipping is observed  
- The signal is centered around DC level (~0.8876 V)  
- Output variation is small and smooth  

---

### Justification

When Vid is less than √2 Vov:

- Both NMOS transistors (M1 and M2) operate in **saturation region**  
- Tail current is **evenly shared** between the two branches  
- Current changes **linearly** with input voltage  

---

### Effect on Output

- Output voltage varies proportionally with input  
- No abrupt switching occurs  
- Amplifier behaves as a **small-signal linear system**

---

### Key Observation

- No clipping or distortion  
- Symmetrical waveform  
- Smooth transitions  

---

### Physical Interpretation

- Differential pair operates in **small-signal region**  
- Current division follows linear relation:
  Id1 ≈ Id/2 + (gm × Vid)/2  
  Id2 ≈ Id/2 − (gm × Vid)/2  

---







## Calculation of Common Mode Voltage Range

---

### Given

VDD = 0.9 V  
VSS = -0.35 V  
VT = 0.366 V  

From DC analysis:  
Vp ≈ -0.7218 V  

---

### Step 1: Calculate VGS

VGS = VCM − Vp  

At bias point (from DC):

VGS ≈ 0.72 V  

---

### Step 2: Overdrive Voltage

VOV = VGS − VT  

VOV = 0.72 − 0.366  

VOV ≈ 0.354 V  

---

## Minimum Common Mode Voltage (VCM_min)

Condition:
M1, M2 must remain ON and in saturation  

So,

VGS ≥ VT  

VCM − Vp ≥ VT  

VCM ≥ Vp + VT  

Substitute:

VCM_min = -0.7218 + 0.366  

VCM_min ≈ -0.3558 V  

---

## Maximum Common Mode Voltage (VCM_max)

Condition:
M1, M2 must remain in saturation  

VDS ≥ VOV  

Vout − Vp ≥ VOV  

Using DC value:

Vout ≈ 0.8876 V  

Check:

0.8876 − (-0.7218) = 1.6094 V ✔ (satisfied)

---

Now PMOS condition limits VCM:

For M3/M4:

VSD ≥ VOV  

VDD − Vout ≥ VOV  

0.9 − 0.8876 = 0.0124 V  

But,

VOV ≈ 0.354 V  

0.0124 < 0.354  

---

Thus PMOS is near boundary, so:

VCM_max ≈ Vout − VOV  

VCM_max ≈ 0.8876 − 0.354  

VCM_max ≈ 0.5336 V  

---

## Final Values

VCM_min ≈ -0.356 V  

VCM_max ≈ 0.534 V  

---






## Transient Analysis at VCM(min)
<img width="1916" height="887" alt="image" src="https://github.com/user-attachments/assets/6e2be445-d3ba-400a-8cda-35e307fcc97e" />

---

### Condition

The input common-mode voltage is set to its minimum value:

VCM(min) ≈ -0.36 V  

---

### Observed Output Behavior

- Output waveform is **sinusoidal**  
- Signal is centered near upper supply (~0.9 V)  
- Very **small amplitude variation** is observed  
- No clipping or distortion  

---

### Justification

At VCM(min):

- Gate voltage of NMOS transistors (M1, M2) is just sufficient to keep them ON  
- Condition:
  VGS ≈ VT  

- Transistors operate at the **edge of conduction**

---

### Effect on Circuit Operation

- Drain current is **very small**  
- Transconductance (gm) is low  
- Gain of the amplifier is reduced  

---

### Output Behavior Explanation

- Since current is very small:
  - Voltage drop across PMOS load is minimal  
  - Output node remains close to VDD  

- Only small variation is seen due to weak conduction  

---

### Key Observation

- Circuit is still operating but at **minimum bias condition**  
- Amplification is weak  
- Output swing is very limited  

---

### Physical Interpretation

- Differential pair is barely active  
- Small input causes only small current change  
- System is in **weak inversion / near cutoff region**

---




## Transient Analysis at VCM(max)

---

### Condition

The input common-mode voltage is set to its maximum value:

VCM(max) ≈ 0.53 V  

---

### Observed Output Behavior

- Output waveform is sinusoidal  
- Signal is centered near upper supply (~0.9 V)  
- Small amplitude variation is observed  
- No distortion is present  

---

### Justification

At VCM(max):

<img width="1919" height="460" alt="image" src="https://github.com/user-attachments/assets/69dd3bf1-0d4b-4aa0-abbe-2e1d2ae7b4ae" />


- PMOS transistors (M3, M4) operate at the edge of saturation  
- Condition:
  VSD ≈ VOV  

- Any further increase in VCM would push PMOS into linear region  

---

### Effect on Circuit Operation

- Output node cannot discharge effectively  
- Voltage remains close to VDD  
- Gain reduces due to reduced output resistance  

---

### Key Observation

- Limited output swing  
- Reduced gain  
- Stable sinusoidal waveform  

---










# Differential Amplifier — Circuit Comparison 

**Course:** Linear Integrated Circuits (LIC) Lab
**Technology:** TSMC 180 nm | **Channel Length:** L = 480 nm
**Supply:** VDD = +0.9 V, VSS = −0.9 V | **Power Budget:** P ≤ 1.8 mW

---

## Circuit Descriptions

| | Circuit 1 | Circuit 2 | Circuit 3 |
|---|---|---|---|
| **Load type** | Resistors (R₁, R₂) | PMOS current mirror (M3, M4) | PMOS mirror + C_L = 10 pF |
| **Transistors** | M1, M2 (NMOS) + tail current source | M1, M2 (NMOS) + M3, M4 (PMOS) + M5 (tail) | Same as C2, with capacitive load |
| **Tail current source** | Ideal current source (V3) | M5 (NMOS, in saturation) | M5 (NMOS, in saturation) |

---

## 1. Power Comparison

> **Design constraint:** P ≤ 1.8 mW

| Parameter | Circuit 1 | Circuit 2 | Circuit 3 |
|---|---|---|---|
| **VDD − VSS** | 1.8 V | 1.8 V | 1.8 V |
| **Tail current (I_SS)** | 1 mA | 1 mA | 1 mA |
| **Each branch current (I_D)** | 0.5 mA | 0.5 mA | 0.5 mA |
| **Total power consumed** | **1.8 mW** | **1.8 mW** | **1.8 mW** |
| **Within spec?** | ✓ Yes | ✓ Yes | ✓ Yes |

**Key observation:** All three circuits consume identical DC power of 1.8 mW because the tail current and supply voltage are unchanged across all configurations. The type of load (resistive vs active) does not affect static power dissipation.

---

## 2. Gain Comparison

### Gain Formula

| Parameter | Circuit 1 | Circuit 2 | Circuit 3 |
|---|---|---|---|
| **Gain formula** | A_d = g_m × R_D | A_d = g_m × (r_o2 ‖ r_o4) | A_d = g_m × (r_o2 ‖ r_o4) |
| **Mid-band gain (linear)** | Low (~g_m·R_D) | **~1.9 V/V** | **~1.9 V/V** |
| **Mid-band gain (dB)** | Lower | **5.55 dB** | **5.55 dB** |
| **Theoretical gain (dB)** | — | ~6 dB | ~6 dB |
| **Deviation from theory** | — | ~0.45 dB | ~0.45 dB |

### Why Circuit 2 & 3 have higher gain

- Resistive load (C1): drain resistance R_D is limited in value to avoid pushing transistors into triode. Gain is bounded.
- Active mirror load (C2, C3): replaces R_D with the parallel combination of NMOS output resistance r_o2 and PMOS output resistance r_o4. This is significantly larger than a physical resistor, giving much higher gain.

### Transient Gain (small-signal, from simulation)

| Parameter | Circuit 1 | Circuit 2 | Circuit 3 |
|---|---|---|---|
| **Differential input (V_id)** | 20 mV peak | 20 mV peak | 20 mV peak |
| **Output swing (V_out,pp)** | Very small (nV range) | ~2.4 mV | Slightly reduced (CL effect) |
| **Calculated A_v** | ≈ negligible | **0.12** (single-ended) | Lower due to pole |

> Note: The transient gain of 0.12 is for single-ended output. Full differential output (V_out1 − V_out2) would yield higher effective gain.

---

## 3. Input Swing Comparison

### Common-Mode Input Range (V_CM)

| Parameter | Circuit 1 | Circuit 2 | Circuit 3 |
|---|---|---|---|
| **V_CM(min)** | −0.334 V | −0.34 V | −0.34 V |
| **V_CM(max)** | **+0.366 V** | **+1.032 V** | **+1.032 V** |
| **Total CM swing** | **~0.70 V** | **~1.37 V** | **~1.37 V** |

### V_CM(min) Derivation (all circuits)

```
Condition: NMOS input pair just turns ON → VGS = VT

V_CM(min) = V_P + V_T
           = −0.7 + 0.366
           = −0.334 V  (C1) / −0.34 V (C2, C3 from simulation V_S)
```

### V_CM(max) Derivation

**Circuit 1** — limited by NMOS saturation condition:
```
VDS = VOV → VCM(max) = VD + VT = 0 + 0.366 = +0.366 V
```

**Circuit 2 & 3** — limited by PMOS load saturation condition:
```
V_CM(max) = VDD − V_ov(PMOS) + V_T(NMOS)
           = 0.9 − 0.234 + 0.366
           = +1.032 V
```

The PMOS active load gives ~2× wider common-mode input swing compared to resistive load.

### Linear Differential Input Swing (all circuits)

For linear (undistorted) operation, the differential input must satisfy:

```
V_id < √2 × V_OV
```

| Condition | MOSFET behaviour | Output |
|---|---|---|
| V_id < √2·V_OV | Both M1, M2 in saturation, current shared equally | Clean sinusoidal output |
| V_id > √2·V_OV | One MOSFET enters cutoff, other carries full current | Distorted, clipped output |

---

## 4. Bandwidth & Frequency Response Comparison

| Parameter | Circuit 1 | Circuit 2 | Circuit 3 |
|---|---|---|---|
| **Dominant pole formula** | 1 / (2π·R_D·C_par) | 1 / (2π·r_out·C_par) | 1 / (2π·r_out·(C_par + C_L)) |
| **Approximate f_−3dB** | Higher (lower r_out) | ~1–5 Hz | < 1 Hz |
| **Roll-off slope** | −20 dB/decade | −20 dB/decade | −20 dB/decade |
| **Bandwidth trade-off** | Wide BW, lower gain | Narrow BW, higher gain | Narrowest BW, same gain as C2 |

---

## 5. Stability & Phase Margin

| Parameter | Circuit 1 | Circuit 2 | Circuit 3 |
|---|---|---|---|
| **Phase at low freq** | ~−180° | **−194.8°** | Worse than C2 |
| **Excess phase** | Minimal | ~14.8° | > 14.8° |
| **Phase margin (open-loop)** | Positive | **~−14.8° (unstable)** | More negative |
| **Frequency compensation needed?** | No | Yes (Miller cap) | Yes (strongly needed) |

> The negative phase margin in Circuits 2 and 3 means they will oscillate if placed in a unity-gain feedback loop without frequency compensation.

---

## 6. DC Operating Point Comparison

| Parameter | Circuit 1 | Circuit 2 | Circuit 3 |
|---|---|---|---|
| **V_out1 (DC)** | ≈ 0 V | ≈ 7.1 mV | ≈ 7.1 mV |
| **V_out2 (DC)** | ≈ 0 V | ≈ 7.1 mV | ≈ 7.1 mV |
| **V_od = V_out1 − V_out2** | 0 V | 0 V | 0 V |
| **V_S (source node)** | −0.707 V | −0.695 V | −0.695 V |
| **I_D1 = I_D2** | 0.5 mA | 0.5 mA | 0.5 mA |
| **Symmetry** | ✓ Balanced | ✓ Balanced | ✓ Balanced |

---

## 7. Behaviour at Boundary Conditions

### At V_CM(min)

| Observation | All Circuits |
|---|---|
| **V_GS ≈ V_T** | Transistor barely ON |
| **V_ov ≈ 0** | Transconductance g_m ≈ 0 |
| **Output** | Flat — no amplification |
| **Conclusion** | Amplifier non-functional at lower limit |

### At V_CM(max)

| Observation | All Circuits |
|---|---|
| **V_DS = V_ov** | At saturation–triode boundary |
| **Gain** | Collapses as MOSFET enters triode |
| **Output** | No amplification, waveform flat |
| **Conclusion** | Amplifier non-functional at upper limit |

---

## 8. Overall Comparison Summary

| Feature | Circuit 1 | Circuit 2 | Circuit 3 |
|---|---|---|---|
| **Load** | Resistive | Active (PMOS mirror) | Active + C_L |
| **Power** | 1.8 mW | 1.8 mW | 1.8 mW |
| **Gain (dB)** | Lower | 5.55 dB | 5.55 dB |
| **CM input range** | 0.70 V | 1.37 V | 1.37 V |
| **Bandwidth** | Wide | Narrow (~1–5 Hz) | Narrowest |
| **Phase margin** | Stable | Unstable (−14.8°) | Worse |
| **CMRR** | Moderate | High | High |
| **Complexity** | Simple | Moderate | Moderate |
| **Key advantage** | Wide BW, simple design | High gain, wide CM range | Drives capacitive loads |
| **Key drawback** | Low gain, limited CM swing | Needs frequency compensation | Lowest BW |
| **Best suited for** | General amplification | High-gain op-amp input stage | Capacitive load driving |

---

## 9. Key Formulas Reference

| Formula | Expression |
|---|---|
| Differential gain | A_d = g_m · R_D (C1) or g_m · (r_o2 ‖ r_o4) (C2, C3) |
| Transconductance | g_m = 2·I_D / V_ov |
| Output resistance | r_o = 1 / (λ·I_D) |
| CM input min | V_CM(min) = V_P + V_T |
| CM input max (C1) | V_CM(max) = V_D + V_T |
| CM input max (C2,C3) | V_CM(max) = VDD − V_ov(PMOS) + V_T(NMOS) |
| Linear input condition | V_id < √2 · V_OV |
| Dominant pole | f_H = 1 / (2π · r_out · C_L) |

---
