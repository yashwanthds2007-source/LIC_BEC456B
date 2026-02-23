# Experiment 1: Common Source (CS) Amplifier

## Aim
To design and analyze a Common Source (CS) amplifier using tsmc018 technology with:
- Power Budget = 0.5mW
- VDD = 1.2V
- Load Capacitance = 0.5pF

---

## Theory

The MOSFET acts as an amplifier when biased in saturation region:

V_DS ≥ V_OV

The CS amplifier provides:
- High voltage gain
- High input impedance
- 180° phase shift

---

## Design Calculations

### Power Equation
P = VDD × ID

ID = 0.5mW / 1.2V  
ID = 333µA

### Transconductance
gm = 2ID / VOV  
gm = 3.33mS (assuming VOV = 0.2V)

### Drain Resistor
RD = 3k

### Gain
Av = -gmRD  
Av ≈ -2.221 V/V

---

## Circuit Diagram
<img width="1366" height="768" alt="Circuit Diagram With Capacitor" src="https://github.com/user-attachments/assets/fac05edf-4c35-4a07-9abd-c271ff4a7c09" />


---

## DC Operating Point
<img width="1366" height="768" alt="DC operating point" src="https://github.com/user-attachments/assets/d5e2227b-bc03-4719-a08e-16eb6311bc56" />

---

## AC Analysis
<img width="1366" height="768" alt="AC Analysis With Capacitor" src="https://github.com/user-attachments/assets/160f4892-b4b5-43a9-9b85-409b135145b8" />

## Transient Analysis
<img width="1366" height="768" alt="trasient analysis both" src="https://github.com/user-attachments/assets/5f022073-a2cf-4f44-9155-f3627e5865f7" />



---

## Conclusion
The CS amplifier was successfully designed under 0.5mW power constraint with gain ≈ -2.221 V/V.
