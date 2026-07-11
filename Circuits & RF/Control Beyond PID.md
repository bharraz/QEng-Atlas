#circuits #control

**Feedback corrects errors after measuring them; feedforward cancels disturbances you can predict before they arrive. PID is one feedback law among many — the right one when you know little about the plant — and everything beyond it comes from exploiting a model: of the plant, of the noise, or of the disturbance.** This page is the map of when PID stops being the answer.

# Reference

**The two architectures, defined:**

- **Feedback**: measure the output, compare to setpoint, drive the actuator with the error. It needs no model of the disturbance — anything that shows up in the error gets fought — but it is *reactive*: nothing is corrected until it has already appeared in the measurement, so performance is bounded by measurement noise and loop delay.
- **Feedforward**: measure or predict the *disturbance itself* (or the setpoint change) and apply the pre-computed counteraction directly, without waiting for an error. It can be perfect in principle and is limited only by how well you know the transfer path — and it is *open-loop*: any model error passes straight to the output, uncorrected.

The standard architecture is both: feedforward removes the bulk of what you can predict (the known thermal load when a shutter opens, the calculated field from a scanned coil, the scheduled trajectory), feedback mops up the residual. Feedforward does the heavy lifting; feedback provides the guarantee.

**The fundamental limit every feedback loop obeys** — the Bode sensitivity integral ("waterbed theorem"): for the sensitivity $S(\omega) = 1/(1 + L(\omega))$ of a stable loop,

$$\int_0^\infty \ln|S(\omega)|\; d\omega = 0 \;\;(\text{for relative degree} \geq 2).$$

Suppression at some frequencies ($|S| < 1$) is *necessarily paid for* by amplification at others ($|S| > 1$). Push the waterbed down where your noise lives, and it bulges elsewhere — the "servo bump" just above a laser lock's bandwidth is not a tuning failure, it's the integral being conserved. Loop delay $\tau$ caps usable bandwidth at roughly $f \lesssim 1/(4\tau)$ regardless of controller cleverness: phase lag $\omega\tau$ eats the phase margin (see [[Stability and Phase Margin]]).

**Where PID fails, and what replaces it:**

- **Dominant delay** (thermal systems, anything with transport lag). PID must stay slow because delay destroys phase margin. The **Smith predictor** wraps the loop around a *model* of the plant-without-delay, so the controller acts on a prediction; the real delayed output only corrects model drift. Works exactly as well as the model.
- **Multiple coupled inputs/outputs** (MIMO — e.g. several heaters on one baseplate, multiple lock points sharing a path). Independent PIDs fight each other through the cross-couplings. State-space design treats the system whole: model $\dot{\mathbf{x}} = A\mathbf{x} + B\mathbf{u}$, feed back the full state, $\mathbf{u} = -K\mathbf{x}$. **LQR** picks $K$ by minimizing $J = \int (\mathbf{x}^\top Q\,\mathbf{x} + \mathbf{u}^\top R\,\mathbf{u})\,dt$ — you state the tradeoff (state error vs actuator effort) and the optimal gains follow, coupling terms included.
- **State not directly measurable / noisy sensors.** The **Kalman filter** is the optimal observer: propagate the model, correct with measurements weighted by their believed noise — a recursive Bayesian update producing the best state estimate; feed *that* to LQR (together: **LQG**). Anywhere you average, you are approximating this; the filter tells you the right, time-varying weighting.
- **Hard constraints** (actuator saturation, forbidden regions, rate limits). PID doesn't know limits exist (integrator windup is the symptom; anti-windup the patch). **MPC** (model predictive control) re-solves, every cycle, a finite-horizon optimization with the constraints built in, applies the first move, repeats. The industrial standard where constraints bind; cost is compute per cycle.
- **Repetitive tasks** (the same scan, shuttle, or pulse sequence every shot). Feedback re-fights the same error every repetition. **Iterative learning control** stores the previous shot's error and adjusts the next shot's *feedforward* waveform — errors deterministic in shot-time converge away over iterations. This is what tuning ion-shuttle or gradiometer waveforms shot-over-shot is, formalized.
- **Plant drifts or is unknown**: adaptive control (estimate plant parameters online, retune) or, increasingly, learned controllers; **robust** ($H_\infty$) design instead fixes a worst-case plant set and guarantees stability over all of it — trading peak performance for immunity to the drift.
- **Cascade** (inner fast loop, outer slow loop — current loop inside a temperature loop, piezo inside a slow motor): not beyond PID so much as PIDs *composed*; the inner loop linearizes and speeds up the actuator that the outer loop then treats as ideal. The default structure for laser locks (fast EOM/current + slow piezo).

**Digital reality.** Any loop in an FPGA/microcontroller samples: aliasing folds high-frequency noise into band (see [[Sampling and Aliasing]]), and the sample-and-compute adds delay ($\sim 1.5$ samples) that eats phase margin exactly like analog delay. Rule of thumb: sample $\gtrsim 10\times$ the target bandwidth or budget the phase explicitly.

> [!question]- Your temperature loop oscillates when you raise the gain, and the period of oscillation is long. What is the physics, and why won't better PID tuning fix it fundamentally?
> A long oscillation period at the stability edge signals a large delay or dominant slow pole: heat takes time $\tau$ to propagate from heater to sensor, so the controller acts on stale information, and at the frequency where the propagation phase reaches ~180° any sufficient gain sustains oscillation. Tuning trades speed for margin but cannot recover the phase the physics discarded. Structural fixes: move the sensor closer to the heater (reduce $\tau$), cascade a fast inner loop around the heater, or Smith-predict the delay with a thermal model — all attack $\tau$ itself, which tuning cannot.

# Connections

- [[PID Control]] — the baseline this page extends
- [[Stability and Phase Margin]] — the stability language (gain/phase margin, Nyquist) all of these are judged in
- [[Transfer Functions and Bode Plots]] — the frequency-domain plant description
- [[Phase-Locked Loops]] — a specialized feedback loop where the "plant" is a phase accumulator
- [[Sampling and Aliasing]] — digital-loop delay and aliasing costs
- [[Pound-Drever-Hall Locking]] — a real system: cascaded actuators, servo bump, delay-limited bandwidth
- [[Kalman Filter]] — optimal state estimation (page pending; the Bayesian update behind LQG)

---
Source: Åström & Murray, *Feedback Systems*, Ch. 10–13; Skogestad & Postlethwaite, *Multivariable Feedback Control*, Ch. 2–5; Bechhoefer, "Feedback for physicists," *Rev. Mod. Phys.* 77, 783 (2005)
