#solid-state

**In a periodic potential, electron eigenstates are plane waves modulated by a lattice-periodic function (Bloch waves), and their energies organize into allowed bands separated by forbidden gaps.** How those bands are filled relative to the gap is what makes a material a metal, insulator, or semiconductor — the single most consequential fact in solid state.

# Reference

**Bloch's theorem**: in a lattice-periodic potential the eigenstates take the form

$$\psi_{n\mathbf{k}}(\mathbf{r}) = e^{i\mathbf{k}\cdot\mathbf{r}}\,u_{n\mathbf{k}}(\mathbf{r}),$$

where $u_{n\mathbf{k}}$ is periodic with the lattice, $\mathbf{k}$ is the crystal momentum in the Brillouin zone, and $n$ is the band index. The energy $E_n(\mathbf{k})$ is a function over the zone — the **band structure**. A **band gap** is an energy range containing no states.

**The two limiting models** (every band structure interpolates between them):

- *Nearly free electrons*: start from the parabola $\hbar^2k^2/2m$, let a weak lattice potential $V_{\mathbf{G}}$ mix degenerate states at the zone boundary — gap of size $2|V_{\mathbf{G}}|$ opens there (see the callout below).
- *Tight binding*: start from atomic orbitals, let electrons hop with amplitude $t$ to neighbors. One orbital per site on a 1D chain of spacing $a$:

$$E(k) = \varepsilon_0 - 2t\cos(ka),$$

a band of width $4t$ centered on the atomic level. Generalizes as $E(\mathbf{k}) = \varepsilon_0 - t\sum_{\boldsymbol\delta} e^{i\mathbf{k}\cdot\boldsymbol\delta}$ over nearest-neighbor vectors. Moral: *bandwidth measures wavefunction overlap* — deep core states give flat bands, extended valence states give dispersive ones.

Near a band edge the dispersion is parabolic, $E(\mathbf{k}) \approx E_0 + \hbar^2 k^2 / 2m^*$, defining the **effective mass** $1/m^* = (1/\hbar^2)\,d^2E/dk^2$ from the band curvature (a tensor in general; for the 1D tight-binding band, $m^* = \hbar^2/2ta^2$ — stronger hopping, lighter electron). It can be negative (near a band top), which is bookkept as a positively charged **hole**.

**Semiclassical dynamics** — how a Bloch electron responds to applied fields:

$$\mathbf{v}_n(\mathbf{k}) = \frac{1}{\hbar}\nabla_{\mathbf{k}} E_n(\mathbf{k}), \qquad \hbar\dot{\mathbf{k}} = -e(\mathbf{E} + \mathbf{v}\times\mathbf{B}).$$

The field steers $\mathbf{k}$ through the band; the *band structure* (not $\hbar\mathbf{k}/m$) sets the velocity. All transport — conductivity, Hall effect, cyclotron resonance — is these two lines plus scattering.

**Density of states** — how many states per energy interval, the quantity that enters every rate and thermodynamic formula:

$$g(E) = \sum_n \int_{\text{BZ}} \frac{d^3k}{(2\pi)^3}\, \delta\!\big(E - E_n(\mathbf{k})\big); \qquad g(E) = \frac{1}{2\pi^2}\left(\frac{2m^*}{\hbar^2}\right)^{3/2}\!\sqrt{E}\quad \text{(parabolic 3D)}.$$

In 2D, $g$ is constant per band; in 1D it diverges as $1/\sqrt{E}$ at band edges — van Hove singularities. Fermi-level numbers to anchor: in a metal $E_F \sim 1\text{–}10$ eV $\sim 10^4\text{–}10^5$ K, so conduction electrons are deeply degenerate at any lab temperature; only the $\sim k_BT$ shell at $E_F$ participates in anything.

**Filling decides everything:** a completely filled band carries no net current, so a full band plus a gap to the next empty band is an **insulator** (or **semiconductor** if the gap is small enough to bridge thermally or by doping); a partly filled band is a **metal**. The **Fermi level** is where the filling stops.

> [!question]- Why does a weak periodic potential open gaps instead of just shifting the free-electron parabola slightly?
> At the Brillouin-zone boundary a forward wave $\mathbf{k}$ and its Bragg-reflected partner $\mathbf{k}-\mathbf{G}$ are degenerate. Any periodic potential, however weak, mixes them into two standing waves — one piling charge on the ion cores, one between them — with different potential energies. That energy splitting is the gap; it is degenerate perturbation theory at the zone boundary.

# Connections

- [[Crystal Lattices and Reciprocal Space]] — the periodicity and Brillouin zone this rests on
- [[Phonons]] — the lattice's other excitation; electrons scatter off them
- [[Superconductivity]] — what happens when electrons near the Fermi level pair up
- [[Fermi's Golden Rule]] — transition rate for scattering between Bloch states
- [[Symmetry in Quantum Mechanics]] — band degeneracies trace to the crystal's symmetry group

---
Source: Ashcroft & Mermin, *Solid State Physics*, Ch. 8–9; Kittel, *Introduction to Solid State Physics*, Ch. 7
