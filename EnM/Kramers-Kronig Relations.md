#EnM

**Causality alone forces the real and imaginary parts of any linear response function to determine each other** — a medium cannot absorb without dispersing, because a response that starts only *after* the stimulus makes χ(ω) analytic in the upper half plane, and analyticity ties Re to Im by a contour integral.

# Reference

For a causal, linear susceptibility $\chi(\omega) = \chi'(\omega) + i\chi''(\omega)$ vanishing at large ω:

$$
\chi'(\omega) = \frac{1}{\pi}\,\mathcal{P}\!\int_{-\infty}^{\infty} \frac{\chi''(\omega')}{\omega' - \omega}\,d\omega', \qquad
\chi''(\omega) = -\frac{1}{\pi}\,\mathcal{P}\!\int_{-\infty}^{\infty} \frac{\chi'(\omega')}{\omega' - \omega}\,d\omega'
$$

($\mathcal{P}$ = principal value; the pair is a Hilbert transform.) Derivation in one line: $\chi(t<0)=0$ ⇒ $\chi(\omega)$ analytic for $\mathrm{Im}\,\omega > 0$ ⇒ close the contour and pick up only the principal-value part.

**Physical content:**
- **Absorption ↔ dispersion, no divorce.** An absorption line at $\omega_0$ *necessarily* produces the dispersive n(ω) wiggle around it — normal dispersion on the wings, anomalous dispersion across the line. Measure one, compute the other (routinely done: absorption spectra → refractive index).
- Applies to *any* causal linear response: ε(ω), σ(ω), circuit impedances Z(ω), atomic susceptibility near resonance, S-parameters. A "flat amplitude, arbitrary phase" filter is unphysical.
- Sum rule spin-off: $\int_0^\infty \omega\,\chi''\,d\omega = \pi\omega_p^2/2$ — total absorption strength is fixed by electron density, you can only move it around.

Gotcha: the relations need the full spectrum; truncated data gives wrong Hilbert transforms at the edges — extend with physical asymptotics before transforming.

> [!question]- Could you build a medium with strong absorption at ω₀ but exactly constant refractive index everywhere?
> No. χ'' localized at ω₀ forces $\chi'(\omega) \propto \mathcal{P}\int \chi''/(\omega'-\omega)$ — a nonzero dispersive structure around ω₀. Causality itself forbids absorption without dispersion.

# Connections

- [[Contour Integration and Residues]] — the derivation is one contour argument; the principal value comes from skirting the pole
- [[Dispersion Relations]] — why anomalous dispersion always sits on top of an absorption line
- [[Dielectrics and Polarizability]] — ε(ω) of any real material obeys these; Lorentz model satisfies them exactly
- [[Fourier Transform]] — causality in time ↔ analyticity in frequency is a Fourier statement

---
Source: Jackson, *Classical Electrodynamics*, §7.10
