# Autonomous Development Loop

## Goal
The Product Owner should not need to supervise routine development. The system advances until a genuine listening decision is required.

## Loop
1. Read CONSTITUTION, LOCKED, DEVELOPMENT_STATE and active Issue.
2. Execute `next_action`.
3. Run objective guards: syntax, load paths where testable, regressions, LOCK violations, latency/structure checks where available.
4. If a technical check fails, repair it without asking the Product Owner.
5. Open/update a focused PR with one hypothesis and explicit unchanged systems.
6. Quality Reviewer evaluates objective criteria independently of the Implementer role.
7. If objective evidence rejects the change: REVERT, document why, update state and try the next allowed diagnostic.
8. If objective evidence passes and listening preference is not required: merge and continue.
9. If subjective listening is the only unresolved gate: set `human_required: true`, create a preview with <=3 instant-switch candidates, ask one question, then stop.
10. After human answer: log exact result, LOCK/REVERT as appropriate, set `human_required: false`, choose next owner/action and resume.

## Escalation rules
Do not ask the human to diagnose browser errors, HTTP failures, syntax errors, Git conflicts, CI failures or which specialist should act.

Do ask the human when the question is inherently experiential, e.g.:
- Which version keeps immersion?
- Which groove makes you move more?
- Which source feels more like a real instrument?

## Safety rails
- Maximum three active hypotheses.
- Maximum three human listening candidates.
- One meaningful production variable per experiment.
- Never stack an unproven fix on another unproven fix.
- A failed experiment is useful evidence; record it and revert.
- Human silence means wait at a Human Gate, not invent a preference.
