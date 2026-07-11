#quantum-optics

**Beat the signal against a strong local oscillator at the *same* frequency on a 50:50 splitter and subtract the two photocurrents — the difference current measures whichever quadrature the LO phase selects.** The LO is both amplifier and phase reference.

# Reference

$$
i_- \;\propto\; |\alpha_{\text{LO}}|\, \hat X_\theta, \qquad \hat X_\theta = \frac{a\, e^{-i\theta} + a^\dagger e^{i\theta}}{2}
$$

where $\theta$ is the LO phase — dial it to pick amplitude quadrature, phase quadrature, or anything between.

**Why balanced (subtracted):** LO classical intensity noise arrives common-mode on both diodes and cancels in $i_-$; what survives is the signal quadrature scaled by $|\alpha_{\text{LO}}|$ plus vacuum. Crank the LO until shot noise clears the electronic floor (10–20 dB clearance is a good detector) and the measurement is vacuum-limited even with mediocre electronics.

**With vacuum at the signal port** the variance is $1/4$ — the shot-noise level *is* a vacuum quadrature measurement. [[Squeezed States]] show up as noise below that line at the right $\theta$.

**State tomography:** collect quadrature histograms at many $\theta$, inverse Radon transform → Wigner function. This is how nonclassical states of light (and of ion motion, via analogous quadrature readout) get their portraits taken.

**vs heterodyne:** offsetting the LO frequency gets both quadratures simultaneously, but the image band ports in an extra half-quantum of vacuum — the 3 dB heterodyne penalty.

> [!question]- Why does balanced homodyne beat detector electronic noise?
> The subtractor sees the signal quadrature multiplied by $|\alpha_{\text{LO}}|$: LO power scales the quantum signal *and* its shot noise together, lifting both above the fixed electronic floor. Gain before the noisy electronics, courtesy of interference.

# Connections

- [[Beamsplitter Transformation]] — the mixing element; the unused-port vacuum sets the noise floor
- [[Heterodyne Detection]] — the offset-LO cousin: both quadratures, 3 dB penalty
- [[Wigner Function]] — homodyne histograms vs $\theta$ are its tomographic projections
- [[Squeezed States]] — the states only this measurement can certify (sub-vacuum quadrature noise)

---
Source: Leonhardt, *Measuring the Quantum State of Light*, Ch. 4
