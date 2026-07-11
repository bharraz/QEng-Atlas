#quantum-optics

**A photodiode is a square-law detector: it measures $|E|^2$, so photon statistics arrive as photocurrent statistics — and optical phase is invisible until you interfere the field with a reference.** Shot noise is not detector noise; it's the light's own number statistics read out as current.

# Reference

Photocurrent from optical power $P$: $i = \eta e P/\hbar\omega$, where $\eta$ is the quantum efficiency. For Poissonian photon arrivals (coherent light) the current noise is white:

$$
S_I = 2e\langle i\rangle \;\; [\mathrm{A^2/Hz}]
$$

so **signal $\propto P$ but shot noise $\propto \sqrt{P}$ — SNR grows as $\sqrt{P}$.** Practical number: 1 mA of photocurrent has shot noise $\sqrt{2eI} \approx 18\ \mathrm{pA/\sqrt{Hz}}$.

**The Fano factor $F=\langle\Delta n^2\rangle/\langle n\rangle$ carries the quantum character through:** coherent $F=1$ (the shot-noise limit), thermal $F>1$, sub-Poissonian/squeezed $F<1$ — current noise *below* $2e\langle i\rangle$. But loss launders nonclassicality: finite $\eta$ pulls $F \to 1 + \eta(F-1)$, so a 50%-efficient detector sees half the squeezing.

**"Shot-noise-limited detection"** means $2e\langle i\rangle$ dominates the electronic noise of the readout chain ([[Photodiode Circuits]] — Johnson noise of the transimpedance resistor, amplifier $e_n$). More photocurrent helps: shot noise grows as $\sqrt{I}$, electronics don't.

**Square-law consequence:** direct detection gives $|E|^2$ only. Phase and quadrature information require beating against a local oscillator — that's the whole reason [[Homodyne Detection]] exists.

> [!question]- Coherent light of fixed power hits two detectors, one with $\eta=1$ and one with $\eta=0.1$. Which is further above its shot-noise floor?
> Neither — coherent light is Poissonian and Bernoulli sampling of a Poisson process is still Poissonian, so both sit exactly at $S_I = 2e\langle i\rangle$. Efficiency only matters when the light is *non*-Poissonian: $\eta<1$ drags $F$ toward 1.

# Connections

- [[Shot Noise]] — the statistics card; this note is its optical front-end
- [[Photodiode Circuits]] — the electronics that must get out of the way to reach the shot-noise limit
- [[Photon Statistics and g2]] — what $F\ne1$ means and how to certify it
- [[Homodyne Detection]] — the fix for the square-law's phase blindness
- [[Poisson Distribution]] — why $\langle\Delta N^2\rangle = \langle N\rangle$ in the first place

---
Source: Loudon, *The Quantum Theory of Light*, 3rd ed., Ch. 6
