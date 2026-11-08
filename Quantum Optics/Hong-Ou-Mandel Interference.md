#quantum-optics

**Send one photon into each port of a 50/50 beamsplitter: if the photons are indistinguishable, they always exit together — the both-transmit and both-reflect amplitudes cancel exactly, and coincidence counts drop to zero.** The HOM dip is two-photon interference with no classical analogue (amplitudes never interfere below 50% classically), and it is the primitive under photonic quantum computing, Bell-state measurement, and every "are these two photons identical?" question.

# Reference

**The mechanism** — pure amplitude bookkeeping from the [[Beamsplitter Transformation]]. Input $|1,1\rangle$; the two paths to a coincidence (both transmitted, both reflected) acquire amplitudes $tt$ and $rr = (i/\sqrt2)(i/\sqrt2) = -1/2$ vs $+1/2$:

$$|1,1\rangle \;\longrightarrow\; \frac{|2,0\rangle - |0,2\rangle}{\sqrt{2}}, \qquad P_{\text{coincidence}} = 0.$$

Photons **bunch** — bosonic statistics made visible in a single event. The cancellation requires the two two-photon amplitudes to be *indistinguishable in every degree of freedom*: any which-path tag (arrival time, frequency, polarization, spatial mode) restores coincidences. Hence the **HOM dip**: scan the relative delay τ and coincidences trace

$$P_{cc}(\tau) = \tfrac12\left[1 - V\, e^{-\tau^2/\tau_c^2}\right] \;(\text{Gaussian wavepackets}),$$

with width = the photon **coherence time** (not the detector resolution — sub-fs delays resolved with ns detectors, which made HOM a precision tool from day one) and visibility $V$ = the overlap of the single-photon wavepackets:

$$V = |\langle \psi_1 | \psi_2 \rangle|^2.$$

**Picture:** two identical photons arriving together at a beamsplitter: the two ways of leaving by different ports cancel, so they leave by the same port.

**That last equation is why HOM matters as a measurement: the dip visibility is a direct meter of photon indistinguishability.** No spectrometer measures this — two sources can have identical spectra yet distinguishable (mixed) wavepackets. Raw visibility > 50% also certifies nonclassical light (classical fields cap at 1/2).

**Where it matters:**

- **Source qualification.** "HOM visibility" is *the* headline spec for single-photon sources ([[Quantum Dots|quantum-dot]] sources: >98% for consecutive photons; the hard version is photons from *separate* emitters, where spectral wander between sources caps V). Also diagnoses purity of heralded SPDC photons.
- **Bell-state measurement = HOM.** Photonic teleportation, entanglement swapping, and quantum repeaters all hinge on projecting two photons onto Bell states, implemented as HOM interference + coincidence pattern (the singlet is the *only* Bell state producing coincidences at the two outputs — antisymmetric under exchange, so it "fermionizes"). No indistinguishability → no repeater network: HOM visibility between independent, remote sources is the metric that gates the entire quantum-network program. The same two-photon interference between "early/late" modes underlies memory-photon entanglement heralding (DLCZ).
- **Linear-optical QC.** KLM and boson sampling are HOM at scale: multiphoton interference in an interferometer, with the computational hardness living entirely in the bosonic exchange amplitudes (permanents). Every photonic-QC fidelity budget starts from pairwise HOM visibilities.
- **Beyond photons:** HOM observed with atoms, phonons, plasmons; electron (fermionic) HOM *anti*-bunches — the exchange-statistics litmus test.

> [!question]- Two photons pass the HOM test with V ≈ 1 against each other. A third source's photons have identical spectra but reach only V ≈ 0.5 against them. What's the diagnosis?
> Spectral *purity*, not spectral shape. V is the overlap of quantum states, and a photon can be mixed over frequency: its emission frequency may wander shot to shot (spectral diffusion in a solid-state emitter), or entanglement with the partner photon may leave a heralded SPDC photon mixed. The averaged spectrum looks identical while each wavepacket differs. Against a pure reference, $V = \langle\psi|\rho|\psi\rangle$: V ≈ 0.5 puts half the photon's weight outside the reference mode. Fixes: lifetime-limited emission ([[Purcell Effect]]), spectral filtering, or a stabilized emitter environment.

# Connections

- [[Beamsplitter Transformation]] — the two-line calculation behind the dip
- [[Photon Statistics and g2]] — the single-source counterpart: g² certifies "one photon," HOM certifies "identical photons"
- [[Quantum Dots]] — the sources whose headline number this is
- [[Purcell Effect]] — how emitters are made lifetime-limited, hence indistinguishable
- [[Quantum Teleportation]] — Bell-state measurement is HOM + coincidence logic
- [[Ion-Cavity Coupling]] — ion–photon interfaces whose photons are interfered to entangle ions in separate traps
- [[Interference]] — one-photon interference for contrast: amplitudes of *one* quantum vs *two*
- [[Remote Entanglement and Quantum Networks]] — the network links built on two-photon interference

---
Source: Hong, Ou & Mandel, *Phys. Rev. Lett.* 59, 2044 (1987); Bouchard et al., "Two-photon interference: the Hong-Ou-Mandel effect," *Rep. Prog. Phys.* 84, 012402 (2021)
