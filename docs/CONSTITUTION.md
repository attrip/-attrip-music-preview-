# ATTRIP MUSIC Development Constitution

## Product objective
The goal is not to add features. The goal is to make a simple input feel like playing inside a great band.

Primary KPI: **Do I want to press the key again?**

## Non-negotiable rules
1. Treat subjective discomfort as a valid bug report.
2. Diagnose before modifying.
3. Change one meaningful variable per experiment.
4. Every experiment must have an A/B comparison or a clear baseline.
5. If improvement is not demonstrated, REVERT.
6. Protect previously successful decisions with LOCKED status.
7. Never hide a Source problem with effects.
8. Never hide a Performance problem with Mix.
9. Complexity is not Groove.
10. Musical feel outranks theoretical correctness when theory and listening disagree.
11. Implementer cannot self-approve the result.
12. Do not change a LOCKED item without an explicit Unlock Request.

## Roles and authority
### Product Owner
Reports what feels good or wrong and makes the final listening decision. Does not need to prescribe technical fixes.

### Music Product Director
Owns problem definition. Reads the current implementation, classifies the issue, creates up to three hypotheses, chooses the diagnostic experiment and assigns exactly one specialist. Has no authority to change sound directly.

### Player Designer
Owns input response, chord voicing, note-on/off, velocity, sustain/release and the feeling that the user is playing the piano. Must not modify Bass, Drums or Mix.

### Groove Engineer
Owns Bass + Drums as one Rhythm Section: pocket, kick/bass interaction, ghost notes, syncopation, accents, microtiming and fills. Must not modify Piano, Mix or source samples.

### Source Engineer
Owns raw Piano/Bass/Kick/Snare/Hat quality, articulations and velocity layers. Tests DRY. Must not use EQ, reverb, compression or pattern changes to rescue a bad source.

### Mix Engineer
Acts only after Player, Groove and Source pass. Owns balance, EQ, pan, dynamics, stereo placement, room/depth and master path. Must not rewrite performance, patterns, voicings or sources.

### Reference Analyst
Research-only role for acid-jazz/funk references. Extracts structural observations such as pocket, anticipation, accents, voicing and space. Does not copy songs and does not implement.

### Quality Reviewer
Does not create the change. Checks regression, isolation, loudness bias, latency, musicality and immersion. Can reject the experiment.

### Tech Lead
Owns architecture and separation of Player Engine, Piano, Groove Engine, Bass, Drums, Mixer and UI. Does not make musical taste decisions.

## Mandatory workflow
OBSERVE -> CLASSIFY -> HYPOTHESES (max 3) -> ISOLATE -> IMPLEMENT ONE CHANGE -> QUALITY REVIEW -> USER A/B -> LOCK or REVERT.

No `maybe better, continue anyway` state exists.

## Gates
Source changes: SOLO -> RHYTHM SECTION -> BAND.
Mix work may begin only after PLAYER PASS + GROOVE PASS + SOURCE PASS.

## Pull request rule
One PR should represent one problem and one falsifiable hypothesis whenever practical. PR description must state what is deliberately NOT being changed.
