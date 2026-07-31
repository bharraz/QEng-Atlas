#circuits #electronics

**Feedback with three knobs on the error e: P reacts now (speed), I remembers (kills steady-state error), D anticipates (damping) — most lab locks are really PI, with D only if the noise budget allows.**

# Reference

$$
u(t) = K_p\,e + K_i\!\int e\,dt + K_d\,\dot e
$$

$e(t)$ = error, setpoint minus measured output (in whatever the sensor reads — volts, Hz, °C); $u(t)$ = actuator command (in whatever the actuator takes — volts to a piezo, current to a coil); $K_p, K_i, K_d$ = gains, each carrying whatever units convert error to command, and each differing in *frequency dependence*, which is the real content: in Laplace form $u/e = K_p + K_i/s + K_d s$, so I has gain $\propto 1/f$ (infinite at DC — kills steady-state error) and D has gain $\propto f$ (grows without bound — hence noise amplification, and why real D is band-limited).

| Term | Fixes | Costs |
|---|---|---|
| P | response speed | finite gain leaves residual offset; too much → oscillation |
| I | steady-state error → 0 (infinite DC gain) | −90° phase lag eats phase margin |
| D | damping, +90° phase lead near crossover | amplifies high-frequency noise; usually band-limited or omitted |

**Integrator windup:** while the actuator is railed (unlock, big transient) the integral keeps charging; on recovery it overshoots violently. Clamp or freeze the integrator during saturation — the #1 reason relocks look dramatic.

**Ziegler–Nichols starting point:** I and D off, raise $K_p$ until steady oscillation at $K_u$ with period $T_u$; then $K_p = 0.6K_u$, $T_i = T_u/2$, $T_d = T_u/8$. Aggressive — back off for quiet loops.

**Lab reality:** the plant's own poles set the ceiling — piezo resonance, thermal lag, AOM transit delay. Rule of thumb: unity-gain crossover at ≲ 1/10 the first plant resonance. The controller can't buy back phase the plant has spent.

> [!question]- A laser lock settles fast but sits with a constant offset from line center. Which knob, and what breaks if you overdo it?
> Integral gain — P-only loops leave offset ∝ 1/K_p; the integrator drives DC error to zero. Overdone, its −90° lag erodes phase margin: the servo bump grows, then the loop sings at the crossover frequency.

# Connections

- [[Stability and Phase Margin]] — what limits how hard you can turn the knobs
- [[Pound-Drever-Hall Locking]] — supplies the error signal these gains act on
- [[Transfer Functions and Bode Plots]] — loop shaping: I is −20 dB/dec at LF, D is lead near crossover
- [[Phase-Locked Loops]] — a PLL loop filter is PI control on phase

---
Source: Horowitz & Hill, *The Art of Electronics* 3rd ed., Ch. 15 (PID controller example)
