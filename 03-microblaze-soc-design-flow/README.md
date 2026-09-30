# MicroBlaze SoC Design Flow: From RTL to Custom AXI IP and DDR

One report with five chapters that build a MicroBlaze system step by step with Vivado and Vitis.

Report: [MicroBlaze SoC Design Flow](docs/MicroBlaze_SoC_Design_Flow.pdf), 239 pages.

## Chapters

1. **Chasing LEDs core on VCU118.** VHDL frequency divider that turns a 100 MHz clock into a one-cycle 1 Hz pulse, used as a clock enable for a state machine. Simulated in ModelSim and verified on hardware with an ILA.
2. **MicroBlaze and UART on Zynq-7000.** MicroBlaze with AXI UART Lite at 115200 baud, 64 KB local memory, reset tied to the Clocking Wizard locked signal, and a Hello World application loaded into BRAM through an associated ELF.
3. **Custom AXI4-Lite IP on VCU118.** Register 0 controls the LED mode. Register 1 is read-only and returns a hard-coded version value. The IP was packaged, integrated and tested with JTAG to AXI Master and Tcl commands.
4. **Software control over JTAG-UART on VCU118.** MDM with JTAG UART, no external UART pins. A Vitis application selects the LED mode from single-character commands and reads the version register with Xil_Out32 and Xil_In32.
5. **DDR and AXI GPIO on Artix-7 AC701.** MicroBlaze with a MIG 7 Series DDR controller and an AXI GPIO input interface. Pushbutton values were checked in a serial terminal and in the Vivado ILA.
