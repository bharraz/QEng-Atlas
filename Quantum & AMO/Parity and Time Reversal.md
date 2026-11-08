#quantum #AMO

**Reflect every coordinate through the origin and an isolated atom's Hamiltonian is unchanged, so each of its nondegenerate eigenstates is either even or odd under the reflection.** That one label makes many integrals vanish before anyone computes them: it decides which transitions an electric dipole can drive, and why an atom in a definite-parity state has no permanent electric dipole. Time reversal, the other discrete symmetry, runs motion backwards; it supplies no quantum number of its own, but it forces degeneracies (Kramers pairs), allows Hamiltonians to be written as real matrices, and is what magnetic fields break.

# Reference

**Parity.** The operator $\Pi$ sends $\vec r \to -\vec r$:

$$
\Pi\,\psi(\vec r) = \psi(-\vec r), \qquad \Pi^2 = \mathbb{1}, \qquad \Pi\,\vec r\,\Pi = -\vec r, \qquad \Pi\,\vec L\,\Pi = \vec L
$$

- $\Pi$ — parity operator: eigenvalues $\pm 1$, since $\Pi^2 = \mathbb{1}$
- $\vec r$, $\vec p$ — polar vectors: change sign
- $\vec L$, $\vec S$ — axial vectors: unchanged

**The vanishing rule.** If $\Pi|a\rangle = \pi_a|a\rangle$, $\Pi|b\rangle = \pi_b|b\rangle$, and $\Pi O \Pi = \pi_O\,O$, then

$$
\langle a|O|b\rangle = \pi_a\,\pi_O\,\pi_b\,\langle a|O|b\rangle
$$

- $\pi_a, \pi_b$ — parities of the two states ($\pm 1$)
- $\pi_O$ — parity of the operator ($\pm 1$)

so the matrix element vanishes unless $\pi_a\pi_O\pi_b = +1$. It is the simplest case of the group-theory rule that an integral vanishes unless its integrand contains the symmetric representation ([[Symmetry in Quantum Mechanics]]).

**Picture:** an integral of an odd function over a symmetric range is zero — every contribution at $\vec r$ is cancelled by its mirror at $-\vec r$.

| Object | Parity | Consequence |
|---|---|---|
| orbital with angular momentum $l$ | $(-1)^l$ | $s, d$ even; $p, f$ odd |
| harmonic-oscillator state $\lvert n\rangle$ | $(-1)^n$ | $\hat x$ connects $n \leftrightarrow n\pm1$; $\hat x^2$ connects $n \leftrightarrow n, n\pm2$ |
| $\vec r$, $\vec p$, electric dipole $\vec d$, field $\vec E$ | odd | electric-dipole (E1) transitions change parity |
| $\vec L$, $\vec S$, magnetic dipole $\vec\mu$, field $\vec B$ | even | magnetic-dipole (M1) transitions keep parity |
| electric quadrupole $r_ir_j$ | even | E2 transitions keep parity ([[Selection Rules]]) |

**Parity arguments in common use:**
- **No permanent dipole.** A nondegenerate state of definite parity has $\langle\psi|\vec d|\psi\rangle = 0$. A linear response to an electric field needs degenerate states of opposite parity: hydrogen's $n = 2$ level, Rydberg manifolds, and rotational levels of polar molecules, whose "permanent" dipole exists in the molecule's frame but averages to zero in a rotational eigenstate until a field mixes neighbouring levels ([[Degeneracy and Level Crossings]]).
- **The atom–light coupling is off-diagonal.** For an E1 transition $|g\rangle$ and $|e\rangle$ have opposite parity, so $\langle g|\vec d|g\rangle = \langle e|\vec d|e\rangle = 0$ and $\vec d = \vec d_{eg}\,\sigma_+ + \text{h.c.}$: the drive appears as a $\sigma_x$-type coupling with no $\sigma_z$ part ([[Dipole Approximation]]).
- **Second-order shifts only.** A state of definite parity has no first-order shift from an odd perturbation; the quadratic Stark effect and anharmonic shifts from odd potentials such as $x^3$ start at second order.
- **Bound states in one dimension.** One-dimensional bound states are nondegenerate, so in a symmetric potential each has definite parity; the ground state is even and nodeless, and parities alternate going up the ladder ([[Quantum Harmonic Oscillator]]).
- **Parametric driving changes $n$ by two.** A modulated trap frequency couples through $\hat x^2$, which is even, so it connects $n$ to $n \pm 2$: squeezing and parametric heating ([[Squeezed States]]).

**Parity as an internal $\mathbb{Z}_2$ symmetry.** Quantum-information papers use "parity" for operators that also square to one but are not spatial reflection:
- **Qubit parity** $Z_1Z_2\cdots Z_N$ is conserved by $X_iX_j$ couplings such as the Mølmer–Sørensen interaction, which therefore connects $|00\rangle \leftrightarrow |11\rangle$ and $|01\rangle \leftrightarrow |10\rangle$ but never even to odd. The parity oscillation of a GHZ state measures the coherence between its two components ([[State and Gate Fidelity]]).
- **Photon-number parity** $(-1)^{a^\dagger a}$: cat states have definite parity, and the Wigner function at the origin equals $(2/\pi)\langle(-1)^{a^\dagger a}\rangle$ ([[Wigner Function]]).

The algebra is the same as for spatial parity: two sectors, and couplings that preserve or flip the label.

**What breaks parity:** an applied electric field, which mixes opposite-parity states; crystal sites without an inversion centre (the $C_{3v}$ site of an NV centre has none); and the weak interaction, which produces atomic parity violation many orders of magnitude below other effects.

**Time reversal.** The operator $\Theta$ reverses momenta and spins and leaves positions alone. It is **antiunitary**: $\Theta = UK$ with $K$ complex conjugation, so $\Theta\,i\,\Theta^{-1} = -i$.

| Case | $\Theta$ | $\Theta^2$ | Consequence |
|---|---|---|---|
| spinless particle | $K$ in the position basis | $+1$ | eigenfunctions can be chosen real; Berry phases are $0$ or $\pi$; avoided crossings need only two conditions |
| spin $\tfrac12$ | $-i\sigma_y K$ | $-1$ | every level is at least doubly degenerate (Kramers) |
| total spin half-integer | | $-1$ | Kramers pairs survive any electric field, strain, or crystal field; only a magnetic field splits them |
| total spin integer | | $+1$ | no Kramers protection: degeneracies come only from spatial symmetry |

Because $\Theta$ is antiunitary, it does not label states with a conserved eigenvalue the way parity does; its consequences come as constraints on degeneracies, phases, and matrix elements. Magnetic fields, currents, rotation, and circularly polarized light (through vector light shifts) are odd under $\Theta$. Non-reciprocal optics such as Faraday isolators therefore require a magnetic field ([[Optical Isolators]]), and the edge states of a time-reversal-invariant topological insulator come in Kramers pairs that non-magnetic disorder cannot split ([[Topological Phases of Matter]]).

**Integer spin with spatial symmetry, the NV example.** The NV$^-$ ground state has spin 1, so $\Theta^2 = +1$. Its $m_s = \pm1$ levels are degenerate at zero magnetic field because of the $C_{3v}$ site symmetry, not because of Kramers' theorem, and transverse strain or electric field splits them even at zero field — the $E(S_x^2 - S_y^2)$ term of the NV Hamiltonian ([[NV Centers (atlas)]]).

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| a linear Stark shift | degenerate states of opposite parity are being mixed |
| a transition that is strong (ns lifetime) or forbidden (ms–s lifetime) | whether E1 is allowed: parity changes, or it does not |
| a doublet that survives any electric field or strain and splits only in $B$ | a Kramers doublet: half-integer total spin |
| a doublet that splits under strain at zero field | integer spin; the degeneracy came from spatial symmetry |
| parity oscillation of a GHZ or Bell state against analysis phase | the coherence between the components that the qubit-parity operator connects |

> [!question]- In a rotating frame the atom–light coupling is written $\frac{\hbar\Omega}{2}(\sigma_+ + \sigma_-)$ with no $\sigma_z$ term. What guarantees there is no diagonal part?
> Parity. For an E1 transition, $|g\rangle$ and $|e\rangle$ have opposite parity and the dipole operator is odd. A diagonal element such as $\langle g|\vec d|g\rangle$ has parity product $\pi_g\pi_d\pi_g = -1$ and vanishes; the off-diagonal $\langle e|\vec d|g\rangle$ has $\pi_e\pi_d\pi_g = +1$ and survives. Diagonal energy shifts do appear, but at second order, from off-resonant couplings to other levels: the light shift.

# Connections

- [[Symmetry in Quantum Mechanics]] — the general rule of which parity is the two-element case
- [[Selection Rules]] — parity and angular momentum applied to photons
- [[Degeneracy and Level Crossings]] — Kramers degeneracy and linear Stark shifts
- [[Dipole Approximation]] — the odd operator that drives E1 transitions
- [[Stark Effect and Light Shifts]] — quadratic shifts of definite-parity states
- [[Quantum Harmonic Oscillator]] — alternating parity of the ladder
- [[Wigner Function]] — photon-number parity as a phase-space value
- [[Molmer-Sorensen Gate]] — qubit parity conserved by $XX$ couplings
- [[Topological Phases of Matter]] — time reversal with $\Theta^2 = -1$ protecting edge states
- [[NV Centers (atlas)]] — integer spin with only spatial protection

---
Source: Sakurai & Napolitano, *Modern Quantum Mechanics*, §4.2 (parity) & §4.4 (time reversal); Cohen-Tannoudji, Diu & Laloë, *Quantum Mechanics*, Complement F_II (parity)
