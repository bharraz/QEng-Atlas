#EnM

**Take the curl of Faraday's law, substitute Ampère's — the fields obey a wave equation with speed $1/\sqrt{\mu\varepsilon}$.** E, B, and k form a right-handed triad, and the E/H ratio is a fixed impedance: 377 Ω in vacuum.

# Reference

$$
\nabla\times(\nabla\times\mathbf{E}) = \nabla(\nabla\cdot\mathbf{E})-\nabla^2\mathbf{E} \;\Rightarrow\; \nabla^2\mathbf{E}=\mu\varepsilon\,\partial_t^2\mathbf{E}
$$

(source-free region, so $\nabla\cdot\mathbf{E}=0$). Same for B. Speed $v=1/\sqrt{\mu\varepsilon}=c/n$ with $n=\sqrt{\varepsilon_r\mu_r}\approx\sqrt{\varepsilon_r}$.

**Plane wave solutions:**
$$
\mathbf{E}=\mathbf{E}_0\,e^{i(\mathbf{k}\cdot\mathbf{r}-\omega t)}, \qquad \omega = v|\mathbf{k}|, \qquad \mathbf{B}=\frac{1}{\omega}\,\mathbf{k}\times\mathbf{E}
$$

Transversality ($\mathbf{k}\cdot\mathbf{E}=0$) comes from $\nabla\cdot\mathbf{E}=0$; **$\mathbf{E}\perp\mathbf{B}\perp\mathbf{k}$, right-handed, in phase.**

**Impedance of free space** — the fixed ratio of field amplitudes:
$$
\eta_0=\sqrt{\mu_0/\varepsilon_0}=\frac{E_0}{H_0}\approx 377\ \Omega \quad (=120\pi\ \Omega)
$$
In a medium $\eta=\eta_0/n$. This is the "load" free space presents to an antenna, the normalization in [[Antennas]] gain formulas, and why radiated-emission specs quote V/m *and* assume far field: there $E/H=377\,\Omega$ automatically. **Near a source that ratio is wrong** — high-Z (electric) or low-Z (magnetic) — see [[Near and Far Field]].

Useful conversions: $I=\frac{1}{2}c\varepsilon_0 E_0^2 = E_0^2/2\eta_0$; so $1\ \mathrm{W/cm^2}\leftrightarrow E_0\approx 2.7\ \mathrm{kV/m}$.

> [!question]- A plane wave has $E_0 = 1$ V/m in the far field. What's $H_0$, and why do you know without more information?
> $H_0=E_0/\eta_0\approx 2.65$ mA/m. In the far field the wave equation locks the ratio to $\eta_0=377\,\Omega$ regardless of the source — that locking is exactly what *fails* in the near field.

# Connections

- [[Maxwell's Equations]] — parent equations; the curl-curl trick lives here
- [[Polarization of EM Waves]] — the leftover vector freedom of $\mathbf{E}_0$ in the transverse plane
- [[Poynting Vector and Energy Flow]] — where the $I=E_0^2/2\eta_0$ conversion comes from
- [[Dispersion Relations]] — what happens when $\varepsilon(\omega)$ makes $v$ frequency-dependent
- [[Near and Far Field]] — where the 377 Ω wave impedance does and doesn't apply

---
Source: Griffiths, *Introduction to Electrodynamics*, Ch. 9.1–9.2
