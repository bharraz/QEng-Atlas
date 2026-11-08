#group-theory #quantum

**If rotating, reflecting, translating, or permuting the parts of a system leaves its Hamiltonian unchanged, the operator that performs the transformation commutes with $H$, and its eigenvalue labels become conserved quantum numbers.** Group theory turns that into three predictions you can check without solving $H$: which levels must be degenerate, which matrix elements must vanish, and how levels split when the symmetry is broken. It does not give energies; it gives the structure every energy calculation must respect, and through the Wigner–Eckart theorem, ratios between matrix elements.

# Reference

**Wigner's theorem.** Any symmetry of a quantum system — a transformation preserving all transition probabilities — acts on the Hilbert space as a unitary or an antiunitary operator $U$. A symmetry of the dynamics also satisfies

$$
[U, H] = 0, \qquad U = e^{-i\theta G} \;\Rightarrow\; [G, H] = 0
$$

- $U$ — the operator implementing the transformation on states
- $G$ — generator of a continuous symmetry (Hermitian): the conserved observable
- $\theta$ — the transformation's parameter (angle, distance)

**Picture:** a symmetry is a relabelling of the system that the Hamiltonian cannot detect; whatever cannot be detected cannot change, and whatever the relabelling exchanges must cost the same energy.

**Three consequences, each visible in data:**
- **Conserved quantities.** $[G, H] = 0$ makes $\langle G\rangle$ constant in time. The generator is the conserved observable: angular momentum for rotations, momentum for translations ([[Noether's Theorem]], [[Lie Algebras (Atlas)]]).
- **Degeneracy.** States that the symmetry maps into each other have equal energy, and a degenerate multiplet is an irreducible representation: its size is the irrep's dimension ([[Group Representations]], [[Degeneracy and Level Crossings]]).
- **Selection rules.** Whether $\langle f|\hat O|i\rangle$ can be nonzero is fixed by how $|i\rangle$, $|f\rangle$, and $\hat O$ transform. If the representations do not match, the matrix element vanishes by symmetry alone, with no integral required.

**The vanishing-integral rule.** With $|i\rangle$ in irrep $\Gamma_i$, $|f\rangle$ in $\Gamma_f$, and $\hat O$ transforming as $\Gamma_O$:

$$
\langle f|\hat O|i\rangle \neq 0 \quad\text{only if}\quad \Gamma_f^* \otimes \Gamma_O \otimes \Gamma_i \ni \Gamma_\text{trivial}
$$

- $\Gamma$ — an irreducible representation of the symmetry group
- $\Gamma_\text{trivial}$ — the representation in which every element acts as 1

The integrand must contain a part that every symmetry operation leaves unchanged; all other parts average to zero over the group. Parity is the two-element case ([[Parity and Time Reversal]]); for rotations the rule becomes the angular-momentum triangle condition ([[Clebsch-Gordan Coefficients]]).

**Good quantum numbers** are the irrep labels of the symmetry group. In $|n, \ell, m\rangle$, $\ell$ and $m$ label representations of the rotation group, and they are conserved because rotations commute with $H$ ([[Simultaneous Diagonalization]]). In matrix terms, the Hamiltonian is block-diagonal in a basis of these labels, one block per irrep ([[Block Matrices]]).

**Applying it to a system, step by step:**
1. **Find the group.** List the transformations that leave $H$ unchanged — geometric (rotations, reflections, a crystal's point group, lattice translations), internal (spin rotations, qubit parity, particle exchange), and discrete ones such as time reversal.
2. **Classify the states.** Assign each basis state, or each orbital, to an irrep, using the character table for finite groups ([[Point Groups and Character Tables]]).
3. **Read off the block structure.** $H$ has no matrix elements between different irreps; diagonalize each block separately.
4. **Read off degeneracies.** Each irrep of dimension $d$ gives a $d$-fold degenerate level, unless a further symmetry joins levels together.
5. **Apply the vanishing-integral rule** to every operator you care about: the drive, the measurement, the noise.
6. **Break the symmetry deliberately,** by a field, strain, or a deformation, and use branching rules to predict the splitting.

| Symmetry | Conserved label | Degeneracy it forces | Selection rule it gives |
|---|---|---|---|
| spatial inversion | parity $\pm1$ | none by itself (one-dimensional irreps) | E1 changes parity |
| rotations, $SO(3)$ or $SU(2)$ | $j$, $m$ | $2j+1$ | $\Delta j = 0, \pm1$, triangle rule, $\Delta m = q$ for a rank-1 operator ([[Wigner-Eckart Theorem]]) |
| rotations about one axis, $SO(2)$ | $m$ | none | $\Delta m$ set by the operator's component |
| a crystal point group (e.g. $C_{3v}$) | irrep label ($A_1$, $A_2$, $E$) | dimension of the irrep: 1, 1, or 2 | allowed transitions by the product rule |
| lattice translations | crystal momentum $k$ | none in general | $k$ conserved up to a reciprocal-lattice vector ([[Bloch's Theorem and Band Structure]]) |
| exchange of identical particles | symmetric or antisymmetric | singlet and triplet spin sectors | no transitions between sectors under spin-independent couplings |
| time reversal, half-integer spin | none (antiunitary) | Kramers pairs | constrains phases and reality of matrix elements |

**Antiunitary symmetries.** Wigner's theorem allows one exception to unitarity: time reversal $\Theta$ is antiunitary, $\Theta i \Theta^{-1} = -i$. For half-integer total spin $\Theta^2 = -1$, which forces **Kramers degeneracy**: every level of a time-reversal-symmetric Hamiltonian is at least doubly degenerate, and only a magnetic field, which breaks $\Theta$, lifts it. Integer-spin systems have no such protection. The NV$^-$ ground state ($S = 1$) is the standard contrast: its $m_s = \pm 1$ pair is degenerate at zero field only because of the $C_{3v}$ site symmetry, and transverse strain or electric field splits it ([[Parity and Time Reversal]]).

**Symmetry breaking reorganizes the spectrum predictably.** When a perturbation reduces the group $G \to H \subset G$, each $G$-irrep splits into the $H$-irreps it contains: the **branching rules**. A magnetic field breaks $SO(3) \to SO(2)$, and the $(2j{+}1)$-fold multiplet splits into $2j+1$ singlets labelled by $m$, the Zeeman effect as pure representation theory ([[Zeeman Effect (Atlas)]]). Counting the split levels tells you the residual symmetry; which levels move tells you how the perturbation transforms.

**Constructing symmetry-adapted states.** The projection operator built from characters, $P^{(\mu)} \propto \sum_g \chi^{(\mu)}(g)^* U(g)$, extracts the component of any trial state that transforms as irrep $\mu$. It is the mechanical route to molecular orbitals, vibrational normal modes, and crystal-field states ([[Group Representations]]).

**What symmetry does not tell you:** the energies of the blocks, the size of allowed matrix elements beyond ratios within a multiplet, or whether an "allowed" transition is strong. An accidental near-degeneracy between different irreps can also look like a symmetry until a small change of parameters separates the levels.

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| degeneracy pattern of a spectrum | dimensions of irreps, and so candidate symmetry groups |
| number of components a line splits into under a field or strain | the residual symmetry after breaking |
| a transition absent despite a nearby resonance | a symmetry-forbidden matrix element; check which symmetry the drive breaks |
| a population that never leaves a sector under any applied drive | a conserved quantity commuting with every term present |

> [!question]- You see two states at exactly the same energy. What does group theory tell you to look for?
> A symmetry whose group has a multi-dimensional irreducible representation. The equal energies are those of states sitting in one irrep; find the transformation that maps them into each other and you have found the symmetry. If the degeneracy lifts when you add a field, you have found what breaks that symmetry. If no symmetry can be found, check for a hidden one (hydrogen's Runge–Lenz vector) or for a tuned crossing between different sectors, which a small change of parameters would separate.

# Connections

- [[(Map) Group Theory]] — the object doing the acting
- [[Group Representations]] — degenerate multiplets are irreps; the precise statement
- [[Lie Algebras (Atlas)]] — continuous symmetries and their conserved generators
- [[Noether's Theorem]] — the classical origin of symmetry-to-conservation
- [[Parity and Time Reversal]] — the discrete symmetries worked through
- [[Degeneracy and Level Crossings]] — where degeneracies come from and why they matter
- [[Selection Rules]] — the atomic-physics application: which transitions are allowed
- [[Wigner-Eckart Theorem]] — matrix elements factored by symmetry; selection rules quantified
- [[Zeeman Effect (Atlas)]] — multiplet splitting as $SO(3) \to SO(2)$ branching
- [[Simultaneous Diagonalization]] — $[G,H]=0$ means shared eigenstates, so good quantum numbers
- [[Point Groups and Character Tables]] — the finite-group case: defect sites, molecules, crystal fields
- [[Reading Matrices and Hamiltonians]] — exact zeros from conserved quantities, in matrix form
- [[Phase Transitions and Critical Phenomena]] — spontaneous symmetry breaking

---
Source: Sakurai & Napolitano, *Modern Quantum Mechanics*, Ch. 4; Tinkham, *Group Theory and Quantum Mechanics*, Ch. 3; Dresselhaus, Dresselhaus & Jorio, *Group Theory: Application to the Physics of Condensed Matter*, Ch. 4–6
