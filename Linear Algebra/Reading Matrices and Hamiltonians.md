#linear-algebra #quantum #math

**A matrix is a machine that takes a vector in and gives a vector out, and every entry has a job: column $n$ is what comes out when basis vector $n$ goes in, so the entry $A_{mn}$ is the amount of output $m$ produced per unit of input $n$.** Read a Hamiltonian this way and its entries become physics. Diagonal entries set how fast each basis state's phase turns; off-diagonal entries set how fast amplitude flows between two states; and comparing a coupling with the energy difference it bridges decides whether the states swap, shift, or follow.

# Reference

**Reading entries.** In a basis $\{|n\rangle\}$:

$$
A|n\rangle = \sum_m A_{mn}\,|m\rangle, \qquad A_{mn} = \langle m|A|n\rangle = \langle \text{output}|A|\text{input}\rangle
$$

- $\lvert n\rangle$ — basis vector fed in: the input, labels the column
- $\lvert m\rangle$ — basis vector read out: the output, labels the row
- $A_{mn}$ — complex amplitude of output $m$ per unit of input $n$

Consequences of reading a matrix this way:
- **Columns are outputs.** Column $n$ of $A$ is the vector $A|n\rangle$ written out, so a matrix is understood column by column.
- **Products read right to left.** $AB|v\rangle$ runs $B$ first. Each entry of a product sums over every intermediate basis state: $(AB)_{mk} = \sum_n A_{mn}B_{nk}$ is the total amplitude for $k \to n \to m$ over all routes $n$.
- **A zero entry is a missing direct connection, not a missing route.** $A_{mn} = 0$ means input $n$ never produces output $m$ in one step, but $(A^2)_{mn}$ can be nonzero through an intermediate state — the origin of effective couplings ([[Effective Hamiltonians and Adiabatic Elimination]]).
- **Hermitian means every connection runs both ways** with conjugate amplitude, $A_{nm} = A_{mn}^*$.

**Picture:** a matrix is a switchboard — column $n$ lists the lines leaving input $n$, and each entry is the gain and phase on one line.

**What the shape of a matrix tells you:**

| Shape | What the machine does | Where it appears |
|---|---|---|
| diagonal | rescales each input separately; nothing mixes | a Hamiltonian in its eigenbasis; a density matrix with no coherences |
| block-diagonal | separate machines on separate subspaces | a conserved quantity: sectors that never exchange amplitude ([[Block Matrices]]) |
| one off-diagonal pair $A_{mn}, A_{nm}$ | connects two inputs | a coupling or transition between two states |
| strictly upper or lower triangular | moves amplitude one way along a ladder | raising and lowering operators $\sigma_\pm$, $a$, $a^\dagger$: not Hermitian alone |
| rank one, $\lvert a\rangle\langle b\rvert$ | reads one component (along $b$), writes one direction ($a$) | an outer product; a pure-state density matrix ([[Dirac Notation]]) |
| projector | keeps a subspace, discards the rest | a measurement outcome; restricting to a subspace ([[Projectors]]) |
| unitary | rotates without stretching: columns orthonormal | time evolution, gates, changes of basis ([[Unitary Matrices]]) |
| Hermitian | stretches by real factors along perpendicular axes | observables and Hamiltonians ([[Hermitian Matrices]]) |

**Off-diagonal is a statement about the basis, not the machine.** The eigenvectors are the inputs the machine only rescales; in their basis a diagonalizable matrix is diagonal, and its off-diagonal entries in any other basis describe how that basis mixes. Eigenvalues, trace, and determinant are the same in every basis ([[Basis Change]], [[Diagonalization]]). A "coupling" is therefore always a coupling between the states you chose to write down — usually the states you can prepare and measure.

**Reading a Hamiltonian.** The Schrödinger equation written in components:

$$
i\hbar\,\dot c_m = H_{mm}\,c_m + \sum_{n \neq m} H_{mn}\,c_n
$$

- $c_m$ — amplitude of basis state $m$ (dimensionless)
- $H_{mm}$ — diagonal entry (J): $\hbar$ × the rate at which $c_m$'s phase turns
- $H_{mn}$ — off-diagonal entry (J): $\hbar$ × the rate amplitude flows from $n$ into $m$

A diagonal entry alone gives $c_m(t) = c_m(0)\,e^{-iH_{mm}t/\hbar}$: a turning phase and no change of population. An off-diagonal entry feeds $c_m$ from $c_n$, but the feed adds up only while the two phases turn together; if $H_{mm} \neq H_{nn}$ the contributions alternate in sign and largely cancel. Both kinds of entry are energies, or angular frequencies after dividing by $\hbar$, which is why a Rabi frequency (off-diagonal) and a light shift (a change of a diagonal entry) are quoted in the same units.

**The comparison that decides the dynamics.** Two states whose diagonal entries differ by $\hbar\Delta$, coupled by an off-diagonal entry $\hbar\Omega/2$:

$$
H = \frac{\hbar}{2}\begin{pmatrix} \Delta & \Omega \\ \Omega & -\Delta \end{pmatrix}, \qquad E_\pm = \pm\frac{\hbar}{2}\sqrt{\Delta^2 + \Omega^2}, \qquad \tan 2\theta = \frac{\Omega}{\Delta}
$$

- $\Delta$ — difference of the diagonal entries over $\hbar$ (rad/s): a detuning in a rotating frame
- $\Omega$ — twice the off-diagonal entry over $\hbar$ (rad/s): the Rabi frequency
- $\theta$ — mixing angle (rad): how far eigenvectors are rotated from basis states

| Regime | Condition | What happens | Where it appears |
|---|---|---|---|
| resonant | $\lvert\Omega\rvert \gg \lvert\Delta\rvert$ | eigenstates are equal superpositions; population swaps completely at rate $\Omega$ | Rabi flopping, $\pi$ pulses ([[Rabi Oscillations]]) |
| far detuned | $\lvert\Omega\rvert \ll \lvert\Delta\rvert$ | transfer capped at $\Omega^2/\Delta^2$; each level shifts by $\pm\hbar\Omega^2/4\Delta$; each state picks up an admixture $\Omega/2\Delta$ of the other | light shifts, dispersive shifts, virtual couplings ([[Stark Effect and Light Shifts]]) |
| slowly varying | parameters change slowly compared with the gap $\hbar\sqrt{\Delta^2+\Omega^2}$ | the state follows the instantaneous eigenvector | adiabatic passage ([[Adiabatic Theorem]]) |
| fast sweep | $\Delta$ swept through zero at a rate large compared with $\Omega^2$ | the state stays in its basis state | diabatic passage ([[Landau-Zener Transitions]]) |

**Two different ways a transition can be suppressed:**
- **Energetically, by a diagonal difference.** A large $\Delta$ makes the coupling's feed alternate in sign every $2\pi/\Delta$, capping transfer at $\Omega^2/(\Omega^2+\Delta^2)$. The coupling still acts: it shifts both levels at second order and leaves a small admixture. The suppression improves with $\Delta$ but is never exact.
- **Exactly, by a conserved quantity.** If $[Q, H] = 0$ and $|m\rangle, |n\rangle$ have different eigenvalues $q_m \neq q_n$ of $Q$, then $(q_m - q_n)\,H_{mn} = \langle m|[Q,H]|n\rangle = 0$, so $H_{mn} = 0$ in every order and at every strength. Only a term that fails to commute with $Q$ can connect the two sectors ([[Symmetry in Quantum Mechanics]]).

Both appear in two-qubit couplings:

| Coupling term | Commutes with | Connects | Never connects |
|---|---|---|---|
| $X_1X_2 + Y_1Y_2$ (exchange, flip-flop) | total $Z_1 + Z_2$ | $\lvert 01\rangle \leftrightarrow \lvert 10\rangle$ | $\lvert 00\rangle$, $\lvert 11\rangle$ to anything |
| $X_1X_2 - Y_1Y_2$ or $X_1Y_2 + Y_1X_2$ | parity $Z_1Z_2$, not $Z_1 + Z_2$ | $\lvert 00\rangle \leftrightarrow \lvert 11\rangle$ | $\lvert 01\rangle \leftrightarrow \lvert 10\rangle$ |
| $X_1X_2$ (Mølmer–Sørensen) | parity $Z_1Z_2$ | both pairs above | even-parity to odd-parity states |
| $Z_1Z_2$ | every $Z$-basis projector | nothing: phases only | any population transfer |

**Frames move entries between the diagonal and the off-diagonal.** In the interaction picture with respect to the diagonal part, each off-diagonal entry becomes $H_{mn}\,e^{i(E_m - E_n)t/\hbar}$: the diagonal difference reappears as rotation of the coupling ([[Interaction Picture]]). The same physics, read in time: a coupling rotating much faster than its own size averages away, and a drive at the right frequency makes the coupling static ([[Rotating Frame Transformation]], [[Rotating Wave Approximation (Atlas)]]).

**Exponentials.** In the eigenbasis, $e^{-iHt/\hbar}$ is diagonal with entries $e^{-iE_nt/\hbar}$: pure phases. Population moves between basis states only because the basis states are superpositions of eigenstates whose phases turn at different rates — every oscillation frequency in the dynamics is an eigenvalue difference ([[Matrix Exponential]]).

**The classical counterpart.** Two pendulums joined by a weak spring obey the same algebra for their slowly varying amplitudes. In the site basis (one pendulum each) the coupling is off-diagonal; in the mode basis (in-phase and out-of-phase motion) the matrix is diagonal. Identical pendulums swap their energy completely; mistuned ones exchange only a fraction, and each normal mode sits mostly on one pendulum ([[Linear ODE Systems]], [[Normal Modes of Ion Chains]]). The analogy covers amplitudes, beating, avoided crossings, and adiabatic following; it does not cover measurement, Born probabilities, or entanglement between subsystems, which need the tensor-product structure of the quantum state space ([[Tensor Product]]).

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| Rabi oscillation rate and contrast against detuning | $\Omega$ and $\Delta$: rate $\sqrt{\Omega^2+\Delta^2}$, contrast $\Omega^2/(\Omega^2+\Delta^2)$ |
| Ramsey frequency shift with an off-resonant beam on | the change of a diagonal entry: a light shift $\Omega^2/4\Delta$ |
| spectrum scanned through an avoided crossing | the minimum splitting, twice the off-diagonal entry |
| population that never leaves a set of states under any drive | a conserved quantity and the block structure it implies |

> [!question]- A two-qubit coupling $J(X_1X_2 + Y_1Y_2)$ acts on $|00\rangle$ and on $|01\rangle$. What happens to each, and how does adding a term $hZ_1$ with $h \gg J$ change the answer?
> The coupling conserves $Z_1 + Z_2$, and $|00\rangle$ is alone in its sector: nothing happens to it, and $hZ_1$ only adds a phase. $|01\rangle$ and $|10\rangle$ share a sector with off-diagonal entry $2J$, so they swap completely. $hZ_1$ makes their diagonal entries differ by $2h$; for $h \gg J$ the maximum transfer falls to $4J^2/(h^2+4J^2)$ and the levels shift by $\pm 2J^2/h$. The first protection is exact, by symmetry; the second is energetic and approximate.

# Connections

- [[Dirac Notation]] — $\langle\text{output}|A|\text{input}\rangle$ in bra-ket form
- [[Basis Change]] — why off-diagonal entries depend on the basis chosen
- [[Diagonalization]] — finding the inputs the machine only rescales
- [[Block Matrices]] — sectors, and couplings between them
- [[Two-Level Systems]] — the $2\times2$ comparison in full
- [[Effective Hamiltonians and Adiabatic Elimination]] — couplings that run through an intermediate state
- [[Symmetry in Quantum Mechanics]] — where exact zeros come from
- [[Degeneracy and Level Crossings]] — when diagonal entries are equal and the coupling decides everything
- [[Interaction Picture]] — diagonal differences turned into rotating couplings
- [[Linear ODE Systems]] — coupled classical oscillators in matrix form

---
Source: R. P. Feynman, R. B. Leighton & M. Sands, *The Feynman Lectures on Physics*, Vol. III, Ch. 8–11; Cohen-Tannoudji, Diu & Laloë, *Quantum Mechanics*, Ch. II & IV
