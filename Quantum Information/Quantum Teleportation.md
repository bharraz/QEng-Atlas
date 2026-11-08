#quantum-info

**Consume a shared Bell pair plus two classical bits to move an unknown qubit state — moved, never copied**; the Bell measurement destroys the original as no-cloning demands.

# Reference

Alice holds unknown $|\psi\rangle$ on qubit 1 and half of $|\Phi^+\rangle_{23}$; Bob holds qubit 3. The entire protocol is one identity:

$$
|\psi\rangle_1 |\Phi^+\rangle_{23} = \frac12 \sum_{k=0}^{3} |\beta_k\rangle_{12}\, \big(\sigma_k |\psi\rangle\big)_3
$$

where $|\beta_k\rangle$ are the four Bell states and $\sigma_k \in \{\mathbb{1}, X, Z, XZ\}$. Bob's qubit *already* holds $|\psi\rangle$ up to a Pauli — the Bell measurement tells you which one.

**Picture:** the Bell pair as a pre-shared key: Alice's measurement leaves the state in Bob's qubit up to one of four known Pauli errors, and her two bits tell him which to undo.

**Protocol**: (1) Alice Bell-measures qubits 1–2 (CNOT, $H$, measure). (2) Sends the 2-bit outcome $(a,b)$. (3) Bob applies $Z^a X^b$. Done — $|\psi\rangle$ never traversed the channel, and Alice's copy is gone (collapsed into the Bell basis).

**No FTL**: before the bits arrive, Bob's marginal is $\mathbb{1}/2$ for every input — the correction is not optional decoration, it's where causality lives.

**Resource ledger**: 1 ebit + 2 cbits → 1 qubit transmitted. **Uses that matter**: quantum repeaters (teleport instead of transmitting through loss), and gate teleportation — the method that injects $T$ gates into fault-tolerant circuits.

> [!question]- Alice's measurement outcomes are uniformly random and independent of $|\psi\rangle$. Where did the state go?
> Into correlations: each outcome $k$ steers Bob's qubit to $\sigma_k|\psi\rangle$. Randomness of $k$ is exactly what keeps Bob's unconditioned marginal at $\mathbb{1}/2$ — the state is recoverable only with the classical key.

# Connections

- [[Bell States]] — the fuel, and the measurement basis
- [[No-Cloning Theorem]] — why the original must be destroyed
- [[Projective Measurement and POVMs]] — the Bell measurement doing the work
- [[Magic and Nonstabilizerness]] — gate teleportation turns this protocol into a $T$-gate factory
- [[Mid-Circuit Measurement and Feedforward]] — the measurement and correction steps in hardware
- [[Remote Entanglement and Quantum Networks]] — entanglement swapping over network links

---
Source: Nielsen & Chuang, Ch. 1.3.7
