#optics

**Two lenses sharing a focal point form an afocal system: collimated in, collimated out, with the beam diameter multiplied by $M = f_2/f_1$ and the divergence divided by the same factor** — that trade is what the device is for, with starlight and laser beams alike.

# Reference

**Keplerian:** two positive lenses, separation $f_1 + f_2$, real internal focus. **Galilean:** positive + negative lens, separation $f_1 - |f_2|$, no internal focus — shorter, and the choice for high power (no plasma/breakdown at an internal focus in air) at the cost of no spatial-filter access (pinhole at the Keplerian focus cleans the mode).

ABCD matrix of the afocal pair:
$$
\begin{pmatrix} -M & \;f_1 + f_2 \\ 0 & -1/M \end{pmatrix}, \qquad M = \frac{f_2}{f_1}
$$
$C = 0$ is the afocal signature: output angle independent of input position. Size $\times M$, angles $\div M$ — étendue conserved.

**Picture:** a magnifying trade: the beam gets $M$ times wider and $M$ times less divergent, so their product (the étendue) stays fixed.

**For Gaussian beams the same $M$ applies** to the waist ($w \to Mw$) and divergence ($\theta \to \theta/M$), hence $z_R \to M^2 z_R$ — expand by 3× and the collimated range grows 9×. Caveat: this holds when the input waist sits near the front focal plane; otherwise the output "collimation" drifts, so fine-tune the lens spacing while watching the beam far away (or shearing-interferometer it). Expanding *before* a long beam path or *before* focusing hard (bigger $D$ at the lens → smaller spot) are the two standard reasons to own one.

**Relay imaging one-liner:** the 4f Keplerian relay ($M=1$ or not) images a plane — including angle information — onto a distant plane; the standard way to put an AOM's steering pivot, or a mirror, optically "at" an atom or an objective's back aperture.

**Failure modes:**

| Failure | Mechanism | What you see |
|---|---|---|
| lens spacing off | the output converges or diverges | beam size changing along a long path; adjust the spacing while watching the beam far away |
| spherical aberration | a plano-convex lens with its flat side toward the collimated beam bends edge rays too strongly | blurred focus and rings; turn the curved side toward the collimated beam |
| tilt or decentering | rays pass the lenses off axis | astigmatism (the focus is elliptical and rotates through focus) or coma (a comet-shaped spot) |
| internal focus at high power (Keplerian) | the intensity at the focus burns dust or breaks down the air | damage or a spark; use the Galilean form |
| clipping | the expanded beam overfills the second lens | diffraction rings and loss |

> [!question]- Why does expanding a beam 3× before a lens shrink the focused spot 3×?
> Spot size at focus is $w \approx \lambda f/\pi w_{in}$ (equivalently $\sim\lambda\, f/\#$): larger input beam = larger numerical aperture = tighter focus. The expander doesn't add brightness; it converts spare beam-path diameter into focusing angle — the same étendue conservation that divides the divergence by $M$.

# Connections

- [[Ray Transfer Matrices]] — the afocal ABCD above; cascade with the rest of the beamline by multiplication
- [[Gaussian Beams]] — the waist/divergence trade-off and the $M^2 z_R$ scaling both follow from the $q$-parameter
- [[Mode Matching]] — a beam expander is half of every mode-matching solution
- [[Acousto-Optic Modulator]] — 4f relays turn AOM angle scans into pure position-preserving scans at the target

---
Source: Siegman, *Lasers*, Ch. 15 (ray optics and ABCD matrices)
