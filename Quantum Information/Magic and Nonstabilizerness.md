#quantum-info

**Cliffords and stabilizer states are classically simulable, so quantum advantage must live in what's left over — "magic," the nonstabilizer resource carried by $T$ gates and magic states.** Entanglement alone is not enough — Clifford circuits create maximal entanglement and remain classically simulable — and magic supplies what is missing.

# Reference

**Magic state**: $|T\rangle = \frac{|0\rangle + e^{i\pi/4}|1\rangle}{\sqrt2}$. Consuming one via gate teleportation — a Clifford circuit plus measurement and Pauli fix-up — executes a $T$ gate. So a fault-tolerant computer needs only (i) Clifford operations and (ii) a supply of $|T\rangle$ states: all the non-Clifford difficulty is pushed into *state preparation*, offline.

**Picture:** Clifford operations move states around inside the polytope of stabilizer mixtures; magic measures how far a state sits outside it, and non-Clifford gates are the only way out.

**Why bother**: codes like the surface code have cheap (transversal / lattice-surgery) Cliffords but no transversal $T$ — Eastin-Knill forbids a universal transversal set. Injection + distillation is the workaround.

**Magic state distillation**: Clifford-only circuits turn many noisy $|T\rangle$'s into fewer, better ones — the 15-to-1 protocol maps error $p \to 35p^3$. Iterate to any fidelity; this factory dominates fault-tolerant resource estimates.

**CCZ states.** For arithmetic-heavy algorithms, factories make $|\mathrm{CCZ}\rangle = \mathrm{CCZ}\,|{+}{+}{+}\rangle$ instead of $|T\rangle$; one CCZ state executes a Toffoli by teleportation in place of several $T$ states, which is why resource estimates are often quoted as a Toffoli or CCZ count ([[Universal Gate Sets]]).

**Resource-theory framing**: free operations = stabilizer ops (Cliffords, Pauli measurements, stabilizer ancillas); free states = the stabilizer polytope; magic monotones (robustness of magic, stabilizer rank) quantify distance from free. Cash value: classical simulation cost scales exponentially in the *$T$-count*, not qubit count — $\sim 2^{0.5 t}$-ish via stabilizer-rank methods. A circuit with 40 $T$ gates is simulable; 100 is not.

> [!question]- Why implement $T$ by teleporting a pre-made state instead of applying $T$ directly?
> In an error-correcting code, a direct physical $T$ isn't fault-tolerant (no transversal implementation exists — Eastin-Knill). Teleportation needs only Cliffords + measurement at runtime, and the hard non-Clifford part becomes a *state* that can be distilled and verified offline before you bet your computation on it.

# Connections

- [[Clifford Group]] — the free operations whose simulability defines the boundary
- [[Universal Gate Sets]] — magic is exactly what upgrades Clifford to universal
- [[Quantum Teleportation]] — the injection mechanism
- [[Stabilizer Formalism]] — free states are its states; magic is what it can't express

---
Source: Preskill, Ph219 lecture notes, fault-tolerance chapter (magic state distillation)
