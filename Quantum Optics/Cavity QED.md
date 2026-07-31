#quantum-optics

**One atom, one cavity mode, three rates: coherent coupling $g$ racing against cavity decay $\kappa$ and atomic emission $\Gamma$.** Win the race ($g \gg \kappa, \Gamma$) and a single quantum coherently swaps between atom and photon before either channel loses it.

# Reference

Single-photon coupling from the zero-point field: $g = d\,\mathcal{E}_0/\hbar = d\sqrt{\omega/2\hbar\varepsilon_0 V}$. $g$ = vacuum Rabi frequency (rad/s) — the rate at which one atom and one photon exchange excitation; $d$ = transition dipole matrix element (C·m); $\mathcal{E}_0 = \sqrt{\hbar\omega/2\varepsilon_0 V}$ = zero-point field amplitude of the mode (V/m); $V$ = mode volume (m³); $\kappa$ = cavity field decay rate (s⁻¹), the photon leaking out through the mirrors, $\kappa = \pi\,\mathrm{FSR}/\mathcal{F}$; $\Gamma$ = atomic spontaneous emission rate (s⁻¹), excitation lost into free space.

**Small $V$ is the whole game**: $g \propto d/\sqrt{V}$ while $\kappa$ is fixed by the mirrors and $\Gamma$ by the atom, so the only lever that improves both $g/\kappa$ and $g/\Gamma$ at once is shrinking the mode.

**Strong coupling** $g \gg \kappa, \Gamma$: the [[Jaynes-Cummings Model]] doublets are resolvable and the **vacuum Rabi splitting $2g$** appears in the transmission spectrum of the coupled system — a single atom visibly splits the cavity line.

**Cooperativity** is the figure of merit that survives even when strong coupling fails:

$$
C = \frac{g^2}{\kappa\Gamma}
$$

$C$ = cooperativity (dimensionless): coherent coupling rate squared over the product of the two loss rates — read as "coherent exchange events per loss event," so it is the ratio of good to bad physics independent of whether oscillation is resolvable. Conventions differ by factors of 2 and 4 — check before comparing papers. $C \gg 1$ with $g < \kappa$ is the **bad-cavity regime**: no coherent oscillation, but the atom still emits preferentially into the cavity mode with probability $\sim 2C/(2C+1)$ — that's the [[Purcell Effect]], and it's enough for photon collection and atom-photon entanglement.

**Platforms:** neutral atoms in high-finesse Fabry-Perots (strong coupling standard), trapped ions in fiber cavities (hard — dielectric mirrors near the trap distort the RF pseudopotential, so ion systems usually settle for large-$C$ Purcell operation), and circuit QED as the microwave analog where $g/\omega$ gets absurdly large.

> [!question]- Your ion-cavity system has $g/2\pi = 1$ MHz, $\kappa/2\pi = 10$ MHz, $\Gamma/2\pi = 0.1$ MHz. Useless?
> No — $C = g^2/\kappa\Gamma = 1$, so roughly two-thirds of emission goes into the cavity mode. No vacuum Rabi splitting (need $g\gg\kappa$), but perfectly good for deterministic photon extraction into a fiber.

# Connections

- [[Jaynes-Cummings Model]] — the Hamiltonian underneath; cavity QED is JC plus dissipation
- [[Purcell Effect]] — what large $C$ buys you when $g \gg \kappa$ is out of reach
- [[Fabry-Perot Cavity]] — where $\kappa$ comes from: FSR/finesse
- [[Spontaneous Emission and Linewidth]] — the $\Gamma$ leg of the triangle
- [[Input-Output Theory]] — how the intracavity dynamics reach your detector

---
Source: Gerry & Knight, *Introductory Quantum Optics*, Ch. 10
