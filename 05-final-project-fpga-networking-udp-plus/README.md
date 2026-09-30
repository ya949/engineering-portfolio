# Final Project: Reliable High-Speed Networking on FPGA Platforms

Fourth-year engineering project at Ben-Gurion University of the Negev, completed together with Elijah Oshrath. Advisers: Prof. Dvora Ron and Eyal Lampel.

Report: [Final Report](docs/Final_Report_Reliable_High-Speed_Networking_on_FPGA.pdf), 116 pages, in English.

## Overview

The project builds and measures three ways of serving a Gigabit Ethernet link from an FPGA platform:

- **TCP server** on a custom Zynq-7000 board. ARM Cortex-A9, external DDR3 and an optimized lwIP stack on the hard Ethernet MAC.
- **UDP echo server** on the VCU118. The data path is implemented in programmable logic with a MicroBlaze, a UDP Offload Engine, AXI DMA and a Tri Mode Ethernet MAC over SGMII. A 64 KB BRAM buffer holds the payload between receive and echo.
- **UDP++ reliability layer** on the same platform. A receiver-driven NAK mechanism with a TX history buffer and selective retransmission, implemented in hardware and inserted inline in the AXI Stream path.

Verification used Wireshark captures, a stress-test tool and ILA probes inside the FPGA. The report also documents the integration problems found on both platforms, each in symptom, diagnosis and resolution form.

## Results

| Metric | TCP (Zynq PS) | UDP (VCU118 PL) | UDP++ (VCU118 PL) |
|---|---|---|---|
| Throughput | about 940 Mbps over 300 s | about 850 Mbps at 1,024 B, 809 Mbps at 512 B | 692 Mbps at 512 B |
| RTT p50 / p99 at 512 B | not instrumented | 413.1 / 3,391 µs | 506.9 / 2,593 µs |
| Loss | none observed, TCP retransmission | about 1% unrecovered | about 1% raw loss, NAK-based recovery demonstrated in the tested scenarios |
| Logic (LUT) | 0% of PL | 16,067 (1.36%) | 18,976 (1.61%) |
| Block RAM | 0% of PL | 52.5 (2.43%) | 255.5 (11.83%) |
| Timing slack (WNS) | not applicable | +1.131 ns | +1.418 ns |

The three systems run on different boards with different architectures. The numbers do not show that TCP is faster than UDP in general. UDP++ adds 2,909 LUTs over the UDP baseline and lowers 512-byte throughput by about 14.5% in exchange for hardware loss detection and selective replay.

The UDP Offload Engine core and the traffic tester were provided by the project advisers and are not part of this repository.
