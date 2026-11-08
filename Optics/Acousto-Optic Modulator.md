#optics

**An RF-driven crystal carries a traveling sound wave whose index ripple Bragg-diffracts the light — and because the grating moves, the diffracted beam is frequency-shifted by exactly $f_{RF}$.** The standard lab tool for fast intensity, frequency, and switching control.

# Reference

Bragg condition: $\sin\theta_B = \lambda/2\Lambda$ with $\Lambda = v_s/f_{RF}$ the acoustic wavelength (m), $v_s$ the acoustic velocity in the crystal (m/s, ~4.2 mm/µs in TeO₂ — the number that sets every timescale here) and $f_{RF}$ the drive frequency (Hz). Deflection angle $2\theta_B \propto \lambda f_{RF}/v_s$: linear in drive frequency, which is why a frequency sweep is also an angle sweep. Order $m$ exits at frequency $\omega + m\,\omega_{RF}$ — the $+1$ order absorbed a phonon, the $-1$ emitted one; sign is set by geometry (which side the acoustic wave comes from).

**Efficiency vs RF power:** diffraction efficiency $\propto \sin^2(\text{const}\cdot\sqrt{P_{RF}})$ — grows, saturates around 80–90%, then rolls over. Vary RF power for analog intensity control; the same curve is why "more RF" eventually makes it *worse*.

**Rise time = beam diameter ÷ sound speed.** The switch completes only when the acoustic front has crossed the beam:
$$
t_r \approx \frac{d}{v_s}
$$

- $t_r$ — switching rise time (s)
- $d$ — beam diameter inside the crystal (m)
- $v_s$ — speed of sound in the crystal (m/s)

Nothing about the RF matters — the limit is purely how long sound takes to cross the beam, so modulation bandwidth $\approx v_s/d$ and the *only* lever is the waist. Focus tighter for speed — but focusing tighter raises beam divergence $\theta \propto \lambda/w_0$, and once that exceeds the Bragg angular acceptance the efficiency collapses. Speed vs efficiency is *the* AOM tradeoff, and it is unavoidable.

**Picture:** light reflecting off a moving grating of sound: the diffracted beam is Doppler-shifted by the grating's motion, which comes out to exactly $f_{RF}$.

**Know which acoustic mode your device uses — the velocities differ by 7×.**

| Material and acoustic mode | $v_s$ | Rise time, 1 mm beam |
|---|---|---|
| Fused silica (the common modulator material) | 5.96 mm/µs | 170 ns (focus to 100 µm → 17 ns) |
| TeO₂ *longitudinal* along [001] | 4.2 mm/µs | 240 ns |
| TeO₂ *slow shear* (used in deflectors and AOTFs — acousto-optic tunable filters — for their large diffraction angles) | 0.62 mm/µs | 1.6 µs: same crystal as the row above |

**Aligning an AOM — the steps and why:**

1. **Size the beam in the crystal.** Smaller is faster ($t_r \approx d/v_s$), but a tight focus diverges beyond the Bragg angular acceptance and loses efficiency, so the waist is a compromise set by the switching speed needed.
2. **Find the Bragg angle.** With RF on, rotate the AOM about the axis parallel to the acoustic wavefronts while watching the first-order power: it peaks, at the expense of the zeroth order, when the input angle meets the Bragg condition.
3. **Set the RF power** at the top of the efficiency curve, not beyond it.
4. **Select the order** with an iris or a mirror edge once the orders have separated. They part by $\lambda f_{RF}/v_s$, of order 10 mrad, so a millimetre-sized beam needs around 10 cm of travel, or a lens, before they separate.

**Double pass (cat's-eye geometry):** place a lens one focal length after the AOM and a mirror one focal length after the lens.
- A change of diffraction angle — which is what changing $f_{RF}$ does — becomes a parallel shift after the lens, so the beam meets the mirror at normal incidence and retraces its path; on the second pass the AOM diffracts it back along the input beam whatever the frequency.
- Block the zeroth order before the mirror so that only the shifted light returns; it is shifted again on the way back, by $2f_{RF}$ in total.
- A quarter-wave plate in the return path, passed twice, rotates the polarization by 90°, so a polarizing beamsplitter before the AOM sends the returning beam out its other port ([[Waveplates]]).

The deflection cancels and the frequency shift doubles — now you can sweep $f_{RF}$ without steering the beam. Costs efficiency². What you watch: the double-passed power while sweeping $f_{RF}$; if the output beam moves during the sweep, the AOM is not at the lens's focal plane.

**Pointing changes with frequency:** deflection angle changes with $f_{RF}$ — the feature of a deflector, the bug of a single-pass frequency tuner (fiber-coupling downstream converts your frequency sweep into an amplitude sweep).

**Failure modes:**

| Failure | Mechanism | What you see |
|---|---|---|
| RF overdrive | efficiency rolls over past its optimum; dissipated power heats the crystal; above the rating the transducer is damaged | lower efficiency at higher power, thermal lensing, pointing drift |
| thermal transients from the duty cycle | switching changes the average RF power and so the crystal temperature | power and pointing drift for ms–s after the pulse sequence changes; keep the average RF power constant |
| light leaking when "off" | finite isolation of the RF switch, and scattered light | residual light on the atoms or ions; two AOMs in series, or a double pass, add extinction |
| wrong polarization | for anisotropic (shear-mode) devices the diffraction depends on polarization | low efficiency |
| clipping | crystal apertures are a few mm or less | diffraction rings and loss |
| RF mismatch | driver and transducer impedances differ, so power is reflected | lower efficiency; the amplifier heats |

> [!question]- Why is the diffracted light shifted by exactly the RF frequency?
> Three equivalent pictures: Doppler shift off a grating moving at $v_s$; photon absorbs/emits one phonon of energy $\hbar\omega_{RF}$; energy–momentum conservation $\mathbf{k}_{out} = \mathbf{k}_{in} \pm \mathbf{K}_{sound}$, which simultaneously fixes the Bragg angle.

# Connections

- [[Diffraction Gratings]] — same Bragg physics, but the grating is written by sound and moves
- [[Heterodyne Detection]] — the AOM shift provides the offset frequency for beat-note measurements
- [[Direct Digital Synthesis]] — the usual RF source: phase-continuous frequency hops become clean optical frequency hops
- [[Gaussian Beams]] — waist in the AOM sets both rise time and Bragg-acceptance efficiency
- [[Intensity Stabilization]] — the AOM as the actuator of a power servo
- [[Fiber Noise Cancellation]] — the AOM as frequency tag and phase actuator

---
Source: Saleh & Teich, *Fundamentals of Photonics*, Ch. 20 (acousto-optics)
