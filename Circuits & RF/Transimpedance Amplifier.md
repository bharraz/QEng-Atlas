#circuits #electronics

**A photodiode delivers a current and works best with no voltage across it. An op-amp with a feedback resistor $R_f$ holds its input at virtual ground and sends the photocurrent through $R_f$, so $V_\text{out} = -IR_f$ with zero voltage across the (capacitive) source; this transimpedance amplifier is the standard photodiode readout.**

# Reference

Gain = $R_f$ in V/A. **Larger $R_f$ improves SNR:** signal ∝ $R_f$, its Johnson noise ∝ $\sqrt{R_f}$ — take all the transimpedance the bandwidth budget allows, then voltage-amplify.

**The stability problem:** source capacitance $C_\text{in}$ (photodiode + input + cable) with $R_f$ puts a pole in the *feedback* path; noise gain rises +20 dB/dec until it hits the op-amp rolloff → ringing or oscillation. Fix with a feedback cap:

$$
C_f \approx \sqrt{\frac{C_\text{in}}{2\pi R_f\,\text{GBW}}}, \qquad f_{-3\text{dB}} \approx \sqrt{\frac{\text{GBW}}{2\pi R_f C_\text{in}}}
$$

- $R_f$ — feedback resistor (Ω), which *is* the gain in V/A
- $C_\text{in}$ — total capacitance at the summing node (F): photodiode, op-amp input, cable, and board strays in parallel
- $C_f$ — feedback capacitor (F), chosen to place a compensating zero
- GBW — op-amp gain–bandwidth product (Hz)

Both results are geometric means, which is the useful reading: bandwidth $\propto \sqrt{\mathrm{GBW}/R_f C_\text{in}}$ means doubling the transimpedance costs only $\sqrt{2}$ in bandwidth (so high-gain TIAs cost less bandwidth than they appear to), but it also means cutting $C_\text{in}$ — reverse bias, short cable — gains bandwidth on the same square-root footing as buying a faster op-amp.

**Picture:** the op-amp keeps the input node's level fixed by draining every arriving electron through $R_f$; the voltage it needs to do so is the output.

Numbers: 10 pF diode, 100 kΩ, 10 MHz GBW → $C_f \approx 1.3$ pF, BW ≈ 1.3 MHz. Sub-pF is real — board strays count as part of $C_f$.

**Noise-gain peaking:** even when stable, the amp's $e_n$ appears at the output multiplied by $1 + C_\text{in}/C_f$ at high frequency — a noise bump near the loop crossover that dominates the integrated noise in wideband measurements. Bigger $C_f$ trades bandwidth for a flatter floor.

Reverse-biasing the photodiode cuts $C_\text{in}$ severalfold → more bandwidth (cost: dark current).

> [!question]- Your photodiode TIA rings at ~1 MHz on every step. Which two fixes work, and which knob caused it?
> Add/increase $C_f$, or cut $C_\text{in}$ (reverse bias, shorter cable — cable capacitance counts). It appeared because $R_f$ or $C_\text{in}$ grew, dragging the feedback pole $1/2\pi R_f C_\text{in}$ down into the loop.

# Connections

- [[Photodiode Circuits]] — the source this amplifier exists for
- [[Op-Amp Golden Rules and Real Limits]] — GBW and $e_n$ set the bandwidth and the noise bump
- [[Stability and Phase Margin]] — the feedback-pole analysis in general form
- [[Shot Noise]] — the floor you're trying to reach with big $R_f$

---
Source: Horowitz & Hill, *The Art of Electronics* 3rd ed., §4.3 & §8.11
