#quantum-optics #AMO

**Put $N$ identical atoms within one wavelength of each other and let them decay: the emitted photon cannot tell which atom it came from, so the emission amplitudes add rather than the intensities, and the ensemble radiates as one large dipole — up to $N$ times faster than a single atom (superradiance) — or, for the opposite phase pattern, hardly at all (subradiance).**

# Reference

**Two atoms first.** Two two-level atoms sharing one excitation, separated by much less than a wavelength:

$$
|S\rangle = \frac{|eg\rangle + |ge\rangle}{\sqrt 2} \;\text{ decays at } 2\Gamma, \qquad |A\rangle = \frac{|eg\rangle - |ge\rangle}{\sqrt 2} \;\text{ decays at } 0
$$

- $\Gamma$ — single-atom [[Spontaneous Emission and Linewidth|spontaneous decay rate]] (s⁻¹)
- $|S\rangle, |A\rangle$ — symmetric and antisymmetric single-excitation states (the [[Bell States]] $\Psi^\pm$)

In $|S\rangle$ the two atomic dipoles oscillate in phase and their fields add; in $|A\rangle$ they cancel, so the state is dark. At finite separation the two rates are $\Gamma \pm \Gamma_{12}$, where the cross-decay rate $\Gamma_{12}$ tends to $\Gamma$ as the atoms approach and oscillates and falls off once they are wavelengths apart.

**Bright turns into dark under a local energy shift.** If one atom's transition is shifted by $\hbar\delta$ relative to the other's (a field gradient, a light shift on one atom), the relative phase of $|eg\rangle$ and $|ge\rangle$ advances at rate $\delta$, and $|S\rangle$ becomes $|A\rangle$ after a time $\pi/\delta$. The same mechanism prepares subradiant states on purpose and destroys them by accident.

**Bright and dark, side by side** (atoms much closer than a wavelength):

| | Superradiant (bright) | Subradiant (dark) |
|---|---|---|
| Dipole phases | add | cancel |
| Two-atom state | $\lvert S\rangle = \Psi^+$ | $\lvert A\rangle = \Psi^-$ |
| Decay rate with one excitation | $N\Gamma$ (the symmetric $W$ state) | down to 0 |
| Reached from the ground state by a uniform drive | yes, at $\sqrt N$ times the single-atom Rabi frequency | no: a uniform drive has no matrix element to it |
| How it is prepared | uniform excitation; or spontaneously, as a fully inverted sample decays | a local energy shift between atoms, as above; or decay from a state that is not fully symmetric |
| How it is seen | fast emission; from an inverted sample, a burst with peak $\propto N^2$ | a slow tail in the fluorescence after the drive is switched off |
| What limits it | dephasing between the atoms | dephasing between the atoms, and any loss each atom suffers independently |

**$N$ atoms — Dicke states.** Treat each atom as a spin-½ and add them ([[Angular Momentum in QM]]). The collective states $|J, M\rangle$ decay one step at a time, $|J, M\rangle \to |J, M-1\rangle$, at

$$
\Gamma_M = \Gamma\,(J + M)(J - M + 1)
$$

- $J$ — total collective spin: $N/2$ for fully symmetric states, smaller otherwise
- $M$ — collective $z$ projection: $M + N/2$ is the number of excitations

| State | Excitations | Emission rate | Compared to $N$ independent atoms |
|---|---|---|---|
| all excited, $M = J$ | $N$ | $N\Gamma$ | the same — no correlations yet |
| half excited, $M \approx 0$ | $N/2$ | $\approx N^2\Gamma/4$ | $\sim N/2$ times faster: the superradiant burst |
| one excitation, symmetric ($W$ state), $M = -J + 1$ | 1 | $N\Gamma$ | $N$ times faster |
| non-symmetric states ($J < N/2$) | any | reduced, down to 0 | subradiant |
| bottom of a non-symmetric ladder, $M = -J$ with $J < N/2$ | $N/2 - J$ | 0 | dark: these excitations are trapped |

Starting fully inverted, the ensemble therefore emits a delayed burst: no dipole correlation exists at first, so emission starts at the independent rate, correlations build up through the shared field, and the peak intensity $\propto N^2\Gamma$ arrives after a delay $\sim \ln N/(N\Gamma)$ and lasts $\sim 1/(N\Gamma)$. The initial phase is seeded by vacuum fluctuations, so the delay jitters from shot to shot.

**Picture:** a single dipole radiates power $\propto d^2$; $N$ dipoles locked in phase radiate as one dipole of size $Nd$, with power $\propto N^2 d^2$ — the same reason $N$ [[Antennas]] driven in phase beam $N^2$ times the power of one. Dipoles whose phases sum to zero radiate like no antenna at all.

**Extended samples** (larger than a wavelength): emissions add in phase only along particular directions, so superradiance becomes directional (pencil-shaped samples emit along their long axis), and the enhancement is set by the number of atoms per $\lambda^2$ of cross-section — the optical depth — rather than by $N$ itself.

**Subradiance beyond two atoms.** The emitted field couples only to the sum of the atomic dipoles, weighted by the phase of each emission direction at each atom; a state whose weighted sum vanishes for every direction cannot radiate. In a sample much smaller than a wavelength this holds exactly for the bottom of each $J < N/2$ ladder (table above), so an ensemble that does not start fully symmetric keeps part of its excitation after the burst.

| System | Subradiant behaviour | Why |
|---|---|---|
| two atoms at separation $r$ | $\lvert A\rangle$ decays at $\Gamma - \Gamma_{12}(r)$, below $\Gamma$ wherever $\Gamma_{12} > 0$ | partial cancellation once $r$ is comparable to $\lambda$ |
| disordered cold cloud | a slow tail in the fluorescence decay, longer for higher optical depth | many weakly radiating collective modes |
| ordered 1D array, spacing below $\lambda/2$ | the darkest modes lose energy only at the chain's ends, at a rate falling as $N^{-3}$ | their phase varies along the chain faster than any free-space photon's can (wavevector beyond $\omega/c$), so, like [[Evanescent Waves]], they are bound to the chain |

**What a fluorescence-decay measurement tells you:** drive the sample weakly, switch the drive off, and record the emitted light against time. A drop faster than $\Gamma$ is the superradiant part; a tail slower than $\Gamma$ is the subradiant part. In an optically thick cloud, radiation trapping (light scattered many times before escaping) also slows the decay, so a slow tail alone does not prove subradiance; the two depend differently on the drive's detuning and on the optical depth, which separates them.

**Uses and limits:** subradiant states keep an excitation longer than a single atom's lifetime, which makes them candidate memories, but the same symmetry that hides them from emission hides them from absorption, so they are hard to address. Ordered arrays with sub-wavelength spacing ([[Optical Tweezers]]) support collective subradiant modes.

**In a cavity, the shared field is the mode.** Atoms coupled to the same cavity mode share its field however far apart they are, so collective emission into the mode needs no sub-wavelength spacing; what matters is the mode's phase at each atom. $N$ atoms at antinodes of the same sign couple to the mode with $g\sqrt N$ in the symmetric state ([[Cavity QED]]); move one to an antinode of the opposite sign and the antisymmetric state becomes the bright one. With two trapped ions prepared in either Bell state by an entangling gate, emission into the cavity was enhanced in one state and suppressed in the other ([[Ion-Cavity Coupling]]), while their emission into free space stayed nearly independent.

**Trapped ions in free space:** ions sit several micrometres apart, many optical wavelengths, so $\Gamma_{12}/\Gamma$ is around a percent; this separation-dependent change was measured with two ions in a [[Paul Traps|Paul trap]]. Collective decay is therefore a small correction, which is why ion qubits can be modelled as decaying independently.

**Same name, different physics:**

| Effect | What it is |
|---|---|
| Dicke superradiance | collective spontaneous emission; a transient |
| superradiant phase transition | an equilibrium transition of the Dicke model ($N$ atoms coupled to one cavity mode) above a critical collective coupling $g\sqrt N$; seen as self-organization of a BEC in a cavity ([[Cavity QED]]) |
| superradiant laser | lasing with the phase coherence stored in the atoms rather than the cavity (bad-cavity regime), so the linewidth can be narrower than the cavity's |
| amplified spontaneous emission | single-pass gain in an inverted medium; also bright and directional, but with no collective atomic coherence |

> [!question]- One excitation shared symmetrically among $N$ atoms decays $N$ times faster than one atom. Does a fully inverted sample also start decaying $N$ times faster?
> No. The fully inverted state $|J, J\rangle$ emits at $N\Gamma$ in total, exactly like $N$ independent atoms, because there is no phase correlation between the atomic dipoles yet. The speed-up and the $N^2$ intensity appear only as the decay passes through $M \approx 0$, where the correlations have built up — which is why superradiance from an inverted sample is a delayed burst.

# Connections

- [[Spontaneous Emission and Linewidth]] — the single-atom rate $\Gamma$ that collective emission multiplies or suppresses
- [[Dipole Radiation]] — why in-phase dipoles add in amplitude
- [[Angular Momentum in QM]] — the Dicke states are collective $|J, M\rangle$ states
- [[Bell States]] — the two-atom bright and dark states are $\Psi^\pm$
- [[Purcell Effect]] — the other way to speed up emission: change the vacuum instead of the emitters
- [[Cavity QED]] — collective coupling $g\sqrt N$, and the Dicke-model phase transition
- [[Ion-Cavity Coupling]] — two ions as bright and dark states of one cavity mode
- [[Evanescent Waves]] — why array modes with wavevector beyond $\omega/c$ cannot radiate
- [[Standard Quantum Limit and Spin Squeezing]] — the same collective spin, used for metrology
- [[Fermi's Golden Rule]] — the decay rate as coupling² × density of final states, here with a collective coupling

---
Source: R. H. Dicke, *Phys. Rev.* 93, 99 (1954); M. Gross & S. Haroche, "Superradiance: an essay on the theory of collective spontaneous emission," *Phys. Rep.* 93, 301 (1982); R. G. DeVoe & R. G. Brewer, *Phys. Rev. Lett.* 76, 2049 (1996); W. Guerin, M. O. Araújo & R. Kaiser, *Phys. Rev. Lett.* 116, 083601 (2016); A. Asenjo-Garcia et al., *Phys. Rev. X* 7, 031024 (2017); B. Casabone et al., *Phys. Rev. Lett.* 114, 023602 (2015)
