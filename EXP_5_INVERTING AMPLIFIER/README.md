# EXPERIMENT - 5  
## BASIC OPERATIONAL AMPLIFIER CIRCUITS  
## CIRCUIT - 1

### Aim

To design and analyze a Voltage Follower (unity gain buffer) using an operational amplifier and study its frequency response.



### Specifications

- Supply Voltage: ±VCC = ±15 V  
- Input Signal: Vin(pp) = 10 Vpp  
- Frequency: f = 1 kHz  
- Load Resistance: RL = 560 Ω


# Introduction

An operational amplifier (Op-Amp) is a high-gain differential amplifier widely used in analog electronics for signal processing applications such as amplification, filtering, and signal conditioning.

Among the basic op-amp configurations, the **Voltage Follower (Unity Gain Buffer)** is one of the most important circuits. It provides a gain of unity (1), meaning the output voltage follows the input voltage.

The primary purpose of a voltage follower is not amplification, but **impedance matching**. It is used to isolate different stages of a circuit by providing:

- Very high input impedance  
- Very low output impedance  

This prevents loading effects and ensures maximum signal transfer between stages.



# Theory

A voltage follower is a special case of the **non-inverting amplifier** where:

Av = 1  

The output is directly connected to the inverting input, creating **100% negative feedback**.



## Voltage Gain

For a non-inverting amplifier:

Av = 1 + (Rf / Rin)  

For voltage follower:

Rf = 0  
Rin = ∞  

So:

Av = 1  

Therefore:

Vout = Vin  



## Key Characteristics

### 1. High Input Impedance

- The op-amp input draws almost zero current  
- Prevents loading of the source  



### 2. Low Output Impedance

- Can drive low-resistance loads  
- Acts as a buffer between stages  



### 3. Unity Gain

- Output voltage equals input voltage  
- No amplification, only signal buffering  



### 4. Negative Feedback

- Stabilizes gain  
- Improves linearity  
- Reduces distortion  



# Working Principle

The voltage follower operates based on the concept of **negative feedback and virtual short**.



## Step-by-Step Operation

### 1. Input Applied

- Input voltage is applied to the **non-inverting terminal (+)**  
- Output is connected to **inverting terminal (−)**  



### 2. Virtual Short Concept

Due to very high open-loop gain of the op-amp:

V+ ≈ V−  

So:

Vin ≈ Vout  



### 3. Feedback Action

- If output tries to deviate from input:
  - Feedback forces it to correct  
- The op-amp continuously adjusts output  



### 4. Final Condition

Vout = Vin  

Thus, output “follows” the input  



# Frequency Response

- At low frequencies:
  - Gain remains unity (0 dB)  

- At high frequencies:
  - Gain decreases due to internal capacitances  

- Bandwidth is very high compared to other configurations  

# CIRCUIT DIAGRAM :

### Load Connection

The load resistance RL = 560 Ω is connected between the output terminal (Vout) and ground. This allows the voltage follower to drive the load and demonstrates its low output impedance characteristics.

<img width="929" height="700" alt="image" src="https://github.com/user-attachments/assets/8cee412d-87d4-460d-aa6b-ea7ffebbf353" />

# DC Operating Point Analysis :

<img width="1515" height="825" alt="Screenshot 2026-04-05 231617" src="https://github.com/user-attachments/assets/2a84ab6c-d8ff-409a-b756-273a6ef6139e" />


## Simulation Results (LTspice)

| Parameter | Value |
|----------|------|
| VDD | +15 V |
| VSS | −15 V |
| Vin | 0 V |
| Vout | 1.925 × 10⁻⁵ V ≈ 0 V |
| I(R1) | 3.43786 × 10⁻⁸ A |



## Analysis

### 1. Output Voltage

- The output voltage is approximately:

  Vout ≈ 0 V  

- This confirms:

  Vout ≈ Vin  

**Voltage follower behavior verified**  



### 2. Load Current

Using Ohm’s Law:

I = V / R  

Since Vout ≈ 0:

I ≈ 0 A  

**Matches simulation result**  



### 3. Op-Amp Operation

- Negative feedback forces:

  V+ ≈ V−  

- Since Vin = 0 V:

  Output stabilizes at 0 V  



### 4. Offset Observation

- Small output value (~µV range) is observed  
- This is due to:
  - Internal offset voltage  
  - Numerical simulation precision  

**Practically considered as zero**  



## Conclusion

The DC operating point analysis confirms that the voltage follower maintains the output voltage equal to the input voltage under steady-state conditions. The negligible output current and near-zero output voltage validate proper unity gain operation and correct circuit design.
# Transient Analysis :

<img width="1919" height="917" alt="image" src="https://github.com/user-attachments/assets/3702b7fd-4e62-47be-9c4a-906b6aa466a3" />


## Observation

- The input waveform (Vin) is a sinusoidal signal  
- The output waveform (Vout) is also sinusoidal  

### Key Observations:

- Output follows input exactly  
- No phase shift observed  
- Amplitude of output ≈ amplitude of input  
- Both waveforms are in phase (0° phase difference)  



## Waveform Analysis

- Peak input voltage ≈ ±5 V  
- Peak output voltage ≈ ±5 V  

So:

Vout ≈ Vin  

 **Confirms unity gain**  



## Circuit Behavior

- Due to negative feedback:
  
  V+ ≈ V−  

- Therefore:

  Vout = Vin  

- The op-amp continuously adjusts output to match input  



## Effect of Load (RL)

- Even with RL = 560 Ω:
  - Output waveform remains unchanged  
  - No amplitude drop observed  

**Demonstrates low output impedance**  



## Conclusion

The transient analysis confirms that the voltage follower accurately reproduces the input signal at the output without distortion or phase shift. The circuit provides unity gain and effectively drives the load, validating its function as a buffer amplifier.



# AC Analysis :

 
- Frequency Sweep:

.ac dec 10 1 1G  

<img width="1919" height="888" alt="image" src="https://github.com/user-attachments/assets/0fb1ffe1-823b-4eaa-a900-ad6fbe14a461" />

## Observation

- At low frequencies:
  - Gain is approximately **0 dB**  
  - Output follows input  

- As frequency increases:
  - Gain starts decreasing  
  - Phase shift increases  



## Midband Gain

Gain (in dB):

Av ≈ 0 dB  

Convert to linear:

Av = 1  

**Confirms unity gain**  



## Cutoff Frequency

- The frequency at which gain drops by **−3 dB** is the cutoff frequency
  <img width="1919" height="898" alt="image" src="https://github.com/user-attachments/assets/af7f2d6a-ce35-44f8-ae1a-88519bc3b57f" /> 

From graph:

fH ≈ 1 MHz (approx)  



## Bandwidth

BW = fH − fL  

Since:

fL ≈ 0 Hz  

BW ≈ 1 MHz  



## Phase Response

- At low frequency:
  - Phase ≈ 0°  

- At high frequency:
  - Phase decreases (lag increases)  



## Interpretation

- The voltage follower maintains unity gain over a wide frequency range  
- At higher frequencies:
  - Internal capacitances reduce gain  
  - Phase lag increases  



## Conclusion

The AC analysis shows that the voltage follower provides a constant gain of unity (0 dB) over the low-frequency range. The gain starts to decrease beyond the cutoff frequency (~1 MHz), indicating the bandwidth limitation of the op-amp. This confirms that the circuit acts as a buffer with wide bandwidth and stable frequency response.

# Results, Inference, Interpretation and Final Conclusion



# 1. Results Table

| Analysis Type | Parameter | Value |
|--------------|----------|------|
| DC Analysis | Vout | ≈ 0 V |
| DC Analysis | Load Current | ≈ 0 A |
| Transient Analysis | Input Peak Voltage | ±5 V |
| Transient Analysis | Output Peak Voltage | ±5 V |
| Transient Analysis | Phase Difference | 0° |
| AC Analysis | Gain (dB) | 0 dB |
| AC Analysis | Gain (Linear) | 1 V/V |
| AC Analysis | Upper Cutoff Frequency (fH) | ≈ 1 MHz |
| AC Analysis | Bandwidth (BW) | ≈ 1 MHz |



# 2. Inference

- The voltage follower maintains **unity gain (Av = 1)** under all operating conditions.  
- The output voltage follows the input voltage accurately, confirming proper buffer operation.  
- The circuit exhibits:
  - **High input impedance** → no loading of source  
  - **Low output impedance** → effective load driving  
- The bandwidth is high (~1 MHz), showing good frequency response.  
- The circuit remains stable due to **negative feedback**.  



# 3. Interpretation

- In DC analysis, the output settles at approximately zero when input is zero, confirming correct biasing and operation.  
- In transient analysis:
  - Output waveform is identical to input  
  - No phase shift or distortion is observed  
  - Confirms linear operation of the circuit  

- In AC analysis:
  - Gain remains constant (0 dB) at low frequencies  
  - Gain decreases at higher frequencies due to internal capacitances  
  - Phase shift increases with frequency  

 This shows that:

- The voltage follower acts as an **ideal buffer at low frequencies**  
- At high frequencies, performance is limited by **op-amp bandwidth**  



# 4. Final Conclusion

The voltage follower circuit is successfully designed and analyzed. The simulation results confirm that the circuit provides unity gain, zero phase shift, and accurate signal reproduction. The high input impedance and low output impedance make it suitable for impedance matching and buffering applications. The frequency response demonstrates a wide bandwidth, validating the effectiveness of the circuit in practical analog systems.

---
# CIRCUIT - 2 

# Inverting Amplifier

## Aim

To design and analyze an inverting amplifier using an operational amplifier and study its frequency response.



## Specifications

- Supply Voltage: ±VCC = ±15 V  
- Input Signal: Vin(pp) = 10 Vpp  
- Frequency: f = 1 kHz  
- Desired Gain: Av = −7 V/V  


## Introduction

An inverting amplifier is one of the fundamental configurations of an operational amplifier (Op-Amp). In this configuration, the input signal is applied to the **inverting terminal (−)** of the op-amp, while the **non-inverting terminal (+)** is connected to ground.

The output signal obtained is an amplified version of the input signal but with a **phase reversal of 180°**, meaning the output is inverted.

Inverting amplifiers are widely used in analog circuits for signal processing applications such as scaling, inversion, filtering, and summing operations.



## Theory

An ideal operational amplifier has the following properties:

- Infinite open-loop gain  
- Infinite input impedance  
- Zero output impedance  
- Zero input current  

Due to the high gain and negative feedback, the op-amp operates under the **virtual ground concept**.



### Virtual Ground Concept

Since the non-inverting terminal is grounded:

V+ = 0 V  

Due to negative feedback:

V− ≈ V+  

So:

V− ≈ 0 V  

This point is called a **virtual ground**, as it is not physically connected to ground but behaves like ground.



## Gain Derivation

Let:

Rin = input resistor  
Rf = feedback resistor  

Input current:

I = Vin / Rin  

Since input current to op-amp is zero, the same current flows through Rf:

I = − Vout / Rf  

Equating currents:

Vin / Rin = − Vout / Rf  

Rearranging:

Vout = − (Rf / Rin) × Vin  



### Voltage Gain

Av = Vout / Vin  

Av = − (Rf / Rin)  



### Key Features

- Output is inverted (180° phase shift)  
- Gain depends only on resistor ratio  
- Input impedance = Rin  
- Stable operation due to negative feedback  



## Working Principle

The working of an inverting amplifier is based on **negative feedback and current flow control**.



### Step-by-Step Operation

1. Input Signal Application  
   - Input voltage is applied to the inverting terminal through resistor Rin  



2. Virtual Ground Formation  
   - Non-inverting terminal is grounded  
   - Due to feedback, inverting terminal is also at ≈ 0 V  



3. Current Flow  
   - Input current flows through Rin:

     I = Vin / Rin  

   - Since op-amp input draws no current, the same current flows through Rf  



4. Output Generation  
   - Voltage across Rf produces output:

     Vout = − I × Rf  



5. Final Output  
   - Output is amplified and inverted version of input  



## Frequency Behavior

- At low frequencies:
  - Gain remains constant  

- At high frequencies:
  - Gain decreases due to internal capacitances  

- Bandwidth depends on op-amp characteristics  


## Gain Formula

Av = Vout / Vin  

For inverting amplifier:

Av = − (Rf / Rin)  



## Design Calculation

Given:

Av = −7  

So:

Rf / Rin = 7  

Choose:

Rin = 1 kΩ  
Rf = 7 kΩ 

## CIRCUIT DIAGRAM:

<img width="975" height="757" alt="image" src="https://github.com/user-attachments/assets/533aa24c-0d8e-402e-be9b-626d06f7c49f" />


# DC Operating Point Analysis 

<img width="1644" height="884" alt="image" src="https://github.com/user-attachments/assets/737fec97-e0a5-48c2-acf0-4313f5bf9cdc" />


## Simulation Results (LTspice)

| Parameter | Value |
|----------|------|
| VDD | +15 V |
| VSS | −15 V |
| Vin | 0 V |
| Vout | 0.000712 V |
| I(Rin) | 1.92485 × 10⁻⁸ A |
| I(Rf) | 9.90104 × 10⁻⁸ A |



## Analysis

### 1. Output Voltage

- Theoretical:

  Vout = − (Rf / Rin) × Vin  

  Vout = 0 V  

- Simulation:

  Vout ≈ 0.712 mV  

**Very small deviation from ideal**  



### 2. Reason for Offset

The small output voltage is due to:

- Input offset voltage of uA741  
- Input bias currents  
- Non-ideal characteristics of op-amp  

**Practically treated as zero**  



### 3. Current Analysis

- Ideally:

  I = Vin / Rin = 0  

- Simulation shows very small currents:

  I(Rin) ≈ 10⁻⁸ A  

**Due to bias currents**  



### 4. Virtual Ground Verification

- Non-inverting terminal is grounded  

- Due to negative feedback:

  V− ≈ 0 V  

 **Virtual ground condition satisfied**  



## Conclusion

The DC operating point analysis confirms that the inverting amplifier is correctly biased. The output voltage is approximately zero for zero input, validating theoretical expectations. The small deviation observed is due to practical limitations of the op-amp and can be neglected.


# Transient Analysis:

## Theoretical Output

Vout = −7 × Vin  

For Vin = ±5 V:

Vout = ±35 V  



## Practical Limitation

- Op-amp supply = ±15 V  
- Maximum output swing ≈ ±13 V  

So:

Output cannot reach ±35 V  

<img width="1919" height="893" alt="image" src="https://github.com/user-attachments/assets/c0d78560-264a-4ccf-a271-7fa984b5a6dc" />

## Observation

- Input waveform is sinusoidal  
- Output waveform is:
  - Inverted  
  - Clipped at ±15 V  
  - Appears like a square wave  



## Reason for Distortion

- Required output exceeds supply limits  
- Op-amp enters **saturation region**  
- Output is limited to supply voltage  



## Key Observations

- Phase shift = 180° (inversion confirmed)  
- Output is not sinusoidal due to clipping  
- Gain is not maintained in large signal condition  



## Conclusion

The transient analysis shows that the inverting amplifier does not operate linearly for large input signals. Since the required output exceeds the supply voltage limits, the op-amp saturates, resulting in a clipped waveform. This demonstrates the importance of keeping the input signal within the linear operating range of the amplifier.


# AC Analysis :
Frequency sweep:

.ac dec 10 1 1G  
<img width="1905" height="881" alt="image" src="https://github.com/user-attachments/assets/9230bf0e-81bc-4033-a02f-0676cd0b626b" />
## Observation

- At low frequencies:
  - Gain is constant  
  - Output is inverted  

- From graph :

  Gain ≈ 16.900 dB  

## Gain Calculation

Theoretical gain:

Av = − (Rf / Rin) = −7  

Convert to dB:

Av(dB) = 20 log(7) ≈ 16.900 dB  

 **Matches simulation**  



## Phase Response

- Phase ≈ 180°  

**Confirms inversion**  

<img width="1919" height="820" alt="image" src="https://github.com/user-attachments/assets/bc06a0ab-1e7f-4fb2-ab37-69f49ba9595f" />


## Cutoff Frequency

- From graph:
  
  fH ≈ 131.77 KHz  



## Bandwidth

BW = fH − fL  

Since:

fL ≈ 0 Hz  

BW ≈ 131.77 KHz 



## Interpretation

- The amplifier maintains constant gain in the midband region  
- At higher frequencies:
  - Gain decreases  
  - Phase shift changes  

- This is due to:
  - Internal capacitances of op-amp  
  - Gain-bandwidth limitation  



## Conclusion

The AC analysis confirms that the inverting amplifier provides a constant gain of approximately 16.9 dB with a phase shift of 180°.  The results match theoretical expectations and demonstrate proper amplifier operation.

# Results, Inference, Interpretation and Final Conclusion



# 1. Results Table

| Analysis Type | Parameter | Value |
|--------------|----------|------|
| DC Analysis | Vout | ≈ 0.000712 V |
| DC Analysis | I(Rin) | 1.92 × 10⁻⁸ A |
| DC Analysis | I(Rf) | 9.90 × 10⁻⁸ A |
| Transient Analysis | Input Peak Voltage | ±5 V |
| Transient Analysis | Output Voltage | Clipped at ±15 V |
| Transient Analysis | Phase Shift | 180° |
| AC Analysis | Gain (V/V) | −7 |
| AC Analysis | Gain (dB) | ≈ 16.9 dB |
| AC Analysis | Cutoff Frequency (fH) | ≈ 131.77 kHz |
| AC Analysis | Bandwidth (BW) | ≈ 131.77 kHz |



# 2. Inference

- The inverting amplifier provides a gain of **−7**, as designed using resistor ratio.  
- The circuit shows **phase inversion (180° shift)** between input and output.  
- DC analysis confirms proper biasing with output near zero for zero input.  
- AC analysis verifies that the gain remains constant in the midband region.  
- The bandwidth is limited (~131.77 kHz) due to op-amp characteristics.  
- For large input signals, the circuit enters **saturation**, causing distortion.  



# 3. Interpretation

- In DC operation, the output remains nearly zero due to the **virtual ground condition**, confirming correct functioning.  

- In transient analysis:
  - The output waveform is inverted  
  - Clipping occurs because required output exceeds supply voltage  
  - The amplifier behaves non-linearly for large signals  

- In AC analysis:
  - Gain remains constant at low frequencies  
  - Gain decreases at high frequencies due to internal capacitances  
  - Phase remains near 180°, confirming inversion  

 This shows that:

- The amplifier operates linearly only within its **dynamic range**  
- Beyond this range, it behaves like a **limiter (clipping device)**  



# 4. Final Conclusion

The inverting amplifier is successfully designed and analyzed. The circuit provides the desired gain of −7 with a phase shift of 180°, confirming theoretical expectations. The DC and AC analyses validate proper operation and frequency response, while the transient analysis highlights the limitations of the amplifier under large signal conditions. The results demonstrate the importance of operating within the linear region to achieve accurate amplification.

---
# Comparison of Voltage Follower and Inverting Amplifier



## Comparison Table

| Parameter | Voltage Follower | Inverting Amplifier |
|----------|----------------|--------------------|
| Gain (Av) | 1 (Unity) | −7 (depends on Rf/Rin) |
| Gain (dB) | 0 dB | ≈ 16.9 dB |
| Phase Shift | 0° (in-phase) | 180° (inverted) |
| Output Voltage | Same as input | Amplified and inverted |
| Function | Buffer / Impedance matching | Signal amplification |
| Input Impedance | Very high | Equal to Rin (finite) |
| Output Impedance | Very low | Moderate |
| Bandwidth | High (~1 MHz) | Lower (~131 kHz) |
| Frequency Response | Flat over wide range | Limited by gain-bandwidth |
| Load Driving | Excellent | Moderate |
| Distortion | Very low | Possible at high input (clipping) |
| Linearity | High | Limited by input range |
| Complexity | Simple | Requires resistor design |
| Application | Isolation, buffering | Amplification, inversion |

---

## Key Differences

### 1. Gain Behavior
- Voltage follower:
  - No amplification (Av = 1)
- Inverting amplifier:
  - Provides controlled gain (Av = −Rf/Rin)



### 2. Phase Relationship
- Voltage follower:
  - Output in phase with input
- Inverting amplifier:
  - Output is 180° out of phase



### 3. Impedance Characteristics
- Voltage follower:
  - High input impedance → no loading
  - Low output impedance → drives load easily
- Inverting amplifier:
  - Input impedance depends on Rin
  - Less ideal for buffering



### 4. Frequency Performance
- Voltage follower:
  - Wider bandwidth
- Inverting amplifier:
  - Bandwidth reduces with gain (GBW limitation)



### 5. Signal Behavior
- Voltage follower:
  - Faithfully reproduces input
  - No distortion
- Inverting amplifier:
  - Amplifies signal
  - Can distort if input is large (clipping)

---

## Interpretation

- The voltage follower is best suited for **signal buffering and impedance matching**.
- The inverting amplifier is used for **controlled amplification and signal inversion**.
- The choice of circuit depends on application:
  - Use voltage follower when signal integrity is important  
  - Use inverting amplifier when gain is required  

---

## Final Comparison Conclusion

The voltage follower and inverting amplifier serve different purposes in analog circuits. The voltage follower ensures accurate signal transfer without amplification, while the inverting amplifier provides gain with phase inversion. Both circuits highlight the importance of negative feedback in achieving stable and predictable performance.

---
