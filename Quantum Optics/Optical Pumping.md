#quantum-optics

**Scatter photons until the population falls into a state the light can't touch — a dark state — where it stays.** It's a random walk with an absorbing wall: selection rules bias each absorption step, spontaneous emission shuffles, and everything piles up in the one state decoupled from the drive. It is the standard state-preparation method in AMO experiments.

# Reference

**Polarization selects the destination.** Drive $\sigma^+$: every absorption steps $\Delta m_F = +1$, every emission steps $\Delta m = 0, \pm 1$ — net drift up the Zeeman ladder until the stretched state $|F, m_F = +F\rangle$, which has no $m+1$ partner to absorb into. Dark. Done in a few scattering times.

**Picture:** a random walk with a trapdoor: each scattering step moves the atom between sublevels, and the walk ends in the one state the light cannot excite.

**Frequency selects too.** Driving $F \to F' = F$ with $\pi$ light makes $|F, m_F = 0\rangle$ dark ($\Delta m = 0$ to $m'=0$ is forbidden for $F' = F$) — this is how clock-state prep works, e.g. pumping into the $|F=0\rangle$ hyperfine ground state by emptying $F=1$.

**Imperfect light makes the dark state leak.** Fidelity limits, in order of typical importance:

| leak | mechanism | fix |
|---|---|---|
| polarization impurity $\epsilon$ | dark state scatters at $\sim\epsilon^2 \times$ full rate | clean polarizer, B-field aligned to k or quantization axis |
| off-resonant excitation | pumps *out* of the target via nearby $F'$ levels | detune choices, weaker intensity, patience |
| decay to metastable/other hyperfine states | population parks outside the cycle | repump laser to close the loop |

Steady-state fidelity is set by the *ratio* of pumping-in to leaking-out rates — more power doesn't always help, since off-resonant depumping scales with intensity too. Typical: >99% in a few μs.

> [!question]- Why can pumping fidelity get *worse* when you turn the pump power up?
> The wanted pumping rate and the off-resonant depumping rate both scale linearly with intensity, so their ratio — which sets the steady-state fidelity — doesn't improve; meanwhile power broadening brings in levels that were assumed to be far off resonance.

# Connections

- [[Selection Rules]] — the $\Delta m$, $\Delta F$ machinery that makes states dark
- [[Hyperfine Structure]] — where the target qubit/clock states live
- [[Zeeman Effect (Atlas)]] — defines the quantization axis and the $m_F$ ladder you walk
- [[Spontaneous Emission and Linewidth]] — the randomizing step of the walk, and the leak channel
- [[Doppler Cooling]] — the other thing photon scattering does for you, usually immediately before it

---
Source: Loudon, *The Quantum Theory of Light*, 3rd ed. (with Foot, *Atomic Physics*, Ch. 9 for working details)
