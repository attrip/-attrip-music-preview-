# ATTRIP MUSIC — Development Method

## Goal

Make a browser instrument where a person who does not know jazz theory can press a laptop key and immediately feel like they are playing inside a jazz/funk band.

The KPI is not version count or feature count.

> Would I press it again for no reason?

## Four product pillars

Every feature must improve at least one of these. Otherwise it goes to the backlog.

1. PLAY — A/S/D/F/G/H/J feel like an instrument.
2. HEAR — the sound itself makes you want to keep playing.
3. SEE — the visual keyboard shows the notes actually sounding.
4. GROOVE — Space puts you inside a convincing jazz/funk rhythm section.

## Roles

### Human / player

Report the experience directly:

- sounds cheap
- bass feels weak
- the change surprises me
- this feels good
- I want to keep playing
- I cannot tell what to press

These observations are treated as evidence.

### Development / analysis

Do not automatically accept the proposed cause.

Example:

- Observation: "the sound feels cheap" — accept.
- Hypothesis: "physical modelling will fix it" — test it.

- Observation: "the chord change surprises me" — accept.
- Hypothesis: "the progression is wrong" — may be wrong; timing, voicing, release or bass movement may be the cause.

Core rule:

> Trust the feeling. Question the cause.

The same rule applies to developer hypotheses. FAUST, samples, FM, physical modelling and any other technology are candidates, not answers.

## Development loop

1. PLAY — use the fixed public test URL.
2. OBSERVE — describe one feeling or problem without solving it yet.
3. DIAGNOSE — split possible causes into variables.
4. EXPERIMENT — change one important variable only.
5. COMPARE — A/B against the previous version and, periodically, a strong reference product.
6. KEEP OR DELETE — keep the winner; remove or archive the loser.

Do not solve several suspected causes in the same experiment unless a technical dependency makes that unavoidable.

## Comparison checkpoint

After roughly 3–4 meaningful iterations, stop adding features and compare with a reference instrument.

The purpose is not copying appearance or code. Ask:

- Why is it easy to understand?
- Why does it feel like an instrument?
- Why do I stay focused?
- What can I hear, see or control there that is missing here?

Recent useful discoveries from comparison:

- dark surroundings improve focus on the instrument
- showing sounding notes on a keyboard is useful, not decorative
- key-down sustain and natural key-up release increase instrument feel
- controls should disappear when they are not needed
- the laptop keyboard itself should feel like the instrument

## Current experiment: SOUND DECISION

Before adding more product features, decide the core keys engine.

Keep all comparison conditions as equal as practical:

- same UI
- same chord
- same voicing
- same velocity target
- same perceived loudness
- backing band OFF

Test four fixed chords:

1. Dm9
2. G13
3. Cmaj9
4. A7#9

Compare candidates:

A. Current Web Audio / FM engine
B. FAUST/WASM modelling prototype
C. High-quality sample-based reference
D. External reference instrument for calibration only

Score 1–5:

- believable instrument
- feels like jazz
- satisfying attack
- want to press it again

The final question has priority over the numerical score:

> Which one would I keep playing for five minutes without being asked?

The winner becomes the production keys engine. A technically interesting loser does not remain merely because time was invested in it.

## Current backlog

Do not prioritize until the sound decision is made:

- MIDI / DAW output
- AI control
- more chord types
- more scales
- elaborate settings
- additional backing-band styles
- advanced recording/export

## Product principle

ATTRIP MUSIC should become simpler on the surface as the engine becomes smarter underneath.

> Press a chord. See what you played. Hear something beautiful. Stay in the groove.
