# 4 GHz Voltage Controlled Oscillator in 180 nm CMOS

Course project, Introduction to RFIC, Ben-Gurion University of the Negev, February 2026.

Report: [4 GHz Current Starved Ring VCO](docs/RFIC_4GHz_Current_Starved_Ring_VCO.pdf), 21 pages, in Hebrew.

## Design

- Current starved ring VCO with 3 inverter stages.
- TowerJazz TS18PM 180 nm process, 1.8 V supply.
- Cadence Virtuoso ADE with transient, parametric sweep, PSS and pnoise analyses.
- The report includes a literature review of Colpitts, relaxation, cross-coupled LC and ring oscillators, and the reasoning behind the chosen topology.

| Block | W / L |
|---|---|
| Inverter (PMOS / NMOS) | 360 nm / 180 nm |
| Current source (PMOS / NMOS) | 1.35 µm / 450 nm |
| Current mirror (PMOS / NMOS) | 900 nm / 300 nm |

## Results

| Metric | Value |
|---|---|
| Center frequency | 4 GHz at Vctrl of about 842 mV |
| Initial tuning sensitivity | about 7.5 GHz/V |
| Final tuning law | f = 4 GHz + 425 MHz/V x Vctrl over a ±1 V sweep |
| Power at 4 GHz | 134 µW |
| Phase noise | -72.9 dBc/Hz at 1 MHz offset |

The initial sensitivity was too high for stable frequency control. A voltage-controlled voltage source with a gain of 0.05 was added in front of the current mirror, which brought the sensitivity down and kept the response linear. The final sweep covers the 300 MHz range requirement with margin. The noise summary shows the NMOS current-source transistors as the main contributors, at about 14.5% each. The output waveform swings close to rail to rail and is sinusoidal in shape, which follows from the parasitic capacitance at this operating frequency.
