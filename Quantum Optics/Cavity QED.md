#quantum-optics

**Put one atom between two mirrors and it can emit its photon into the one optical mode the mirrors support, where the photon can be reabsorbed before it leaks out; three rates then decide what happens — the rate $g$ at which atom and photon exchange the excitation, the rate $\kappa$ at which the photon leaks through the mirrors, and the rate $\Gamma$ at which the atom emits into every other direction.** If $g$ exceeds both losses, a single quantum swaps coherently between atom and photon; if not, the cooperativity $C$ still decides how much of the emission the cavity collects.

# Reference

The single-photon coupling comes from the zero-point field of the mode:

$$
g = \frac{d\,\mathcal{E}_0}{\hbar} = d\sqrt{\frac{\omega}{2\hbar\varepsilon_0 V}}
$$

- $g$ — vacuum Rabi frequency (rad/s): rate one atom and one photon exchange excitation
- $d$ — transition dipole matrix element (C·m)
- $\mathcal{E}_0 = \sqrt{\hbar\omega/2\varepsilon_0 V}$ — zero-point field amplitude of the mode (V/m)
- $V$ — mode volume (m³): standing-wave Gaussian mode, $\pi w_0^2L/4$ (waist $w_0$, length $L$)
- $\kappa$ — cavity field decay rate (s⁻¹): photon leaking through the mirrors, $\kappa = \pi\,\mathrm{FSR}/\mathcal{F}$
- $\Gamma$ — atomic spontaneous emission rate (s⁻¹): excitation lost into free space
- $\mathcal{F}$, FSR — the cavity's finesse and free spectral range ([[Fabry-Perot Cavity]])

**Mode volume sets the coupling**: $g \propto d/\sqrt{V}$ while $\kappa$ is fixed by the mirrors and $\Gamma$ by the atom, so the only lever that improves both $g/\kappa$ and $g/\Gamma$ at once is shrinking the mode.

**Strong coupling** $g \gg \kappa, \Gamma$: the [[Jaynes-Cummings Model (Atlas)]] doublets are resolvable and the **vacuum Rabi splitting $2g$** appears in the transmission spectrum of the coupled system — a single atom visibly splits the cavity line.

**Cooperativity** is the figure of merit that applies even when strong coupling fails:

$$
C = \frac{g^2}{\kappa\Gamma}
$$

- $C$ — cooperativity (dimensionless): coupling rate squared over the product of loss rates

It counts coherent exchange events per loss event, so it compares coupling to loss whether or not the oscillation is resolvable. Conventions differ by factors of 2 and 4 — check before comparing papers.

**What sets $C$:** $g^2 \propto 1/(w_0^2 L)$ and $\kappa \propto 1/(L\mathcal F)$, so $C \propto \mathcal{F}/w_0^2$, independent of the cavity length. A long cavity with high finesse and a small waist reaches the same $C$ as a short one, with lower $g$ and lower $\kappa$ — and therefore longer photons (duration $\gtrsim 1/\kappa$).

**Picture:** the mirrors send the light past the atom many times (a number proportional to $\mathcal F$), and on each pass the atom absorbs a fraction $\sim \lambda^2/w_0^2$ of the mode; $C$ is roughly the product.

**Bad-cavity regime** ($C \gg 1$ with $g < \kappa$): no coherent oscillation, but the atom still emits preferentially into the cavity mode, with probability $\sim 2C/(2C+1)$ — the [[Purcell Effect]]. That is enough for photon collection and atom–photon entanglement.

**Platforms:**

| Platform | Typical regime | Limiting factor |
|---|---|---|
| neutral atoms in high-finesse Fabry–Pérot cavities | strong coupling is standard | atom delivery and localization in the mode |
| trapped ions, in macroscopic or fiber-tip cavities | large-$C$ Purcell operation rather than strong coupling ([[Ion-Cavity Coupling]]) | dielectric mirrors near the trap distort the RF pseudopotential |
| circuit QED, the microwave analog ([[Superconducting Qubits]]) | strong coupling, with $g/\omega$ very large | material losses in the resonator and qubit |

> [!question]- An emitter–cavity system has $g/2\pi = 1$ MHz, $\kappa/2\pi = 10$ MHz, $\Gamma/2\pi = 0.1$ MHz. Is it useful?
> Yes. $C = g^2/\kappa\Gamma = 1$, so roughly two-thirds of the emission goes into the cavity mode. There is no vacuum Rabi splitting (that needs $g\gg\kappa$), but the system works for deterministic photon extraction into a fiber.

# Connections

- [[Jaynes-Cummings Model (Atlas)]] — the Hamiltonian underneath; cavity QED is JC plus dissipation
- [[Purcell Effect]] — what large $C$ gives when $g \gg \kappa$ is out of reach
- [[Fabry-Perot Cavity]] — where $\kappa$ comes from: FSR/finesse
- [[Gaussian Beams]] — the waist $w_0$ that sets the mode volume
- [[Spontaneous Emission and Linewidth]] — the $\Gamma$ leg of the triangle
- [[Input-Output Theory]] — how the intracavity dynamics reach your detector
- [[Ion-Cavity Coupling]] — trapped ions in cavities: why they work at $C \sim 1$, and how the photon is generated
- [[Superradiance and Subradiance]] — collective coupling $g\sqrt N$ and collective emission
- [[Circuit QED]] — the same physics with superconducting circuits and microwave photons

---
Source: Gerry & Knight, *Introductory Quantum Optics*, Ch. 10; H. Tanji-Suzuki et al., "Interaction between atomic ensembles and optical resonators: classical description," *Adv. At. Mol. Opt. Phys.* 60, 201 (2011)
