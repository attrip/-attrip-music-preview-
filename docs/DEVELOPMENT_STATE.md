# DEVELOPMENT STATE

This file is the restart point for autonomous work. Read `docs/CONSTITUTION.md` and `docs/LOCKED.md` before acting.

```yaml
objective: preserve the feeling of playing inside a convincing jazz-funk band
current_issue: 2
current_stage: diagnostic_design
human_required: false
blocked: false
owner: Music Product Director
active_hypotheses:
  - player_harmonic_tail
  - groove_or_source_bass_exposure
  - mix_shared_depth
next_action: build issue-2 A/B/C diagnostic without changing locked production decisions
human_gate_question: null
candidate_preview: null
last_decision: PR #1 merged; development constitution is active
```

## Autonomous execution policy
Continue without human input while the next action can be evaluated objectively.

Stop and set `human_required: true` only when:
- two or more technically valid candidates require a listening preference;
- a LOCKED decision needs an Unlock Request;
- a product-direction decision cannot be inferred from the Constitution/current issue;
- credentials, destructive actions, costs, or external approvals are required.

Do not stop for syntax errors, failed sample loads, regressions, CI failures, malformed PRs or other technical defects. Diagnose and repair those autonomously.

## Human gate contract
When human input is required, provide:
1. one short listening question;
2. at most three candidates;
3. a direct preview URL for each candidate or a single page with instant switching;
4. no technical homework.

After the answer, record the result in `docs/LISTENING_LOG.md`, update this state file, and continue autonomously.
