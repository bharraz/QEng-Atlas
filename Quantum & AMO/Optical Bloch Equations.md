#quantum #AMO

**Coherent Rabi driving plus spontaneous decay in one set of equations: the Bloch vector precesses under the drive while $\Gamma$ drags it toward the ground state.** This is the two-level atom you actually have, and its steady state is where scattering rates, saturation, and power broadening all come from.

# Reference

Bloch vector $(u, v, w)$ (coherences and inversion) in the rotating frame, detuning $\delta = \omega_L - \omega_0$:

$$\dot{u} = \delta v - \tfrac{\Gamma}{2}u, \qquad \dot{v} = -\delta u + \Omega w - \tfrac{\Gamma}{2}v, \qquad \dot{w} = -\Omega v - \Gamma(w + 1)$$

$u, v$ = in-phase and out-of-phase coherences (dimensionless, $u + iv = 2\rho_{ge}e^{i\omega_L t}$ — the dispersive and absorptive quadratures of the atomic dipole); $w = \rho_{ee} - \rho_{gg}$ = inversion, running $-1$ (ground) to $+1$; $\delta = \omega_L - \omega_0$ = detuning (rad/s); $\Omega$ = Rabi frequency (rad/s), from $\hbar\Omega = -\mathbf{d}\cdot\mathbf{E}_0$ so $\Omega \propto d\sqrt{I}$ — linear in dipole matrix element, square-root in intensity; $\Gamma$ = excited-state decay rate (s⁻¹), the natural linewidth in angular units. Structurally a damped driven oscillator: coherences ring at $\delta$ and decay at $\Gamma/2$, populations relax at $\Gamma$ — the factor 2 is why $T_2 \leq 2T_1$.

**Steady state** (the lookup result), with on-resonance saturation parameter $s_0 = 2\Omega^2/\Gamma^2 = I/I_{\mathrm{sat}}$ (dimensionless — drive strength measured against decay):

$$\rho_{ee} = \frac{s_0/2}{1 + s_0 + (2\delta/\Gamma)^2}, \qquad R_{\mathrm{scatt}} = \Gamma\rho_{ee} \xrightarrow{s_0 \to \infty} \frac{\Gamma}{2}$$

Scattering saturates at $\Gamma/2$ — no amount of power scatters faster; extra intensity only broadens. **Power broadening:**

$$\Delta\omega_{\mathrm{FWHM}} = \Gamma\sqrt{1 + s_0}$$

$s_0 = 1$ defines saturation intensity $I_{\mathrm{sat}}$ (e.g. a few mW/cm² for alkali D lines, ~tens for ion cooling lines). Transient solutions: damped Rabi oscillations settling to the above in a few $1/\Gamma$.

**Regime map:** $\Omega \gg \Gamma$ — coherent flopping, OBEs reduce to Rabi; $\Omega \ll \Gamma$ — rate equations suffice; in between (Doppler cooling territory) you need the full thing.

> [!question]- Why does the fluorescence lineshape broaden with power even though $\Gamma$ is fixed?
> The transition saturates on resonance first — $\rho_{ee}$ can't exceed $\tfrac{1}{2}$ — while the wings still have headroom. Clipping the peak while the wings keep growing widens the curve: FWHM $= \Gamma\sqrt{1+s_0}$. The atom's linewidth didn't change; your response did.

# Connections

- [[Spontaneous Emission and Linewidth]] — the $\Gamma$ terms; OBEs are Lindblad decay in Bloch-vector clothes
- [[Rabi Oscillations]] — the $\Gamma \to 0$ limit
- [[Driven Damped Harmonic Oscillator]] — same steady-state-vs-detuning anatomy, one abstraction level down
- [[Lindblad Master Equation]] — the general formalism these are the two-level instance of

---
Source: Foot, *Atomic Physics*, Ch. 7
