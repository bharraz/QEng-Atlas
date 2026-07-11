#optics

**The TEM$_{00}$ Gaussian is the ground state of a complete mode family** — Hermite-Gaussians in rectangular symmetry, Laguerre-Gaussians in cylindrical — all sharing $w(z)$ and $R(z)$ but carrying extra transverse structure and extra Gouy phase.

# Reference

**Hermite-Gaussian TEM$_{mn}$:** transverse profile $H_m(\sqrt{2}x/w)\,H_n(\sqrt{2}y/w)\,e^{-r^2/w^2}$ — $m$ and $n$ count the dark nodal lines along $x$ and $y$. What a misaligned cavity or clipped beam couples into first is TEM$_{10}$ (the two-lobed "misalignment mode").

**Laguerre-Gaussian LG$_{pl}$:** ring structure ($p$ radial nodes) with helical phase $e^{il\phi}$ — carries orbital angular momentum $l\hbar$ per photon; $l \ne 0$ modes have a phase singularity (dark core) on axis.

**Gouy phase scales with mode order:**
$$
\psi_{mn}(z) = (m+n+1)\arctan(z/z_R)
$$

so in a cavity, transverse modes are **not** degenerate with the fundamental:
$$
\nu_{qmn} = \mathrm{FSR}\left[ q + (m+n+1)\frac{\arccos(\pm\sqrt{g_1 g_2})}{\pi} \right]
$$

**Practical:** transverse mode splitting is a feature — scan a cavity and the little peaks between TEM$_{00}$ resonances diagnose your mode matching (each higher-order peak is power you failed to couple). Degenerate geometries (confocal: splitting = FSR/2, modes overlap in pairs) hide this information.

> [!question]- You scan a cavity and see a strong peak at ~1/3 of an FSR after the main one. What is it telling you?
> That's a low-order transverse mode (its offset is $(m+n)\arccos\sqrt{g_1g_2}/\pi$ of an FSR) — your input beam is mismatched or misaligned, and the peak height over the TEM$_{00}$ height estimates the coupling error. Fix alignment first (TEM$_{10}$/TEM$_{01}$), then waist size (TEM$_{20}$-family).

# Connections

- [[Gaussian Beams]] — the $m=n=0$ member; all modes share its $w(z)$, $R(z)$, $z_R$
- [[Hermite Polynomials]] — same functions as QHO eigenstates; paraxial optics is a 2D oscillator
- [[Optical Cavity Stability]] — $g_1g_2$ sets the transverse mode spacing via the Gouy phase
- [[Mode Matching]] — mismatch decomposes into higher-order modes; the cavity scan shows the coefficients
- [[Fabry-Perot Cavity]] — where the mode spectrum is actually observed

---
Source: Siegman, *Lasers*, Ch. 16–17, 19
