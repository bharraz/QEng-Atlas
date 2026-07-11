#quantum-info

**Encode one logical qubit in an entangled state of many, then measure operators that reveal where an error struck without revealing the data** — the syndrome measures relative parities, which commute with the logical information.

# Reference

**Three-qubit repetition code, walked**: $|\bar 0\rangle = |000\rangle$, $|\bar 1\rangle = |111\rangle$; stabilizers $Z_1Z_2$ and $Z_2Z_3$ (parities, measured via ancillas — never measure the data qubits themselves).

| Error | $Z_1Z_2$ | $Z_2Z_3$ | Fix |
|---|---|---|---|
| none | $+$ | $+$ | — |
| $X_1$ | $-$ | $+$ | $X_1$ |
| $X_2$ | $-$ | $-$ | $X_2$ |
| $X_3$ | $+$ | $-$ | $X_3$ |

Works on any $\alpha|000\rangle + \beta|111\rangle$: both branches give the *same* syndrome, so the superposition survives. This code catches only bit flips — $Z$ errors pass invisibly; protecting both needs concatenation (Shor 9-qubit) or CSS-style codes using the $X$/$Z$ dual bases.

**Discretization of errors — the miracle clause**: any error, including a tiny coherent over-rotation $e^{-i\epsilon X}$, is a linear combination of Paulis; the syndrome measurement *collapses* it onto a definite Pauli, which the correction then undoes exactly. Continuous noise becomes a discrete, correctable event (Pauli twirling is the same collapse done in software).

**Knill-Laflamme condition** (one line): $\{E_a\}$ correctable iff $P E_a^\dagger E_b P \propto P$ on the code projector — errors must neither distinguish nor deform code words. Distance $d$ corrects $\lfloor (d-1)/2 \rfloor$ arbitrary single-qubit errors.

> [!question]- How does the syndrome find the error without collapsing $\alpha|\bar 0\rangle + \beta|\bar 1\rangle$?
> The stabilizers commute with every logical operator, so their eigenvalues carry zero information about $\alpha, \beta$ — measuring them projects in the *error* direction only. You learn "qubit 2 flipped," never "the state was mostly $|\bar 1\rangle$."

# Connections

- [[Stabilizer Formalism]] — the bookkeeping language of syndromes and code spaces
- [[Surface Code]] — the version that hardware actually builds
- [[Pauli Group]] — errors discretize onto it
- [[Projectors]] — syndrome extraction is projection onto stabilizer eigenspaces

---
Source: Nielsen & Chuang, Ch. 10
