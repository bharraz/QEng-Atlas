#optics

**Counter-propagating pump and probe only talk to the same atoms when those atoms have zero velocity along the beam — so saturation dips appear at the true transition frequencies, Doppler-free, inside the Doppler profile.** The standard absolute frequency reference for laser locking.

# Reference

**The scheme:** strong pump and weak probe, counter-propagating through a vapor cell, both from the same laser at $\nu$. An atom with velocity $v$ sees pump at $\nu(1 - v/c)$ and probe at $\nu(1 + v/c)$ — they address the *same* atoms only at $v = 0$, exactly when $\nu = \nu_0$. There the pump saturates the transition (burns a hole in the $v=0$ velocity class) and the probe absorption dips: a **Lamb dip** of near-natural width sitting in the ~GHz Doppler valley (hundreds of MHz to ~GHz wide at room temperature).

**Picture:** the pump burns a hole in one velocity class; the counter-propagating probe sees that hole only for atoms both beams address, the ones at rest along the beam.

**Crossover resonances — a common source of misidentified lines.** Two transitions sharing a ground state, separated by less than the Doppler width, produce an *extra* dip exactly midway between them: at $\nu = (\nu_1+\nu_2)/2$ a velocity class exists for which the pump drives one transition and the probe the other. Crossovers are often *stronger* than the real lines (more atoms in the moving class, plus optical-pumping enhancement) — locking to a crossover unknowingly is the most common mistake; sometimes it's the deliberate choice because it's the biggest feature.

**Locking practice:** dither the laser (or use a modulation-free variant) and lock-in detect to get a dispersion-shaped error signal from each dip; pump/probe from one beam via a thick beamsplitter or double-pass. Linewidth floor: natural width ⊕ power broadening ($\sqrt{1+s}$) ⊕ residual angle between beams ⊕ transit time.

**Failure modes:**

| Failure | Mechanism | What you see |
|---|---|---|
| locked to a crossover | (above) | a lock midway between two transitions |
| power broadening | a pump that strongly saturates the transition widens the dip | wide, shallow features and a less steep error signal |
| stray magnetic field | Zeeman shifts split and move the lines | a lock point that moves with lab fields; shield the cell or apply a known bias field |
| cell temperature drift | vapour density varies steeply with temperature | signal size drifts |
| beams not exactly counter-propagating | residual Doppler shift from the angle between them | broadened dips |
| dither reaching the experiment | modulating the laser frequency for the lock modulates all of its light | sidebands on the light sent to the experiment; modulate only the spectroscopy beam (with an AOM or EOM) or use a modulation-free scheme |
| etalons on the cell windows | reflections between window surfaces | ripple in the baseline under the dips |

> [!question]- Why does a crossover resonance appear midway between two transitions, and why is it often the biggest dip?
> At the midpoint frequency there's a velocity class Doppler-shifted so the pump is resonant with transition 1 while the counter-propagating probe is resonant with transition 2 (and vice versa for $-v$). Since both transitions share a ground state, the pump depletes (or optically pumps away) the population the probe needs. Two velocity classes contribute instead of one, and hyperfine pumping piles population changes on top — hence dips that dwarf the true lines.

# Connections

- [[Laser Fundamentals]] — what's being locked; the sat-abs cell is the wavelength anchor
- [[Doppler Cooling]] — same Doppler-shift physics, used as a force instead of a filter
- [[Lock-In Detection]] — how the dips become an error signal
- [[Optical Bloch Equations]] — saturation parameter and power broadening set the dip depth and width
- [[Laser Sources]] — the lasers this locks, and how they mode-hop

---
Source: Demtröder, *Laser Spectroscopy* Vol. 2, Ch. 2 (nonlinear/saturation spectroscopy)
