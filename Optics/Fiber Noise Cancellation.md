#optics #labwork

**Light sent through an optical fiber picks up phase noise from everything that stretches or heats the fiber — sound, vibration, temperature — so a laser that is narrow at the source arrives broadened; reflecting a little light back from the far end gives a sample that has crossed the fiber twice, and comparing it with light that never entered the fiber measures the fiber's noise, so an actuator at the input can cancel it in advance.** The same scheme stabilizes any optical path that changes with time, fiber or free space.

# Reference

**The scheme:**

- An AOM at the fiber input shifts the light by $f_A$ ([[Acousto-Optic Modulator]]).
- A partial reflector at the far end — the fiber's end face, or a partially reflecting mirror — sends some light back.
- The returning light passes the AOM again, so it is shifted by $2f_A$ and carries the fiber's phase twice.
- On a photodiode it beats with light that never entered the fiber ([[Heterodyne Detection]]), giving a signal at $2f_A$ whose phase is

$$
\phi_\text{beat} = 2\,(\phi_\text{AOM} + \phi_\text{fiber})
$$

- $\phi_\text{fiber}$ — one-way phase picked up in the fiber (rad): the noise to cancel
- $\phi_\text{AOM}$ — phase written by the AOM's RF drive (rad): the actuator
- $\phi_\text{beat}$ — phase of the beat note against a stable RF reference (rad)

A phase-locked loop ([[Phase-Locked Loops]]) adjusts the AOM's RF phase to hold $\phi_\text{beat}$ fixed, which forces $\phi_\text{AOM} = -\phi_\text{fiber}$ + constant. Because the correction is applied once on the way in, it pre-compensates the one-way trip, and light arriving at the far end carries no fiber noise.

**Picture:** a two-way trip measures the path, and half the measured correction, applied in advance, cancels the one-way trip — like adjusting a clock by half the round-trip delay of a signal echoed back.

**What the scheme assumes:**

| Assumption | Why it is needed | When it fails |
|---|---|---|
| the noise is the same in both directions | the round trip must measure exactly twice the one-way phase | non-reciprocal effects, such as polarization changes in non-polarization-maintaining fiber |
| the noise is slower than the round trip | the correction must be measured before the noise changes | above roughly $1/(4\tau)$, with $\tau$ the one-way delay (~5 ns per metre of fiber): about MHz for a lab fiber, tens of kHz for a kilometre |
| the reflector marks the point of use | the phase is stabilized at the reflector | any path after the reflector is uncompensated; put it as close to the experiment as possible |

**When it is needed.** Fiber noise is negligible next to a MHz-linewidth laser, but it broadens sub-kHz lasers (clock lasers, narrow references), and it matters whenever the *relative* phase of two beams is used — Raman transitions, optical lattices, interferometers ([[Two-Beam Interferometers]]). Two beams through two separate fibers pick up independent phase noise; two beams sharing one fiber pick up nearly the same noise, which cancels in their relative phase.

**Setting it up — the steps and why:**

1. **Get a beat.** Overlap the returned light with the reference light on a photodiode, and find the beat at $2f_A$ on a spectrum analyzer. Its open-loop width shows the fiber's noise.
2. **Tag the wanted reflection.** Reflections from connectors and the near end face also return; a second AOM at the far end, or angled connectors, gives the far-end light a frequency or direction no other reflection has.
3. **Lock the beat** to a stable RF reference with the AOM's RF drive as the actuator.
4. **Verify out of loop.** Beat the delivered light against an independent path at the far end.

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| beat note with the loop open | the fiber's noise spectrum: acoustic peaks, thermal drift |
| beat note with the loop closed | suppression, and the servo bump at the loop bandwidth |
| an out-of-loop beat at the far end | the phase noise delivered |
| a beat amplitude that fades and returns | polarization drift between returned and reference light |

**Failure modes:**

| Failure | Mechanism | What you see |
|---|---|---|
| spurious reflections | light reflected before the far end beats at the same frequency | a lock to the wrong path, with poor suppression |
| polarization drift | in ordinary fiber the returning polarization wanders, so the beat fades | intermittent lock; use polarization-maintaining fiber, or a Faraday rotator mirror at the far end |
| phase slips | a disturbance larger than the phase detector's range | sudden $2\pi$ jumps; dividing the beat frequency or a phase-frequency detector widens the range |
| delay-limited bandwidth | the round trip is too slow for fast noise | residual noise above $\sim 1/(4\tau)$ |
| reflector not at the point of use | path after the reflector is outside the loop | noise remaining at the experiment despite a good in-loop signal |

> [!question]- Two beams that must keep a fixed relative phase are delivered through two separate 5 m fibers. Each looks clean on its own, but the interference between them is noisy. Why, and what are the fixes?
> Each fiber adds its own, independent phase noise, and the experiment depends on the difference between them. The fixes: send both beams through the same fiber (separated by frequency or polarization), so most of the noise is common and cancels in the difference; or cancel each fiber's noise with its own loop; or measure the relative phase after the fibers and lock it directly.

# Connections

- [[Optical Fibers and Fiber Coupling]] — the fiber whose noise is cancelled
- [[Acousto-Optic Modulator]] — the frequency shifter and actuator
- [[Heterodyne Detection]] — the beat note that measures the phase
- [[Phase-Locked Loops]] — the loop that holds the beat phase
- [[Laser Linewidth]] — the broadening the fiber adds
- [[Intensity Stabilization]] — the same idea applied to power
- [[Two-Beam Interferometers]] — relative-phase stability between paths
- [[Raman Transitions]] — a relative phase that must survive delivery

---
Source: L.-S. Ma, P. Jungner, J. Ye & J. L. Hall, "Delivering the same optical frequency at two places: accurate cancellation of phase noise introduced by an optical fiber or other time-varying path," *Opt. Lett.* 19, 1777 (1994); S. M. Foreman et al., "Remote transfer of ultrastable frequency references via fiber networks," *Rev. Sci. Instrum.* 78, 021101 (2007)
