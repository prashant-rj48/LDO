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
Transient response
Line regulation
Load regulation
Efficiency
PSRR
Stability
Phase margin
Gain margin


---


## Band-Gap Reference (BGR)

The Band-Gap Reference generates a relatively temperature-independent reference voltage for the LDO.

The BGR is divided into three branches:

Branch B1: BJT Q2
Branch B2: BJT Q3
Branch B3: BJT Q4 / current-mirrored branch

The PMOS stages ensure that approximately the same current flows through the branches, while the NMOS stages keep the source voltages close to each other.

A quiescent current of:
Iq = 15 µA
was selected for the BGR branches.







