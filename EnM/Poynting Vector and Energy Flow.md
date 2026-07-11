#EnM

**$\mathbf{S}=\mathbf{E}\times\mathbf{H}$ is the energy flux — where the E and H fields cross, power flows.** Energy lives in the fields, not the wires: a coax cable's power travels in the dielectric between the conductors.

# Reference

$$
\mathbf{S} = \mathbf{E}\times\mathbf{H} \quad [\mathrm{W/m^2}], \qquad u = \frac{\varepsilon_0 E^2}{2} + \frac{B^2}{2\mu_0}
$$

with Poynting's theorem $\partial_t u + \nabla\cdot\mathbf{S} = -\mathbf{J}\cdot\mathbf{E}$ (field energy leaves either by flowing out or by doing work on charges).

**Time-averaged intensity of a plane/quasi-plane wave:**
$$
I = \langle S\rangle = \frac{1}{2}c\varepsilon_0 E_0^2 = \frac{E_0^2}{2\eta_0}
$$

Handy inversions: $E_0 = \sqrt{2\eta_0 I} \approx 27.4\sqrt{I\,[\mathrm{W/m^2}]}\ \mathrm{V/m}$. A 1 mW Gaussian beam at $w=1$ mm has peak $I = 2P/\pi w^2 \approx 64\ \mathrm{mW/cm^2}$ and $E_0\approx 690$ V/m — laser fields are *large* compared to your intuition from circuits.

**Radiation pressure:** momentum flux $= I/c$ (absorbed) or $2I/c$ (reflected). 1 W retroreflected: 6.7 nN — tiny, but it's the classical face of photon recoil and the raw force behind optical tweezers and laser cooling.

For a wave in a medium use $\eta=\eta_0/n$: intensity for the same $E_0$ is $n$ times larger.

> [!question]- In a DC circuit powering a resistor, along what path does the energy actually travel from battery to resistor?
> Through the *fields around the wires*: E points from wire to wire, H circles the current, and $\mathbf{E}\times\mathbf{H}$ points down the gap toward the resistor, converging into it. The wires guide the energy; they don't carry it. This picture becomes literal in [[Transmission Lines]].

# Connections

- [[Electromagnetic Wave Equation]] — provides the $E/H=\eta_0$ ratio used in the intensity formula
- [[Dipole Radiation]] — integrate S over a sphere to get total radiated power
- [[Gaussian Beams]] — the intensity profile you're usually plugging into $I(r)$
- [[Transmission Lines]] — energy flow in the dielectric, not the copper, made practical
- [[Photodetection and Shot Noise]] — detectors measure $\langle S\rangle$, i.e. $|E|^2$, never the field itself

---
Source: Griffiths, *Introduction to Electrodynamics*, Ch. 8.1
