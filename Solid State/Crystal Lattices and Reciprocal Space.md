#solid-state

**A crystal is a lattice (a periodic array of points) plus a basis (the atoms hung on each point), and its natural language is reciprocal space — the Fourier dual where the periodicity becomes a discrete set of wavevectors.** Almost everything in solid state is stated in reciprocal space, so this is the coordinate system to internalize first.

# Reference

A **Bravais lattice** is the set of points $\mathbf{R} = n_1\mathbf{a}_1 + n_2\mathbf{a}_2 + n_3\mathbf{a}_3$ for integers $n_i$; there are 14 in 3D. The **basis** is the group of atoms attached to each lattice point — crystal = lattice + basis. The **primitive cell** is the smallest region that tiles space; the **Wigner–Seitz cell** is the primitive cell centered on a lattice point (all points closer to that point than any other).

**The lattices you actually meet** (cubic family, conventional cube edge $a$):

| Lattice                      | Points/cube | Nearest-neighbor distance | Examples          |
| ---------------------------- | ----------- | ------------------------- | ----------------- |
| simple cubic                 | 1           | $a$                       | polonium (rare)   |
| bcc - body centered cubic    | 2           | $\sqrt{3}\,a/2$           | Fe, Nb, W         |
| fcc - face centered cubic    | 4           | $a/\sqrt{2}$              | Cu, Al, Au, Ar(s) |
| diamond = fcc + 2-atom basis | 8           | $\sqrt{3}\,a/4$           | C, Si, Ge         |

Diamond structure is the NV-relevant one: fcc lattice with basis atoms at $(0,0,0)$ and $\tfrac{a}{4}(1,1,1)$; the $\langle 111\rangle$ bond directions are the four possible NV axes.

The **reciprocal lattice** is spanned by $\mathbf{b}_i$ defined by $\mathbf{a}_i\cdot\mathbf{b}_j = 2\pi\delta_{ij}$, constructed explicitly as

$$\mathbf{b}_1 = 2\pi\,\frac{\mathbf{a}_2 \times \mathbf{a}_3}{\mathbf{a}_1 \cdot (\mathbf{a}_2 \times \mathbf{a}_3)} \quad (\text{+ cyclic}),$$

with the denominator = the primitive-cell volume $V_c$. Its points $\mathbf{G} = h\mathbf{b}_1 + k\mathbf{b}_2 + l\mathbf{b}_3$ satisfy $e^{i\mathbf{G}\cdot\mathbf{R}} = 1$ for every lattice vector — they are exactly the wavevectors of plane waves that share the crystal's periodicity. Duality facts worth caching: reciprocal of fcc is bcc and vice versa; reciprocal-cell volume is $(2\pi)^3/V_c$. The **Brillouin zone** is the Wigner–Seitz cell of the reciprocal lattice, and it is the domain of **crystal momentum** $\mathbf{k}$. Its scale is $\pi/a \sim 10^{10}\,\mathrm{m^{-1}}$ — three orders above optical $k \approx 10^7\,\mathrm{m^{-1}}$, which is why light probes only the zone center $\Gamma$ ($\mathbf{k} \approx 0$) of any dispersion.

**The Fourier statement** (the actual content of "reciprocal space"): any lattice-periodic function expands as

$$f(\mathbf{r}) = \sum_{\mathbf{G}} f_{\mathbf{G}}\, e^{i\mathbf{G}\cdot\mathbf{r}}, \qquad f_{\mathbf{G}} = \frac{1}{V_c}\int_{\text{cell}} f(\mathbf{r})\, e^{-i\mathbf{G}\cdot\mathbf{r}}\, d^3r.$$

Periodicity collapses the Fourier *integral* to a Fourier *series* on the discrete set $\{\mathbf{G}\}$ — the crystal potential, charge density, and Bloch functions $u_{n\mathbf{k}}$ all live in this basis. Counting states: periodic boundary conditions over $N$ cells put $N$ allowed $\mathbf{k}$ points in the zone, spacing $2\pi/L$ per dimension — one $\mathbf{k}$ state per cell per band.

**Miller indices** $(hkl)$ label lattice planes; the reciprocal vector $\mathbf{G}_{hkl}$ is perpendicular to those planes with spacing $d = 2\pi/|\mathbf{G}_{hkl}|$. For cubic lattices:

$$d_{hkl} = \frac{a}{\sqrt{h^2 + k^2 + l^2}}.$$

Directions $[hkl]$ use square brackets; $\{hkl\}$ and $\langle hkl \rangle$ denote the symmetry-equivalent families of planes and directions.

Why reciprocal space is the right home: anything periodic in the lattice is a sum of $e^{i\mathbf{G}\cdot\mathbf{r}}$; waves propagating in the crystal are labeled by $\mathbf{k}$ in the Brillouin zone; and diffraction measures $\mathbf{G}$ directly (see [[Crystal Diffraction]]).

> [!question]- Why does crystal momentum live only in the Brillouin zone, i.e. why is $\mathbf{k}$ defined only modulo $\mathbf{G}$?
> Because the lattice has discrete rather than continuous translational symmetry, momentum is conserved only up to a reciprocal lattice vector. States at $\mathbf{k}$ and $\mathbf{k}+\mathbf{G}$ are physically identical (their Bloch phases agree on every lattice site), so all inequivalent $\mathbf{k}$ fit inside one Brillouin zone; scattering that changes $\mathbf{k}$ by a $\mathbf{G}$ is an umklapp process.

# Connections

- [[Bloch's Theorem and Band Structure]] — electron states labeled by $\mathbf{k}$ in the Brillouin zone
- [[Crystal Diffraction]] — the reciprocal lattice is literally what a diffraction experiment images
- [[Phonons]] — lattice vibrations are also labeled by $\mathbf{k}$ in the zone
- [[Fourier Transform]] — reciprocal space is the Fourier dual of the crystal
- [[Symmetry in Quantum Mechanics]] — the crystal's discrete translation group is the symmetry behind all of this

---
Source: Ashcroft & Mermin, *Solid State Physics*, Ch. 4–5; Kittel, *Introduction to Solid State Physics*, Ch. 1–2
