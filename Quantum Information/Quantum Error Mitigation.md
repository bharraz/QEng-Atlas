#quantum-info

**Without enough qubits to correct errors, an experiment can still estimate the expectation value a perfect device would have produced: run the circuit in deliberately varied ways — with the noise amplified, with random extra operations chosen so the noise cancels on average, or keeping only runs that pass a symmetry check — and combine the results so the errors cancel in the average.** The price is many more repetitions, a number that grows exponentially with the total error in the circuit.

# Reference

| Method | Idea | Cost | Assumes |
|---|---|---|---|
| zero-noise extrapolation (ZNE) | run at several deliberately amplified noise levels (stretched pulses, or each gate $G$ replaced by $GG^\dagger G$) and extrapolate to zero noise | a few noise levels, more shots | noise scales as intended; the extrapolation model is right |
| probabilistic error cancellation (PEC) | write the inverse of the noise as a weighted mix of operations the device can run, with some negative weights, and sample from it | shots multiplied by $\gamma^2$ | an accurate noise model, usually learned ([[Benchmarking and Characterization]]) |
| symmetry verification / post-selection | discard runs that violate a known conserved quantity (particle number, parity) | discarded runs | errors violate the symmetry |
| virtual distillation | combine several copies of the output state to suppress everything except its dominant eigenvector | copies and entangling operations between them | the dominant eigenvector is close to the ideal state |
| readout-error mitigation | invert the measured assignment matrix | calibration runs | readout errors characterized and stable |
| learning-based correction (e.g. Clifford data regression) | fit a correction from similar circuits that can be simulated classically | training circuits | the same error behaviour in training and target circuits |
| error suppression in hardware | dynamical decoupling of idle qubits, randomized compiling of coherent errors | small | — |

**Zero-noise extrapolation**, in its simplest (linear) form:

$$
E_0 \approx \frac{\lambda_2 E(\lambda_1) - \lambda_1 E(\lambda_2)}{\lambda_2 - \lambda_1}
$$

- $\lambda$ — noise scale factor: 1 at native noise, larger when amplified
- $E(\lambda)$ — expectation value measured at noise scale $\lambda$
- $E_0$ — the extrapolated zero-noise estimate

**The sampling cost of cancellation.** In PEC each layer's inverse noise has a quasi-probability norm $\gamma_l = \sum_i |q_i| \ge 1$, and the number of shots needed for a given precision grows by the square of the product over layers:

$$
N_\text{shots} \propto \Big(\prod_l \gamma_l\Big)^2 \approx e^{4\epsilon L}
$$

- $\gamma_l$ — quasi-probability norm of layer $l$'s inverse noise: 1 if noiseless
- $\epsilon$ — error per layer, small, so $\gamma_l \approx 1 + 2\epsilon$
- $L$ — number of layers

so mitigation is practical only while the circuit's total error $\epsilon L$ is of order one.

**Picture:** mitigation corrects the statistics of many noisy runs, not any single run — a pollster weighting a biased sample, not a better sample.

**Mitigation compared with correction:**

| | Error mitigation | Error correction |
|---|---|---|
| output | estimates of expectation values, unbiased only if the noise model is exact | corrected individual runs, including samples of bitstrings |
| qubit overhead | none or small | many physical qubits per logical qubit |
| shot overhead | exponential in total error | polynomial once below threshold |
| limit | total circuit error of order one | logical error rate |

**What each check tells you:**

| Check | What it tells you |
|---|---|
| mitigation applied to circuits with known answers (Clifford or mirror circuits) | remaining bias of the method |
| spread of the mitigated estimate against number of shots | the actual sampling overhead |
| ZNE result for different extrapolation models | systematic uncertainty from the model choice |

> [!question]- Why does error mitigation stop working for deep circuits, however many shots are available?
> The variance of the mitigated estimate grows exponentially with the circuit's total error, so the shots needed for a fixed precision grow exponentially with depth and width. Once the total error is a few units, the required shots exceed any feasible run; and errors in the noise model add a bias that more shots cannot remove.

# Connections

- [[Benchmarking and Characterization]] — learning the noise model mitigation needs
- [[Quantum Error Correction (Atlas)]] — the scalable alternative once qubits allow it
- [[Quantum Channels]] — noise channels and their inverses
- [[Randomized Benchmarking]] — twirling, which makes noise models simple enough to invert
- [[Spin Echo and Dynamical Decoupling]] — suppressing idle errors in hardware
- [[Variational Quantum Algorithms]] — the variational algorithms mitigation is mostly used with
- [[Monte Carlo Methods]] — the sampling behind quasi-probability estimates
- [[Binomial Errors in State Detection]] — the readout statistics behind assignment-matrix correction

---
Source: Z. Cai et al., "Quantum error mitigation," *Rev. Mod. Phys.* 95, 045005 (2023); K. Temme, S. Bravyi & J. M. Gambetta, "Error mitigation for short-depth quantum circuits," *Phys. Rev. Lett.* 119, 180509 (2017); S. Endo, Z. Cai, S. C. Benjamin & X. Yuan, *J. Phys. Soc. Jpn.* 90, 032001 (2021)
