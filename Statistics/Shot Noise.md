#statistics #math

**Discreteness noise: current and light arrive in lumps, and independent lumps mean Poisson statistics** — variance equals the mean count, so the *relative* fluctuation falls as $1/\sqrt{N}$. It's a floor set by counting, not by temperature.

# Reference

Counting form: $\langle \Delta N^2 \rangle = \langle N \rangle$, so $\mathrm{SNR} = \langle N\rangle/\sqrt{\langle N\rangle} = \sqrt{\langle N\rangle}$.

Current form (one-sided, white up to the transit-time scale):

$$
S_I = 2eI \qquad \Rightarrow \qquad i_{\text{rms}} = \sqrt{2eIB}
$$

Number to carry: $I = 1\ \mu\mathrm{A}$ → $\sqrt{2eI} \approx 0.57\ \mathrm{pA/\sqrt{Hz}}$; scales as $\sqrt{I}$, so relative noise $\propto 1/\sqrt{I}$.

**Photon shot noise:** same statement for photocurrent — a shot-noise-limited photodiode measurement has $\mathrm{SNR} \propto \sqrt{P_{\text{opt}}}$. **Quantum projection noise is the same idea's cousin**: reading out $N$ qubits gives binomial $\sqrt{p(1-p)/N}$ fluctuations — discreteness of measurement outcomes instead of charges.

**When it dominates:** shot noise of a current through resistance $R$ beats the Johnson noise of that $R$ when $2eI R^2 > 4k_BTR$, i.e. $V = IR > 2k_BT/e \approx 50$ mV at 300 K. In photodetection: LO/signal power high enough that $2eI$ swamps amplifier and Johnson terms — the design target of every shot-noise-limited detector.

> [!question]- Why does increasing optical power *improve* SNR if shot noise grows with power?
> Signal grows $\propto P$ but shot noise only $\propto \sqrt{P}$ — SNR $\propto \sqrt{P}$. Discreteness noise is additive in variance, and the mean outruns its own fluctuations.

# Connections

- [[Poisson Distribution]] — the statistics underneath: variance = mean
- [[Poisson Process]] — independent arrivals in time, which is *why* the spectrum is white
- [[Photodiode Circuits]] — where the shot-noise-limited condition is engineered
- [[Photodetection and Shot Noise]] — the quantum-optics view (vacuum fluctuations enter here)
- [[Binomial Errors in State Detection]] — projection noise, the qubit-readout analog
- [[Noise Spectra and Coupling to Systems]] — the general taxonomy this white floor belongs to

---
Source: Horowitz & Hill, *The Art of Electronics* 3rd ed., §8.1 (noise fundamentals)
