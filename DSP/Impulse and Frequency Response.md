#dsp #math

**A linear time-invariant system is completely characterized by its impulse response $h(t)$ — the output when you hit it with a delta — and its frequency response $H(\omega)$, the Fourier transform of $h(t)$, tells you the complex gain applied to each frequency.** Two views of the same system: how it rings in time, how it weights frequencies.

# Reference

A system is **LTI** if it is linear and time-invariant. Any such system acts by convolution with its impulse response (see [[Convolution]]):

$$y(t) = (h * x)(t) = \int h(\tau)\,x(t-\tau)\,d\tau.$$

**Impulse response** $h(t)$: the output when the input is $\delta(t)$ (see [[Dirac Delta]]). Because any input is a superposition of shifted, scaled impulses, $h(t)$ determines the response to *everything*. It is precisely the [[Green's Functions|Green's function]] of the system's equation of motion.

**Frequency response** $H(\omega)$: feed a pure tone $e^{i\omega t}$. An LTI system returns the *same frequency*, only scaled by a complex number:

$$x(t) = e^{i\omega t} \;\longrightarrow\; y(t) = H(\omega)\,e^{i\omega t}.$$

Complex exponentials are the eigenfunctions of LTI systems, and $H(\omega)$ is the eigenvalue. It equals the transform of the impulse response,

$$H(\omega) = \int h(t)\,e^{-i\omega t}\,dt,$$

so time-domain and frequency-domain descriptions carry identical information (see [[Fourier Transform]]). $|H(\omega)|$ is the gain at that frequency, $\arg H(\omega)$ the phase shift — this is the transfer function evaluated on the imaginary axis, the thing a Bode plot draws (see [[Transfer Functions and Bode Plots]]).

**Convolution theorem**: convolution in time is multiplication in frequency, $Y(\omega) = H(\omega)\,X(\omega)$. That is why the frequency domain is the natural home for LTI response — a messy integral becomes a product. **Causality** ($h(t)=0$ for $t<0$) constrains $H(\omega)$, linking its real and imaginary parts through the [[Kramers-Kronig Relations]].

**Connection to resonance**: a resonator is an LTI system. Its frequency response is the complex Lorentzian of [[Resonance]], and its impulse response is a decaying oscillation $h(t)\propto e^{-\gamma t/2}\cos(\omega_0 t)$ — the ringdown. Measuring the ringdown or sweeping the frequency response yields the same $\omega_0$ and $\gamma$.

> [!question]- Why are complex exponentials special for LTI systems, and not for systems in general?
> Because for an LTI system $e^{i\omega t}$ is an eigenfunction: the system can rescale its amplitude and shift its phase, but it can never change its frequency or generate new ones. Diagonalizing convolution by the Fourier transform is the precise expression of this — each frequency passes through independently with its own complex gain $H(\omega)$. A nonlinear or time-varying system breaks this and mixes frequencies.

# Connections

- [[Convolution]] — the operation an LTI system performs; multiplication in the frequency domain
- [[Fourier Transform]] — the map between impulse response and frequency response
- [[Dirac Delta]] — the input that defines the impulse response
- [[Green's Functions]] — the impulse response is the Green's function of the system
- [[Transfer Functions and Bode Plots]] — $H(\omega)$ read off as gain and phase vs. frequency
- [[Resonance]] — a resonator's frequency response is the complex Lorentzian; its impulse response is the ringdown
- [[Kramers-Kronig Relations]] — causality tying the real and imaginary parts of $H(\omega)$

---
Source: Oppenheim & Willsky, *Signals and Systems*, Ch. 2–3; Lyons, *Understanding Digital Signal Processing*, Ch. 5–6
