#circuits #electronics

**Voltage only exists between two conductors, and a signal pair in a lab is never alone: the instrument chassis, the optical table, the cable shield, and the building earth form a third conductor around it, called ground.** So the pair carries two voltages: red relative to black (differential mode, DM, which carries your signal) and the pair as a whole relative to ground (common mode, CM, where most interference arrives).

# Reference

**Setup:** a sensor sends its signal down a two-wire cable (red and black) to a receiver — a data-acquisition input, an amplifier, or an oscilloscope. Each end has its own local ground. The receiver's is its metal chassis, earthed through its power cord; the sensor's is whatever metal it is mounted on or powered from. The two grounds are joined only through building wiring that carries other equipment's return current, so they sit at slightly different voltages, typically a fraction of a volt at 50/60 Hz. Probe each wire against the receiver's chassis:

$$
V_\text{dm} = V_+ - V_-, \qquad V_\text{cm} = \tfrac12\left(V_+ + V_-\right)
$$

- $V_+, V_-$ — red to ground, black to ground (V): one probe on the wire, the other on the receiver's chassis
- $V_\text{dm}$ — red relative to black (V): produced by the sensor
- $V_\text{cm}$ — the pair's average height above ground (V): produced by the ground difference, not the sensor

**Picture:** two people in an elevator. Their height difference (DM) is the same on every floor; the elevator's height (CM) has nothing to do with them. A tape held between their heads — a differential input — ignores the floor. A laser from the lobby to one head — a single-ended input, which measures one wire against its own chassis — reads floor plus person.

**Currents:** DM current goes out on one wire and back on the other, a small loop whose fields cancel a short distance away. CM current goes out on both wires in the same direction and returns through ground (shield, chassis, earth, or stray capacitance), a large loop that radiates and picks up like an antenna. A ferrite (a ring of magnetic ceramic clamped around the cable) responds only to the net current through it, so it acts on CM alone.

| | Differential mode | Common mode |
|---|---|---|
| Voltage | red relative to black | the pair relative to ground |
| Current | out on one wire, back on the other | out on both, back through ground |
| Noise sources | magnetic field threading the loop between the two wires | ground difference between the two ends ([[Ground Loops]]); equal capacitive pickup on both wires; radio-frequency signals received by the cable acting as an antenna |
| Reduced by | twisting the pair (shrinks its loop); a capacitor from red to black | a differential input; a ferrite, or a common-mode choke (both wires wound together through one ferrite core); isolation (a transformer, or an optical link) so no wire joins the two grounds |
| Unaffected by | differential inputs, ferrites, common-mode chokes | a capacitor from red to black |

**Common-mode rejection ratio (CMRR):** a real differential input lets a small fraction of CM through as if it were signal, and CMRR is that fraction in dB: $\text{CMRR} = 20\log_{10}(A_\text{dm}/A_\text{cm})$, with $A_\text{dm}, A_\text{cm}$ the input's gain for each mode. At 100 dB, 1 V of CM appears as 10 µV of signal. Instrumentation amplifiers reach 100–120 dB at DC, but **CMRR falls with frequency**, typically by 20 dB per decade above a few kHz, so read the datasheet curve at the frequency of the interference.

**CM → DM conversion:** CM is an offset shared by both wires. On the way to the receiver, each wire passes through its own series impedance (sensor output plus cable) and then sees its own impedance to ground at the input (input resistance, stray capacitance, any filter capacitor). Each wire is therefore a voltage divider for that offset, delivering the fraction $Z_\text{in}/(Z_\text{in} + Z_s)$ of it. Matched dividers deliver equal fractions and the difference stays zero; unmatched dividers deliver different fractions, and the difference is a DM voltage the receiver cannot tell from signal:

$$
\left|\frac{V_\text{dm}}{V_\text{cm}}\right| \approx \left|\frac{Z_{s,1}}{Z_{\text{in},1}} - \frac{Z_{s,2}}{Z_{\text{in},2}}\right| \qquad (Z_s \ll Z_\text{in})
$$

- $Z_s$ — that wire's series impedance, sensor output plus cable (Ω)
- $Z_\text{in}$ — that wire's impedance to ground at the receiver (Ω)

With 1 MΩ inputs, source resistances of 1.0 and 1.1 kΩ convert $10^{-4}$ of the CM, which limits the system to 80 dB of rejection however high the receiver's CMRR. Common causes: a filter capacitor on one wire only, unequal sensor output resistances, one wire routed closer to grounded metal. Once converted, no receiver CMRR can remove it, so in practice the system's rejection is usually set by this **impedance imbalance**, not by the receiver.

**Measuring which limit you have:** at the sensor end of the cable, disconnect the sensor and join red to black there. If the sensor was electrically connected to its ground, connect the joined wires to that same ground; if it was floating, leave them floating. The true signal is now zero and CM is unchanged, so whatever the receiver still reads is CM that got through. Compare that reading with $V_\text{cm}$ (oscilloscope from either wire to the receiver's chassis) divided by the receiver's CMRR as a plain ratio (100 dB = $10^5$):
- **Close to $V_\text{cm}$/CMRR:** the receiver's own rejection is the limit.
- **Much larger:** conversion between the joined wires and the receiver — unequal cable runs, or an input component on one wire only.
- **Quiet with the wires joined, noisy with the sensor connected:** the imbalance is in the sensor's own two outputs, which joining the wires removed.

> [!question]- A receiver rated at 120 dB CMRR is connected to a cable carrying 1 V of 60 Hz common mode, yet reads 1 mV at 60 Hz. What is limiting it?
> 1 mV out of 1 V is 60 dB of rejection; the receiver alone would let through 1 µV. The rest is CM → DM conversion: the two wires reach the receiver through unequal impedances, so the shared 60 Hz offset arrives as a difference. Matching the two wires fixes it; a better receiver does not.

# Connections

- [[Instrumentation Amplifier]] — the standard differential input for small signals
- [[Differential Signaling]] — designing a link so interference lands in CM
- [[Ground Loops]] — the main source of the ground difference
- [[Ferrites and Common-Mode Chokes]] — an impedance only CM current sees
- [[Antennas]] — why CM current on a cable radiates and receives
- [[Noise Coupling Mechanisms]] — which coupling route produces which mode

---
Source: Ott, *Electromagnetic Compatibility Engineering*, Ch. 4
