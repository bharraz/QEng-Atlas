#quantum-info

**A quantum channel is the most general physical evolution of a density matrix: a completely positive, trace-preserving (CPTP) linear map** — unitaries, noise, and measurement-and-forget are all special cases.

# Reference

$\mathcal{E}(\rho)$ must be linear, trace-preserving, and **completely** positive: $(\mathcal{E}\otimes\mathbb{1})$ positive on any enlarged system. Plain positivity isn't enough because your system may be entangled with a bystander — transpose is positive but $(\mathrm{T}\otimes\mathbb{1})$ on half a Bell state goes negative (which is precisely why partial transpose works as an entanglement *test*).

Every channel has a Kraus form $\mathcal{E}(\rho) = \sum_k K_k \rho K_k^\dagger$, $\sum_k K_k^\dagger K_k = \mathbb{1}$.

**The standard qubit noise zoo:**

| Channel | Kraus operators | What it does |
|---|---|---|
| Depolarizing | $\sqrt{1-\tfrac{3p}{4}}\,\mathbb{1},\ \sqrt{\tfrac{p}{4}}\,\sigma_{x,y,z}$ | shrinks Bloch vector isotropically |
| Dephasing | $\sqrt{1-p}\,\mathbb{1},\ \sqrt{p}\,Z$ | kills off-diagonals, $z$ untouched |
| Amplitude damping | $\begin{pmatrix}1&0\\0&\sqrt{1-\gamma}\end{pmatrix},\ \begin{pmatrix}0&\sqrt{\gamma}\\0&0\end{pmatrix}$ | decay toward $|0\rangle$ ($T_1$) |

Continuous-time noise integrates to a channel: $\mathcal{E}_t = e^{\mathcal{L}t}$ with $\mathcal{L}$ a Lindblad generator. Depolarizing is the "averaged" noise every RB twirl produces.

> [!question]- Why demand *complete* positivity rather than just positivity?
> Apply the map to half an entangled pair: a merely-positive map like transpose sends $|\Phi^+\rangle\langle\Phi^+|$ to an operator with eigenvalue $-\tfrac12$. Physics must stay positive even when the map acts on part of a larger state — and your qubit is never guaranteed to be unentangled.

# Connections

- [[Kraus Operators]] — the representation theorem and where it comes from
- [[Lindblad Master Equation]] — the differential generator of these maps
- [[Density Matrix]] — the object channels act on
- [[Positive Semidefinite Matrices]] — the cone all of this must preserve

---
Source: Nielsen & Chuang, Ch. 8.2–8.3
