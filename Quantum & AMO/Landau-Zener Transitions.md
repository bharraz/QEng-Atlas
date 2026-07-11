#quantum

**Sweep a two-level system through its avoided crossing and the jump probability is a clean exponential in (gap²/speed) — slow sweeps follow the curve adiabatically, fast sweeps punch straight through.** The exactly-solvable benchmark for every "how slow is slow enough" question.

# Reference

Linear sweep of the bare splitting, $H = \frac{1}{2}\begin{pmatrix}\alpha t & \hbar\Omega\\ \hbar\Omega & -\alpha t\end{pmatrix}$, with gap $\hbar\Omega$ at the crossing and sweep rate $\alpha = d(E_1 - E_2)/dt$. Probability of a **diabatic jump** (staying in the bare state, hopping between adiabatic curves):

$$
P_{LZ} = \exp\!\left(-\frac{\pi\,\hbar\,\Omega^2}{2\,\alpha}\right)
$$

(One form among equivalent conventions — check the factor when comparing papers; here $\hbar\Omega$ = full minimum gap.)

| Regime | $\hbar\Omega^2/\alpha$ | Outcome |
|---|---|---|
| Fast (diabatic) | $\ll 1$ | $P_{LZ} \to 1$: sails through, no transfer between adiabatic states |
| Slow (adiabatic) | $\gg 1$ | $P_{LZ} \to 0$: follows the avoided crossing, population transferred |

The exponential is brutal in both directions: a modest change in gap (enters **squared**) or speed moves you decades in jump probability. Intermediate sweeps create coherent superpositions of the two outcomes — sweep back and forth and the amplitudes interfere (Landau-Zener-Stückelberg interferometry, a spectroscopy tool in its own right).

Where you meet it: RAP pulse design (choose $\alpha \ll \Omega^2$), qubit transport across level crossings, molecular curve crossings, and diagnosing unwanted population loss when a frequency ramp crosses a spectator resonance too slowly to ignore, too fast to follow.

> [!question]- You double your sweep speed through a crossing and transfer efficiency barely changes; you double it again and transfer collapses. Why the cliff?
> $P_{LZ} = e^{-\pi\hbar\Omega^2/2\alpha}$ is flat while the exponent is $\gg 1$ (deep adiabatic) and then turns over sharply once $\alpha \sim \Omega^2$ — the exponential has a knee, not a slope. Adiabaticity fails suddenly, not gracefully.

# Connections

- [[Adiabatic Theorem]] — the general criterion this makes exact for one solvable case
- [[Two-Level Systems]] — the avoided crossing being swept
- [[Dressed States]] — the adiabatic curves you either follow or jump between

---
Source: Zener, *Proc. R. Soc. A* **137**, 696 (1932); modern review: Shevchenko et al., *Phys. Rep.* **492**, 1 (2010)
