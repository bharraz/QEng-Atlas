#quantum #AMO

**When two or more states have the same energy, any superposition of them is also a stationary state, so the Hamiltonian alone does not decide which basis the eigenstates are — something else does: a symmetry label, a small perturbation, or the measurement.** That indeterminacy is why degeneracies matter. A perturbation acts on a degenerate level at first order instead of second, it chooses the basis, and degeneracies are where Berry curvature, symmetry, and topology leave their marks. A generic one-parameter family of Hamiltonians has no degeneracies at all, so an exact degeneracy is itself evidence of structure.

# Reference

**Degenerate perturbation theory.** A level of $H_0$ with a $g$-fold degenerate subspace (projector $P$) and a perturbation $V$:

$$
\det\!\big(PVP - E^{(1)}\,\mathbb{1}_P\big) = 0
$$

- $P$ — projector onto the degenerate subspace ([[Projectors]])
- $PVP$ — the perturbation restricted to that subspace: a $g\times g$ matrix
- $E^{(1)}$ — first-order energy shifts: the eigenvalues of $PVP$

The correct zeroth-order states are the eigenvectors of $PVP$: the perturbation, not $H_0$, picks the basis. For a nondegenerate level the first-order shift is a diagonal element and states mix only by $V_{mn}/\Delta E$; for a degenerate level the mixing is of order one, however weak $V$ is ([[Time-Independent Perturbation Theory]]).

**Picture:** a ball in a perfectly round bowl has no preferred direction to roll; the slightest tilt chooses one, and the tilt's direction — not its size — decides which.

**Where degeneracies come from:**

| Origin | Mechanism | Lifted by | Example |
|---|---|---|---|
| a symmetry with a multi-dimensional irreducible representation | states in one irrep share an energy (Schur's lemma) | any perturbation that breaks the symmetry | the $2l+1$ states of angular momentum $l$ ([[Group Representations]]) |
| time reversal with half-integer spin | $\Theta^2 = -1$ forces Kramers pairs | only time-reversal-odd fields, such as a magnetic field | odd-electron atoms and ions; Kramers doublets in crystals ([[Parity and Time Reversal]]) |
| a hidden (dynamical) symmetry, larger than the geometric one | extra conserved quantities | perturbations that break the hidden symmetry | hydrogen's $n^2$ degeneracy (Runge–Lenz vector, $SO(4)$); the 3D isotropic oscillator ($SU(3)$) |
| tuning a parameter to a crossing | two levels from different symmetry sectors cross freely | any coupling between the sectors | level-crossing spectroscopy; magnetic-field crossings of Zeeman sublevels |
| many-body ground-state manifolds | states that no local operator distinguishes | only nonlocal operators; residual splitting falls as $e^{-L/\xi}$ | symmetry-broken ground states of a magnet; topological ground-state degeneracy ([[Topological Phases of Matter]]) |

**Crossing or avoided crossing.** Near a near-degeneracy, the two relevant levels obey a $2\times 2$ Hamiltonian:

$$
H = \epsilon\,\mathbb{1} + \vec d\cdot\vec\sigma, \qquad E_\pm = \epsilon \pm \lvert\vec d\rvert
$$

- $\epsilon$ — mean energy of the pair (J)
- $\vec d = (d_x, d_y, d_z)$ — half the splitting, as a vector (J)
- $\vec\sigma$ — Pauli matrices in the basis of the two levels

A degeneracy needs $\vec d = 0$: three conditions for a complex Hermitian $H$, and two if $H$ can be made real (time-reversal symmetry without spin makes $d_y = 0$). One tuning knob therefore produces an **avoided crossing** with minimum gap $2\lvert d\rvert$, not a crossing (von Neumann–Wigner). Levels cross when a symmetry forces the coupling to vanish, which is when they belong to different symmetry sectors. In a space of two parameters with real $H$, or three parameters with complex $H$, degeneracies are isolated points: conical intersections in molecules, Dirac points in graphene, Weyl points in 3D crystals.

**Why degeneracies matter:**
- **First-order sensitivity.** A degenerate manifold responds linearly to a field that couples its states, while a nondegenerate state of definite parity responds only quadratically. Highly excited Rydberg manifolds show a linear Stark effect for this reason ([[Stark Effect and Light Shifts]]).
- **The basis is set by the perturbation.** At zero magnetic field the $m$ sublevels have no preferred axis; stray fields pick one and states precess about it, which is why optical pumping and state preparation use a bias field to define the quantization axis ([[Zeeman Effect (Atlas)]]).
- **Protection.** If the noise operator acts identically on a set of states, those states form a degenerate subspace for the noise, and information stored there is not dephased: decoherence-free subspaces and clock-like encodings.
- **Geometric phases.** A degeneracy is a source of Berry curvature, like a monopole at the crossing point. Carrying a real eigenvector around a conical intersection reverses its sign, a geometric phase of $\pi$ ([[Berry Phase and Geometric Phases]]).
- **Topology.** Topological invariants of gapped bands can change only where a gap closes, which is a degeneracy; and topological order shows itself as a ground-state degeneracy that depends on the shape of space ([[Topology and Topological Invariants]]).
- **Leakage and spectators.** A drive resonant with one transition is also resonant with any transition degenerate with it — a reason for bias fields and anharmonicity ([[Leakage, Erasure, and Biased Noise]]).

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| number of lines a level splits into under a small field | dimension of the degenerate multiplet, and so the symmetry |
| shift linear or quadratic in an applied field | degenerate states of opposite parity are being mixed (linear), or a nondegenerate state is (quadratic) |
| minimum splitting as one parameter is scanned | twice the coupling between the two states |
| two levels crossing with no repulsion | they lie in different symmetry sectors, or the coupling is forbidden |
| ground-state splitting against system size | exponential decrease: a symmetry-broken or topological manifold; power law: a gapless system |

> [!question]- Why does hydrogen's $n = 2$ level show a linear Stark shift while an alkali atom's ground state shows only a quadratic one?
> In hydrogen, $2s$ and $2p$ are degenerate (the hidden $SO(4)$ symmetry of the Coulomb potential) and have opposite parity. The field operator $ezE$ is odd, so it couples them, and within the degenerate subspace $PVP$ has eigenvalues $\pm 3ea_0E$: first order. An alkali's $nS$ ground state is nondegenerate and has definite parity, so $\langle nS|z|nS\rangle = 0$ and the first-order shift vanishes, leaving $-\tfrac12\alpha E^2$. The core electrons break the Coulomb symmetry, splitting $nS$ from $nP$ (quantum defects), which is what removes the linear effect.

# Connections

- [[Time-Independent Perturbation Theory]] — the nondegenerate formulas that fail here
- [[Symmetry in Quantum Mechanics]] — symmetry as the usual reason for a degeneracy
- [[Group Representations]] — degenerate multiplets are irreducible representations
- [[Parity and Time Reversal]] — Kramers degeneracy and parity mixing
- [[Two-Level Systems]] — the avoided crossing in full
- [[Landau-Zener Transitions]] — sweeping through an avoided crossing
- [[Berry Phase and Geometric Phases]] — degeneracies as sources of curvature
- [[Topological Phases of Matter]] — gap closings and topological ground-state degeneracy
- [[Simultaneous Diagonalization]] — commuting operators that label degenerate states
- [[Reading Matrices and Hamiltonians]] — equal diagonal entries let any coupling act fully

---
Source: Sakurai & Napolitano, *Modern Quantum Mechanics*, §4.1–4.4 & §5.2; L. D. Landau & E. M. Lifshitz, *Quantum Mechanics*, 3rd ed., §79 (intersection of energy levels); J. von Neumann & E. Wigner, *Phys. Z.* 30, 467 (1929)
