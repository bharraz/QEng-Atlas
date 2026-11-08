#optics

**Coupling efficiency is the squared overlap integral of your beam with the target mode** — you must match the waist *size* and *position* (two real conditions = the one complex condition $q_{\rm in} = q_{\rm target}$), which generically takes two lenses.

# Reference

$$
\eta = \left| \int E_{\rm in}^*\, E_{\rm target}\, dA \right|^2 \Big/ \left(\int |E_{\rm in}|^2 dA \int |E_{\rm target}|^2 dA\right)
$$

For two Gaussian waists of size $w_1, w_2$ at the same location: $\eta = \left(\frac{2 w_1 w_2}{w_1^2 + w_2^2}\right)^2$ — forgiving: a 20% waist mismatch still gives $\eta \approx 0.97$. Axial offset $\Delta z$ and tilt cost you on the scale of $z_R$ and $\theta$ respectively; small errors add in quadrature.

**Picture:** fitting a hand into a glove: size (waist) and position (waist location) both have to match, and the coupling is the overlap of the two shapes.

**Design recipe:** know your source $q$, know the target $q$ (fiber MFD/2 at the tip; cavity waist from geometry), then pick two lenses and spacings so the ABCD chain maps one to the other. One lens gives one knob — it can match size *or* position, not both, except at the single magic distance. Two lenses with an adjustable gap span a continuous range (a beam-expander-plus-focus is the standard pattern).

**Typical values, single-mode fiber:** 90%+ is achievable with an aspheric matched to the MFD; 70–85% is routine; persistent <60% means wrong focal length, $M^2 > 1$, or aberrations — not walking error. Walk the two steering mirrors iteratively (near mirror for position, far for angle); what walking is and why it works is on [[Optical Fibers and Fiber Coupling]].

**Aligning into a cavity — the steps and why:**

1. **Match on paper first.** The cavity's mirrors and spacing fix the waist size and position of its mode ([[Optical Cavity Stability]]); choose lenses so the input beam has that waist at that place.
2. **Put the beam on the cavity axis roughly.** Centre the beam on both mirrors and make the light reflected from the far mirror come back on itself; the beam is then close to the axis.
3. **Scan and read the transmission.** Sweep the cavity length (piezo) or the laser frequency over a free spectral range and watch the transmitted power. Each extra peak is power going into a transverse mode, and which modes appear says what is wrong ([[Higher-Order Beam Modes]]): odd-order modes (TEM₁₀, TEM₀₁) mean the beam is tilted or offset, so walk with two mirrors; even-order, ring-shaped modes (the TEM₂₀/LG₁₀ family) mean the waist size or position is wrong, so move a lens.
4. **Finish on a camera.** Watching the transmitted beam while scanning slowly shows which mode is resonant. When only TEM₀₀ is left, the fraction of power in its peak estimates the mode-matching efficiency.

The cavity is then ready to be locked ([[Pound-Drever-Hall Locking]]).

> [!question]- Why does mode matching take two lenses in general?
> Matching means hitting a specific complex $q$ — two real numbers (waist size and location). One lens at a fixed position gives one degree of freedom (its $f$, or its position for fixed $f$). Two lenses (or one lens with both $f$ and position free) give two knobs, so the map can hit any reachable $(w_0, z_0)$ pair.

# Connections

- [[Gaussian Beams]] — the $q$-parameter language the matching condition is written in
- [[Ray Transfer Matrices]] — the ABCD chain you solve for lens positions
- [[Optical Fibers and Fiber Coupling]] — the most common target mode in the lab
- [[Fabry-Perot Cavity]] — cavity coupling is mode matching to the geometric eigenmode
- [[Higher-Order Beam Modes]] — the mismatch budget, mode by mode, visible on a cavity scan

---
Source: Kogelnik & Li, "Laser Beams and Resonators," Appl. Opt. 5, 1550 (1966)
