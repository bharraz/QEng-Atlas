#optics

**Two lenses sharing a focal point form an afocal system: collimated in, collimated out, with the beam diameter multiplied by $M = f_2/f_1$ and the divergence divided by the same factor** — that trade is the whole point, for starlight and laser beams alike.

# Reference

**Keplerian:** two positive lenses, separation $f_1 + f_2$, real internal focus. **Galilean:** positive + negative lens, separation $f_1 - |f_2|$, no internal focus — shorter, and the choice for high power (no plasma/breakdown at an internal focus in air) at the cost of no spatial-filter access (pinhole at the Keplerian focus cleans the mode).

ABCD matrix of the afocal pair:
$$
\begin{pmatrix} -M & \;f_1 + f_2 \\ 0 & -1/M \end{pmatrix}, \qquad M = \frac{f_2}{f_1}
$$
$C = 0$ is the afocal signature: output angle independent of input position. Size $\times M$, angles $\div M$ — étendue conserved.

**For Gaussian beams the same $M$ applies** to the waist ($w \to Mw$) and divergence ($\theta \to \theta/M$), hence $z_R \to M^2 z_R$ — expand by 3× and the collimated range grows 9×. Caveat: this holds when the input waist sits near the front focal plane; otherwise the output "collimation" drifts, so fine-tune the lens spacing while watching the beam far away (or shearing-interferometer it). Expanding *before* a long beam path or *before* focusing hard (bigger $D$ at the lens → smaller spot) are the two standard reasons to own one.

**Relay imaging one-liner:** the 4f Keplerian relay ($M=1$ or not) images a plane — including angle information — onto a distant plane; the trick for putting an AOM's steering pivot, or a mirror, optically "at" an atom or an objective's back aperture.

> [!question]- Why does expanding a beam 3× before a lens shrink the focused spot 3×?
> Spot size at focus is $w \approx \lambda f/\pi w_{in}$ (equivalently $\sim\lambda\, f/\#$): larger input beam = larger numerical aperture = tighter focus. The expander doesn't add brightness; it converts spare beam-path diameter into focusing angle — the same étendue conservation that divides the divergence by $M$.

# Connections

- [[Ray Transfer Matrices]] — the afocal ABCD above; cascade with the rest of the beamline by multiplication
- [[Gaussian Beams]] — waist/divergence trade and the $M^2 z_R$ payoff live in the $q$-parameter
- [[Mode Matching]] — a beam expander is half of every mode-matching solution
- [[Acousto-Optic Modulator]] — 4f relays turn AOM angle scans into pure position-preserving scans at the target

---
Source: Siegman, *Lasers*, Ch. 15 (ray optics and ABCD matrices)
