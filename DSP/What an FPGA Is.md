#dsp #electronics

**An FPGA is a reconfigurable sea of logic gates and wiring you shape into a custom digital circuit — not a processor running code, but hardware you describe.** Everything happens in parallel, every clock edge, with timing deterministic to the nanosecond, because there is no OS, no scheduler, no instruction stream to interrupt.

# Reference

**What's inside:** lookup tables (small programmable truth tables) + flip-flops, arranged in a grid with programmable routing, plus hard blocks: block RAM, DSP slices (fast multiply-accumulate), and high-speed I/O. "Programming" it means loading a bitstream that configures all of these into your circuit.

**CPU vs FPGA, the decision table:**

| | CPU/microcontroller | FPGA |
|---|---|---|
| Execution | sequential instructions | everything parallel, every clock |
| Latency | µs–ms, jittery (interrupts, OS) | ns–µs, cycle-deterministic |
| Ease | write Python/C today | HDL + toolchain, days–weeks |
| Change a parameter | trivial | trivial *if* exposed as a register; otherwise re-synthesize (minutes–hours) |

**When the lab actually needs one:** (1) **feedback faster than ~µs** — a digital servo ([[PID Control]] in fabric) closing at MHz rates, e.g. cavity or intensity locks; (2) **pulse sequencing** with ns resolution and guaranteed timing — experiment control, gate sequences; (3) **counting and timestamping** photon clicks at high rates; (4) real-time DSP like demodulation or [[Direct Digital Synthesis]] with phase-coherent switching. If a Raspberry Pi or a lock-in can do it in software at your bandwidth, use that — FPGA development cost is real.

**HDL one-liner:** you describe hardware in Verilog/VHDL (or higher-level flows), and synthesis maps it to fabric; the mental shift is that every line describes a circuit that exists simultaneously, not a step that executes in order.

**Lab reality:** you rarely start from a blank chip. Platforms like ARTIQ/Sinara, STEMlab/Red Pitaya (ADC+DAC+FPGA with servo/lock-in images), and Moku ship with the hard part done — the FPGA question is usually "which platform," not "write HDL from scratch."

> [!question]- Your intensity lock needs 200 ns latency from photodiode to AOM correction. Why can't a fast CPU do this, and what does the FPGA change?
> A CPU's path (ADC driver → interrupt → OS scheduling → code → DAC) has µs-scale, *jittery* latency; worst-case spikes break the loop. An FPGA pipelines ADC→filter→DAC in fabric with a fixed, guaranteed cycle count — latency is deterministic and can be tens of ns.

# Connections

- [[Direct Digital Synthesis]] — the classic FPGA-adjacent block: phase accumulator lives naturally in fabric
- [[PID Control]] — the servo math FPGAs run when analog loops aren't flexible enough
- [[ADC and DAC Realities]] — the converters flanking the FPGA set the analog performance ceiling
- [[Digital Filters]] — IIR biquads and FIR MACs are what those DSP slices are for

---
Source: Lyons, *Understanding Digital Signal Processing*, Ch. 13 intro; Xilinx/AMD *FPGAs for Dummies* (free primer) for the fabric picture
