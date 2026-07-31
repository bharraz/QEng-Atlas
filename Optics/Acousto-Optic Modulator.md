#optics

**An RF-driven crystal carries a traveling sound wave whose index ripple Bragg-diffracts the light — and because the grating moves, the diffracted beam is frequency-shifted by exactly $f_{RF}$.** The lab workhorse for fast intensity, frequency, and switching control.

# Reference

Bragg condition: $\sin\theta_B = \lambda/2\Lambda$ with $\Lambda = v_s/f_{RF}$ the acoustic wavelength (m), $v_s$ the acoustic velocity in the crystal (m/s, ~4.2 mm/µs in TeO₂ — the number that sets every timescale here) and $f_{RF}$ the drive frequency (Hz). Deflection angle $2\theta_B \propto \lambda f_{RF}/v_s$: linear in drive frequency, which is why a frequency sweep is also an angle sweep. Order $m$ exits at frequency $\omega + m\,\omega_{RF}$ — the $+1$ order absorbed a phonon, the $-1$ emitted one; sign is set by geometry (which side the acoustic wave comes from).

**Efficiency vs RF power:** diffraction efficiency $\propto \sin^2(\text{const}\cdot\sqrt{P_{RF}})$ — grows, saturates around 80–90%, then rolls over. Vary RF power for analog intensity control; the same curve is why "more RF" eventually makes it *worse*.

**Rise time = beam diameter ÷ sound speed.** The switch completes only when the acoustic front has crossed the beam:
$$
t_r \approx \frac{d}{v_s}
$$

$t_r$ = switching rise time (s); $d$ = beam diameter inside the crystal (m). Nothing about the RF matters — the limit is purely how long sound takes to cross the beam, so modulation bandwidth $\approx v_s/d$ and the *only* lever is the waist. This is also why the tradeoff is unavoidable: focusing tighter raises beam divergence $\theta \propto \lambda/w_0$, and once that exceeds the Bragg angular acceptance the efficiency collapses.
**Know which acoustic mode your device uses — the velocities differ by 7×.** Fused silica (the common modulator material): $v_s = 5.96$ mm/µs. TeO₂ *longitudinal* along [001]: 4.2 mm/µs. TeO₂ *slow shear* (used in deflectors and AOTFs for their large diffraction angles): 0.62 mm/µs — same crystal, and a 1 mm beam then gives 1.6 µs rather than 240 ns. Worked: 1 mm beam in fused silica → 170 ns; focus to 100 µm → 17 ns. Focus tighter for speed — but too tight and the beam's angular spread exceeds the Bragg acceptance and efficiency dies. Speed vs efficiency is *the* AOM tradeoff.

**Double-pass trick:** retroreflect through the AOM with a cat's eye (lens + mirror at focus). The deflection cancels, the frequency shift doubles — now you can sweep $f_{RF}$ without steering the beam. Costs efficiency².

Gotcha: deflection angle changes with $f_{RF}$ — the feature of a deflector, the bug of a single-pass frequency tuner (fiber-coupling downstream converts your frequency sweep into an amplitude sweep).

> [!question]- Why is the diffracted light shifted by exactly the RF frequency?
> Three equivalent pictures: Doppler shift off a grating moving at $v_s$; photon absorbs/emits one phonon of energy $\hbar\omega_{RF}$; energy–momentum conservation $\mathbf{k}_{out} = \mathbf{k}_{in} \pm \mathbf{K}_{sound}$, which simultaneously fixes the Bragg angle.

# Connections

- [[Diffraction Gratings]] — same Bragg physics, but the grating is written by sound and moves
- [[Heterodyne Detection]] — the AOM shift provides the offset frequency for beat-note measurements
- [[Direct Digital Synthesis]] — the usual RF source: phase-continuous frequency hops become clean optical frequency hops
- [[Gaussian Beams]] — waist in the AOM sets both rise time and Bragg-acceptance efficiency

---
Source: Saleh & Teich, *Fundamentals of Photonics*, Ch. 20 (acousto-optics)
