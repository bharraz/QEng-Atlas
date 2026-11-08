#quantum-info

**Encode one logical qubit in an entangled state of many, then measure operators that reveal where an error struck without revealing the data** — the syndrome measures relative parities, which commute with the logical information.

# Reference

**Three-qubit repetition code, step by step**: $|\bar 0\rangle = |000\rangle$, $|\bar 1\rangle = |111\rangle$; stabilizers $Z_1Z_2$ and $Z_2Z_3$ (parities, measured via ancillas — never measure the data qubits themselves).

| Error | $Z_1Z_2$ | $Z_2Z_3$ | Fix |
|---|---|---|---|
| none | $+$ | $+$ | — |
| $X_1$ | $-$ | $+$ | $X_1$ |
| $X_2$ | $-$ | $-$ | $X_2$ |
| $X_3$ | $+$ | $-$ | $X_3$ |

Works on any $\alpha|000\rangle + \beta|111\rangle$: both branches give the *same* syndrome, so the superposition survives. This code catches only bit flips — $Z$ errors pass invisibly; protecting both needs concatenation (Shor 9-qubit) or CSS-style codes using the $X$/$Z$ dual bases.

**Picture:** a syndrome is like checking that pairs of copies agree without reading any copy — disagreement locates the faulty one, while the common content stays unread.

**Discretization of errors**: any error, including a tiny coherent over-rotation $e^{-i\epsilon X}$, is a linear combination of Paulis; the syndrome measurement *collapses* it onto a definite Pauli, which the correction then undoes exactly. Continuous noise becomes a discrete, correctable event (Pauli twirling is the same collapse done in software).

**Knill-Laflamme condition** (one line): $\{E_a\}$ correctable iff $P E_a^\dagger E_b P \propto P$ on the code projector — errors must neither distinguish nor deform code words. Distance $d$ corrects $\lfloor (d-1)/2 \rfloor$ arbitrary single-qubit errors.

**Code notation** $[\![n, k, d]\!]$: $n$ physical qubits encode $k$ logical qubits with distance $d$, the smallest number of single-qubit errors that can change the logical state undetected. **Threshold theorem:** if every physical operation fails with probability below a threshold, logical errors can be made arbitrarily small with resources growing only polylogarithmically in the target error.

**Syndrome extraction in hardware.** Each stabilizer is measured by entangling an ancilla with the data qubits it checks and reading the ancilla, every round. Two complications follow:
- the ancilla, the entangling gates, and the readout can fail too, so one faulty ancilla can spread errors to several data qubits; extraction circuits are ordered so such spreading cannot shorten the distance;
- measurements themselves err, so a single round's syndrome cannot be trusted and rounds are repeated, about $d$ of them, before a decision.

**Detection events — what experiments plot.** A detection event is a stabilizer outcome that differs from the same stabilizer's outcome in the previous round. A data-qubit error between rounds creates detection events on neighbouring stabilizers at the same time; a measurement error creates a pair on one stabilizer in consecutive rounds. A decoder — a classical algorithm running alongside the experiment — receives detection events in space and time and infers the most likely errors.

**Decoders:**

| Decoder | Idea | Where it fits |
|---|---|---|
| minimum-weight perfect matching | pair up detection events along the most probable error chains | surface and repetition codes |
| union-find | grow clusters around detection events until they can be neutralized | surface codes when decoding speed matters; accuracy close to matching |
| belief propagation with ordered-statistics post-processing | iterative message passing on the check graph | qLDPC codes |
| tensor-network or maximum-likelihood | sum over all error histories | small codes, when accuracy matters most |
| neural-network decoders | learned from data, including correlated noise | noise with correlations or drift that simple models miss |

A decoder must keep up with the rounds as they arrive; if it falls behind, the backlog grows without bound.

**Codes beyond the surface code:**

| Code | Feature | Price |
|---|---|---|
| repetition code | protects against one error type; tests decoders deep below threshold | no protection against the other type |
| Steane $[\![7,1,3]\!]$ | all Clifford gates transversal | distance 3 only; larger versions need concatenation |
| colour codes | transversal Cliffords in 2D | higher-weight checks |
| quantum LDPC codes (e.g. bivariate bicycle) | many logical qubits per physical qubit | checks need long-range connectivity |
| [[Bosonic Codes]] | redundancy inside one oscillator | one dominant error channel, loss |

**What error-correction experiments report:**

| Quantity | What it tells you |
|---|---|
| detection-event fraction per round | physical error level; drift or bursts show as changes over time |
| logical error per round, from logical fidelity against number of rounds | the code's performance |
| suppression factor $\Lambda = \epsilon_L(d)/\epsilon_L(d+2)$ | below threshold if $\Lambda > 1$: each step up in distance divides the logical error by $\Lambda$ |
| logical lifetime against the best physical qubit | whether encoding beats not encoding ("break-even") |

Decoders assume errors are independent and Pauli. Correlated errors — leakage that persists for many rounds ([[Leakage, Erasure, and Biased Noise]]), crosstalk, bursts that hit many qubits at once — violate this and show as detection events clustered in space or time.

> [!question]- How does the syndrome find the error without collapsing $\alpha|\bar 0\rangle + \beta|\bar 1\rangle$?
> The stabilizers commute with every logical operator, so their eigenvalues carry zero information about $\alpha, \beta$ — measuring them projects in the *error* direction only. You learn "qubit 2 flipped," never "the state was mostly $|\bar 1\rangle$."

# Connections

- [[Stabilizer Formalism]] — the bookkeeping language of syndromes and code spaces
- [[Bosonic Codes]] — encoding in one oscillator instead of many qubits; designed around photon loss
- [[Surface Code]] — the version that hardware builds
- [[Pauli Group]] — errors discretize onto it
- [[Projectors]] — syndrome extraction is projection onto stabilizer eigenspaces
- [[Mid-Circuit Measurement and Feedforward]] — the repeated ancilla readout every round needs
- [[Leakage, Erasure, and Biased Noise]] — error types that break the decoder's assumptions, and those that help it

---
Source: Nielsen & Chuang, Ch. 10; B. M. Terhal, "Quantum error correction for quantum memories," *Rev. Mod. Phys.* 87, 307 (2015)
