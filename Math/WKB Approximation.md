#quantum #math

**When the potential varies slowly on the scale of a wavelength, the wavefunction is locally a plane wave with slowly drifting wavenumber and amplitude — and everything hard about the method is what happens where that assumption fails.**

# Reference

Write $\psi = e^{iS/\hbar}$ in $-\tfrac{\hbar^2}{2m}\psi'' + V\psi = E\psi$ and expand $S = S_0 + \hbar S_1 + \cdots$. In the classically allowed region ($E > V$):

$$\psi(x) \approx \frac{C}{\sqrt{p(x)}}\exp\!\left[\pm\frac{i}{\hbar}\int^x p(x')\,dx'\right], \qquad p(x) = \sqrt{2m\,[E - V(x)]}$$

and in the forbidden region ($E < V$), with $\kappa = \sqrt{2m[V-E]}/\hbar$:

$$\psi(x) \approx \frac{C}{\sqrt{\kappa(x)}}\exp\!\left[\pm\int^x \kappa(x')\,dx'\right]$$

**Picture:** a wave crossing slowly changing terrain: locally a plane wave whose wavelength stretches where the kinetic energy is small, and whose amplitude grows there, because the particle lingers.

Two things to read off:

- **The phase** $\tfrac1\hbar\int p\,dx$ is the classical action — this is the semiclassical limit, and the stationary points of that action are the classical trajectories ([[Stationary Phase and Steepest Descent]]).
- **The amplitude** $1/\sqrt{p}$ is probability conservation: $|\psi|^2 \propto 1/p \propto 1/v$, so the particle is found where it moves slowly. That factor is not an approximation artifact — it is flux conservation.

**Validity condition.** The expansion requires the local wavelength to change little over itself:
$$\left|\frac{d\lambda}{dx}\right| \ll 1, \qquad \text{equivalently}\qquad \left|\frac{m\hbar}{p^3}\frac{dV}{dx}\right| \ll 1$$

**This fails precisely at turning points**, where $E = V$ and $p \to 0$: the expansion parameter blows up, and the amplitude $1/\sqrt p$ diverges. It is a **singular perturbation** in $\hbar$ — the small parameter multiplies the highest derivative — and the turning point is its boundary layer ([[Asymptotic Series and Dominant Balance]]).

## Turning points and connection formulas

Near a turning point, linearize $V(x) - E \approx V'(x_0)(x - x_0)$. The Schrödinger equation becomes Airy's equation, whose solutions interpolate between oscillating and decaying behaviour. Matching the Airy asymptotics onto the WKB forms on each side gives the **connection formulas**, and they are what carry the $\pi/4$:

$$\frac{2}{\sqrt p}\cos\!\left(\frac{1}{\hbar}\int_x^{x_0}\! p\,dx' - \frac{\pi}{4}\right) \;\longleftrightarrow\; \frac{1}{\sqrt\kappa}\exp\!\left(-\frac{1}{\hbar}\int_{x_0}^{x}\!\kappa\,dx'\right)$$

The $\pi/4$ is the stationary-phase phase, arriving here through Airy's asymptotic form — the same $\pi/4$ as in the [[Bessel Functions|Bessel]] large-argument expansion, and the reason a hard wall (where the wavefunction must vanish) and a soft turning point quantize differently.

**Bohr–Sommerfeld quantization** follows from requiring single-valuedness between two soft turning points:
$$\oint p\,dx = 2\pi\hbar\left(n + \tfrac12\right)$$

- The $\tfrac12$ is two turning points $\times\ \pi/4$ each — a **Maslov index**, not an empirical correction.
- One hard wall and one soft turning point gives $n + \tfrac34$; two hard walls give $n+1$, recovering the infinite square well exactly.
- For the harmonic oscillator it returns $E_n = \hbar\omega(n+\tfrac12)$ **exactly**, including the ground state — a coincidence of the quadratic potential, not a general guarantee.

## Tunneling

Through a barrier between turning points $a$ and $b$:
$$T \approx \exp\!\left[-\frac{2}{\hbar}\int_a^b \sqrt{2m\,[V(x)-E]}\;dx\right]$$

**This is the non-perturbative content the asymptotic series cannot see.** $e^{-1/\hbar}$ is smaller than every power of $\hbar$, so no order of perturbation theory produces tunneling — it is exactly the exponentially small remainder sitting under optimal truncation. Instances: alpha decay and the Gamow factor, field emission and STM current (exponential in tip–sample distance, which is what gives atomic resolution), and the exponential thickness dependence of a [[Josephson Junction]] barrier.

## Where the same approximation appears

The method is about a *slowly varying medium*, not about quantum mechanics:

| Setting | Slowly varying | Result |
|---|---|---|
| Optics | refractive index $n(x)$ | eikonal approximation; geometric optics; ray tracing |
| Waveguides / plasmas | cutoff or density profile | mode conversion and reflection at cutoffs ([[Waveguides]]) |
| Adiabatic dynamics | slowly changing $H(t)$ | the adiabatic theorem, with WKB-in-time; [[Landau-Zener Transitions]] is the failure of this at an avoided crossing |
| Classical mechanics | slowly changing parameter | adiabatic invariants, $\oint p\,dx$ conserved |

The Landau–Zener row is the most useful cross-reference: LZ is what happens where the adiabatic (WKB-in-time) approximation breaks, exactly as tunneling is what happens where the spatial one does. Both answers are exponentially small in the ratio of scales.

> [!question]- Why does Bohr–Sommerfeld carry $n+\tfrac12$ for a smooth well but $n+1$ for an infinite square well?
> The $\tfrac12$ is $\pi/4$ per soft turning point, from matching onto Airy behaviour — a Maslov index counting the turning points. A hard wall is not a soft turning point: the wavefunction is forced to zero rather than leaking into a forbidden region, contributing $\pi/2$ instead. Two hard walls give $n+1$.

# Connections

- [[Asymptotic Series and Dominant Balance]] — WKB as a singular perturbation in $\hbar$; turning points as boundary layers
- [[Stationary Phase and Steepest Descent]] — where the $\pi/4$ comes from; classical paths as stationary action
- [[Adiabatic Theorem]] — the time-domain version of the same slowness condition
- [[Landau-Zener Transitions]] — the exponentially small failure of adiabaticity
- [[Bessel Functions]] — the same $\pi/4$ in a large-argument asymptotic form
- [[Josephson Junction]] — barrier tunneling exponential in thickness
- [[Schrodinger Equation]] — the equation being approximated
- [[Quantum Harmonic Oscillator]] — where Bohr–Sommerfeld happens to be exact

---
Source: Griffiths, *Introduction to Quantum Mechanics*, Ch. 9; Bender & Orszag, *Advanced Mathematical Methods*, Ch. 10
