#quantum-info

**Every single-qubit gate is a rotation of the Bloch vector**: $U = e^{-i\theta\,\hat n\cdot\vec\sigma/2}$ rotates by $\theta$ about axis $\hat n$, so gate compilation is just composing rotations.

# Reference

$$
R_{\hat n}(\theta) = e^{-i\theta\,\hat n\cdot\vec\sigma/2} = \cos\tfrac\theta2\,\mathbb{1} - i\sin\tfrac\theta2\,\hat n\cdot\vec\sigma
$$

| Gate | Matrix | Bloch action |
|---|---|---|
| $X$ | $\begin{pmatrix}0&1\\1&0\end{pmatrix}$ | $\pi$ about x — bit flip |
| $Y$ | $\begin{pmatrix}0&-i\\i&0\end{pmatrix}$ | $\pi$ about y |
| $Z$ | $\begin{pmatrix}1&0\\0&-1\end{pmatrix}$ | $\pi$ about z — phase flip |
| $H$ | $\tfrac{1}{\sqrt2}\begin{pmatrix}1&1\\1&-1\end{pmatrix}$ | $\pi$ about $(\hat x+\hat z)/\sqrt2$; swaps X↔Z bases |
| $S$ | $\mathrm{diag}(1,i)$ | $\pi/2$ about z; $S^2=Z$ |
| $T$ | $\mathrm{diag}(1,e^{i\pi/4})$ | $\pi/4$ about z; $T^2=S$; the non-Clifford one |

**Any SU(2) from two fixed axes** (Euler): $U = e^{i\alpha}R_z(\beta)\,R_x(\gamma)\,R_z(\delta)$ — which is why a resonant drive with controllable phase (axis anywhere in the xy-plane) plus z-rotations suffices. **Virtual Z gates are free**: just shift the phase reference of all subsequent pulses.

**H as basis switch**: $HZH = X$ — conjugating by $H$ moves operators (and measurements) between the Z and X bases.

> [!question]- $R_{\hat n}(2\pi) = -\mathbb{1}$, not identity — why doesn't this break anything?
> A global phase is unobservable on one qubit. It becomes real physics when the rotation is *conditional*: a controlled-$2\pi$ rotation imprints an honest relative phase — the working principle of several geometric gates.

# Connections

- [[Reference Atlas/Linear Algebra/Pauli Matrices]] — the generators; the rotation formula is theirs
- [[Bloch Sphere]] — where these rotations act
- [[Rabi Oscillations]] — how a resonant drive physically implements $R_{x,y}(\theta)$
- [[Universal Gate Sets]] — why the T gate has to join the party

---
Source: Nielsen & Chuang, §4.2
