#optics

**Fully polarized light is a complex 2-vector; every polarization element is a 2×2 matrix** — chain elements by matrix multiplication, last element leftmost.

# Reference

Basis $\begin{pmatrix}E_x \\ E_y\end{pmatrix}$: horizontal $\binom{1}{0}$, diagonal $\frac{1}{\sqrt2}\binom{1}{1}$, circular $\frac{1}{\sqrt2}\binom{1}{\pm i}$.

| Element | Jones matrix |
|---|---|
| Polarizer along $x$ | $\begin{pmatrix}1 & 0\\ 0 & 0\end{pmatrix}$ |
| Half-wave plate, fast axis at $\theta$ | $\begin{pmatrix}\cos 2\theta & \sin 2\theta\\ \sin 2\theta & -\cos 2\theta\end{pmatrix}$ |
| Quarter-wave plate, fast axis $x$ | $e^{-i\pi/4}\begin{pmatrix}1 & 0\\ 0 & i\end{pmatrix}$ |
| Rotation by $\theta$ | $\begin{pmatrix}\cos\theta & -\sin\theta\\ \sin\theta & \cos\theta\end{pmatrix}$ |

Arbitrary-angle element: $M(\theta) = R(\theta)\, M(0)\, R(-\theta)$ — rotate into the element's frame, act, rotate back. Global phases are usually ignorable (until you interfere two paths — then keep them).

**Lossless elements are unitary** (waveplates); polarizers are projectors. This is the same 2-level linear algebra as a qubit — waveplates are SU(2) rotations on the polarization Poincaré/Bloch sphere, and QWP–HWP–QWP reaches any unitary.

**When it fails:** partial polarization and depolarization (multimode fiber, scattering) — Jones vectors describe pure states only. Then go to 4-component Stokes vectors and 4×4 Mueller matrices, the density-matrix analogue.

> [!question]- Why does a half-wave plate at angle $\theta$ rotate linear polarization by $2\theta$, not $\theta$?
> The HWP reflects the polarization about its fast axis (it flips the sign of the component along the slow axis). Reflection about an axis at $\theta$ takes a line at $0$ to a line at $2\theta$ — same reason two mirrors at angle $\alpha$ rotate by $2\alpha$.

# Connections

- [[Polarization of EM Waves]] — the physical states these 2-vectors encode
- [[Waveplates]] — the workhorse matrices above, with their lab gotchas
- [[Birefringence]] — where the differential phase in waveplate matrices physically comes from
- [[Pauli Matrices]] — Jones matrices of lossless elements are exactly SU(2); polarization is a flying qubit

---
Source: Hecht, *Optics*, Ch. 8
