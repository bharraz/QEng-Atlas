#circuits #electronics

**A DDS is a phase accumulator that adds a tuning word every clock, a sine lookup table, and a DAC — frequency is just "how fast the phase wraps," set digitally to sub-Hz precision.**

# Reference

$$
f_\text{out} = \frac{\text{FTW}}{2^N}\,f_\text{clk}, \qquad \Delta f = \frac{f_\text{clk}}{2^N}
$$

A 32-bit accumulator at 1 GHz: 0.23 Hz steps; 48-bit parts reach µHz. Frequency, phase, and amplitude all numerically programmable — which is why every AOM driver and ion-addressing synth is a DDS.

**Phase-continuous switching:** changing the FTW changes the *slope* of the phase, not its value — no glitch, no jump (or program a deliberate phase offset). An analog oscillator can't do this.

**The dirt:**
- **Images** at $k f_\text{clk} \pm f_\text{out}$ under a sinc envelope — reconstruction filter mandatory; keep $f_\text{out} \lesssim 0.4\,f_\text{clk}$
- **Spurs** from phase-word truncation and DAC nonlinearity, −50 to −80 dBc, scattered *non-harmonically* — and they move as you tune, so a spur can sit in your linewidth at one setting and vanish at the next
- Output phase noise inherits the clock's (improved by $20\log(f_\text{clk}/f_\text{out})$, but a dirty clock means a dirty DDS)

> [!question]- Why can a DDS hop frequencies mid-pulse-sequence with no phase discontinuity — and when is that exactly what you don't want?
> The accumulator never resets: phase is continuous by construction, frequency is its slope. But if the experiment needs *phase-coherent* returns to a frequency (as though the old tone had kept running), continuity isn't coherence — you need parallel phase registers or synchronized resets.

# Connections

- [[Phase-Locked Loops]] — the analog synthesis alternative, and the hybrid DDS-in-PLL
- [[ADC and DAC Realities]] — DAC images, sinc rolloff, and spur mechanisms quantified
- [[Sampling and Aliasing]] — the image frequencies are aliasing run in reverse
- [[Acousto-Optic Modulator]] — the standard load on a lab DDS channel
- [[What an FPGA Is]] — where the accumulator lives in home-built rigs

---
Source: Horowitz & Hill, *The Art of Electronics* 3rd ed., §13.13
