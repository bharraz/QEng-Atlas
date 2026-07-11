#quantum-info

**Characterize a channel by feeding it a complete basis of input states and running state tomography on every output** — full information about the gate, at a cost that scales even worse than state tomography.

# Reference

A channel on $d$ dimensions is fixed by its action on $d^2$ basis operators. Standard packaging is the **$\chi$ (process) matrix** over a Pauli basis:

$$
\mathcal{E}(\rho) = \sum_{mn} \chi_{mn}\, P_m\, \rho\, P_n^\dagger
$$

$\chi$ is $d^2 \times d^2$, positive semidefinite, with trace preservation constraints: $d^4 - d^2$ real parameters — 12 for one qubit, 240 for two, $\sim 16^n$ growth. Ideal gate = rank-1 $\chi$; off-target weight reads as specific error Paulis.

**Procedure**: prepare $d^2$ linearly independent inputs (e.g. $|0\rangle, |1\rangle, |+\rangle, |+i\rangle$ per qubit), apply the gate, state-tomograph each output, invert linearly, then MLE/constrain to keep $\chi$ CP.

**The catch**: QPT inherits every SPAM error — you characterize prep + gate + readout as a lump, and for good gates the SPAM errors are often *larger* than the gate error you're hunting. Gate set tomography fixes this by fitting SPAM and gates self-consistently, at even more cost.

**RB vs QPT tradeoff**: QPT = full error map, exponential cost, SPAM-limited; RB = one number ($F_{\text{avg}}$), scalable, SPAM-free. Debugging a bad two-qubit gate → QPT/GST; tracking calibration → RB.

> [!question]- Your RB says 99.8% but QPT says 99.0% for the same gate. Which is lying?
> Probably neither — QPT lumps SPAM into the gate estimate (biasing error upward), while RB reports the average over the twirled channel and can understate coherent errors. The gap itself is diagnostic: large SPAM or coherent error present.

# Connections

- [[Quantum State Tomography]] — the subroutine run on every output state
- [[Quantum Channels]] — $\chi$ is one parametrization of a CPTP map
- [[Randomized Benchmarking]] — the scalable, SPAM-free alternative
- [[Kraus Operators]] — diagonalizing $\chi$ hands you a Kraus set

---
Source: Nielsen & Chuang, Ch. 8.4.2
