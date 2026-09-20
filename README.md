# LDO
In this project we design and simulation of an Analog Low-Dropout (LDO) Regulator using SCL 180nm CMOS Technology.

The LDO is designed to generate a regulated DC output of approximately 1.5 V while supporting load currents up to 100 mA. The design integrates a Band-Gap Reference (BGR), OTA/Error Amplifier, PMOS pass transistor, feedback network, and Miller compensation to achieve regulation, stability, transient performance, and power-supply rejection.

The final simulated design achieves a regulated output voltage of 1.502353 V and an efficiency of 83.12% at 20 mA load current.

---

## 🎯 Objectives

The main objectives of this project are:         
 
Design an analog LDO regulator using SCL 180 nm CMOS technology.                                                
Generate a stable reference voltage using a Band-Gap Reference (BGR).                                                 
Design an OTA/Error Amplifier for feedback control.                                                   
Implement a PMOS pass transistor for voltage regulation.                                                        
Design suitable feedback and compensation networks.                                                    
Analyze the LDO under different temperatures and load conditions.                                              
Evaluate:                  
        - ⚡ Transient Response
- 📈 Line Regulation
- 📉 Load Regulation
- 🔋 Efficiency
- 📡 PSRR
- 🌡️ Temperature Variation
- 📐 Stability
- 🔄 Load Transient Response
                                 


---


## Band-Gap Reference (BGR)

The Band-Gap Reference generates a relatively temperature-independent reference voltage for the LDO.

The BGR is divided into three branches:

Branch B1: BJT Q2                     
Branch B2: BJT Q3                          
Branch B3: BJT Q4 / current-mirrored branch

The PMOS stages ensure that approximately the same current flows through the branches, while the NMOS stages keep the source voltages close to each other.

-A quiescent current of:
Iq = 15 µA
was selected for the BGR branches.


<img width="1057" height="742" alt="image" src="https://github.com/user-attachments/assets/f30b80d2-5a71-4916-b431-b2894046ea17" />













````markdown
# 🔋 Analog LDO Regulator — SCL 180nm CMOS

<p align="center">

<img src="https://img.shields.io/badge/Technology-SCL%20180nm-blue?style=for-the-badge">
<img src="https://img.shields.io/badge/Domain-Analog%20IC%20Design-orange?style=for-the-badge">
<img src="https://img.shields.io/badge/Circuit-LDO%20Regulator-green?style=for-the-badge">
<img src="https://img.shields.io/badge/Output-1.5V-red?style=for-the-badge">

</p>

<p align="center">
<b>Design and Simulation of an Analog Low-Dropout Regulator using SCL 180nm CMOS Technology</b>
</p>

---

## 📌 Project Overview

This project focuses on the **design and simulation of an Analog Low-Dropout (LDO) Regulator using SCL 180nm CMOS Technology**.

The LDO is designed to generate a regulated output voltage of approximately **1.5 V** while supporting load-current analysis up to **100 mA**.

The complete regulator consists of several analog building blocks working together in a feedback loop:

- 🔹 **Band-Gap Reference (BGR)** — Generates the reference voltage
- 🔹 **OTA / Error Amplifier** — Compares feedback voltage with the reference
- 🔹 **PMOS Pass Transistor** — Controls the output current
- 🔹 **Feedback Network** — Senses and regulates the output voltage
- 🔹 **Miller Compensation** — Provides loop stability

The design was evaluated for:

- ⚡ Transient Response
- 📈 Line Regulation
- 📉 Load Regulation
- 🔋 Efficiency
- 📡 Power Supply Rejection Ratio (PSRR)
- 🌡️ Temperature Variation
- 📐 Stability
- 🔄 Load Transient Response

---

# ✨ Key Features

### 🔋 Voltage Regulation

- Regulated output voltage ≈ **1.5 V**
- Final simulated output voltage: **1.502353 V**
- Feedback-based voltage regulation

### ⚡ Load Capability

- Performance evaluated at **20 mA**
- Stability evaluated at **20 mA, 50 mA and 100 mA**

### 🌡️ Temperature Analysis

The LDO was analyzed at:

- **0°C**
- **27°C**
- **60°C**

### 📡 Frequency & Stability Analysis

- Loop-gain analysis
- Phase-margin analysis
- Gain-margin analysis
- Gain crossover frequency
- Miller compensation
- PSRR analysis

### 🔄 Transient Analysis

The regulator was tested under:

- **20 mA → 50 mA**
- **50 mA → 20 mA**

load transitions.

---

# 🏗️ System Architecture

```text
                         VIN
                          │
                          ▼
                ┌──────────────────┐
                │   PMOS PASS      │
                │   TRANSISTOR     │
                └────────┬─────────┘
                         │
                         ▼
                       VOUT
                         │
                    ┌────┴────┐
                    │         │
                    │ R3 / R4 │
                    │ Feedback│
                    │ Network  │
                    └────┬────┘
                         │
                         │ VFB
                         ▼
              ┌─────────────────────┐
              │   OTA / ERROR       │
              │     AMPLIFIER       │
              └──────────┬──────────┘
                         │
                         │ Control
                         ▼
                   PMOS Gate


              ┌─────────────────────┐
              │       BGR           │
              │  Band-Gap Reference │
              └──────────┬──────────┘
                         │
                        VREF
                         │
                         ▼
                    OTA Input
````

---

# 🔬 Design Methodology

The LDO was designed in multiple stages.

```text
BGR Design
    ↓
Temperature Compensation
    ↓
OTA / Error Amplifier
    ↓
PMOS Pass Transistor
    ↓
Feedback Network
    ↓
Miller Compensation
    ↓
Stability Analysis
    ↓
Transient / DC / AC Analysis
    ↓
Final Performance Evaluation
```

---

# 🔹 1. Band-Gap Reference (BGR)

The **Band-Gap Reference (BGR)** provides the reference voltage required by the LDO control loop.

The BGR consists of three main branches:

| Branch | Device                           |
| ------ | -------------------------------- |
| 🟢 B1  | BJT Q2                           |
| 🟢 B2  | BJT Q3                           |
| 🟢 B3  | BJT Q4 / Current-Mirrored Branch |

The PMOS stages are used to maintain approximately equal branch currents.

The NMOS stages help keep the source voltages close to each other and reduce errors caused by channel-length modulation.

### ⚡ BGR Quiescent Current

The selected current through the BGR branches was:

```text
Iq = 15 µA
```

A higher quiescent current can provide advantages in terms of noise and mismatch, but increases power consumption and reduces efficiency.

---

# 🌡️ 2. BGR Temperature Compensation

The BGR uses the cancellation of two temperature-dependent components:

```text
CTAT + PTAT → Temperature-Compensated Reference
```

Where:

* **CTAT** → Complementary To Absolute Temperature
* **PTAT** → Proportional To Absolute Temperature

The BJT \(V_{BE}\) provides the CTAT component.

The difference between the BJT junction voltages generates the PTAT component.

### 📊 BJT Simulation

For the BJT with multiplier = 8:

```text
VBE @ 27°C = 731.914 mV
```

For the BJT with multiplier = 1:

```text
VBE @ 27°C = 788.615 mV
```

The CTAT slope obtained for the multiplier = 1 BJT was:

```text
CTAT Slope = -1.33832 mV/K
```

---

# 🧮 3. BGR Design Calculations

The PTAT slope is given by:

```text
PTAT slope = VT × (R1 / R0) × ln(n)
```

The selected design values were:

```text
VT = 26 mV
T  = 300 K
R0 = 3.78 kΩ
n  = 8
```

The calculated resistance was:

```text
R1 ≈ 23.4 kΩ
```

The final value was adjusted by observing the temperature dependence of the reference voltage.

---

# 🔹 4. OTA / Error Amplifier

The error amplifier consists of:

* Differential amplifier
* PMOS common-source stage
* Biasing circuitry

The differential amplifier provides the initial gain and the PMOS common-source stage provides additional amplification.

### ⚙️ Differential Amplifier

The selected tail current was:

```text
I_TAIL = 5 µA
```

The differential amplifier alone achieved approximately:

```text
Gain ≈ 45 dB
```

The amplified error signal is used to control the gate of the PMOS pass transistor.

---

# 🔧 5. OTA Transistor Sizing

The final reported OTA transistor sizing is:

| MOSFET | W (µm) | L (µm) |   W/L | Multiplier |  Overdrive |
| ------ | -----: | -----: | ----: | ---------: | ---------: |
| M0     |    0.6 |    1.2 |   0.5 |          1 | 211.275 mV |
| M1     |    0.6 |    1.2 |   0.5 |          1 | 214.844 mV |
| M2     |    0.6 |    1.0 |   0.6 |          1 | 436.251 mV |
| M3     |    0.6 |    1.0 |   0.6 |          1 | 436.266 mV |
| M4     |   2.13 |    1.0 |  2.13 |          1 | 126.095 mV |
| M5     |    3.8 |    1.0 |   3.8 |          5 | 154.117 mV |
| M6     |    1.0 |    1.0 |   1.0 |          5 |  131.42 mV |
| M7     |   1.64 |   0.45 | 3.645 |          1 | 236.702 mV |
| M8     |   1.69 |    0.5 |  3.38 |          1 | 94.7928 mV |

---

# 🔋 6. PMOS Pass Transistor

The main regulating element of the LDO is the **PMOS pass transistor**.

Its primary function is to control the current delivered to the load based on the control signal generated by the OTA.

The transistor width and multiplier were adjusted to provide sufficient current during load-transient conditions.

### ⚙️ Pass Transistor — M9

| Parameter  |      Value |
| ---------- | ---------: |
| Width      |      70 µm |
| Length     |    0.18 µm |
| W/L        |     388.89 |
| Multiplier |         80 |
| Overdrive  | 89.1108 mV |

---

# 🔄 7. Feedback Network

The output voltage is sensed using the resistor feedback network:

```text
R3 + R4
```

The resistor ratio determines the feedback factor \(β\).

The feedback network provides the OTA with a scaled version of the output voltage, allowing the error amplifier to regulate the output around the reference voltage.

The final simulated output voltage was:

```text
VOUT = 1.502353 V
```

The report notes that the output can be trimmed closer to **1.5 V** using more precise feedback resistor values.

---

# 📐 8. Miller Compensation

The uncompensated loop did not provide sufficient stability.

Therefore, **Miller compensation** was introduced.

Increasing the Miller capacitance:

* 📉 Reduces bandwidth
* 📉 Reduces high-frequency loop gain
* 📈 Improves phase margin
* 🔄 Improves stability

The target phase margin was approximately:

```text
PM ≈ 45°
```

at the worst-case load.

The final selected Miller capacitance was:

```text
Cc = 15 pF
```

A compensation resistor \(R_c\) was selected to position the nulling zero near the second pole.

---

# 🧪 Simulation Analysis

The complete LDO was analyzed using multiple simulation cases.

```text
                 ┌─────────────────────┐
                 │    LDO Simulation    │
                 └──────────┬──────────┘
                            │
          ┌─────────────────┼─────────────────┐
          ▼                 ▼                 ▼
      DC Analysis       AC Analysis      Transient
          │                 │                 │
          ▼                 ▼                 ▼
   Line Regulation       PSRR          Load Transient
   Load Regulation      Stability          Response
   Output Voltage       Loop Gain
          │                 │
          └─────────────────┼─────────────────┘
                            ▼
                     Final Results
```

---

# 📊 RESULTS

## 🏆 Final Performance Summary

| Parameter              | Condition  | Achieved Value |
| ---------------------- | ---------- | -------------: |
| 🔋 Output Voltage      | —          | **1.502353 V** |
| ⚡ Efficiency           | 20 mA      |     **83.12%** |
| 📡 PSRR @ 100 kHz      | 20 mA      |  **−27.68 dB** |
| 📈 Line Regulation     | 20 mA      |   **40.95 mV** |
| 📉 Load Regulation     | 20 mA      |    **−406 µΩ** |
| 🔻 Undershoot          | 20 → 50 mA | **190.455 mV** |
| ⏱️ Undershoot Duration | 20 → 50 mA |      **80 ns** |
| 🔺 Overshoot           | 50 → 20 mA | **160.844 mV** |
| ⏱️ Overshoot Duration  | 50 → 20 mA |      **73 ns** |

---

# ⚡ 1. Transient Response

The transient response was evaluated at:

```text
🌡️ 0°C
🌡️ 27°C
🌡️ 60°C
```

### 🔻 Load Increase

```text
20 mA → 50 mA
```

Result:

```text
Undershoot = 190.455 mV
Duration   = 80 ns
```

### 🔺 Load Decrease

```text
50 mA → 20 mA
```

Result:

```text
Overshoot = 160.844 mV
Duration  = 73 ns
```

### 📈 Result Files

Recommended repository location:

```text
results/
└── transient_response/
    ├── transient_0C.png
    ├── transient_27C.png
    ├── transient_60C.png
    ├── load_20mA_to_50mA.png
    └── load_50mA_to_20mA.png
```

---

# 📈 2. Line Regulation

Line regulation was evaluated at:

```text
🌡️ 0°C
🌡️ 27°C
🌡️ 60°C
```

Final reported value:

```text
Line Regulation = 40.95 mV
```

### 📊 Result Files

```text
results/
└── line_regulation/
    ├── line_regulation_0C.png
    ├── line_regulation_27C.png
    └── line_regulation_60C.png
```

---

# 📉 3. Load Regulation

Load regulation was evaluated at:

```text
🌡️ 0°C
🌡️ 27°C
🌡️ 60°C
```

Final reported value:

```text
Load Regulation = -406 µΩ
```

### 📊 Result Files

```text
results/
└── load_regulation/
    ├── load_regulation_0C.png
    ├── load_regulation_27C.png
    └── load_regulation_60C.png
```

---

# 🔋 4. Efficiency

The simulated efficiency at 20 mA load was:

```text
Efficiency = 83.12%
```

### 📊 Result

```text
results/
└── efficiency/
    ├── efficiency_0C.png
    ├── efficiency_27C.png
    └── efficiency_60C.png
```

---

# 📡 5. Power Supply Rejection Ratio — PSRR

The PSRR was evaluated under worst-load conditions at different temperatures.

The final reported value at **100 kHz and 20 mA** was:

```text
PSRR @ 100 kHz = -27.68 dB
```

The BGR itself showed approximately:

```text
BGR PSRR ≈ -26 dB
```

This indicates that the BGR contributes significantly to the overall PSRR limitation.

### 📊 Result Files

```text
results/
└── psrr/
    ├── psrr_0C.png
    ├── psrr_27C.png
    └── psrr_60C.png
```

---

# 📐 6. Stability Analysis

## 🌡️ Stability vs Temperature

| Temperature | Phase Margin | Gain Margin | Gain Crossover Frequency |
| ----------: | -----------: | ----------: | -----------------------: |
|         0°C |       42.72° |     9.14 dB |                 9.28 MHz |
|        27°C |       43.10° |     9.62 dB |                 8.70 MHz |
|        60°C |       43.31° |    10.07 dB |                 8.18 MHz |

---

## 🔄 Stability vs Load

The LDO stability was also evaluated at **27°C** for different load currents.

| Load Current | Phase Margin | Gain Margin | Gain Crossover Frequency |
| -----------: | -----------: | ----------: | -----------------------: |
|        20 mA |       42.72° |     9.14 dB |                 9.28 MHz |
|        50 mA |       46.40° |    12.49 dB |                 8.24 MHz |
|       100 mA |       44.47° |    16.26 dB |                 7.41 MHz |

### 📊 Result Files

```text
results/
└── stability/
    ├── stability_0C.png
    ├── stability_27C.png
    ├── stability_60C.png
    ├── stability_20mA.png
    ├── stability_50mA.png
    └── stability_100mA.png
```

---

# 🔌 7. Quiescent Current

The block-wise quiescent current consumption was:

| Block           | Quiescent Current |
| --------------- | ----------------: |
| Voltage Divider |           13.8 µA |
| BGR             |        45.1331 µA |
| OTA             |       24.84125 µA |

---

# 🌡️ Temperature Analysis

The complete LDO was evaluated over three temperature points:

```text
0°C ─────────► 27°C ─────────► 60°C
```

The following



