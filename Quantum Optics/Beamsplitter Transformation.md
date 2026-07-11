#quantum-optics

**A beamsplitter is a two-mode unitary — it mixes mode operators, it never splits photons.** Both ports are always in play: an "unused" input port injects vacuum, and forgetting that gets every noise budget wrong.

# Reference

50:50 convention (the $i$ on reflection keeps it unitary; conventions vary — pick one and stay consistent):

$$
a_{\text{out}} = \frac{a + i b}{\sqrt 2}, \qquad b_{\text{out}} = \frac{i a + b}{\sqrt 2}
$$

**Single photon in one port:**
$$
|1,0\rangle \;\to\; \frac{1}{\sqrt 2}\left(|1,0\rangle + i\,|0,1\rangle\right)
$$
— a superposition over output ports, NOT half a photon in each. Two detectors never click simultaneously; that's exactly how you verify $g^{(2)}(0)=0$.

**HOM dip:** two indistinguishable photons, one per port — the both-transmit and both-reflect amplitudes cancel, leaving $\frac{1}{\sqrt2}(|2,0\rangle + |0,2\rangle)$: zero coincidences, and the dip depth is a direct meter of photon indistinguishability.

**The vacuum port matters:** even with nothing entering port $b$, its vacuum fluctuations appear in both outputs. This is why optical loss is modeled as a beamsplitter tapping in vacuum, and why homodyne subtraction bottoms out at shot noise rather than zero.

> [!question]- Why is "the photon splits 50/50" wrong, and what actually happens?
> The *mode* splits; the excitation goes into a superposition of being entirely in one output or the other. Coincidence counting settles it: $g^{(2)}(0)=0$ persists after the splitter — there are never two halves to detect.

# Connections

- [[Homodyne Detection]] — built on this: mix signal with LO on a 50:50, subtract
- [[Two-Beam Interferometers]] — classical amplitude division, same transformation, two of them back-to-back
- [[Photon Statistics and g2]] — the HBT setup is a beamsplitter plus coincidence logic
- [[Vacuum Fluctuations]] — what the empty port contributes; loss = beamsplitter to vacuum

---
Source: Gerry & Knight, *Introductory Quantum Optics*, Ch. 6
