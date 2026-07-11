#group-theory #quantum

**A symmetry of a quantum system is a transformation that commutes with the Hamiltonian, and it forces structure onto the spectrum: degeneracies, conserved quantities, and selection rules all follow from which group leaves $H$ invariant.** This is where group theory stops being algebra and starts predicting measurements.

# Reference

**Wigner's theorem**: any symmetry of a quantum system is realized on the Hilbert space by a unitary (or antiunitary) operator $U$ that preserves transition probabilities. Symmetries of the dynamics satisfy

$$[U, H] = 0.$$

Three consequences follow directly, and each is something you can spot in data:

- **Conserved quantities.** If $U = e^{-i\theta G}$ is a continuous symmetry, then $[G, H] = 0$, so $\langle G \rangle$ is constant in time. The generator $G$ *is* the conserved observable — angular momentum for rotational symmetry, momentum for translations. (See [[Lie Algebras]] for why the generator carries the physics.)
- **Degeneracy.** States related by a symmetry have equal energy. A degeneracy in a spectrum is almost never accidental; it signals a symmetry group, and the size of the degenerate multiplet is the dimension of an irreducible representation (see [[Group Representations]]).
- **Selection rules.** Whether $\langle f | \hat{O} | i \rangle$ can be nonzero is fixed by how $|i\rangle$, $|f\rangle$, and $\hat{O}$ transform under the group. If the representations don't match, the matrix element vanishes by symmetry alone — no integral required.

**Good quantum numbers** are the labels of the irreducible representations of the symmetry group. When you write a state as $|n, \ell, m\rangle$, the $\ell, m$ are rotation-group labels; they are conserved precisely because rotations commute with $H$.

**Antiunitary symmetries.** Wigner's theorem allows one exception to unitarity: time reversal $\Theta$ is antiunitary ($\Theta i \Theta^{-1} = -i$). For half-integer total spin, $\Theta^2 = -1$, forcing **Kramers degeneracy**: every level of a time-reversal-symmetric Hamiltonian is at least doubly degenerate, and only a magnetic field (which breaks $\Theta$) can lift it. This is why an odd-electron system (or NV$^-$'s $m_s = \pm 1$ pair at zero field... with the caveat that $S=1$ is integer spin and that degeneracy is instead protected by the $C_{3v}$ symmetry) keeps degenerate pairs under any electric-field or strain perturbation.

**Symmetry breaking reorganizes the spectrum predictably.** When a perturbation reduces the group $G \to H \subset G$, each $G$-irrep splits into the $H$-irreps it contains — **branching rules**. The classic case: a magnetic field breaks $SO(3) \to SO(2)$, and the $(2j{+}1)$-fold multiplet splits into $2j+1$ singlets labeled by $m$ — the Zeeman effect as pure representation theory. Counting the split levels tells you the residual symmetry; which levels move tells you how the perturbation transforms.

**Constructing symmetry-adapted states.** The projection operator built from characters, $P^{(\mu)} \propto \sum_g \chi^{(\mu)}(g)^* U(g)$, extracts the component of any trial state transforming as irrep $\mu$ — the mechanical route to molecular orbitals, vibrational normal modes, and crystal-field states (see [[Group Representations]]).

> [!question]- You see two states at exactly the same energy. What does group theory tell you to look for?
> A symmetry whose group has a multi-dimensional irreducible representation. The equal energies are those states sitting in one irrep; find the transformation that maps them into each other and you've found the symmetry. If the degeneracy lifts when you add a field, you've found what breaks that symmetry.

# Connections

- [[(Atlas) Group Theory]] — the object doing the acting
- [[Group Representations]] — degenerate multiplets are irreps; this is the precise statement
- [[Lie Algebras]] — continuous symmetries and their conserved generators
- [[Selection Rules]] — the atomic-physics payoff: which transitions are allowed
- [[Wigner-Eckart Theorem]] — matrix elements factored by symmetry; selection rules quantified
- [[Zeeman Effect (Atlas)]] — multiplet splitting as $SO(3) \to SO(2)$ branching
- [[Simultaneous Diagonalization]] — $[G,H]=0$ means shared eigenstates, i.e. good quantum numbers
- [[Point Groups and Character Tables]] — the finite-group case: defect sites, molecules, crystal fields

---
Source: Sakurai & Napolitano, *Modern Quantum Mechanics*, Ch. 4; Tinkham, *Group Theory and Quantum Mechanics*, Ch. 3
