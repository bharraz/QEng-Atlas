#quantum-optics

**$g^{(2)}(0)$ asks: given one photodetection, how likely is a second at the same moment, compared with random arrivals? Thermal light gives 2 (bunched), coherent light 1 (random), and a single-photon source 0 (antibunched).** It's the intensity-correlation fingerprint that separates classical from quantum light.

# Reference

$$
g^{(2)}(\tau) = \frac{\langle a^\dagger(0)\, a^\dagger(\tau)\, a(\tau)\, a(0)\rangle}{\langle a^\dagger a\rangle^2}
$$

- $\tau$ — delay between the two detections (s)
- numerator — normally-ordered joint detection probability (both creation operators outside, because detection *removes* a photon; that ordering is what makes $g^{(2)}(0) = 0$ possible)
- denominator — the same quantity for uncorrelated detections, so $g^{(2)}$ is dimensionless and normalized to 1 for no correlation

**Picture:** photon arrivals as clicks: thermal light comes in clumps, coherent light at random like raindrops, and a single emitter needs time to re-excite after each click, so it never clicks twice at once.

Being a *ratio* of two-photon to (one-photon)² rates is why detection efficiency cancels: both scale as $\eta^2$.

| Light | $g^{(2)}(0)$ | Number statistics |
|---|---|---|
| Thermal | 2 | super-Poissonian (bunched) |
| Coherent | 1 | Poissonian (random arrivals) |
| Fock $\|n\rangle$ | $1 - 1/n$ | sub-Poissonian; single photon → 0 |

**Classical bounds:** any classical intensity distribution gives $g^{(2)}(0) \ge 1$ and $g^{(2)}(0) \ge g^{(2)}(\tau)$. Antibunching ($g^{(2)}(0) < 1$) violates both — it's a nonclassicality certificate, no loopholes about detector efficiency needed.

**HBT measurement:** 50:50 beamsplitter, one detector per port, histogram coincidences vs delay. Splitting dodges detector dead time (one detector can't ask about $\tau \to 0$). Normalize by accidental rate at large $\tau$.

**Main advantage, independence from loss:** numerator and denominator both scale as $\eta^2$, so $g^{(2)}$ survives 1% collection efficiency unchanged — that's why it's THE single-emitter test. (Contrast the Mandel $Q = \langle n\rangle[g^{(2)}(0)-1]$, which loss drags toward 0.)

> [!question]- Why can no classical intensity model give $g^{(2)}(0) < 1$?
> Classically $g^{(2)}(0) = \langle I^2\rangle / \langle I\rangle^2 = 1 + \mathrm{Var}(I)/\langle I\rangle^2 \ge 1$ — variances aren't negative. Getting below 1 needs the detection itself to remove a quantum: one photon detected means none left, which no fluctuating $I(t)$ can mimic.

# Connections

- [[Coherent States]] — the $g^{(2)}=1$ benchmark; Poisson arrivals define "shot-noise-limited"
- [[Fock States]] — the antibunched extreme; $g^{(2)}(0)=0$ for a single photon
- [[Thermal States]] — bunching at 2; intensity fluctuations double the coincidences
- [[Beamsplitter Transformation]] — the HBT splitter, and why a photon never triggers both ports
- [[Photon Detectors]] — dead time, afterpulsing, and jitter: the detector artifacts in a $g^{(2)}$ measurement

---
Source: Loudon, *The Quantum Theory of Light*, 3rd ed., Ch. 5–6
