#solid-state #quantum

**Two gapped Hamiltonians — two band insulators, or two many-body systems at zero temperature — belong to the same phase if one can be deformed into the other without closing the energy gap; topological phases are distinct phases that no local order parameter tells apart, separated only by an integer computed from the ground-state wavefunctions or by the pattern of their entanglement.** Their signatures are quantized responses, boundary states that cannot be removed, and ground-state degeneracies that depend on the shape of space. All are robust because changing them requires closing the gap or breaking a protecting symmetry.

# Reference

**The setup.** A conventional (Landau) phase is identified by a local order parameter and the symmetry it breaks: a magnetization, a density wave. A topological phase breaks no symmetry and has no local order parameter; it differs from a trivial insulator in a global property of its ground state ([[Topology and Topological Invariants]]).

**Picture:** two knots in a closed loop of rope — no inspection of a short piece tells them apart, and one becomes the other only if the rope is cut.

**The three families:**

| Family | What distinguishes it | Invariant | At the boundary | Protected by | Examples |
|---|---|---|---|---|---|
| Chern insulators and the integer quantum Hall effect | winding of the occupied Bloch states over the Brillouin zone | Chern number $C \in \mathbb{Z}$ | $C$ one-way (chiral) edge modes | the gap alone | quantum Hall systems; Haldane-model bands in cold atoms and photonics |
| symmetry-protected topological (SPT) phases | a winding or entanglement pattern that exists only while a symmetry holds | $\mathbb{Z}$ or $\mathbb{Z}_2$ (SSH winding, Kane–Mele $\mathbb{Z}_2$); string order in interacting chains | zero-energy end states; Kramers pairs of edge modes; fractional edge spins | a symmetry: chiral, time reversal with $\Theta^2=-1$, particle–hole, or a spin rotation | SSH chain; topological insulators; Kitaev chain (Majorana end modes); Haldane spin-1 chain ([[Spin Chains and Magnons]]) |
| intrinsic topological order | long-range entanglement | ground-state degeneracy on a torus; anyon types; topological entanglement entropy | gapless or gapped edges; anyons in the bulk | nothing beyond the gap: robust to all weak local perturbations | toric code; fractional quantum Hall states; $\mathbb{Z}_2$ spin liquids |

**The SSH chain, the smallest example.** A 1D chain with two sites per cell, $A$ and $B$, and alternating hopping amplitudes:

$$
H = \sum_n \left(v\, c^\dagger_{n,B}c_{n,A} + w\, c^\dagger_{n+1,A}c_{n,B} + \text{h.c.}\right), \qquad \vec d(k) = (v + w\cos k,\; w\sin k,\; 0)
$$

- $v$ — hopping within a unit cell (J)
- $w$ — hopping between neighbouring cells (J)
- $\vec d(k)$ — the Bloch Hamiltonian's vector: $H(k) = \vec d(k)\cdot\vec\sigma$

As $k$ crosses the zone, $\vec d$ traces a circle of radius $w$ centred at $(v, 0)$. It encloses the origin when $\lvert w\rvert > \lvert v\rvert$ (winding 1, topological) and not when $\lvert w\rvert < \lvert v\rvert$ (winding 0, trivial). The gap closes at $\lvert v\rvert = \lvert w\rvert$, the only place the winding can change. An open chain in the topological phase has one zero-energy state localized at each end, decaying into the bulk over a length set by $\ln\lvert w/v\rvert$.

**Bulk–boundary correspondence.** Where two regions with different invariants meet, the invariant must change across the interface; it can change only where the gap closes, so states inside the bulk gap must appear at the interface. The number of boundary modes is fixed by the difference of the invariants. A sample's edge with the vacuum is such an interface, with the vacuum as the trivial side.

**Chern number and the quantized Hall response.** For a filled band, the transverse conductance is

$$
\sigma_{xy} = C\,\frac{e^2}{h}
$$

- $\sigma_{xy}$ — Hall conductance (S)
- $C$ — sum of Chern numbers of the filled bands (integer)
- $e^2/h$ — conductance quantum, about $1/(25.8\ \mathrm{k\Omega})$

The integer is set by Berry curvature integrated over the zone (TKNN), which is why the plateaus are flat to parts per billion independent of sample details ([[Electronic Transport]], [[Berry Phase and Geometric Phases]]).

**Topological order and quantum codes.** The toric code, $H = -\sum_v A_v - \sum_p B_p$ with commuting star and plaquette stabilizers, has these properties:
- Four degenerate ground states on a torus, $2^{2g}$ on a surface of genus $g$, distinguished only by operators along non-contractible loops.
- Excitations that are anyons: moving an $e$ particle around an $m$ particle multiplies the state by $-1$.
- An entanglement entropy of a region of boundary length $L$ equal to $\alpha L - \gamma$, with $\gamma = \ln 2$ the topological entanglement entropy.

The surface code is a planar version, and its logical operators are the non-contractible strings ([[Surface Code]], [[Stabilizer Formalism]], [[Quantum Entropies and Information]]).

**What "protected" covers, and what it does not:**
- Protected against local perturbations weaker than the gap, and, for SPT phases, ones that respect the symmetry.
- Not protected against perturbations comparable to the gap; symmetry-breaking terms for SPT phases (a magnetic field opens the edge of a time-reversal-protected topological insulator); temperature, which creates excitations at a rate $\propto e^{-\Delta/k_BT}$; or finite size, which splits degenerate edge or ground states by roughly $e^{-L/\xi}$.
- A two-dimensional topological quantum memory such as the toric code is not stable at nonzero temperature on its own: thermally created anyons wander and destroy the stored information, which is why active error correction is still needed ([[Quantum Error Correction (Atlas)]]).

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| Hall conductance plateau at $C\,e^2/h$ | the Chern number of the filled bands |
| displacement per cycle of a slow periodic modulation (Thouless pump) | a Chern number: an integer number of unit cells per cycle |
| Zak phase (0 or $\pi$) from interferometry in a 1D lattice | SSH winding; the value depends on the choice of unit cell, so the difference between two phases is the robust quantity |
| zero-energy states at the ends of an open chain | nontrivial winding, if they survive disorder that respects the symmetry but move under disorder that breaks it |
| string order parameter from site-resolved snapshots | hidden SPT order in spin chains ([[Analog Quantum Simulation]]) |
| topological entanglement entropy from Rényi entropies of regions | $\gamma \neq 0$: intrinsic topological order |
| interferometric phase from moving one excitation around another | anyon statistics |
| ground-state or edge-state splitting against system size | exponential decrease: a topological degeneracy |

> [!question]- Why do the end states of an SSH chain sit at exactly zero energy, and what perturbation moves them?
> The Hamiltonian only hops between $A$ and $B$ sites, so $\sigma_z H\sigma_z = -H$ (chiral symmetry): every state at energy $E$ has a partner at $-E$ obtained by flipping the sign on the $B$ sites. An isolated end state lives on a single sublattice, so it is its own partner and must sit at $E = 0$. Disorder in the hoppings preserves chiral symmetry and leaves it there. An on-site energy difference between $A$ and $B$ (a $d_z\sigma_z$ term) breaks chiral symmetry and moves the two end states away from zero in opposite directions. In a finite chain the two end states also overlap and split by about $e^{-L/\xi}$.

# Connections

- [[Topology and Topological Invariants]] — winding numbers, Chern numbers, and homotopy
- [[Berry Phase and Geometric Phases]] — the curvature whose integral is the Chern number
- [[Bloch's Theorem and Band Structure]] — the band structures being classified
- [[Degeneracy and Level Crossings]] — gap closings and topological ground-state degeneracy
- [[Parity and Time Reversal]] — Kramers pairs protecting topological-insulator edge states
- [[Spin Chains and Magnons]] — the Haldane gap and SPT order in spin chains
- [[Surface Code]] — topological order used as a quantum code
- [[Analog Quantum Simulation]] — measuring topological invariants with snapshots and pumps
- [[Electronic Transport]] — the quantum Hall effect in transport measurements
- [[Phase Transitions and Critical Phenomena]] — the Landau framework that topological phases fall outside

---
Source: J. K. Asbóth, L. Oroszlány & A. Pályi, *A Short Course on Topological Insulators* (Springer, 2016); M. Z. Hasan & C. L. Kane, *Rev. Mod. Phys.* 82, 3045 (2010); X.-G. Wen, *Rev. Mod. Phys.* 89, 041004 (2017); A. Yu. Kitaev, *Ann. Phys.* 303, 2 (2003)
