#quantum-info

**Drive a qubit with a resonant field for a time $t$ and its Bloch vector rotates: about an axis in the equatorial plane chosen by the drive's phase, through an angle set by the pulse area.** Every single-qubit gate is such a rotation, $U = e^{-i\theta\,\hat n\cdot\vec\sigma/2}$, so compiling gates means composing rotations.

# Reference

$$
R_{\hat n}(\theta) = e^{-i\theta\,\hat n\cdot\vec\sigma/2} = \cos\tfrac\theta2\,\mathbb{1} - i\sin\tfrac\theta2\,\hat n\cdot\vec\sigma
$$

- $\theta$ — rotation angle (rad): the pulse area, Rabi frequency × duration
- $\hat n$ — unit rotation axis: in the $xy$ plane at the drive's phase
- $\vec\sigma$ — the [[Pauli Matrices (Atlas)|Pauli matrices]] $(X, Y, Z)$

**Picture:** in the frame rotating with the drive, a resonant field is a static magnetic field in the equatorial plane, and the qubit precesses about it ([[Rotating Frame Transformation]]).

| Gate | Matrix | Bloch action |
|---|---|---|
| $X$ | $\begin{pmatrix}0&1\\1&0\end{pmatrix}$ | $\pi$ about x — bit flip |
| $Y$ | $\begin{pmatrix}0&-i\\i&0\end{pmatrix}$ | $\pi$ about y |
| $Z$ | $\begin{pmatrix}1&0\\0&-1\end{pmatrix}$ | $\pi$ about z — phase flip |
| $H$ | $\tfrac{1}{\sqrt2}\begin{pmatrix}1&1\\1&-1\end{pmatrix}$ | $\pi$ about $(\hat x+\hat z)/\sqrt2$; swaps X↔Z bases |
| $S$ | $\mathrm{diag}(1,i)$ | $\pi/2$ about z; $S^2=Z$ |
| $T$ | $\mathrm{diag}(1,e^{i\pi/4})$ | $\pi/4$ about z; $T^2=S$; the non-Clifford one |

**Any SU(2) from two fixed axes** (Euler): $U = e^{i\alpha}R_z(\beta)\,R_x(\gamma)\,R_z(\delta)$ — which is why a resonant drive with controllable phase (axis anywhere in the xy-plane) plus z-rotations suffices. **Virtual Z gates cost nothing**: a $z$-rotation is made by shifting the phase reference of all subsequent pulses, with no pulse applied.

**H as basis switch**: $HZH = X$ — conjugating by $H$ moves operators (and measurements) between the Z and X bases.

**How the rotation is driven, by platform:**

| Platform | Drive | Note |
|---|---|---|
| hyperfine or spin qubits (ions, atoms, NV) | microwave or RF field, or a two-photon [[Raman Transitions\|Raman]] pair | Raman beams also couple to motion unless co-propagating |
| optical qubits (ions) | a narrow laser on a quadrupole transition | laser phase noise becomes gate error |
| transmons | shaped microwave pulses through a drive line | pulses must avoid the nearby $\lvert 1\rangle\to\lvert 2\rangle$ transition ([[Pulse Shaping and Optimal Control]]) |
| spins in dots | electric-dipole spin resonance, or magnetic resonance | spin–orbit or a micromagnet converts electric drive to spin rotation |

**Errors, and how each shows itself:**

| Error | Mechanism | Signature |
|---|---|---|
| over- or under-rotation | pulse area wrong (amplitude or timing) | repeating the gate $N$ times multiplies the error by $N$ |
| detuning | drive off resonance tilts the axis out of the equatorial plane | a phase that builds up between pulses; Ramsey fringes oscillate at the detuning |
| phase error | drive phase drifts relative to the qubit's frame | axis rotation within the plane |
| leakage | spectral content of the pulse drives other levels ([[Leakage, Erasure, and Biased Noise]]) | population outside $\lvert 0\rangle, \lvert 1\rangle$ |
| crosstalk | the field reaches neighbouring qubits | rotations on idle qubits |
| decoherence during the pulse | $T_1$, $T_2$ act while the gate runs | an error floor that falls with gate duration |

The first three are coherent and add in amplitude, so they are found by **error amplification**: apply the gate many times in a row, and a small over-rotation grows into a visible one.

> [!question]- $R_{\hat n}(2\pi) = -\mathbb{1}$, not identity — why doesn't this break anything?
> A global phase is unobservable on one qubit. It becomes real physics when the rotation is *conditional*: a controlled-$2\pi$ rotation imprints a measurable relative phase — the working principle of several geometric gates.

# Connections

- [[Pauli Matrices (Atlas)]] — the generators; the rotation formula is theirs
- [[Bloch Sphere]] — where these rotations act
- [[Rabi Oscillations]] — how a resonant drive physically implements $R_{x,y}(\theta)$
- [[Universal Gate Sets]] — why the T gate is needed in addition to the Clifford gates
- [[Rotating Frame Transformation]] — the frame in which the drive is a static field
- [[Pulse Shaping and Optimal Control]] — shaping pulses against leakage and calibration error
- [[Two-Qubit Gate Mechanisms]] — the gates these rotations are combined with

---
Source: Nielsen & Chuang, §4.2
