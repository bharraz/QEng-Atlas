#quantum-info

**Prepare a state or run a gate, and what comes out differs from what was intended; fidelity scores the overlap — for a pure target, the probability that the prepared state passes the test "is it the target?", and for a gate, that probability averaged over all inputs.**

# Reference

$$
F(\rho, \sigma) = \left( \mathrm{Tr}\sqrt{ \sqrt{\rho}\, \sigma \sqrt{\rho} } \right)^2
$$

- $\rho$ — the state that was prepared (density matrix)
- $\sigma$ — the intended state (density matrix)

**Convention conflict**: some authors define $F$ without the outer square — check before comparing numbers. For two pure states it reduces to $|\langle\psi|\phi\rangle|^2$. Pure target: $F = \langle\psi|\rho|\psi\rangle$, plain probability of passing the "are you $|\psi\rangle$?" test. Trace-distance sandwich: $1-\sqrt{F} \le D(\rho,\sigma) \le \sqrt{1-F}$.

**Picture:** fidelity is the pass rate of a test that only the target passes with certainty.

**Gate fidelity**: compare channel $\mathcal{E}$ to target $U$ averaged over Haar-random inputs. Related to process (entanglement) fidelity $F_{\text{pro}}$ by

$$
F_{\text{avg}} = \frac{d\, F_{\text{pro}} + 1}{d + 1}
$$

- $F_{\text{avg}}$ — fidelity averaged over all pure input states
- $F_{\text{pro}}$ — overlap of the channel's Choi state with the ideal one ([[Quantum Channels]])
- $d$ — Hilbert-space dimension: $2^n$ for $n$ qubits

($d=2$: $F_{\text{avg}} = (2F_{\text{pro}}+1)/3$ — why "average" and "process" numbers for the same gate differ, another quoting trap.)

**Operationally**: $F = 99.9\%$ means error per gate $\epsilon \approx 10^{-3}$, so $\sim 1000$ gates before success $\sim e^{-1}$ — circuit depth budget is $\sim 1/\epsilon$. Average fidelity is the RB observable; the *worst-case* error (diamond norm) can be far larger for coherent errors ($\sqrt\epsilon$ vs $\epsilon$) — the number that matters for fault-tolerance thresholds.

**Bell-state fidelity from populations and parity oscillations** — how most two-qubit gate experiments report entangled-state quality. For the target $(|00\rangle + |11\rangle)/\sqrt2$,

$$
F = \tfrac12\left(P_{00} + P_{11}\right) + \tfrac12 A
$$

- $P_{00}, P_{11}$ — measured probabilities of $\lvert 00\rangle$ and $\lvert 11\rangle$
- $A$ — amplitude of the parity oscillation: twice the coherence $\lvert\rho_{00,11}\rvert$

The populations come from measuring both qubits directly. The coherence comes from rotating both qubits by $\pi/2$ about an axis at phase $\varphi$ and measuring the parity $P_{00}+P_{11}-P_{01}-P_{10}$, which oscillates as $A\cos(2\varphi + \varphi_0)$. The oscillation at *twice* the analysis phase is the signature of a two-qubit coherence: a mixture of $|00\rangle$ and $|11\rangle$ gives no oscillation at all, and an $N$-qubit GHZ state oscillates at $N\varphi$.

**Raw vs corrected numbers:** readout errors lower measured populations and parity amplitude, so papers often quote both a raw fidelity and one corrected for state-preparation and measurement (SPAM) errors; the corrected value is the gate's, the raw value what the experiment delivered.

| Quantity | Measures | Use |
|---|---|---|
| state fidelity | overlap with a target state | quality of a prepared state |
| trace distance $D$ | sets the best single-shot probability of telling two states apart, $\tfrac12(1+D)$ | worst-case statements about states |
| average gate fidelity | input-averaged overlap | what RB reports |
| process fidelity | overlap of Choi states | what process tomography reports |
| diamond distance | worst-case distinguishability of two channels, with ancillas allowed | the quantity fault-tolerance proofs need |

> [!question]- Two gates both have $F_{\text{avg}} = 99.9\%$: one limited by depolarizing noise, one by a systematic over-rotation. Why is the second worse in a long circuit?
> Incoherent errors add as probabilities ($\propto N\epsilon$); coherent errors add as amplitudes ($\propto (N\theta)^2$) and can dominate — same average fidelity, much larger worst-case (diamond) error. Twirling or RB-style randomization converts the second into the first.

# Connections

- [[Randomized Benchmarking]] — measures $F_{\text{avg}}$ without trusting SPAM
- [[Matrix Norms]] — trace distance and diamond norm, the worst-case counterparts
- [[Quantum Process Tomography]] — full characterization when one number isn't enough
- [[Binomial Errors in State Detection]] — the statistics floor under any measured fidelity
- [[Bell States]] — the states whose fidelity parity oscillations measure
- [[Quantum Channels]] — Choi states and the diamond norm
- [[Benchmarking and Characterization]] — the other numbers papers report

---
Source: Nielsen & Chuang, Ch. 9; C. A. Sackett et al., "Experimental entanglement of four particles," *Nature* 404, 256 (2000)
