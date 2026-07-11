#quantum-info

**The n-qubit Pauli group is all tensor products of $I,X,Y,Z$ with phases $\pm1,\pm i$** — its two superpowers: any two elements either commute or anticommute, and the Paulis form a complete basis for errors.

# Reference

$$
\mathcal{P}_n = \{\, i^k\, P_1\otimes\cdots\otimes P_n \;:\; P_j\in\{I,X,Y,Z\},\; k=0,\dots,3 \,\}
$$

$4^{n+1}$ elements; the phases make it a genuine group ($XY = iZ$ needs the $i$).

**The ± check**: two Pauli strings commute iff they anticommute on an *even* number of tensor slots. Per slot: identical or one is $I$ → commute; two different non-identity Paulis → anticommute. Count odd slots, take parity. This binary (symplectic over $\mathbb{F}_2$) structure is why stabilizer codes reduce to classical linear algebra.

**Weight** = number of non-identity slots. A distance-$d$ code corrects all Paulis of weight $\le \lfloor(d-1)/2\rfloor$.

**Error basis**: the $4^n$ phase-free Paulis span all operators — any error, including a coherent over-rotation, is a linear combination of Paulis. Correct the Paulis and you've corrected everything: the discretization miracle of QEC.

> [!question]- Why does correcting only bit and phase flips handle *arbitrary* single-qubit errors?
> Any error acts as $E = \alpha I + \beta X + \gamma Y + \delta Z$. Syndrome measurement projects the state onto one definite Pauli branch, which recovery then undoes — the measurement discretizes the continuum for you.

# Connections

- [[Pauli Matrices]] — the single-qubit generators and their algebra
- [[Stabilizer Formalism]] — states defined as +1 eigenspaces of commuting Pauli subsets
- [[Clifford Group]] — the unitaries that permute the Pauli group
- [[Quantum Error Correction]] — where the error-basis property pays rent

---
Source: Gottesman, *Stabilizer Codes and Quantum Error Correction*, PhD thesis (1997), Ch. 2
