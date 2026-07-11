#quantum-optics

**Send one photon into each port of a 50/50 beamsplitter: if the photons are indistinguishable, they always exit together — the both-transmit and both-reflect amplitudes cancel exactly, and coincidence counts drop to zero.** The HOM dip is two-photon interference with no classical analogue (amplitudes never interfere below 50% classically), and it is the primitive under photonic quantum computing, Bell-state measurement, and every "are these two photons identical?" question.

# Reference

**The mechanism** — pure amplitude bookkeeping from the [[Beamsplitter Transformation]]. Input $|1,1\rangle$; the two paths to a coincidence (both transmitted, both reflected) acquire amplitudes $tt$ and $rr = (i/\sqrt2)(i/\sqrt2) = -1/2$ vs $+1/2$:

$$|1,1\rangle \;\longrightarrow\; \frac{|2,0\rangle - |0,2\rangle}{\sqrt{2}}, \qquad P_{\text{coincidence}} = 0.$$

Photons **bunch** — bosonic statistics made visible in a single event. The cancellation requires the two two-photon amplitudes to be *indistinguishable in every degree of freedom*: any which-path tag (arrival time, frequency, polarization, spatial mode) restores coincidences. Hence the **HOM dip**: scan the relative delay τ and coincidences trace

$$P_{cc}(\tau) = \tfrac12\left[1 - V\, e^{-\tau^2/\tau_c^2}\right] \;(\text{Gaussian wavepackets}),$$

with width = the photon **coherence time** (not the detector resolution — sub-fs delays resolved with ns detectors, which made HOM a precision tool from day one) and visibility $V$ = the overlap of the single-photon wavepackets:

$$V = |\langle \psi_1 | \psi_2 \rangle|^2.$$

**That last equation is why HOM matters beyond being a pretty effect: the dip visibility is a direct meter of photon indistinguishability.** No spectrometer measures this — two sources can have identical spectra yet distinguishable (mixed) wavepackets. Raw visibility > 50% also certifies nonclassical light (classical fields cap at 1/2).

**Where it is load-bearing:**

- **Source qualification.** "HOM visibility" is *the* headline spec for single-photon sources ([[Quantum Dots|quantum-dot]] sources: >98% for consecutive photons; the hard version is photons from *separate* emitters, where spectral wander between sources caps V). Also diagnoses purity of heralded SPDC photons.
- **Bell-state measurement = HOM.** Photonic teleportation, entanglement swapping, and quantum repeaters all hinge on projecting two photons onto Bell states, implemented as HOM interference + coincidence pattern (the singlet is the *only* Bell state producing coincidences at the two outputs — antisymmetric under exchange, so it "fermionizes"). No indistinguishability → no repeater network: HOM visibility between independent, remote sources is the metric that gates the whole quantum-network program. The same two-photon interference between "early/late" modes underlies memory-photon entanglement heralding (DLCZ).
- **Linear-optical QC.** KLM and boson sampling are HOM at scale: multiphoton interference in an interferometer, with the computational hardness living entirely in the bosonic exchange amplitudes (permanents). Every photonic-QC fidelity budget starts from pairwise HOM visibilities.
- **Beyond photons:** HOM observed with atoms, phonons, plasmons; electron (fermionic) HOM *anti*-bunches — the exchange-statistics litmus test.

> [!question]- Two photons pass the HOM test with V ≈ 1 against each other. A third source's photons each show identical spectra to the first two but only V ≈ 0.5 against them. What's the diagnosis?
> Spectral *purity*, not spectral shape. V is the overlap of quantum states, and a photon can occupy a mixed state over frequency — e.g. its emission time/frequency fluctuates shot-to-shot (spectral diffusion in a solid-state emitter, or SPDC heralded without tight filtering, where entanglement with the partner photon mixes the heralded state). The averaged spectrum looks identical; each individual wavepacket differs. V ≈ 0.5 against a pure reference is the fingerprint of a maximally impure single mode. Fixes attack the purity: lifetime-limited emission (Purcell enhancement — see [[Purcell Effect]]), spectral filtering at the cost of rate, or active stabilization of the emitter's environment.

# Connections

- [[Beamsplitter Transformation]] — the two-line calculation behind the dip
- [[Photon Statistics and g2]] — the single-source counterpart: g² certifies "one photon," HOM certifies "identical photons"
- [[Quantum Dots]] — the sources whose headline number this is
- [[Purcell Effect]] — how emitters are made lifetime-limited, hence indistinguishable
- [[Quantum Teleportation]] — Bell-state measurement is HOM + coincidence logic
- [[Interference]] — one-photon interference for contrast: amplitudes of *one* quantum vs *two*

---
Source: Hong, Ou & Mandel, *Phys. Rev. Lett.* 59, 2044 (1987); Bouchard et al., "Two-photon interference: the Hong-Ou-Mandel effect," *Rep. Prog. Phys.* 84, 012402 (2021)
