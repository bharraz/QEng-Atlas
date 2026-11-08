#AMO

**An excited atom decays because vacuum fluctuations tickle it: Fermi's golden rule with the vacuum mode density gives $\Gamma$, and that decay stamps a Lorentzian of width $\Gamma/2\pi$ on the transition.** Linewidth and lifetime are the same number.

# Reference

Golden rule + free-space mode density $\rho(\omega) \propto \omega^2$:

$$\Gamma = \frac{\omega_0^3 d^2}{3\pi\varepsilon_0 \hbar c^3}, \qquad \tau = \frac{1}{\Gamma}$$

- $\Gamma$ — decay rate (s⁻¹, angular — divide by $2\pi$ for linewidth in Hz)
- $\omega_0$ — transition frequency (rad/s)
- $d = \langle e|\hat d|g\rangle$ — transition dipole matrix element (C·m, of order $ea_0$ for a strong optical line)
- $\tau$ — excited-state lifetime (s)

The $\omega_0^3$ comes from the vacuum mode density ($\propto\omega^2$) times the photon energy scaling of the coupling; $d^2$ is the usual coupling-squared of the golden rule.

**Picture:** an excited atom as a bell coupled to the vacuum's continuum of modes: the energy rings away exponentially, and the same leak broadens the line by exactly the decay rate.

**The $\omega^3 d^2$ scaling** is the one to remember: strong optical dipole lines decay in ns–tens of ns ($\Gamma/2\pi \sim 10\text{–}30$ MHz — Ca⁺ 397 nm: ≈22 MHz; Yb⁺ 369 nm: 19.6 MHz), while microwave hyperfine transitions, down by $(\omega_{\mathrm{opt}}/\omega_{\mu w})^3 \sim 10^{14}$–$10^{15}$ and further by being magnetic-dipole rather than electric-dipole transitions (roughly $\alpha^2 \sim 10^{-4}$), effectively never decay — free $T_1$ for hyperfine qubits. Quadrupole and octupole clock lines are slow because their multipole moments are small: $\tau \approx 0.4$–30 s for the $D_{5/2}$ levels of Sr⁺, Ca⁺, and Ba⁺, and years for the Yb⁺ octupole line.

**Lineshape:** exponential decay $e^{-\Gamma t/2}$ of the amplitude Fourier-transforms to a Lorentzian in the spectrum:

$$S(\omega) \propto \frac{\Gamma/2\pi}{(\omega - \omega_0)^2 + (\Gamma/2)^2}, \qquad \Delta\nu_{\mathrm{FWHM}} = \frac{\Gamma}{2\pi}$$

— the *natural* linewidth, the floor under all broadening (Doppler, power, magnetic) that you can engineer away.

**Branching ratios:** with several decay channels, $\Gamma = \sum_i \Gamma_i$; each branch's fraction $\Gamma_i/\Gamma$ is set by $\omega_i^3 |d_i|^2$. This is why Ca⁺ $P_{1/2}$ leaks ~6% to $D_{3/2}$ and every cooling scheme drags a repumper along.

> [!question]- Why does a hyperfine qubit have essentially infinite $T_1$ while an optical qubit's is set by its upper level's lifetime?
> $\Gamma \propto \omega^3 d^2$. The hyperfine splitting is $\sim 10^5$ times smaller in frequency than an optical gap, so spontaneous decay is suppressed by $\sim 10^{15}$ from the frequency alone, and the transition is magnetic-dipole, weaker again by roughly $\alpha^2$: lifetimes of thousands of years or more. The optical qubit's upper state decays at whatever its (weak) multipole moment allows.

# Connections

- [[Fermi's Golden Rule]] — the rate formula; the "continuum" here is the vacuum's photon modes
- [[Vacuum Fluctuations]] — what triggers the decay; no fluctuations, no spontaneous emission
- [[Dipole Radiation]] — the classical $\omega^4 p^2$ radiated-power scaling this quantizes into $\Gamma$
- [[Optical Bloch Equations]] — where $\Gamma$ enters the dynamics as damping
- [[Superradiance and Subradiance]] — collective emission: $N$ atoms within a wavelength decay faster or slower than one

---
Source: Foot, *Atomic Physics*, Ch. 7
