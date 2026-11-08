#quantum-info

**Send each of a complete set of input states through a gate and reconstruct each output by state tomography: because a channel is linear, its action on that set fixes it entirely.** The price is a cost that grows as $16^n$ for $n$ qubits, with every state-preparation and measurement error folded into the answer.

# Reference

A channel on $d$ dimensions is fixed by its action on $d^2$ basis operators. Standard packaging is the **$\chi$ (process) matrix** over a Pauli basis:

$$
\mathcal{E}(\rho) = \sum_{mn} \chi_{mn}\, P_m\, \rho\, P_n^\dagger
$$

- $P_m$ — Pauli strings on the qubits ($d^2$ of them)
- $\chi_{mn}$ — process-matrix elements: how the channel mixes Paulis
- $d$ — Hilbert-space dimension, $2^n$

$\chi$ is $d^2 \times d^2$, positive semidefinite, with trace preservation constraints: $d^4 - d^2$ real parameters — 12 for one qubit, 240 for two, $\sim 16^n$ growth. Ideal gate = rank-1 $\chi$; off-target weight reads as specific error Paulis. The Pauli transfer matrix carries the same information in a real-valued form ([[Quantum Channels]]).

**Picture:** process tomography is state tomography of the gate's Choi state — the output when the input is half of an entangled pair.

**Procedure**: prepare $d^2$ linearly independent inputs (e.g. $|0\rangle, |1\rangle, |+\rangle, |+i\rangle$ per qubit), apply the gate, state-tomograph each output, invert linearly, then MLE/constrain to keep $\chi$ CP.

**Reading a $\chi$ matrix** (usually shown as a 3D bar plot after transforming to the error frame, where the ideal gate is the identity):

| Feature | Meaning |
|---|---|
| diagonal elements away from the identity | probabilities of Pauli errors after twirling: incoherent error |
| off-diagonal elements | coherent errors — a systematic rotation shows as coherence between identity and one Pauli |
| total weight outside the identity element | $1 - F_\text{pro}$, the process infidelity ([[State and Gate Fidelity]]) |

**The limitation**: QPT inherits every SPAM error — you characterize prep + gate + readout as a lump, and for good gates the SPAM errors are often *larger* than the gate error being measured. Gate set tomography fixes this by fitting SPAM and gates self-consistently, at even more cost ([[Benchmarking and Characterization]]).

**RB vs QPT tradeoff**: QPT = full error map, exponential cost, SPAM-limited; RB = one number ($F_{\text{avg}}$), scalable, SPAM-free. Debugging a bad two-qubit gate → QPT/GST; tracking calibration → RB.

> [!question]- Your RB says 99.8% but QPT says 99.0% for the same gate. Which is wrong?
> Probably neither — QPT lumps SPAM into the gate estimate (biasing error upward), while RB reports the average over the twirled channel and can understate coherent errors. The gap itself is diagnostic: large SPAM or coherent error present.

# Connections

- [[Quantum State Tomography (Atlas)]] — the subroutine run on every output state
- [[Quantum Channels]] — $\chi$ is one parametrization of a CPTP map
- [[Randomized Benchmarking]] — the scalable, SPAM-free alternative
- [[Kraus Operators]] — diagonalizing $\chi$ hands you a Kraus set
- [[Benchmarking and Characterization]] — gate set tomography and scalable alternatives

---
Source: Nielsen & Chuang, Ch. 8.4.2
