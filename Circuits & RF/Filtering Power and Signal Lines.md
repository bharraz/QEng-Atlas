#circuits #electronics

**Noise reaches a sensitive device along every wire connected to it — the supply, the bias and control lines, the signal leads, the cable shields — so filtering means placing, where each wire enters the protected region, a series element that impedes the noise (a resistor, inductor, or ferrite) and a shunt element that returns it to ground before it arrives (a capacitor).** The filter is a voltage divider whose ratio changes with frequency, and it works only as well as the path the shunted noise takes back to its source.

# Reference

$$
\frac{V_\text{out}}{V_\text{in}} = \frac{Z_p}{Z_s + Z_p} \approx \frac{Z_p}{Z_s} \quad (|Z_s| \gg |Z_p|)
$$

- $Z_s$ — series impedance in the line (Ω): resistor, inductor, or ferrite
- $Z_p$ — shunt impedance to the return (Ω): usually a capacitor
- $V_\text{in}, V_\text{out}$ — noise voltage before and after the filter (V)

A single RC attenuates by $f/f_c$ above its corner, 20 dB per decade ([[RC and RL Filters]]). Reaching 60 dB at 1 MHz with one pole needs the corner at 1 kHz; two poles reach it with corners near 30 kHz, provided each stage does not load the previous one.

**Picture:** every wire into the protected region as a doorway: the series element narrows it for noise, and the shunt capacitor gives the noise a shorter way home.

**Choosing the filter for the line:**

| Line | Typical filter | Why | Watch for |
|---|---|---|---|
| DC bias or control voltage (gate, piezo, current-driver input, electrode) | RC low-pass, corner far below the noise | no DC current flows, so a large resistor costs nothing | settling time $RC$ slows deliberate changes; leakage current × $R$ becomes an offset; the resistor's own [[Johnson-Nyquist Noise]] |
| DC line carrying current (supply rail, coil current) | inductor or ferrite plus capacitor; a capacitor–inductor–capacitor "π" for more attenuation | a resistor would drop voltage and dissipate power, an inductor passes DC freely | the LC resonance amplifies noise at $1/2\pi\sqrt{LC}$ unless damped; DC current can saturate the inductor's core |
| supply from a switching converter | LC post-filter, or a linear regulator followed by an LC or ferrite | ripple and spikes at the switching frequency and its harmonics | regulators reject well at low frequency and poorly at high frequency |
| analog signal line | low-pass just above the signal band, at the receiving end | removes out-of-band RF that amplifier inputs would rectify into DC shifts | phase shift in the band, and loading of the source |
| any line entering a shielded enclosure | feedthrough capacitors or filtered connectors mounted in the wall | the shunted noise must return to the shield at the entry point ([[Grounding and Shielding Practice]]) | a filter inside the box leaves the incoming cable as an antenna inside |
| RF and microwave lines | packaged low-pass, band-pass, or DC-block | reflective filters send rejected power back toward the source; absorptive filters dissipate it | reflections set up standing waves on the line ([[Impedance Matching]]) |
| lines into a cryostat | attenuators on RF lines and RC or absorptive filters on DC lines, at the cold stages | room-temperature noise must be absorbed where its heat can be removed ([[Cryogenics]]) | each element's heat load on its stage |

**Damping an LC filter.** A low-loss inductor and capacitor form a resonator: at $f_0 = 1/2\pi\sqrt{LC}$ the filter *amplifies* by its quality factor $Q = \sqrt{L/C}/R$, with $R$ the total series resistance ([[LC Resonators]]). Damping adds loss at resonance without spoiling the DC path: a resistor of about $\sqrt{L/C}$ in series with an extra capacitor several times larger, placed across the output, or a lossy ferrite in place of the inductor ([[Ferrites and Common-Mode Chokes]]).

**Placement and the return path.** The shunt capacitor works by giving the noise current a short way back, so its connection to ground or shield must be short: about 1 nH of inductance per millimetre limits it at high frequency ([[Decoupling and Bypassing]]). A filter at the source end of a long cable lets the cable pick up noise after the filter, so filter at the device. Keep the filter's input and output wiring apart: stray capacitance between an input wire and an output wire carries high frequencies straight past the filter.

**Capacitor choice** matters: class-2 ceramics lose capacitance under DC bias and are piezoelectric, electrolytics leak and fail above ~100 kHz, film capacitors are stable but large ([[Capacitors in Practice]]).

**What each measurement tells you:**

| Measurement | What it tells you |
|---|---|
| noise spectrum at the device with and without the filter | the actual attenuation, including any path around the filter |
| noise that does not fall when the filter is added | the noise enters another way — another wire, the ground, radiation ([[Noise Coupling Mechanisms]]) — or the filter's return path is poor |
| a step applied at the input, output on a scope | settling time, and ringing from an undamped LC resonance |
| DC voltage at the output under load | the drop across the series element, and offsets from leakage |

**Failure modes:**

| Failure | Mechanism | What you see |
|---|---|---|
| LC resonance | undamped inductor and capacitor | noise amplified at one frequency; ringing on steps |
| filter bypassed | input and output wires close together, or a long ground lead on the capacitor | little attenuation at high frequency |
| inductor saturation | DC current saturates the core and the inductance collapses | filtering lost at high current |
| ceramic capacitor derating | class-2 dielectric loses capacitance under DC bias | corner frequency higher than designed |
| new ground loop | shunt capacitors tie the line to a different ground than its source uses ([[Ground Loops]]) | fresh hum after adding the filter |
| slow response | large $RC$ on a control line | a voltage that lags its command |

> [!question]- A 100 µH inductor and a 10 µF capacitor added to a noisy supply line made the noise *worse* near 5 kHz. Why, and what fixes it?
> They resonate at $1/2\pi\sqrt{LC} \approx 5$ kHz, and with only a fraction of an ohm of series resistance against $\sqrt{L/C} \approx 3$ Ω the quality factor is in the tens, so noise near 5 kHz is amplified rather than removed. Add damping: about 3 Ω in series with a capacitor several times larger than 10 µF, across the output, or replace the inductor with a lossy ferrite.

# Connections

- [[RC and RL Filters]] — the single-pole corner and loading
- [[Capacitors in Practice]] — which dielectric to use
- [[Decoupling and Bypassing]] — capacitors at the supply pins of chips
- [[LC Resonators]] — the resonance an LC filter must not have
- [[Ferrites and Common-Mode Chokes]] — lossy series elements and common-mode filtering
- [[Grounding and Shielding Practice]] — where the shunted noise goes
- [[Noise Coupling Mechanisms]] — the other ways noise arrives
- [[Ground Loops]] — what a careless filter ground can create
- [[Filter Families]] — active filters when a passive one is not steep enough
- [[Johnson-Nyquist Noise]] — the noise a filter's resistor adds

---
Source: H. W. Ott, *Electromagnetic Compatibility Engineering* (Wiley, 2009), Ch. 5; P. Horowitz & W. Hill, *The Art of Electronics*, 3rd ed. (Cambridge, 2015), Ch. 1 and 9
