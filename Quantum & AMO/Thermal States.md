#quantum

**The maximum-ignorance state of an oscillator at temperature T: diagonal in the Fock basis with geometric (Bose-Einstein) populations, no coherences, no phase.** What you have before cooling, and what heating drags you back toward.

# Reference

$$
\rho_{th} = \sum_n \frac{\bar n^n}{(\bar n + 1)^{n+1}}\,|n\rangle\langle n|, \qquad \bar n = \frac{1}{e^{\hbar\omega/k_BT} - 1}
$$

**The crossover is $\hbar\omega$ vs $k_BT$:**

| Regime | $\bar n$ | Feel |
|---|---|---|
| $k_BT \gg \hbar\omega$ | $\approx k_BT/\hbar\omega \gg 1$ | classical equipartition |
| $k_BT \ll \hbar\omega$ | $\approx e^{-\hbar\omega/k_BT} \to 0$ | frozen out, effectively vacuum |

Numbers: 1 MHz trap mode at 300 K → $\bar n \sim 6\times10^6$; same mode Doppler-cooled to 0.5 mK → $\bar n \sim 10$; optical mode at 300 K → $\bar n \sim 10^{-25}$ (why optics starts in vacuum for free but motion must be cooled).

**Statistics — super-Poissonian:** $P(n)$ geometric (monotonically decreasing — most probable $n$ is 0 even for huge $\bar n$!),
$$
\Delta n^2 = \bar n^2 + \bar n, \qquad g^{(2)}(0) = 2
$$
The $\bar n^2$ excess is thermal bunching. Phase-space picture: a Gaussian centered at the origin, $\bar n + \tfrac12$ times the vacuum area — like a coherent state's blob but bloated and centered, with zero mean amplitude.

Practical: thermal motion smears Rabi rates through the $n$-dependence of sideband couplings — the decay of carrier/sideband flopping contrast is a thermometer, and red/blue sideband asymmetry gives $\bar n$ directly.

> [!question]- For a thermal state with $\bar n = 20$, what is the most probable Fock state, and why isn't it $n \approx 20$?
> $n = 0$. The distribution is geometric, $P(n) \propto (\bar n/(\bar n+1))^n$ — strictly decreasing. The *mean* is 20 because of the long tail, but each successive rung is less occupied than the last; a thermal state is mostly "sometimes very excited," not "steadily excited."

# Connections

- [[Fock States]] — the basis this ρ is diagonal in
- [[Density Matrix]] — thermal state as the canonical mixed state $e^{-H/k_BT}/Z$
- [[Photon Statistics and g2]] — $g^{(2)}(0)=2$ bunching benchmark
- [[Resolved Sideband Cooling]] — how $\bar n$ gets driven below 1, and measured
- [[Poisson Distribution]] — the coherent-state contrast: variance $\bar n$ vs $\bar n^2 + \bar n$

---
Source: Gerry & Knight, *Introductory Quantum Optics*, §2.5
