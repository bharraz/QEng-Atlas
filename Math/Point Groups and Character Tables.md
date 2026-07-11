#group-theory #math #solid-state

**A point group is the finite set of rotations, reflections, and improper rotations leaving at least one point fixed — the symmetry group of a molecule or a defect site — and its character table is the complete lookup device: it tells you level degeneracies, selection rules, and how states split, without solving anything.** For a defect qubit like the NV center, the point group is doing the job the full rotation group does for a free atom.

# Reference

**Operations and Schoenflies notation:** $E$ (identity), $C_n$ (rotation by $2\pi/n$), $\sigma_v / \sigma_h$ (mirror containing / perpendicular to the main axis), $S_n$ (rotation-reflection), $i$ (inversion). Common groups: $C_{2v}$ (water), $C_{3v}$ (NH$_3$, NV center), $D_{4h}$ (square-planar), $T_d$ (methane, substitutional defects in diamond), $O_h$ (octahedral sites).

**Reading a character table** — the worked case, $C_{3v} = \{E,\, 2C_3,\, 3\sigma_v\}$ (order 6, $\cong D_3 \cong S_3$):

| $C_{3v}$ | $E$ | $2C_3$ | $3\sigma_v$ | linear | quadratic |
|---|---|---|---|---|---|
| $A_1$ | 1 | 1 | 1 | $z$ | $z^2$, $x^2{+}y^2$ |
| $A_2$ | 1 | 1 | $-1$ | $R_z$ | — |
| $E$ | 2 | $-1$ | 0 | $(x, y)$ | $(x^2{-}y^2, xy)$, $(xz, yz)$ |

Conventions: columns are conjugacy classes (with class sizes), rows are irreps. $A/B$ = 1D, $E$ = 2D, $T$ = 3D (unfortunate clash: irrep "$E$" vs identity "$E$"). The "linear" column says how $x, y, z$ transform — i.e. which irrep the **electric dipole** components belong to. Checks: number of irreps = number of classes; $\sum d_\mu^2 = |G|$ ($1+1+4=6$).

**The three standard uses:**

1. **Degeneracies.** Orbital levels at a $C_{3v}$ site come only in singlets ($A_1, A_2$) and doublets ($E$) — no 2D irrep, no orbital doublet. The NV$^-$ level structure ($^3A_2$ ground, $^3E$ excited, $^1A_1/^1E$ singlets) is literally labeled by these irreps; the $E$ orbital degeneracy of the excited state is what strain splits.

2. **Splitting under symmetry lowering (branching).** Embed an atom in a crystal field: the $SO(3)$ irrep $\ell$ becomes reducible under the site's point group. Compute the character of the rotation rep, $\chi_\ell(\theta) = \sin\big((2\ell{+}1)\theta/2\big)/\sin(\theta/2)$ (with $\chi(\sigma), \chi(S_n)$ from the improper extension), then project with the multiplicity formula $n_\mu = \frac{1}{|G|}\sum_g \chi^{(\mu)}(g)^* \chi(g)$. Classic results: in an octahedral field, $d$ ($\ell=2$) $\to e_g \oplus t_{2g}$ — the crystal-field splitting; $p$ ($\ell = 1$) in $C_{3v}$ $\to A_1 \oplus E$ ($z$ vs $(x,y)$: axial site distinguishes along-axis from in-plane).

3. **Selection rules.** $\langle f | \hat{O} | i \rangle$ can be nonzero only if $\Gamma_f \otimes \Gamma_O \otimes \Gamma_i$ contains $A_1$ (the trivial irrep). Multiply characters, decompose, look for $A_1$. Example in $C_{3v}$: is $A_1 \to A_2$ dipole-allowed? Dipole is $A_1 (z) \oplus E (x,y)$. $A_2 \otimes A_1 = A_2$; $A_2 \otimes E = E$; neither contains $A_1$ — forbidden for all polarizations. $A_2 \to E$ via $(x,y)$: $E \otimes E = A_1 \oplus A_2 \oplus E \ni A_1$ — allowed, in-plane polarized. This is why the NV optical transition ($^3A_2 \leftrightarrow {}^3E$) is driven by light polarized perpendicular to the NV axis.

**Spin and double groups** (flag, not full treatment): half-integer spin picks up $-1$ under $2\pi$, so spin states transform under the **double group** (each class doubled by the $2\pi$ element) with extra spinor irreps — needed whenever spin-orbit coupling matters at a site, e.g. the NV excited-state fine structure.

**Space groups**: point group + lattice translations (+ screw axes/glide planes) = the 230 space groups of crystals; the point group of the wavevector governs degeneracies in band structures at high-symmetry points (see [[Bloch's Theorem and Band Structure]]).

> [!question]- Zero-field NV: what protects the $m_s = \pm 1$ degeneracy, given that $S=1$ has no Kramers protection?
> The $C_{3v}$ symmetry. $m_s = \pm 1$ transform into each other under the point group (they form the 2D $E$ representation of the spin part); as long as the defect keeps its threefold symmetry, no perturbation that respects it can split them. Transverse strain or electric fields *break* $C_{3v}$ and split the pair (the $E$ parameter in the spin Hamiltonian), while axial perturbations only shift $D$. Symmetry tells you which knob does what before any calculation.

# Connections

- [[(Atlas) Group Theory]] — $C_{3v} \cong D_3$: the abstract group behind the worked triangle example
- [[Group Representations]] — character orthogonality and the multiplicity formula used throughout
- [[Symmetry in Quantum Mechanics]] — degeneracy, branching, and selection rules in general form
- [[NV Centers (atlas)]] — the flagship application: level labels, strain splitting, optical polarization
- [[Selection Rules]] — the free-atom ($SO(3)$) version of use #3
- [[Bloch's Theorem and Band Structure]] — space groups and band degeneracies

---
Source: Dresselhaus, Dresselhaus & Jorio, *Group Theory: Application to the Physics of Condensed Matter*, Ch. 3–5; Tinkham, *Group Theory and Quantum Mechanics*, Ch. 4; Maze et al., *New J. Phys.* 13, 025025 (2011) (NV group theory)
