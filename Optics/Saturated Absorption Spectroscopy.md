#optics

**Counter-propagating pump and probe only talk to the same atoms when those atoms have zero velocity along the beam — so saturation dips appear at the true transition frequencies, Doppler-free, inside the Doppler profile.** The standard absolute frequency reference for laser locking.

# Reference

**The scheme:** strong pump and weak probe, counter-propagating through a vapor cell, both from the same laser at $\nu$. An atom with velocity $v$ sees pump at $\nu(1 - v/c)$ and probe at $\nu(1 + v/c)$ — they address the *same* atoms only at $v = 0$, exactly when $\nu = \nu_0$. There the pump saturates the transition (burns a hole in the $v=0$ velocity class) and the probe absorption dips: a **Lamb dip** of near-natural width sitting in the ~GHz Doppler valley (hundreds of MHz to ~GHz wide at room temperature).

**Crossover resonances — the gotcha.** Two transitions sharing a ground state, separated by less than the Doppler width, produce an *extra* dip exactly midway between them: at $\nu = (\nu_1+\nu_2)/2$ a velocity class exists for which the pump drives one transition and the probe the other. Crossovers are often *stronger* than the real lines (more atoms in the moving class, plus optical-pumping enhancement) — locking to a crossover unknowingly is the classic mistake; sometimes it's the deliberate choice because it's the biggest feature.

**Locking practice:** dither the laser (or use a modulation-free variant) and lock-in detect to get a dispersion-shaped error signal from each dip; pump/probe from one beam via a thick beamsplitter or double-pass. Linewidth floor: natural width ⊕ power broadening ($\sqrt{1+s}$) ⊕ residual angle between beams ⊕ transit time.

> [!question]- Why does a crossover resonance appear midway between two transitions, and why is it often the biggest dip?
> At the midpoint frequency there's a velocity class Doppler-shifted so the pump is resonant with transition 1 while the counter-propagating probe is resonant with transition 2 (and vice versa for $-v$). Since both transitions share a ground state, the pump depletes (or optically pumps away) the population the probe needs. Two velocity classes contribute instead of one, and hyperfine pumping piles population changes on top — hence dips that dwarf the true lines.

# Connections

- [[Laser Fundamentals]] — what's being locked; the sat-abs cell is the wavelength anchor
- [[Doppler Cooling]] — same Doppler-shift physics, used as a force instead of a filter
- [[Lock-In Detection]] — how the dips become an error signal
- [[Optical Bloch Equations]] — saturation parameter and power broadening set the dip depth and width

---
Source: Demtröder, *Laser Spectroscopy* Vol. 2, Ch. 2 (nonlinear/saturation spectroscopy)
