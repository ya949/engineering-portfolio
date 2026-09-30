# Engineering Portfolio

Yair Tayri, Electrical and Computer Engineering student at Ben-Gurion University of the Negev, specializing in VLSI and Control Systems.

This repository collects technical reports from FPGA, embedded, analog IC and PCB design work. Each folder has an English README with a summary and the main results, and the full report as a PDF. The final project report is in English. The other reports are written in Hebrew.

## Projects

| Project | Key result | Platforms | Tools |
|---|---|---|---|
| [Final project: TCP, UDP and UDP++ on Gigabit Ethernet](05-final-project-fpga-networking-udp-plus) | UDP++ reliability layer in hardware: 692 Mbps at 512 B, median RTT 507 µs | Zynq-7000, VCU118 | Vivado, Vitis 2024.2, ILA, Wireshark, iperf |
| [4 GHz current starved ring VCO](01-rfic-4ghz-vco-180nm) | 134 µW at 4 GHz, phase noise -72.9 dBc/Hz at 1 MHz offset | TowerJazz 180 nm CMOS | Cadence Virtuoso |
| [TCP and UDP performance servers](04-fpga-ethernet-tcp-udp) | TCP about 940 Mbps, UDP about 850 Mbps | Zynq-7000, VCU118 | Vivado, Vitis 2024.2, ILA, Wireshark, iperf |
| [MicroBlaze SoC design flow](03-microblaze-soc-design-flow) | Five chapters from RTL to a custom AXI4-Lite IP verified on hardware | VCU118, Zynq-7000, AC701 | Vivado, Vitis, ModelSim, ILA |
| [KiCad power and RGB LED blocks](02-kicad-power-and-led-blocks) | TPS55288 5 to 14 V to 5 V block and an I2C RGB LED driver block | KiCad 9 | KiCad, Git, GitHub |

## Reading the reports

Each PDF opens directly in the GitHub viewer. The long reports have a table of contents on the first pages.
