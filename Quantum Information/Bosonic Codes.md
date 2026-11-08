#quantum-info #quantum-optics

**Encode a qubit inside one oscillator's infinite Hilbert space rather than across many two-level systems — the redundancy lives in a single mode, and the code is designed around photon loss because that is the error an oscillator has.**

# Reference

**The hardware-efficiency argument.** A qubit-based code needs many physical qubits, each with its own control lines and its own error channels. An oscillator supplies unlimited Hilbert space in *one* mode with *one* dominant error channel — so you can build in redundancy without multiplying the hardware.

**Picture:** one oscillator's ladder of levels as the redundancy: code words are spread out so that losing one photon moves the state into a recognizable error space instead of onto another code word.

**The error to design against** is photon loss, $\hat a$, from the [[Lindblad Master Equation|Lindblad]] term $\mathcal D[\hat a]$. Also present but usually subdominant: dephasing $\hat a^\dagger\hat a$, and heating $\hat a^\dagger$. A bosonic code is a choice of two states in the oscillator such that loss maps them to a *detectable and reversible* place.

| Family | Logical states built from | Syndrome | Corrects |
|---|---|---|---|
| **Cat** | coherent states $\lvert\pm\alpha\rangle$ | photon-number **parity** | loss (detected), with biased noise |
| **Binomial** | finite Fock superpositions with binomial weights | photon number mod $(L{+}1)$ | up to $L$ losses, exactly, in finite dimension |
| **GKP** | grid of position eigenstates | quadratures **mod $\sqrt\pi$** | small displacements in *both* quadratures |

## Cat codes

Take the even and odd superpositions $\lvert\mathcal C^\pm_\alpha\rangle \propto \lvert\alpha\rangle \pm \lvert{-\alpha}\rangle$. These are eigenstates of the **parity operator** $\hat\Pi = e^{i\pi\hat a^\dagger\hat a}$ with eigenvalue $\pm1$.

- **Loss flips parity**: $\hat a\lvert\mathcal C^+\rangle \propto \lvert\mathcal C^-\rangle$. Parity is therefore the error syndrome — and it is measurable **QND** by dispersively coupling to an ancilla qubit, which is exactly the readout a transmon already provides ([[Superconducting Qubits]]).
- Two-legged cats give **biased noise**: bit flips are exponentially suppressed in $\lvert\alpha\rvert^2$ while phase flips are not. A biased-noise qubit is cheaper to protect — the outer code only has to handle one error type.
- Four-legged cats (superpositions of four coherent states) upgrade this to full loss correction, at the cost of a larger mean photon number.
- Cats are the canonical non-Gaussian state, and their [[Wigner Function]] interference fringes are the direct signature of coherence rather than a mixture.

## GKP codes

Gottesman–Kitaev–Preskill states are superpositions of position eigenstates on a lattice — a comb in $\hat q$ that is *also* a comb in $\hat p$. The stabilizers are large displacements:

$$\hat S_q = e^{i2\sqrt\pi\,\hat q}, \qquad \hat S_p = e^{-i2\sqrt\pi\,\hat p}$$

with logical operators the half-lattice displacements $\bar Z = e^{i\sqrt\pi\hat q}$, $\bar X = e^{-i\sqrt\pi\hat p}$.

- **The syndrome is modular.** Measuring $\hat q \bmod \sqrt\pi$ and $\hat p \bmod \sqrt\pi$ reveals a small shift without revealing the logical state, so any displacement smaller than $\sqrt\pi/2$ is diagnosed and undone. GKP corrects **small errors in both quadratures**, which no qubit code does.
- Loss is approximately a small displacement plus damping, so GKP corrects it too, indirectly.
- **Ideal GKP states are unphysical** — infinitely squeezed, infinite energy. Real ones are finitely squeezed, and the squeezing (in dB) is the code's quality parameter; below roughly 10 dB the code stops helping.
- **GKP is the non-Gaussian resource that makes continuous-variable computing universal.** Gaussian operations alone are efficiently simulable ([[Symplectic Group]]); Gaussian operations *plus* GKP states are universal and fault-tolerant, which is why GKP sits at the centre of CV architectures ([[Photonic Quantum Computing]]).
- **Concatenation** is the standard plan: GKP as the inner code turning an oscillator into a decent qubit, then a [[Surface Code]] outer layer over many such qubits. The GKP syndrome is analog, so it hands the outer decoder a confidence value rather than a bit — extra information that measurably improves the threshold.

## Where they are realized

| Platform | The oscillator is | Note |
|---|---|---|
| Superconducting | a 3D or planar microwave cavity | transmon as the ancilla for parity measurement; cat and binomial codes originate here |
| **Trapped ions** | a **motional mode** | GKP states prepared in the ion's motion, with the internal state as ancilla — the same $\hat x,\hat p$ you already control ([[Normal Modes of Ion Chains]], [[Displacement Operator]]) |
| Photonics | a propagating mode | GKP for CV cluster states; generation is the hard part |

The trapped-ion row is worth noting: the motional mode you cool and displace for gates is a bosonic mode, and the operations a bosonic code needs — displacements, squeezing, spin-dependent forces — are the [[Molmer-Sorensen Gate]] toolkit.

**The common structure:** all three families work by making the error take you to a state *orthogonal* to the code space, so the syndrome measurement learns that an error occurred without learning the logical state. That is the same principle as any stabilizer code ([[Stabilizer Formalism]]); only the group being stabilized is a group of displacements or a parity, rather than Paulis on qubits.

> [!question]- Why is photon loss the design target rather than a generic "bit flip"?
> Because it is the error an oscillator suffers — $\mathcal D[\hat a]$ dominates the Lindbladian for a cavity or a motional mode. Codes are designed against the physical noise channel, not an abstract one: cat codes use parity because loss flips parity, and GKP uses modular quadratures because loss looks like a small displacement. Importing a qubit code would protect against errors that do not occur while ignoring the one that does.

# Connections

- [[Coherent States]] / [[Fock States]] / [[Squeezed States]] — the ingredients the code words are built from
- [[Wigner Function]] — how these states are visualized and verified; negativity as non-classicality
- [[Displacement Operator]] — the operations GKP stabilizers and logicals are made of
- [[Stabilizer Formalism]] — the same principle, with displacements in place of Paulis
- [[Surface Code]] — the usual outer layer; analog GKP syndromes improve its decoding
- [[Symplectic Group]] — why Gaussian operations alone are not enough
- [[Photonic Quantum Computing]] — GKP as the enabling non-Gaussian resource for CV
- [[Superconducting Qubits]] — dispersive ancilla coupling, the parity-measurement tool
- [[Lindblad Master Equation]] — where $\mathcal D[\hat a]$ comes from
- [[Quantum Error Correction (Atlas)]] — the general framework this specializes
- [[Leakage, Erasure, and Biased Noise]] — biased noise in cat qubits and why it is cheaper to correct
- [[Controlling Bosonic Modes]] — the operations that prepare and manipulate code words

---
Source: Terhal, Conrad & Vuillot, "Towards scalable bosonic quantum error correction," *Quantum Sci. Technol.* 5, 043001 (2020); Gottesman, Kitaev & Preskill, *Phys. Rev. A* 64, 012310 (2001)
