#quantum-optics #quantum-info

**Two qubits too far apart to interact can still be entangled through light: each emits a photon entangled with it, the two photons meet on a beamsplitter between them, and a detection pattern that cannot reveal which qubit sent which photon heralds that the qubits are now entangled.** That heralded link is the basic element of a quantum network, extended over long distances by swapping entanglement between links.

# Reference

**Encoding the photon:**

| Encoding | Photon carries the qubit in | Strength | Weakness |
|---|---|---|---|
| polarization | two polarizations | simple analysis | birefringence of fiber scrambles it |
| time-bin | early or late emission | robust in fiber | needs stable delay interferometers |
| frequency | two colours | natural for some level schemes | needs frequency conversion or filtering to interfere |
| photon number | photon present or absent | one photon per link | requires optical phase stability between nodes |

**Two ways to herald:**

| | Single-photon scheme | Two-photon scheme |
|---|---|---|
| What is detected | one click after the beamsplitter | two clicks, one from each node, in a Bell-state measurement ([[Hong-Ou-Mandel Interference]]) |
| Success probability per attempt | $\approx 2p\,\eta$, with $p$ the excitation probability | $\tfrac12\eta^2$ |
| Fidelity limit | $1 - p$: double excitation goes undetected | set by photon distinguishability |
| Requirement | optical path lengths stable to a fraction of a wavelength ([[Fiber Noise Cancellation]]) | none on optical phase |

- $\eta$ — probability that one emitted photon reaches and fires a detector
- $p$ — probability that a node is excited and emits in one attempt

The single-photon scheme trades fidelity for rate and needs interferometric stability; the two-photon scheme is phase-insensitive but scales as $\eta^2$, which is why collection efficiency sets network rates ([[Ion-Cavity Coupling]]).

**Picture:** the beamsplitter erases the "which emitter" information — a detection that could have come from either node leaves the two nodes in a superposition of having sent it.

**Rate and distance.** Each attempt must wait for the heralding signal to travel back, so

$$
R \approx \frac{P}{T_\text{attempt}}, \qquad T_\text{attempt} \gtrsim \frac{L}{c_\text{fiber}}, \qquad \eta \propto e^{-L/L_\text{att}}
$$

- $R$ — rate of heralded entangled pairs (s⁻¹)
- $P$ — success probability per attempt (from the table)
- $L$ — distance between the nodes (m)
- $c_\text{fiber}$ — light speed in fiber, ~2×10⁸ m/s
- $L_\text{att}$ — attenuation length: ~22 km at 1550 nm, far shorter at visible wavelengths

so the rate falls exponentially with distance, and memories must hold their state for at least the communication time.

**Repeaters.** A long link is divided into shorter segments; each segment is entangled independently and stored, and Bell-state measurements at intermediate nodes swap the entanglement to the ends ([[Quantum Teleportation]]). Entanglement distillation consumes several noisy pairs to make fewer, better ones. Later designs replace heralding and distillation with error-corrected encodings sent one way.

**Platforms:**

| Platform | Strength | Main difficulty |
|---|---|---|
| trapped ions | long memory, high-fidelity local gates | collection efficiency; UV and visible wavelengths need conversion ([[Ion-Cavity Coupling]]) |
| neutral atoms in cavities | efficient cavity interfaces | trapping inside a cavity |
| colour centres (NV, SiV, SnV) | nuclear-spin memories; nanophotonic cavities | small zero-phonon fraction for NV; spectral diffusion ([[Color Centers]]) |
| quantum dots | bright, fast photon sources | spin coherence; inhomogeneous emission frequencies |
| rare-earth ions | telecom-wavelength transitions (Er³⁺), long-lived memories | weak optical transitions |
| superconducting qubits | fast local processing | photons are microwave: optical links need microwave-to-optical transduction (electro-optic, optomechanical, and other converters), an open research area ([[Cavity Optomechanics]]) |

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| HOM visibility between photons from the two nodes | their indistinguishability, which caps the link fidelity |
| correlations of the heralded pair in two or more bases | the entangled-state fidelity |
| heralding rate against attempt rate | the end-to-end efficiency $\eta$ |
| photon linewidth compared with the lifetime limit | spectral diffusion and dephasing of the emitter |
| $g^{(2)}(0)$ of each source | multi-photon emission, a source of false heralds ([[Photon Statistics and g2]]) |

**Failure modes:**

| Failure | Mechanism | What you see |
|---|---|---|
| distinguishable photons | frequency mismatch, timing jitter, polarization mismatch | reduced HOM visibility and fidelity |
| multi-photon emission | double excitation of an emitter | heralds with the wrong state |
| optical phase drift | path-length changes between nodes in single-photon schemes | fidelity that varies over time |
| memory decoherence | the stored qubit dephases while waiting for the herald | fidelity falling with distance and wait time |
| detector dark counts | false clicks ([[Photon Detectors]]) | heralds with no entanglement, dominant when $\eta$ is small |

> [!question]- What does the two-photon heralding scheme give up compared with the single-photon scheme, and what does it gain?
> It gives up rate: success scales as $\eta^2$ instead of $\eta$, which costs heavily over lossy links. It gains phase insensitivity — no interferometric stabilization of the path between nodes — and a fidelity not limited by the excitation probability. Short links with good collection favour two photons; long, lossy links favour single-photon schemes with active phase stabilization.

# Connections

- [[Ion-Cavity Coupling]] — collecting photons from an emitter into one mode
- [[Hong-Ou-Mandel Interference]] — the two-photon interference behind the Bell-state measurement
- [[Bell States]] — what a heralded link produces
- [[Quantum Teleportation]] — entanglement swapping is teleportation of entanglement
- [[Color Centers]] — solid-state network nodes
- [[Photon Detectors]] — the detectors whose efficiency and dark counts set rate and fidelity
- [[Fiber Noise Cancellation]] — phase stability for single-photon schemes
- [[Optical Fibers and Fiber Coupling]] — the channel and its loss
- [[Purcell Effect]] — enhancing emission into the collected mode
- [[Quantum Entropies and Information]] — capacities of quantum channels
- [[Bell Inequalities and Nonlocality]] — loophole-free tests and device-independent links

---
Source: H. J. Kimble, "The quantum internet," *Nature* 453, 1023 (2008); S. D. Barrett & P. Kok, *Phys. Rev. A* 71, 060310 (2005); S. Wehner, D. Elkouss & R. Hanson, "Quantum internet: a vision for the road ahead," *Science* 362, eaam9288 (2018); A. Reiserer & G. Rempe, *Rev. Mod. Phys.* 87, 1379 (2015)
