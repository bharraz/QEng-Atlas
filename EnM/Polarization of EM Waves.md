#EnM

**A transverse wave has two leftover degrees of freedom in the plane ⊥ k — their relative amplitude and phase define the polarization state.** Equal amplitudes in phase = linear; equal amplitudes at ±90° = circular; anything else = elliptical.

# Reference

General transverse field along $\hat{z}$:
$$
\mathbf{E} = \left(E_x\,\hat{x} + E_y e^{i\phi}\,\hat{y}\right)e^{i(kz-\omega t)}
$$

| $\phi$ | $E_x{:}E_y$ | State |
|---|---|---|
| 0 or $\pi$ | any | linear, at angle $\arctan(E_y/E_x)$ |
| $\pm\pi/2$ | 1:1 | circular ($\sigma^\pm$) |
| else | else | elliptical |

**Helicity basis:** $\hat{\sigma}^\pm = \mp(\hat{x}\pm i\hat{y})/\sqrt{2}$ — eigenstates of rotation about $\mathbf{k}$, carrying $\pm\hbar$ angular momentum per photon. This is the basis atoms care about: $\sigma^\pm$ drives $\Delta m=\pm1$, $\pi$ ($\parallel \mathbf{B}$) drives $\Delta m=0$ — see [[Selection Rules]]. **Gotcha: helicity is defined relative to $\mathbf{k}$, but $\Delta m$ is relative to the quantization axis $\mathbf{B}$** — flip the beam direction and your $\sigma^+$ becomes $\sigma^-$.

Any linear state = equal superposition of $\sigma^+$ and $\sigma^-$; their relative phase sets the linear angle.

**For calculating optics chains:** write the state as a 2-vector and multiply matrices — [[Jones Calculus]]. Partial/unpolarized light needs Stokes/Mueller instead.

> [!question]- Circularly polarized light reflects off a mirror at normal incidence. What comes back?
> Opposite circular. Helicity is tied to $\mathbf{k}$: the spin direction in the lab is unchanged but $\mathbf{k}$ reversed, so $\sigma^+\to\sigma^-$. This is why double-passed quarter waveplates rotate linear polarization by 90° — and why back-reflections into polarization optics do surprising things.

# Connections

- [[Jones Calculus]] — the 2-vector formalism for pushing polarization through optics
- [[Waveplates]] — the hardware that transforms these states
- [[Selection Rules]] — $\pi/\sigma^\pm$ light ↔ $\Delta m$ transitions; why polarization purity matters at the atom
- [[Electromagnetic Wave Equation]] — transversality is where the 2D freedom comes from
- [[Birefringence]] — how materials treat the two components differently

---
Source: Hecht, *Optics*, Ch. 8; Jackson §7.2 for helicity
