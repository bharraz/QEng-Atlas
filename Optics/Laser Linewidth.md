#optics

**Laser linewidth is phase diffusion: spontaneous emission kicks the phase randomly, and technical noise usually kicks it much harder** — the quantum floor is almost never what you see; current, acoustic, and temperature noise are.

# Reference

**Schawlow-Townes floor:** spontaneous photons entering the lasing mode with random phase give
$$
\Delta\nu_{ST} \approx \frac{\pi h \nu\, (\Delta\nu_c)^2}{P_{out}}
$$
$\Delta\nu_{ST}$ = fundamental FWHM linewidth (Hz); $h\nu$ = photon energy (J); $\Delta\nu_c$ = cold-cavity linewidth (Hz), the resonator's own bandwidth; $P_{out}$ = output power (W). Two proportionalities carry the design logic: linewidth falls as $1/P$ (each stimulated photon dilutes the random spontaneous one) and as $\Delta\nu_c^{\,2}$ — a *quadratic* payoff for a better cavity, since a narrower resonator both filters the noise and stores photons longer. Numerically this is sub-Hz for most lasers.

**Two convention traps on this formula.** The original Schawlow–Townes result is 4× larger than the form above; the modern version includes Lax's factor $\tfrac12$ (lasing, not below threshold) and is quoted as FWHM. And for semiconductor lasers the **Henry linewidth-enhancement factor** multiplies it by $(1 + \alpha^2)$ with $\alpha \approx 3$–6 — a factor of 10–37 — which is most of why diode linewidths are orders above the naive floor. Reality: free-running diodes sit at ~MHz (enhanced by the Henry $\alpha$ factor), ECDLs at ~100 kHz, and the gap to the floor is all *technical* noise. Narrowing = servo to a better reference (cavity via PDH), not a better gain medium.

**Linewidth ↔ coherence:**
$$
\tau_c \sim \frac{1}{\pi\Delta\nu}, \qquad \ell_c = c\,\tau_c
$$
1 MHz → ~100 m coherence length; 1 Hz → light that stays phase-coherent for a third of a second.

**Why you care:** the laser is the LO for your qubit — laser phase noise enters gate errors exactly like qubit dephasing; spectroscopic resolution and cavity-coupling stability are linewidth-limited too. A "1 Hz linewidth" claim means nothing without the timescale: slow drift vs fast phase noise are different beasts (the Allan-variance question).

**Measurement — beat note:** overlap two lasers on a fast photodiode; the RF beat at $\nu_1 - \nu_2$ carries the combined lineshape (identical lasers: measured width = 2× each, Lorentzian assumption). Only one laser? Delayed self-heterodyne: beat it against itself through a fiber longer than $\ell_c$, with an AOM offset so the beat isn't at DC.

> [!question]- Why does measuring a narrow laser require either a second laser or a long fiber?
> A photodiode sees only $|E|^2$ — absolute optical phase is invisible. You need an independent (or decorrelated) phase reference to beat against. The delay fiber works only if the delay exceeds $\tau_c$, so the two copies have forgotten each other; sub-kHz lasers need impractically long fiber, hence two-laser beats against a reference.

# Connections

- [[Heterodyne Detection]] — the beat-note measurement is exactly this
- [[Laser Fundamentals]] — gain clamping sets the stage; the surviving mode's purity is this note
- [[Pound-Drever-Hall Locking]] — how you actually narrow a laser: servo the phase to a cavity
- [[Allan Variance]] — the right language for "linewidth" across timescales
- [[Power Spectral Density]] — frequency-noise PSD is the complete description; linewidth is one number squeezed out of it

---
Source: Siegman, *Lasers*, Ch. 12 (fundamental line broadening); Henry α-factor lore
