#solid-state

**Fire waves — X-rays, neutrons, electrons — at a crystal and the scattered intensity peaks exactly at the reciprocal lattice vectors; the peak positions reconstruct the lattice and the peak amplitudes (the structure factor) reveal the atomic basis.** It is the Fourier transform made into an experiment, and it is how essentially all crystal structure is known.

# Reference

**Bragg condition** (planes view): constructive reflection when $2d\sin\theta = n\lambda$, with $d$ the plane spacing. **Laue condition** (equivalent, reciprocal view): the scattering wavevector change equals a reciprocal lattice vector,

$$\Delta\mathbf{k} = \mathbf{k}' - \mathbf{k} = \mathbf{G}.$$

Scattering is elastic ($|\mathbf{k}'| = |\mathbf{k}|$). The intensity at each allowed $\mathbf{G}$ is set by the **structure factor**

$$S(\mathbf{G}) = \sum_j f_j\, e^{i\mathbf{G}\cdot\mathbf{r}_j},$$

summed over the basis atoms at $\mathbf{r}_j$ with scattering strengths $f_j$; when $S(\mathbf{G})=0$ a peak is systematically absent even though $\mathbf{G}$ is allowed.

**Extinction rules** (indices $hkl$ on the conventional cubic cell):

- **bcc**: peaks survive only for $h+k+l$ even.
- **fcc**: peaks survive only for $h,k,l$ all even or all odd.
- **diamond**: fcc rule, *plus* $h+k+l = 4n$ or all-odd (the two-atom basis kills e.g. $(200)$).

Reading absences backwards is how you identify the lattice from a powder pattern. For cubic crystals the peak positions follow from $d_{hkl} = a/\sqrt{h^2+k^2+l^2}$ in Bragg's law, so $\sin^2\theta \propto h^2+k^2+l^2$ — the allowed integer sequences (bcc: 2,4,6,8,...; fcc: 3,4,8,11,...) fingerprint the structure.

**Ewald construction** — the geometric solver: draw a sphere of radius $|\mathbf{k}|$ through the reciprocal-lattice origin; diffraction fires for every $\mathbf{G}$ on the sphere's surface. It makes two facts visible at once: you need $\lambda \lesssim 2d$ (sphere big enough to reach the first $\mathbf{G}$ — hence X-rays, not visible light), and a fixed single crystal at fixed $\lambda$ generically hits *no* peaks (measure zero), which is why experiments rotate the crystal, use powder (all orientations at once), or use white-beam Laue.

**Thermal motion** attenuates but does not broaden peaks: each intensity carries the Debye–Waller factor $e^{-G^2\langle u^2\rangle/3}$ (see [[Phonons]]). Periodicity is preserved on average, so peaks stay sharp; the lost weight reappears as diffuse background between them.

**Probes differ by what they see:** X-rays scatter off the electron density; neutrons off nuclei and off magnetic moments (so they map magnetic order); electrons scatter strongly and probe surfaces. In all cases the far-field pattern is $|\text{FT of the density}|^2$ — the same physics as an optical [[Diffraction Gratings|grating]] with the crystal as the grating.

> [!question]- Why do diffraction peaks appear only at reciprocal lattice vectors and nowhere else?
> Constructive interference from the periodic array of scatterers requires the phase $e^{i\Delta\mathbf{k}\cdot\mathbf{R}}$ to equal 1 at every lattice vector $\mathbf{R}$. That condition is met exactly when $\Delta\mathbf{k}$ is a reciprocal lattice vector $\mathbf{G}$, by the definition of the reciprocal lattice. For any other $\Delta\mathbf{k}$ the contributions from different cells run through all phases and cancel.

# Connections

- [[Crystal Lattices and Reciprocal Space]] — the reciprocal lattice this measures directly
- [[Fourier Transform]] — the diffraction pattern is the transform of the density, made physical
- [[Diffraction]] — the same far-field interference physics in optics
- [[Diffraction Gratings]] — a crystal is a 3D grating; the grating equation is Bragg's law
- [[Fermi's Golden Rule]] — scattering rate into a final state at $\mathbf{k}+\mathbf{G}$

---
Source: Ashcroft & Mermin, *Solid State Physics*, Ch. 6; Kittel, *Introduction to Solid State Physics*, Ch. 2; Warren, *X-Ray Diffraction*
