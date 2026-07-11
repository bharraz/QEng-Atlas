#quantum-info

**Projective measurement is the textbook case; POVMs are what detectors actually do** — the most general statistics quantum mechanics allows, obtained by dropping the requirement that outcomes be orthogonal projectors.

# Reference

**Projective**: observable $A = \sum_m a_m P_m$; $p_m = \mathrm{Tr}(P_m \rho)$, post-state $P_m \rho P_m / p_m$. Repeatable — measure twice, same answer. At most $d$ outcomes in $d$ dimensions.

**POVM**: any set $\{E_m\}$ with $E_m \ge 0$, $\sum_m E_m = \mathbb{1}$;

$$
p_m = \mathrm{Tr}(E_m \rho)
$$

No orthogonality, no repeatability, any number of outcomes. The POVM fixes only the *statistics*; the post-measurement state needs the finer-grained Kraus decomposition $E_m = K_m^\dagger K_m$.

**Why the extra generality earns its keep**: discriminating nonorthogonal states. Unambiguous discrimination of $|0\rangle$ vs $|+\rangle$ needs three outcomes on one qubit — "definitely 0", "definitely +", "don't know" — impossible projectively. Real readout (finite fidelity, dark counts, photon loss) is also a POVM, not a projector.

**Naimark dilation**: every POVM is a projective measurement on system + ancilla — generalized measurement isn't new physics, just projective measurement with the ancilla swept under the rug.

**Weak measurement** (one line): $E_m \approx \tfrac{1}{d}(\mathbb{1} + \epsilon\, \sigma)$ — little information, little back-action; continuous monitoring is a stream of these.

> [!question]- Why can no projective measurement implement the 3-outcome "trine" POVM on a qubit?
> Projectors on a qubit come in orthogonal pairs — at most 2 outcomes. Three positive operators summing to $\mathbb{1}$ can't all be rank-1 projectors in $d=2$; you need the Naimark ancilla to make room.

# Connections

- [[Postulates of Quantum Mechanics]] — the projective postulate this generalizes
- [[Projectors]] — the special case, and the Naimark endpoint
- [[Kraus Operators]] — post-measurement states and the channel-measurement unification
- [[Quantum State Tomography]] — informationally complete POVMs are its input

---
Source: Nielsen & Chuang, Ch. 2.2.3–2.2.6
