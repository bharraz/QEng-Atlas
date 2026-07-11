#quantum-info

**Run random Clifford sequences of growing length, invert at the end, and fit the exponential decay of survival — the decay rate is your error per gate, and SPAM errors cancel out of it.** That immunity is the whole point.

# Reference

Protocol: apply $m$ uniformly random Cliffords + the one Clifford that inverts the product (efficient to compute — Gottesman-Knill), measure return probability, average over many random sequences:

$$
F(m) = A\, p^m + B, \qquad r = \frac{(d-1)(1-p)}{d} \;\overset{d=2}{=}\; \frac{1-p}{2}
$$

$r$ = average error per Clifford. **SPAM insensitivity**: preparation and readout errors land in $A$ and $B$; the physics you want is in the *base* $p$ of the exponential, extracted from how survival scales with $m$, not from any absolute value.

**Why a clean exponential at all**: averaging over random Cliffords twirls arbitrary noise into a depolarizing channel (Clifford group is a unitary 2-design) — one decay parameter survives.

**Interleaved RB**: alternate the gate under test with random Cliffords; the ratio of the two decay constants isolates that gate's error.

**Caveats**: assumes Markovian, gate-independent noise. Coherent or low-frequency-correlated errors bend the decay away from a single exponential and can make $r$ optimistic — RB one number, not a noise model; it also says nothing about SPAM itself (see tomography for that).

> [!question]- Your state prep is 5% bad. Why doesn't the extracted error per gate budge?
> Prep error just rescales the amplitude $A$ of $Ap^m + B$ — the same factor at every sequence length. The fit parameter $p$ only measures how survival *changes* with $m$, which only gates touch.

# Connections

- [[Clifford Group]] — supplies both the random sequences and the 2-design twirl
- [[State and Gate Fidelity]] — $r$ is $1 - F_{\text{avg}}$ for the twirled channel
- [[Quantum Process Tomography]] — the opposite tradeoff: full information, SPAM-poisoned, unscalable

---
Source: Preskill, Ph219 lecture notes, Ch. 3 (channels); RB protocol: Magesan et al., PRL 106, 180504 (2011)
