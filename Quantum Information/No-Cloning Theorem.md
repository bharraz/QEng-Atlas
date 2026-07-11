#quantum-info

**No machine can copy an unknown quantum state — linearity alone forbids it.** Cloning would have to act linearly on superpositions, but $|\psi\rangle|\psi\rangle$ is quadratic in $|\psi\rangle$.

# Reference

Claim: no unitary satisfies $U|\psi\rangle|0\rangle = |\psi\rangle|\psi\rangle$ for all $|\psi\rangle$.

> [!question]- Prove it in three lines.
> Suppose $U|\psi\rangle|0\rangle = |\psi\rangle|\psi\rangle$ and $U|\phi\rangle|0\rangle = |\phi\rangle|\phi\rangle$.
> Unitarity preserves inner products: $\langle\phi|\psi\rangle = \langle\phi|\psi\rangle^2$.
> So $\langle\phi|\psi\rangle \in \{0,1\}$ — only *orthogonal* states can share a cloner. Classical copying survives because pointer states are orthogonal.

**Consequences, all load-bearing:**

- **QKD is secure**: an eavesdropper can't copy the qubit and forward the original intact — interception leaves fingerprints.
- **No noiseless quantum amplifier**: amplifying a signal is cloning its state onto more photons; the mandatory added noise is this theorem in gain form.
- **Measurement is destructive**: you can't dodge back-action by copying first and measuring the copy.
- **Teleportation must destroy the original** — otherwise it would be a cloner.

Approximate cloning exists: the optimal universal qubit cloner reaches fidelity $5/6$ — quantum information leaks, it just can't leak perfectly.

# Connections

- [[Quantum Teleportation]] — moves a state precisely because it can't copy one
- [[Postulates of Quantum Mechanics]] — the proof uses only linearity/unitarity of evolution
- [[Projective Measurement and POVMs]] — why "measure the copy" is not an escape hatch

---
Source: Nielsen & Chuang, Ch. 12.1.1 (Box 12.1)
