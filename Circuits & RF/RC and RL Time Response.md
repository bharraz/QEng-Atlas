#circuits #electronics

**Close a switch that connects a battery, through a resistor, to an uncharged capacitor: at first the current flows as if the capacitor were a wire, then the capacitor's voltage rises toward the battery's along an exponential, because the current still charging it is proportional to the voltage left across the resistor.** An inductor in place of the capacitor does the same to the current. One time constant $\tau$ describes every such first-order circuit, and a sine-wave input reproduces the impedance result once the exponential has decayed.

# Reference

**The setup.** A source of voltage $V_s(t)$ drives a resistor $R$ in series with a capacitor $C$; $V_C$ is the voltage across the capacitor and $i$ the current around the loop. Kirchhoff's voltage law, $V_s = iR + V_C$, together with $i = C\,dV_C/dt$, gives one equation. With an inductor $L$ in place of the capacitor, $V_s = iR + L\,di/dt$ gives the same equation for the current:

$$
\tau\frac{dx}{dt} + x = x_\infty(t), \qquad \tau_{RC} = RC, \qquad \tau_{RL} = \frac{L}{R}
$$

- $x$ — the quantity that cannot jump: $V_C$ for RC, $i$ for RL
- $x_\infty$ — where $x$ is driven: $V_s$ for RC, $V_s/R$ for RL
- $\tau$ — time constant (s): sets every rate in the circuit

Rearranged, $dx/dt = (x_\infty - x)/\tau$: $x$ moves toward its target at a rate proportional to the remaining gap.

**Picture:** a bucket filled through a narrow pipe from a tank — the flow is proportional to the difference in water levels, so the bucket fills fast at first and ever more slowly near the top.

**Step response** — any step in any first-order circuit:

$$
x(t) = x_\infty + \big[x(0) - x_\infty\big]\,e^{-t/\tau}
$$

- $x(0)$ — value immediately before the step, kept through it
- $x_\infty$ — value the circuit settles to after the step

In words: the final value, plus the initial gap shrinking by $e$ every $\tau$.

| Circuit and event | Quantity | Result |
|---|---|---|
| RC charging: source steps from 0 to $V_s$, capacitor empty | capacitor voltage | $V_C = V_s\,(1 - e^{-t/\tau})$ |
| RC charging | current, and voltage across $R$ | $i = (V_s/R)\,e^{-t/\tau}$, $V_R = V_s\,e^{-t/\tau}$ |
| RC discharging: source set to 0, capacitor at $V_0$ | capacitor voltage | $V_C = V_0\,e^{-t/\tau}$, with the current reversed |
| RL: source steps from 0 to $V_s$ | current | $i = (V_s/R)\,(1 - e^{-t/\tau})$ |
| RL: source steps from 0 to $V_s$ | voltage across $L$ | $V_L = V_s\,e^{-t/\tau}$ |
| RL: source replaced by a short while current $I_0$ flows | current | $i = I_0\,e^{-t/\tau}$ |
| RL: circuit opened while current flows | voltage across $L$ | $V_L = L\,di/dt$ grows as large as it must to keep $i$ flowing: an arc across the switch, unless a diode or resistor gives the current a path |

**Rules that follow from the equation:**
- A capacitor's voltage and an inductor's current cannot jump; either would need an infinite current or voltage. At the instant of a step, an uncharged capacitor therefore acts as a short and a current-free inductor as an open.
- Long after a step, a capacitor acts as an open and an inductor as a short.
- The $R$ in $\tau$ is the resistance between the capacitor's or inductor's two terminals with the source replaced by a short — source and load resistances included ([[Time Constants and Reactance Rules of Thumb]]).
- Charging a capacitor to $V_s$ by a step dissipates $\tfrac12 C V_s^2$ in the resistor, whatever its value: half of the $C V_s^2$ the source delivers.

**Settling:**

| Elapsed time | Fraction of the step completed |
|---|---|
| $\tau$ | 63% |
| $2\tau$ | 86% |
| $3\tau$ | 95% |
| $5\tau$ | 99.3% |
| $\tau\ln N$ | all but 1 part in $N$: $7\tau$ for 0.1%, $11\tau$ for 16-bit accuracy |

The 10–90% rise time is $\tau\ln 9 = 2.2\,\tau$.

**A sine switched on.** The source is $V_0\cos\omega t$ from $t = 0$, with the capacitor empty:

$$
V_C(t) = \frac{V_0}{\sqrt{1+(\omega\tau)^2}}\cos(\omega t - \phi) \;-\; \frac{V_0}{1+(\omega\tau)^2}\,e^{-t/\tau}, \qquad \tan\phi = \omega\tau
$$

- $V_0$ — amplitude of the source (V)
- $\omega$ — angular frequency of the source (rad/s)
- $\phi$ — lag of the capacitor voltage behind the source (rad)
- first term — steady state: all that remains after a few $\tau$
- second term — transient: makes $V_C(0) = 0$, then decays away

The first term is $\mathrm{Re}\big[V_0 e^{j\omega t}/(1 + j\omega\tau)\big]$, the impedance divider of [[Complex Impedance]]. Phasor analysis keeps only this term, so it describes the circuit after the first few $\tau$ and says nothing about switch-on.

| Output | Slow input, $\omega\tau \ll 1$ | Fast input, $\omega\tau \gg 1$ |
|---|---|---|
| across $C$ (low-pass) | follows the input | $\approx \tfrac{1}{\tau}\int V_s\,dt$: amplitude $V_0/\omega\tau$, lagging 90° — an integrator |
| across $R$ (high-pass) | $\approx \tau\,dV_s/dt$: small, leading 90° — a differentiator | follows the input |

In an RL circuit the roles swap: the voltage across $R$ behaves like that across $C$ in an RC, and the voltage across $L$ like that across $R$.

**Any input.** For an input that has been on for a long time, the capacitor voltage is a weighted average of the input's past:

$$
V_C(t) = \int_0^\infty \frac{1}{\tau}\,e^{-t'/\tau}\,V_s(t - t')\,dt'
$$

- $t'$ — how long ago an input value occurred (s)
- $\tfrac{1}{\tau}e^{-t'/\tau}$ — its weight, the impulse response: integrates to 1

An RC low-pass is a running average over roughly the last $\tau$, which is why it serves as the output filter of a lock-in amplifier ([[Lock-In Detection]], [[Convolution]]).

**What each measurement tells you:**

| What the scope shows | What it tells you |
|---|---|
| an exponential edge after a step | a single pole; $\tau$ is the time to 63%, or the inverse slope of $\ln(\text{remaining gap})$ against time |
| square wave in, square wave with rounded edges out | low-pass with $\tau$ much shorter than the period |
| square wave in, small triangle wave out, centred on the average | low-pass with $\tau$ much longer than the period: integrating |
| square wave through a coupling capacitor, flat tops sloping toward zero | high-pass; the droop over one half-period is about $T/2\tau$ for period $T$ |
| square wave through a high-pass, a decaying spike at each edge | high-pass with $\tau$ much shorter than the half-period |
| sine in, output at $1/\sqrt2$ of the input and shifted 45° | the drive frequency is the corner, $f = 1/2\pi\tau$ |
| overshoot and ringing at a definite frequency after a step | not first order: an inductance and a capacitance together ([[LC Resonators]]) |

> [!question]- A 1 kHz square wave sent through a 10 µF coupling capacitor into a 1 kΩ input arrives with its flat tops sloping toward zero. Why, and by how much?
> The capacitor and the input resistance form a high-pass with $\tau = RC = 10$ ms. During each 0.5 ms flat top the capacitor charges, so the voltage left across the input decays as $e^{-t/\tau}$: a droop of about $0.5/10 = 5\%$. In frequency terms, the 16 Hz corner shifts the phase of the square wave's lowest harmonics slightly, and a flat top needs every harmonic at its original phase. A larger $\tau$ reduces the droop; a DC-coupled path removes it.

# Connections

- [[Complex Impedance]] — the steady state of these circuits, as one complex number
- [[RC and RL Filters]] — the same circuits described against frequency
- [[Time Constants and Reactance Rules of Thumb]] — finding the $\tau$ of a real circuit, parasitics included
- [[Laplace Transform]] — solving the circuit equation for any input, switch-on included
- [[Impulse and Frequency Response]] — the exponential kernel and $1/(1+j\omega\tau)$ as one object in two domains
- [[Convolution]] — the running-average form of the response
- [[LC Resonators]] — second order, where steps ring instead of settling
- [[Bandwidth]] — rise time × bandwidth ≈ 0.35 for a single pole
- [[Lock-In Detection]] — an RC output filter as a running average

---
Source: Horowitz & Hill, *The Art of Electronics* 3rd ed., Ch. 1; A. Agarwal & J. H. Lang, *Foundations of Analog and Digital Electronic Circuits*, Ch. 10 (first-order transients)
