#quantum-info

**Fidelity is the overlap score between what you made and what you meant to make** — for states, a generalized $|\langle\psi|\phi\rangle|^2$; for gates, that overlap averaged over all inputs.

# Reference

$$
F(\rho, \sigma) = \left( \mathrm{Tr}\sqrt{ \sqrt{\rho}\, \sigma \sqrt{\rho} } \right)^2
$$

**Convention landmine**: some authors define $F$ without the outer square — check before comparing numbers. Pure target: $F = \langle\psi|\rho|\psi\rangle$, plain probability of passing the "are you $|\psi\rangle$?" test. Trace-distance sandwich: $1-\sqrt{F} \le D(\rho,\sigma) \le \sqrt{1-F}$.

**Gate fidelity**: compare channel $\mathcal{E}$ to target $U$ averaged over Haar-random inputs. Related to process (entanglement) fidelity $F_{\text{pro}}$ by

$$
F_{\text{avg}} = \frac{d\, F_{\text{pro}} + 1}{d + 1}
$$

($d=2$: $F_{\text{avg}} = (2F_{\text{pro}}+1)/3$ — why "average" and "process" numbers for the same gate differ, another quoting trap).

**Operationally**: $F = 99.9\%$ means error per gate $\epsilon \approx 10^{-3}$, so $\sim 1000$ gates before success $\sim e^{-1}$ — circuit depth budget is $\sim 1/\epsilon$. Average fidelity is the RB observable; the *worst-case* error (diamond norm) can be far larger for coherent errors ($\sqrt\epsilon$ vs $\epsilon$!) — the number that matters for fault-tolerance thresholds.

> [!question]- Two gates both have $F_{\text{avg}} = 99.9\%$: one limited by depolarizing noise, one by a systematic over-rotation. Why is the second worse in a long circuit?
> Incoherent errors add as probabilities ($\propto N\epsilon$); coherent errors add as amplitudes ($\propto (N\theta)^2$) and can dominate — same average fidelity, much larger worst-case (diamond) error. Twirling or RB-style randomization converts the second into the first.

# Connections

- [[Randomized Benchmarking]] — measures $F_{\text{avg}}$ without trusting SPAM
- [[Matrix Norms]] — trace distance and diamond norm, the worst-case cousins
- [[Quantum Process Tomography]] — full characterization when one number isn't enough
- [[Binomial Errors in State Detection]] — the statistics floor under any measured fidelity

---
Source: Nielsen & Chuang, Ch. 9
