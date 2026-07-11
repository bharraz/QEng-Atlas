#quantum-info

**The DFT applied to amplitudes rather than data — exponentially fewer gates than an FFT, but you can't read the answer out**; its power appears only when you need to *sample* the spectrum, not see it.

# Reference

$$
|j\rangle \;\to\; \frac{1}{\sqrt{2^n}} \sum_{k=0}^{2^n-1} e^{2\pi i jk / 2^n} |k\rangle
$$

**Why the circuit is small** — the output factorizes into a product state:

$$
\bigotimes_{l=1}^{n} \frac{|0\rangle + e^{2\pi i\, 0.j_l j_{l-1} \cdots j_1}|1\rangle}{\sqrt2}
$$

each factor needs one $H$ plus controlled phase rotations $R_k = \mathrm{diag}(1, e^{2\pi i/2^k})$ from the lower bits: **$O(n^2)$ gates** for a $2^n$-point transform (classical FFT: $n2^n$). Small rotations matter less than they look — dropping $R_k$ for $k \gtrsim \log(n/\epsilon)$ gives an $O(n\log n)$ approximate QFT. (Plus swaps: output bits come out reversed.)

**NOT a data FFT**: the transform acts on amplitudes you cannot access — extracting all $2^n$ Fourier coefficients would cost $2^n$ measurements, killing the speedup. No exponential win for spectral analysis of your lab data. The QFT pays off when the *answer is a property of the spectrum you can sample*: a state with period $r$ measures to peaks at multiples of $2^n/r$ — the heart of phase estimation and Shor.

> [!question]- QFT is exponentially faster than FFT — why can't you use it to Fourier-transform a signal?
> Loading $2^n$ data points into amplitudes costs $2^n$ operations, and reading the transformed amplitudes back out costs $2^n$ measurements — the transform is cheap, the I/O is not. Only sampling-type questions (where's the peak?) survive.

# Connections

- [[Quantum Phase Estimation]] — inverse QFT as the phase-readout stage
- [[Fourier Transform]] — the underlying transform, physicist conventions
- [[Canonical Quantum Algorithms]] — Shor's period finding is QFT sampling
- [[Phase Kickback]] — how the phases get onto the register in the first place

---
Source: Nielsen & Chuang, Ch. 5.1
