#quantum

**In the interaction picture, iterate the equation of motion: the transition amplitude to first order is just the Fourier transform of the perturbation evaluated at the transition frequency.** A drive transfers population only through the spectral content it has at $\omega_{fi}$.

# Reference

Interaction picture, $H = H_0 + V(t)$. Iterating $i\hbar\,\partial_t|\psi_I\rangle = V_I|\psi_I\rangle$ gives the **Dyson series**:
$$
U_I(t) = \mathbb{1} + \frac{1}{i\hbar}\int_0^t dt_1\, V_I(t_1) + \frac{1}{(i\hbar)^2}\int_0^t dt_1\!\int_0^{t_1} dt_2\, V_I(t_1)V_I(t_2) + \cdots
$$
(time-ordered: later times to the left; each order = one more "interaction vertex").

**First-order transition amplitude** $i \to f$:
$$
c_f^{(1)}(t) = \frac{1}{i\hbar}\int_0^t dt'\; \langle f|V(t')|i\rangle\, e^{i\omega_{fi}t'}, \qquad \omega_{fi} = \frac{E_f - E_i}{\hbar}
$$

**This is a Fourier transform of the perturbation's matrix element at $\omega_{fi}$.** Consequences you use constantly:
- Monochromatic drive at $\omega$: response peaked at $\omega = \omega_{fi}$ with $\mathrm{sinc}^2$ lineshape of width $\sim 1/t$ — Fourier-limited linewidth of a finite pulse.
- Sudden switch (broadband) excites everything; slow ramp (narrowband, no content at $\omega_{fi}$) excites nothing — the adiabatic theorem seen spectrally.
- Pulse shaping = sculpting which transitions see spectral weight (why Blackman pulses beat square pulses for spectator suppression).

Validity: $|c_f^{(1)}| \ll 1$. Second order handles two-step (Raman) processes through intermediate states.

> [!question]- Why does a smoothly ramped perturbation cause almost no transitions while an abrupt one does?
> $c_f^{(1)}$ is the FT of $V(t)$ at $\omega_{fi}$: a smooth ramp of duration $\tau$ has exponentially little spectral content beyond $1/\tau \ll \omega_{fi}$, while a step function falls off only as $1/\omega$. Transitions are driven by spectral weight at the transition frequency, not by the size of the change.

# Connections

- [[Interaction Picture]] — the frame that makes the series converge
- [[Fermi's Golden Rule]] — first order + continuum of final states = constant rate
- [[Fourier Transform]] — the amplitude formula literally is one
- [[Time-Independent Perturbation Theory]] — the static sibling; same $V/\Delta E$ bookkeeping

---
Source: Sakurai & Napolitano, *Modern Quantum Mechanics*, §5.6–5.7
