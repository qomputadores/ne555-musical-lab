# Project 01: 555 Piano Lab - Functional User Guide

## Description
The 555 Piano Lab is an interactive auditing tool designed to verify the frequency accuracy of a 555-based electronic organ. It serves as a visual and auditory bridge, allowing users to compare calculated mathematical ideals with real-world component implementations. The dashboard provides immediate feedback on frequency deviation and component selection for a one-octave scale ($C_4$ to $C_5$).

## Hardware Anatomy (Physics/Theory)
The system simulates a **555 Timer in Astable Mode**. 
- **Oscillation:** The circuit generates a continuous square wave signal.
- **Timing Cycle:** The frequency is dictated by the charge/discharge rates of capacitor $C$ ($100\text{ nF}$) through resistors $R_1$ ($1\text{ k}\Omega$) and $R_2$ (Variable per note).
- **Signal Characteristic:** The output is a square wave, which is mathematically rich in harmonics, providing the distinct "electronic" timbre heard during the audio audit.

## Library Methods
The dashboard utilizes three core functional modules to process information:
- **Synthesis Engine:** Translates the "Obtained Frequency" data into a real-time square wave using the Web Audio API (Oscillators and Gain nodes).
- **Logic Controller:** Manages the interactive state, updating all data cards and mathematical substitutions instantly when a key is triggered.
- **Formatting Module:** Ensures all numerical data follows strict pedagogical standards (dot for thousands, comma for decimals).

## Instructions
Users should follow this workflow to interact with the data:
1. **Note Activation:** Click any color-coded key on the piano to trigger the sound and data profile.
2. **Frequency Comparison:** Locate the **Frequency Analysis** card to compare the musical target (Expected) against the circuit's result (Obtained).
3. **Component Audit:** Review the **Resistor Specs** card. It displays the precision required (Ideal) versus the standard value actually used.
4. **Assembly Guide:** Check the **Hardware & Precision** card for the specific resistor association needed on the breadboard.
5. **Mathematical Breakdown:** Use the **Engineering Equation** section to see exactly how the $R_2$ value was derived.

### Technical Calculation Reference Table
| Note | Expected Freq. (Hz) | Obtained Freq. (Hz) | Ideal R2 (Ω) | Suggested Association | Real R2 (Ω) | Error % |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **C4** | 261,63 | 261,81 | 27.017 | 27 kΩ (1 resistor) | 27.000 | 0,07% |
| **D4** | 293,66 | 293,87 | 24.003 | 12k + 12k (Series) | 24.000 | 0,07% |
| **E4** | 329,63 | 329,80 | 21.323 | 39k // 47k (Parallel) | 21.313 | 0,05% |
| **F4** | 349,23 | 351,21 | 20.117 | 10k + 10k (Series) | 20.000 | 0,56% |
| **G4** | 392,00 | 389,18 | 17.857 | 18 kΩ (1 resistor) | 18.000 | 0,72% |
| **A4** | 440,00 | 439,02 | 15.863 | 15k + 820 (Series) | 15.820 | 0,22% |
| **B4** | 493,88 | 494,75 | 14.089 | 22k // 39k (Parallel) | 14.065 | 0,17% |
| **C5** | 523,25 | 523,63 | 13.264 | 22k // 33k (Parallel) | 13.200 | 0,07% |

## Power/Safety Protocols
- **Voltage Range:** The 555 IC requires a stable supply between $4,5\text{V}$ and $15\text{V}$.
- **Polarity Protection:** Always verify the capacitor orientation and the $V_{CC}$/GND rails to prevent IC damage.
- **Discharge Limit:** Never omit $R_1$ ($1\text{ k}\Omega$); it protects the internal discharge transistor at Pin 7.
- **Output Load:** Use a $10\text{ }\mu\text{F}$ capacitor in series with the speaker to block DC components.

## Connection Table
| COMPONENT | 555 PIN | NOTES |
| :--- | :--- | :--- |
| Supply ($V_{CC}$) | Pin 8 | Main power input |
| Ground (GND) | Pin 1 | Common negative rail |
| Resistor R1 | Pin 8 to 7 | Fixed 1 kΩ charging resistor |
| Resistor R2 | Pin 7 to 6 | Note-specific resistor association |
| Capacitor C | Pin 6 to 1 | 100 nF (104) timing capacitor |
| Jump Wire | Pin 6 to 2 | Enables self-triggering loop |
| Reset | Pin 4 | Tied to $V_{CC}$ to enable operation |
| Output | Pin 3 | Signal to speaker or amplifier |

This material is for classroom use only. 
Commercial distribution is strictly prohibited.
Author: Iwan.
