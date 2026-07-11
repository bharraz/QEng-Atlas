#quantum-info

**Describe a state not by its amplitudes but by the Pauli operators that fix it** — $n$ commuting generators pin down one $n$-qubit state, turning $2^n$ amplitudes into $\sim 2n^2$ bits.

# Reference

$|\psi\rangle$ is stabilized by $S$ if $S|\psi\rangle = +|\psi\rangle$. Each independent commuting Pauli generator halves the surviving subspace, so **$n$ generators ⇒ unique state**; $n-k$ generators ⇒ a $2^k$-dimensional code space.

$$
|\Phi^+\rangle \;\leftrightarrow\; \langle XX,\; ZZ \rangle, \qquad |0\rangle^{\otimes n} \;\leftrightarrow\; \langle Z_1, \dots, Z_n \rangle
$$

**Dynamics without amplitudes**: a Clifford $U$ updates generators by conjugation, $S \to USU^\dagger$ — still Paulis, still $n$ of them. This is the engine of Gottesman-Knill simulation and of tracking QEC circuits by hand.

**Measurement of a Pauli $P$**, in two cases:
- $P$ commutes with all generators → outcome is deterministic ($\pm 1$ fixed by whether $\pm P$ is in the group); state unchanged.
- $P$ anticommutes with some generator $g$ → outcome is a coin flip; replace $g$ by $(\pm 1)P$, fix up other anticommuting generators by multiplying them with $g$.

**QEC speaks this language natively**: code space = joint $+1$ eigenspace of the stabilizer group; errors flip generator eigenvalues; the syndrome is just the list of signs. Logical operators = Paulis that commute with the stabilizer but aren't in it.

> [!question]- Measure $Z_1$ on $|\Phi^+\rangle = \langle XX, ZZ\rangle$ — walk the update.
> $Z_1$ anticommutes with $XX$, commutes with $ZZ$. Random outcome $\pm 1$; replace $XX$ by $\pm Z_1$. New group $\langle \pm Z_1, ZZ\rangle$ = the product state $|00\rangle$ or $|11\rangle$ — collapse, correlations and all, done in two lines of bookkeeping.

# Connections

- [[Pauli Group]] — the raw material; commute-or-anticommute is what makes updates cheap
- [[Quantum Error Correction]] — syndromes are stabilizer eigenvalues
- [[Clifford Group]] — the gates that preserve the formalism
- [[Bell States]] — two-generator worked example above

---
Source: Gottesman thesis (1997), Ch. 2
