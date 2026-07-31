#AMO

**An excited atom decays because vacuum fluctuations tickle it: Fermi's golden rule with the vacuum mode density gives $\Gamma$, and that decay stamps a Lorentzian of width $\Gamma/2\pi$ on the transition.** Linewidth and lifetime are the same number.

# Reference

Golden rule + free-space mode density $\rho(\omega) \propto \omega^2$:

$$\Gamma = \frac{\omega_0^3 d^2}{3\pi\varepsilon_0 \hbar c^3}, \qquad \tau = \frac{1}{\Gamma}$$

$\Gamma$ = decay rate (s⁻¹, angular — divide by $2\pi$ for linewidth in Hz); $\omega_0$ = transition frequency (rad/s); $d = \langle e|\hat d|g\rangle$ = transition dipole matrix element (C·m, of order $ea_0$ for a strong optical line); $\tau$ = excited-state lifetime (s). The $\omega_0^3$ comes from the vacuum mode density ($\propto\omega^2$) times the photon energy scaling of the coupling; $d^2$ is the usual coupling-squared of the golden rule.

**The $\omega^3 d^2$ scaling** is the one to remember: strong optical dipole lines decay in ns–tens of ns ($\Gamma/2\pi \sim 10\text{–}30$ MHz — Ca⁺ 397 nm: 21.6 MHz; Yb⁺ 369 nm: 19.6 MHz), while microwave hyperfine transitions, down by $(\omega_{\mathrm{opt}}/\omega_{\mu w})^3 \sim 10^{12}$, effectively never decay — free $T_1$ for hyperfine qubits. Quadrupole clock lines are slow via small $d_{\mathrm{eff}}$ instead: $\tau \sim 1$ s.

**Lineshape:** exponential decay $e^{-\Gamma t/2}$ of the amplitude Fourier-transforms to a Lorentzian in the spectrum:

$$S(\omega) \propto \frac{\Gamma/2\pi}{(\omega - \omega_0)^2 + (\Gamma/2)^2}, \qquad \Delta\nu_{\mathrm{FWHM}} = \frac{\Gamma}{2\pi}$$

— the *natural* linewidth, the floor under all broadening (Doppler, power, magnetic) that you can engineer away.

**Branching ratios:** with several decay channels, $\Gamma = \sum_i \Gamma_i$; each branch's fraction $\Gamma_i/\Gamma$ is set by $\omega_i^3 |d_i|^2$. This is why Ca⁺ $P_{1/2}$ leaks ~7% to $D_{3/2}$ and every cooling scheme drags a repumper along.

> [!question]- Why does a hyperfine qubit have essentially infinite $T_1$ while an optical qubit's is ~1 s at best?
> $\Gamma \propto \omega^3 d^2$. The hyperfine splitting is $\sim 10^5$ times smaller in frequency than an optical gap, so spontaneous decay is suppressed by $\sim 10^{15}$ — lifetime of millennia. The optical qubit's upper state decays at whatever its (weak) multipole moment allows.

# Connections

- [[Fermi's Golden Rule]] — the rate formula; the "continuum" here is the vacuum's photon modes
- [[Vacuum Fluctuations]] — what actually triggers the decay; no fluctuations, no spontaneous emission
- [[Dipole Radiation]] — the classical $\omega^4 p^2$ radiated-power scaling this quantizes into $\Gamma$
- [[Optical Bloch Equations]] — where $\Gamma$ enters the dynamics as damping

---
Source: Foot, *Atomic Physics*, Ch. 7
