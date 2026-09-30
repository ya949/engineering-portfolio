# FPGA Ethernet Performance: TCP and UDP

Two reports that build gigabit Ethernet performance servers on Xilinx hardware and measure them on the bench. The same two systems are the baselines of the [final project](../05-final-project-fpga-networking-udp-plus).

## Reports

| Report | Platform | Pages |
|---|---|---|
| [TCP lwIP Perf Server](docs/TCP_lwIP_Perf_Server_Zynq.pdf) | Custom Zynq board, XC7Z020CLG400-1 | 20 |
| [UDP Ethernet Performance Server](docs/UDP_Ethernet_Performance_Server_VCU118.pdf) | Xilinx VCU118 | 152 |

## TCP on Zynq

- lwIP TCP Perf Server built with Vitis 2024.2 on a custom Zynq board.
- MIO, DDR and ENET0 clock configuration in Vivado, with the Ethernet clock set for 1000 Mbps.
- Throughput measured with iperf over a direct cable link with static IP addresses. Result: about 940 Mbps.

## UDP on VCU118

- MicroBlaze system with Tri Mode Ethernet MAC, Ethernet PCS/PMA in SGMII mode and AXI DMA.
- UDP Offload Engine integrated as a packaged Vivado IP, with a custom TUSER generator block and a stream splitter written in VHDL.
- ILA probes used to verify packet decoding and DMA interrupts on hardware.
- Software echo application in Vitis with a TX/RX loopback test.

### Measured results

| Metric | Value |
|---|---|
| Average throughput | about 850 Mbps |
| TX rate | 860 Mbps |
| RX rate | 851 Mbps |
| Packet loss | about 1% |

BRAM buffer size sweep, 1000 packets with a 1024-byte payload:

| Buffer | Packets returned |
|---|---|
| 8 KB | 993 of 1000 |
| 32 KB | 998 of 1000 |
| 64 KB | 1000 of 1000 |

The UDP Offload Engine core and the traffic tester were provided by the project supervisor and are not part of this repository.
