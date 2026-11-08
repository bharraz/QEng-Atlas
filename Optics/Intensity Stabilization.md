#optics #labwork

**A laser beam's power fluctuates — from the laser itself, from pointing into a fiber, from polarization drifting through a polarizer — so it is stabilized by sampling a little of the beam onto a photodiode and adjusting an actuator upstream until the measured power matches a setpoint.** The loop makes the light quiet only at the point where it is sampled, and only as quiet as that photodiode can measure.

# Reference

**The loop:** a pickoff (a weak beamsplitter or a glass surface) sends a fraction of the beam to a photodiode; the photodiode voltage is compared with a setpoint; a servo ([[PID Control]]) drives an actuator upstream that changes the power.

| Actuator | Speed | Drawbacks |
|---|---|---|
| AOM RF amplitude ([[Acousto-Optic Modulator]]) | loop bandwidths up to ~100 kHz–1 MHz | the sound's travel time from transducer to beam adds a delay that limits the bandwidth; efficiency rolls over at high RF power; thermal pointing drift |
| EOM between polarizers ([[Electro-Optic Modulator]]) | the fastest, MHz and above | high drive voltage; the bias point drifts |
| laser diode current | fast | changes the frequency along with the power |
| amplifier pump current | moderate | slow thermal response of the gain medium |
| motorized waveplate before a polarizer | seconds | slow drift only |

**The loop stabilizes the light at the pickoff.** Anything after it — fiber coupling, polarization drift into a polarizer, clipping, pointing onto the target — is not corrected. Sample as close to where the light is used as possible: after the fiber, after the last polarizer. A glass pickoff reflects s- and p-polarization differently ([[Fresnel Equations]]), so a polarizer before the pickoff stops polarization drift from appearing as false power changes.

**In-loop and out-of-loop detectors.** The servo forces the in-loop photodiode's signal to the setpoint — including that photodiode's own noise, which is therefore written onto the light. Real stability is measured by a second, out-of-loop photodiode. The in-loop detector's shot noise sets the best achievable stability:

$$
S_\text{RIN} \geq \frac{2h\nu}{\eta\,P_\text{det}}
$$

- $S_\text{RIN}$ — relative intensity noise: one-sided spectral density of $\delta P/P$ (1/Hz; quoted in dB/Hz)
- $h\nu$ — photon energy (J)
- $\eta$ — photodiode quantum efficiency (dimensionless)
- $P_\text{det}$ — power on the in-loop photodiode (W)

1 mW detected at 780 nm gives about −150 dB/Hz. Halving the in-loop power raises this floor by 3 dB, so the pickoff fraction is a trade between the power that reaches the experiment and the stability it can have. The photodiode amplifier must also be quieter than this shot noise ([[Photodiode Circuits]]).

**Picture:** a thermostat for light: it holds the photodiode reading constant, so anything that happens after the pickoff, or any noise the photodiode cannot see, is not corrected.

**Bandwidth.** Noise is suppressed by roughly the loop gain at each frequency; above the loop's unity-gain frequency the loop does nothing, and near it the servo bump adds noise ([[Stability and Phase Margin]]). Delays — the AOM's acoustic travel time, detector and filter bandwidth — set where the crossover can go.

**Switched light.** When the beam is pulsed, the photodiode sees nothing between pulses and the integrator winds up. The usual remedy is sample-and-hold: the loop runs while the light is on in a calibration window, and the actuator holds its value during the sequence.

**Why it matters:** intensity noise becomes
- frequency noise through light shifts ([[Stark Effect and Light Shifts]]);
- Rabi-frequency noise and therefore pulse-area errors ([[Rabi Oscillations]]);
- heating in optical traps — trap-depth noise at twice the trap frequency drives parametric heating ([[Optical Tweezers]]);
- noise and drift in anything locked or measured by power.

**Stabilizing a beam — the steps and why:**

1. **Measure the free-running relative intensity noise** with the photodiode where the light is used; this says which frequencies need suppression.
2. **Place the pickoff** after everything that drifts (fiber, polarizer), with a polarizer before it.
3. **Choose the actuator** fast enough for the noise band.
4. **Close the loop and set the gain:** raise it until the servo bump appears, then back off.
5. **Check out of loop.** Only an independent detector shows what the light at the experiment is doing.

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| out-of-loop noise spectrum against in-loop | the real suppression; out-of-loop well above in-loop means noise is added after the pickoff or written on by the in-loop detector |
| noise with the loop open and closed | suppression against frequency; the servo bump marks the loop bandwidth |
| step in the setpoint | bandwidth and overshoot |
| out-of-loop noise against in-loop power | falling as $1/P$ means the loop is limited by in-loop shot noise; flat means a technical limit |

**Failure modes:**

| Failure | Mechanism | What you see |
|---|---|---|
| pickoff before polarization-sensitive optics | drift introduced after the pickoff is invisible to the loop | power at the experiment drifts while the loop reads steady |
| setpoint drift | the photodiode amplifier's offset and gain drift with temperature | slow drift of the stabilized power |
| loop sign flip | past the AOM's efficiency maximum, more RF gives less light | the loop runs to the end of its range instead of locking |
| ground loop between photodiode and servo | hum enters the error signal ([[Ground Loops]]) | line-frequency ripple written onto the light |
| pointing onto a small photodiode | beam motion across a nonuniform detector reads as power change | noise that depends on alignment |
| integrator windup with pulsed light | the loop integrates while the light is off | large transients when the light returns |

> [!question]- The in-loop photodiode shows intensity noise 40 dB below the free-running level, but an out-of-loop photodiode shows little improvement. What are the two likely causes?
> Either noise is added after the pickoff — fiber coupling, polarization drift, pointing — which the loop cannot see; or the in-loop detector's own noise (too little light, amplifier noise, pointing on the detector) is being imprinted on the beam, because the loop makes the light follow whatever that detector reports. Moving the pickoff downstream separates the first; raising the in-loop power or swapping the two detectors separates the second.

# Connections

- [[Photodiode Circuits]] — the detector and amplifier whose noise floor the loop inherits
- [[Photodetection and Shot Noise]] — the shot-noise limit on any intensity measurement
- [[Acousto-Optic Modulator]] — the usual actuator, and its delay
- [[PID Control]] — the servo
- [[Stability and Phase Margin]] — gain, bandwidth, and the servo bump
- [[Fiber Noise Cancellation]] — the same idea applied to optical phase
- [[Stark Effect and Light Shifts]] — intensity noise as frequency noise
- [[Optical Tweezers]] — intensity noise as trap heating
- [[Noise Spectra and Coupling to Systems]] — how a noise spectrum acts on a system

---
Source: T. A. Savard, K. M. O'Hara & J. E. Thomas, "Laser-noise-induced heating in far-off resonance optical traps," *Phys. Rev. A* 56, R1095 (1997); Saleh & Teich, *Fundamentals of Photonics*, Ch. 18 (photon detection and noise)
