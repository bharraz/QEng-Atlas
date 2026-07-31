#labwork #reference

**Debugging is a procedure, not an inspiration. Agans' nine rules are the procedure; the failure modes they prevent are the ones that cost days.** Stated below with their laboratory instances — the rules are domain-independent, the examples are apparatus.

# Reference

## 1. Understand the system

Know the intended design before probing it. Read the manual, the schematic, the pulse-sequence code — including the parts you wrote and have forgotten. Know the *nominal* values so you can recognize a wrong one: what should the AOM RF power be, what is the photodiode's expected DC level, what trap frequency does this voltage set. A measurement you cannot compare to an expectation is not evidence.

Corollary: know the tools too. A scope's bandwidth, a spectrum analyzer's resolution bandwidth, and a probe's loading capacitance are part of the system while they are attached ([[Time Constants and Reactance Rules of Thumb]]).

## 2. Make it fail

Get a reliable reproduction before attempting a fix. Intermittent problems are hard *because you cannot run the loop* — each test carries no information unless the failure is on demand.

- Find the trigger and make it a knob: does the lock drop when the AC compressor cycles, when someone opens the door, at a particular point in the sequence?
- Stimulate rather than wait: shake the table, breathe on the fiber, tap the mount, step the temperature, deliberately inject the suspected interference.
- Automate repetition — run the sequence 10⁴ times and histogram the failures; a 1% failure needs statistics, not anecdote.
- Don't "fix" an intermittent by changing something and observing its absence for an hour. That is rule 9's trap.

## 3. Quit thinking and look

Instrument the failure instead of reasoning about it. Theories tell you *where to put the probe*; they do not substitute for the trace.

- **Scope**: look at the actual waveform, not the expected one. Trigger on the failure (pulse-width, runt, or logic-pattern triggers exist for this). Use the fastest timebase that still shows the event — the interesting structure is usually at a timescale you weren't displaying. Check DC offsets and coupling before believing amplitudes.
- **Spectrum analyzer**: the frequency domain names sources that the time domain hides. A spur at 50/60 Hz and harmonics is mains; a comb at the trap RF is micromotion or pickup; a broad hump near a servo's crossover is the servo bump ([[Control Beyond PID]]); switching-supply noise sits at tens to hundreds of kHz with harmonics. Set RBW deliberately — narrow to resolve, wide to see transients — and remember the analyzer's own noise floor moves with RBW ([[Bandwidth]]).
- Add instrumentation where none exists: a pickup loop near the RF line, a photodiode on a leakage beam, a spare DAC channel logging the servo output, a temperature sensor on the suspect mount.
- Look at the *whole* signal chain, not just its ends. The bug is usually somewhere you had no visibility.

## 4. Divide and conquer

Binary-search the failure space. Each test should cut the remaining candidates roughly in half, and you should start at whichever end has better observability.

- Inject a known-good signal partway down the chain (function generator in place of the DDS; a torch in place of the fluorescence) and see whether the failure survives.
- Bypass suspect stages: terminate the servo input, disconnect the fiber and measure at the source, replace the AOM drive with a static tone.
- Bracket in time as well as space: at what point in the sequence does the state go wrong? Insert measurements mid-sequence.
- Start at the bad end (where the symptom is) and walk upstream; work toward the middle if both ends look fine.

## 5. Change one thing at a time

Use a rifle, not a shotgun. Change one parameter, observe, change it back.

- Keep a known-good configuration you can return to — a saved parameter set, a photographed beam path, a git commit of the sequence code.
- Compare against a working instance: another channel, another ion, yesterday's data, an identical setup on the next table. The *difference* is the lead.
- When something you changed did not fix it, put it back. Accumulated undone changes are how a debuggable system becomes an unfamiliar one.

## 6. Keep an audit trail

Write down what you did, in what order, and what happened — including the numbers, not "looked fine."

- The detail you don't record is the one that turns out to matter; two days later you cannot reconstruct whether the drift started before or after you re-tuned the AOM.
- Timestamp against the environment: HVAC cycles, building activity, lab temperature logs, other experiments on the same power circuit.
- Save raw traces, not conclusions. Screenshots of the scope and analyzer cost nothing and are re-interpretable later.

## 7. Check the plug

Question assumptions, especially the ones too basic to state.

- Is it powered, enabled, unblocked, connected to the port you think? Is the shutter open, the flipper down, the interlock satisfied?
- **Test the tool**: is the scope on 50 Ω or 1 MΩ ([[Time Constants and Reactance Rules of Thumb]])? Is the probe compensated? Is the analyzer's reference level clipping the front end? Is the DMM on the right range? Is the "dead" photodiode reverse-biased the right way round?
- Is the calibration you're trusting still valid — and was the instrument reading a stale or averaged value?
- Start at the beginning: verify the input is what you think before debugging the output.

## 8. Get a fresh view

Ask someone. Report **symptoms, not theories** — describing the fault to a colleague forces the ordering of facts that often solves it, and your own expertise is precisely what makes you skip the wrong assumption. Someone who does not know the design cannot make the same skip. Also: ask the people who built the thing, and read what other groups found (this failure is usually not new).

## 9. If you didn't fix it, it ain't fixed

A problem that stopped appearing has not been shown to be solved.

- Verify by turning the cause back on: reintroduce the stray field, re-loosen the connector, put the noisy supply back. If the symptom returns and then leaves again with the fix, you found it. If it does not return, you never understood it.
- Distinguish "fixed" from "masked" — increasing servo gain until the drift is invisible leaves the drift.
- Check it stays fixed over the timescale that matters (a lock that survives 10 minutes is not a lock that survives a data run).

> [!question]- An ion chain loses one ion every few hours, always overnight. What do the rules say to do first, and what is the tempting mistake?
> The tempting mistake is rule 5 violated as a shotgun — retune the trap voltages, raise the cooling power, bake the chamber, all at once, then declare victory when a night passes cleanly. Rule 2 comes first: make it fail on demand. Correlate against logged variables (pressure gauge, lab temperature, HVAC schedule, other equipment on the timer) to find the trigger, then reproduce it deliberately during the day — spike the pressure, cycle the temperature, switch the suspect equipment. Only with a reproduction can rule 4 bisect the cause, and only then can rule 9 confirm the fix by re-triggering it.

# Connections

- [[Noise Coupling Mechanisms]] — rule 4 applied to interference: a diagnosis table that halves the candidates per test
- [[Time Constants and Reactance Rules of Thumb]] — rule 3's symptom→cause map for analog signals
- [[Conventions and Factor-of-Two Traps]] — rule 7 for numbers: the assumption most often wrong is a convention
- [[Control Beyond PID]] — recognizing servo-induced symptoms rather than chasing them upstream
- [[Vacuum Engineering]] — the rate-of-rise test as a textbook rule-4 bisection
- [[Surface and Film Metrology]] — cross-checking one instrument against another (rule 8 for measurements)

---
Source: D. J. Agans, *Debugging: The 9 Indispensable Rules for Finding Even the Most Elusive Software and Hardware Problems* (AMACOM, 2002)
