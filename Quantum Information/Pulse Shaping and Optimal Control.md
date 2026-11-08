#quantum-info

**A gate is made by a control field — a laser, microwave, or voltage pulse — whose shape in time decides what the qubit does, and a square pulse of the right area works only if the qubit is an exact two-level system with exactly known parameters.** Real gates therefore shape their pulses to cancel known errors — leakage to nearby levels, crosstalk, calibration error — or let an optimizer search for the shape that does.

# Reference

**Analytic shaping — pulses designed against a named error:**

| Technique | Error it targets | Idea |
|---|---|---|
| smooth envelopes (Gaussian, Blackman, cosine) | driving nearby transitions through the pulse's spectral tails | a smooth turn-on narrows the spectrum ([[Window Functions and Apodization]]) |
| DRAG | leakage and phase error from a nearby level, as in a transmon's $\lvert 2\rangle$ | add a quadrature component proportional to the envelope's derivative |
| composite pulses (BB1, CORPSE, SK1) | amplitude or detuning miscalibration | a sequence of rotations whose errors cancel to first or higher order |
| adiabatic and shortcut pulses | amplitude and detuning variation | follow an eigenstate instead of timing a rotation ([[Adiabatic Ramps and Shortcuts]]) |
| dynamically corrected gates | slow noise during the gate | build decoupling into the gate itself ([[Spin Echo and Dynamical Decoupling]]) |
| amplitude, phase, or frequency modulation of Mølmer–Sørensen pulses | coupling to many motional modes; mode-frequency drift | close every mode's phase-space loop at once ([[Molmer-Sorensen Gate]]) |

**DRAG**, to first order:

$$
\Omega_y(t) = -\frac{\dot\Omega_x(t)}{\alpha}
$$

- $\Omega_x(t)$ — the in-phase drive envelope (rad/s): the intended rotation
- $\Omega_y(t)$ — the added quadrature component (rad/s)
- $\alpha$ — anharmonicity (rad/s): detuning of the leakage transition from the qubit

The quadrature term cancels the drive's component at the leakage transition and the phase error it would cause; sign conventions differ between papers.

**Picture:** a shaped pulse is an equalizer setting — it keeps the part of the spectrum that drives the wanted transition and notches out the parts that would drive unwanted ones.

**Numerical optimal control:**

| Method | Idea | Strength | Weakness |
|---|---|---|---|
| GRAPE | gradient of the gate fidelity with respect to every time-slice amplitude ([[Gradient Descent and Backpropagation]]) | many parameters, fast convergence | needs an accurate model; jagged pulses unless smoothness is enforced |
| Krotov | sequential updates that improve the fidelity at every iteration | guaranteed monotonic improvement | slower per iteration |
| CRAB / dCRAB | optimize a few coefficients of a smooth basis (Fourier, Chebyshev) | few parameters; works with the experiment in the loop | local optima |
| closed-loop optimization | measure fidelity on hardware and adjust (Nelder–Mead, Bayesian optimization) | includes errors the model does not know | slow and noisy objective ([[Optimization and Curve Fitting]]) |
| robust optimal control | optimize average fidelity over a range of parameter errors | tolerates miscalibration and drift | longer pulses |

**Constraints that decide what is achievable:**
- the bandwidth of control electronics, cables, and filters, which distorts pulses — corrected by predistorting with the measured response of the line;
- maximum amplitude;
- the quantum speed limit, the minimum time needed to reach a target operation with the available couplings.

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| a gate repeated $N$ times, against $N$ | coherent over- or under-rotation, amplified $N$ times |
| leakage population after repeated pulses | whether shaping suppresses leakage ([[Leakage, Erasure, and Biased Noise]]) |
| Rabi oscillation against pulse length and amplitude | calibration of the rotation per unit pulse area ([[Rabi Oscillations]]) |
| the qubit's response to a fast step on its control line | distortion of the line, measured with the qubit itself as the sensor |

> [!question]- A numerically optimized pulse works perfectly in simulation but underperforms on hardware. Why, and what fixes it?
> The model differs from the device: unknown couplings and levels, distortion of the pulse by cables and filters, drift of parameters during use. Optimized pulses often exploit fine structure the model gets wrong. Including the measured line response and bandwidth limits, optimizing for robustness over a range of parameters, and finishing with closed-loop refinement on the hardware all close the gap.

# Connections

- [[Single-Qubit Gates]] — the rotations these pulses implement
- [[Two-Qubit Gate Mechanisms]] — shaping as the way to move the speed–error trade
- [[Leakage, Erasure, and Biased Noise]] — the leakage DRAG suppresses
- [[Adiabatic Ramps and Shortcuts]] — robust transfers by following eigenstates
- [[Gradient Descent and Backpropagation]] — the gradient method GRAPE uses
- [[Optimization and Curve Fitting]] — optimizers for closed-loop control
- [[Window Functions and Apodization]] — why smooth envelopes have narrow spectra
- [[Magnus Expansion]] — designing sequences by their average Hamiltonian
- [[Rabi Oscillations]] — calibrating the basic rotation
- [[Variational Quantum Algorithms]] — the same closed optimization loop, over circuit angles

---
Source: S. J. Glaser et al., "Training Schrödinger's cat: quantum optimal control," *Eur. Phys. J. D* 69, 279 (2015); F. Motzoi, J. M. Gambetta, P. Rebentrost & F. K. Wilhelm, *Phys. Rev. Lett.* 103, 110501 (2009); N. Khaneja et al., *J. Magn. Reson.* 172, 296 (2005); S. Wimperis, *J. Magn. Reson. A* 109, 221 (1994)
