#EnM

**Close a region with reflecting boundaries and the wave equation only admits discrete standing-wave solutions** — the boundary conditions quantize k, so the continuous spectrum collapses into a comb of resonant modes. A microwave cavity and an optical Fabry-Perot are the same physics at different λ.

# Reference

Rectangular conducting box $(a,b,d)$, from $E_\parallel = 0$ on the walls:

$$
\frac{\omega_{mnp}}{c} = \pi\sqrt{\left(\frac{m}{a}\right)^2 + \left(\frac{n}{b}\right)^2 + \left(\frac{p}{d}\right)^2}
$$

Each mode is an independent harmonic oscillator of the field — the starting point for field quantization.

**Mode density** grows fast: the number of modes below ω follows

$$
N(\omega) \approx \frac{V\omega^3}{3\pi^2 c^3} \;\Rightarrow\; \rho(\omega) = \frac{V\omega^2}{\pi^2 c^3}
$$

— the ω² density behind blackbody radiation and spontaneous emission rates. Cavities matter precisely because they *reshape* this density: on resonance a high-Q mode concentrates density of states (Purcell enhancement), off resonance it suppresses it.

**Q ties it to the real world:** finite wall/mirror loss gives each mode a linewidth $\Delta\omega = \omega/Q$ and ring-down time $\tau = Q/\omega$. Machined microwave cavities reach $Q\sim10^4$ (superconducting: $10^{10}$); optical cavities quote finesse, which is Q per free spectral range.

Practical gotcha: any conducting enclosure — a vacuum chamber, an electronics box — *is* a cavity, and its lowest modes (GHz-scale for ~10 cm boxes) can resonantly enhance interference or RF drive fields at specific frequencies.

> [!question]- Why does an atom in a small high-Q cavity emit faster on resonance and slower off resonance?
> Emission rate ∝ density of final photon states (Fermi's golden rule). The cavity piles the mode density into its resonances — enhanced ρ(ω) on resonance (Purcell), depleted between them.

# Connections

- [[Waveguides]] — a cavity is a guide with both ends closed; the third k quantizes
- [[Fabry-Perot Cavity]] — the optical two-mirror limit: FSR, finesse, the same comb
- [[Resonance and Q Factor]] — each mode is one entry in the universal resonator table
- [[Separation of Variables]] — how the mode problem actually gets solved; separation constants become the mode indices
- [[Field Quantization of Light]] — mode-by-mode, each cavity mode becomes a quantum harmonic oscillator

---
Source: Jackson, *Classical Electrodynamics*, §8.7
