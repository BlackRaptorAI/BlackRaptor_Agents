---
name: gate-verdict-format
description: >-
  The standard output format every gate agent uses so verdicts drop cleanly into
  a Change Record. Use when a security/privacy/compliance/domain/schema gate
  agent produces a verdict on a diff. Triggers: "gate review", "produce a
  verdict", "review for the change record". Shared by all blocking-gate agents.
---

# Gate verdict format (Change-Record-ready)

Every gate agent's output is pasted verbatim into §3 of the PR's Change Record
(`docs/change-records/CR-*.md`) and its verdict fills the §2 gate table. Make it
paste-ready and self-contained.

## Structure

```
## <Gate name> — <agent name>

**Verdict:** PASS | CONCERNS | FAIL
(map to the gate table: PASS = ACCEPT-eligible, CONCERNS = accept-with-
conditions, FAIL = rework or requires a §5 risk-acceptance to overrule)

**Scope reviewed:** <what you looked at — files/paths/diff range>

**Findings:**
- [severity] <finding> — evidence: `path:line` — why it matters — fix.
- (repeat; every finding needs file:line evidence, no vibes)

**Conditions to clear (if CONCERNS/FAIL):** <specific, testable>

**Model/agent version:** <if the agent definition changed recently>
```

## Rules
- **The verdict is advice; the human decides.** You never fill the "My decision"
  column or sign — the human records ACCEPT / ACCEPT-WITH-RISK / REWORK.
- If the human overrules a FAIL, the Change Record's §5 risk-acceptance entry is
  **mandatory** — state that in your output.
- Every finding carries `file:line` evidence. No-evidence items are dropped.
- N/A is a valid verdict for a gate that doesn't apply — but state one line of
  why. An unexplained N/A is the rubber stamp an auditor looks for.
