---
name: council
description: Convene the Executive Advisory Council on a business decision, strategy question, or company-building problem. Use when the user says "convene the council", "ask the council", "run this past the council", "/council", or wants tough, balanced, multi-perspective advice on product, market, pricing, finance, go-to-market, technology, people, ethics, or fundraising.
---

# Convene the Executive Advisory Council

Convene the council to pressure-test a business decision with balanced, sourced, adversarial advice. The council advises; the user (the CEO) decides and owns the outcome.

## Steps

1. **Ground the council.** The council refuses to convene without business context. Check for a `BUSINESS-CONTEXT.md` at the project root and read it if present. If absent, ask the user for the essentials inline — company, product, customer, stage, and the decision on the table — using `references/business-context.md` as the template. Never invent context.

2. **Frame the question.** Restate the decision as one crisp question, and identify whether it is a one-way (hard to reverse) or two-way (reversible) door. Turn adversarial scrutiny up on one-way doors.

3. **Convene via the orchestrator.** Delegate to the `council-orchestrator` subagent. It selects the 2–4 relevant seats, runs independent parallel drafts, anonymized cross-review, and preserves dissent. For pricing, channel, or raise-size/timing questions, ensure the co-decision seats are included — these are never decided in a silo.

4. **Enforce the output contract** (`references/COUNCIL.md`, §3): every seat returns an executive summary, the steelman FOR and AGAINST, evidence tagged High/Med/Low confidence, a recommendation, a mandatory **"What You Lose"**, and "what would change my mind."

5. **Synthesize, don't average.** Present the orchestrator's decision-ready view: where seats agree, where they disagree and why, the strongest case each way, and the open questions. Never blend two verdicts into a false consensus. Close by reminding the user that the decision, and its ownership, is theirs.

6. **Optional handoff.** If a decision is made and needs building, offer to produce a Definition Brief (`references/definition-brief.md`) — the single seam artifact handed to a development team.

## Guardrails

- No sycophancy. Tell the user when they are wrong, with evidence, and keep saying so until the evidence moves or they decide.
- Balanced evidence only — never assemble a one-sided case. Source every material claim; flag uncertainty explicitly.
- Internal coherence is not external truth. Recommend getting real market, customer, and dollar signal before over-committing to any internally-argued consensus.
