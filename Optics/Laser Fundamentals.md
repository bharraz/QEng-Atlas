#optics

**A laser is gain inside a cavity, with saturation as the thermostat** — pump inverts a medium, the cavity feeds photons back through it, and stimulated emission (coherent copying) wins once round-trip gain exceeds round-trip loss. Above threshold, saturation clamps the gain at exactly the loss, and every extra pump photon becomes output.

# Reference

**Threshold:** lasing starts when small-signal round-trip gain = round-trip loss (mirror transmission + internal loss):
$$
R_1 R_2\, e^{2gL} = 1
$$

**Gain clamping:** above threshold, intensity grows until the saturated gain $g = g_0/(1 + I/I_{sat})$ is pinned at the loss. Consequence: output power rises linearly with pump above threshold (slope efficiency), and the intracavity intensity is what does the clamping.

**Longitudinal modes:** the cavity only supports frequencies with integer round-trip phase — a comb spaced by the FSR $\Delta\nu = c/2L$. The gain bandwidth typically covers many; which ones lase is a fight between gain, loss, and spatial hole burning.

**Single-mode selection:** make the mode spacing exceed the gain bandwidth (short cavity), or add frequency-dependent loss — intracavity etalon, or grating feedback (Littrow ECDL) that both narrows and tunes. One-liner rule: one element to select, one to tune, and they must track together or you mode-hop.

Practical diode-laser corollary: the free-running diode is a bad cavity with huge gain bandwidth — feedback from *anywhere* (fiber tip, filter, cuvette) becomes an uninvited external cavity. Hence isolators.

> [!question]- Why is the gain pinned exactly at the loss above threshold, and what does that buy you?
> If gain exceeded loss, intensity would grow, saturating the gain back down; below loss, intensity decays and gain recovers — a stable fixed point at gain = loss. This clamping is why laser output is spectrally pure and why pump fluctuations map to amplitude, not gain, dynamics.

# Connections

- [[Fabry-Perot Cavity]] — the resonator: FSR, finesse, and mode structure all come from here
- [[Laser Linewidth]] — what limits the purity of the one surviving mode
- [[Diffraction Gratings]] — Littrow feedback, the standard ECDL single-mode selector
- [[Optical Isolators]] — protection from parasitic external cavities
- [[Spontaneous Emission and Linewidth]] — the seed photons, and the noise floor of the whole process

---
Source: Siegman, *Lasers*, Ch. 11–13 (laser oscillation and mirrors/regeneration)
