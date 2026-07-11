#quantum-info

**The four algorithms worth keeping loaded: one interference demo, one optimal search, one exponential-speedup factoring engine, one NISQ workhorse** — each built from a different primitive.

# Reference

| Algorithm | Claimed speedup | Primitive |
|---|---|---|
| Deutsch-Jozsa | exponential (vs deterministic classical) | phase kickback + interference |
| Grover | $\sqrt{N}$, provably optimal | amplitude amplification |
| Shor | superpolynomial (vs best known) | period finding via QPE/QFT |
| VQE | heuristic, none proven | variational principle |

**Deutsch-Jozsa**: is $f$ constant or balanced? One query vs classical $2^{n-1}+1$ deterministic. Phase oracle + Hadamards: all-$|0\rangle$ outcome iff constant. Contrived (classical randomized is easy), but it's *the* demo that interference reads out a global property of $f$ no single evaluation contains.

**Grover**: unstructured search among $N$ items in $\sim \frac{\pi}{4}\sqrt{N}$ oracle calls. Geometry: state lives in the 2D span of {target, uniform}; each iteration (phase-flip target, invert about mean) rotates by $2\theta$, $\sin\theta = 1/\sqrt{N}$. **Overshoot gotcha**: it keeps rotating — iterate past the optimum and success probability *falls*. Quadratic is all you get, and it's optimal.

**Shor**: factor $N$ via the period $r$ of $a^x \bmod N$. Quantum part = QPE on the modular-multiplication unitary; measurement samples multiples of $1/r$; classical continued fractions extract $r$, then $\gcd(a^{r/2}\pm 1, N)$ yields factors. Needs fault tolerance — thousands of logical qubits.

**VQE**: hybrid loop — parametrized ansatz circuit, measure $\langle H\rangle$ term-by-term as Pauli expectations, classical optimizer updates parameters. Rayleigh-quotient minimization with a quantum trial state. Shallow-circuit friendly; the catches are barren plateaus and brutal measurement-shot counts.

> [!question]- Why does running Grover for too many iterations hurt?
> The iterate is a rotation, not a projector: amplitude on the target is $\sin((2k+1)\theta)$, which peaks near $k = \frac{\pi}{4}\sqrt{N}$ and then decreases. You must *count* iterations — the algorithm doesn't converge, it swings.

# Connections

- [[Quantum Phase Estimation]] — Shor's quantum core
- [[Quantum Fourier Transform]] — the sampling step behind period finding
- [[Phase Kickback]] — the oracle mechanism in DJ and Grover
- [[Rayleigh Quotient and Variational Principle]] — what VQE is actually minimizing

---
Source: Nielsen & Chuang, Ch. 5–6
