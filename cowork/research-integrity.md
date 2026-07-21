---
name: research-integrity
description: >-
  Load for ANY research, analysis, or evidence-based reporting task — market /
  competitive research, source appraisal, "which X is best / most
  cost-effective", market sizing or statistics, synthesizing studies, or before
  publishing any finding or citing a number a decision rests on. Enforces
  mode-appropriate methodology, separate source-reliability × evidence-certainty
  grading, citation-independence (anti-woozle), root-to-mechanism verification,
  and a release gate so conclusions withstand scrutiny and challenge. Triggers:
  "research X", "is there a market for", "which is better", "how big is",
  "what does the evidence say", "cite a source", "before we publish".
---

> **Self-contained Cowork edition** — the fillable artifact templates are included at the bottom of this file (§ Artifact templates), so nothing is lost on a single-file upload. Full design rationale + all 29 artifacts: `BlackRaptor_Agents/development/docs/research-integrity-spec.md`.

# Research Integrity

We are usually **analysts appraising and synthesizing what others produced** — occasionally generating our own data. The job is not to find the stat that fits the story; it is to reach **our own graded judgment that survives adversarial challenge**, and to trace claims to the **root** (primary source) and the **mechanism** (why it's true) — because the root holds the justification and the path forward. This skill is the process. Scale it to stakes (§1).

## 0. Non-negotiables (every mode)
1. **Grade two things separately, never as one word:** source *reliability* (trust the messenger?) and claim *certainty* (how much do we believe *this* claim?). Use the Admiralty grid (reliability A–F × credibility 1–6) + a GRADE-style certainty for a body of evidence.
2. **Repetition ≠ evidence. Independence is the master variable.** Collapse citation chains to their **origin** and count the **effective-N of independent origins**, not raw source volume. N sources reciting one origin = one source. (This is the Woozle effect — how "everyone knows" a number that traces to one weak study. Don't continue one; don't originate one.)
3. **A reachable root is not a true root.** Separate **root-reachability** (did we find the origin?) from **root-veracity** (is the origin likely correct?). Never let the first stand in for the second.
4. **Mechanism must be a *testable entailment*, not a story.** "Why it's true" earns nothing unless it implies something else observable ("if this holds, X and Y must also be true") that you then check. Articulate confabulation is not understanding.
5. **Disconfirmation beats confirmation.** Rank hypotheses/options by evidence *inconsistent* with each (ACH), and actively fetch the strongest *credible dissent*. A claim you didn't try to kill is ungraded.
6. **Freeze the method before the answer** (Mode C especially): commit the question + analysis plan / decision weights before you see the data or scores.
7. **Our judgment ≠ raw reporting.** Every output labels each claim as sourced-fact / stated-assumption / our-inference, carries calibrated confidence, and **preserves dissent**.
8. **The release gate.** Grade everything internally; **publish only claims that clear the "withstands reasonable scrutiny" bar.** Low-confidence material stays in the working set, labeled — it informs thinking, it is not asserted externally.

## 1. Intake triage (run FIRST — sets how heavy to go)
| Tier | When | Effort |
|---|---|---|
| **LITE** | low-stakes AND reversible AND not published (e.g. "which $400 dev GPU") | trace-to-root the 1–2 load-bearing numbers, verify at the primary/vendor source, one-axis grade, BLUF out. Skip the heavy artifacts. |
| **STANDARD** | consequential but internal/reversible | full mode track; core artifacts; single-grader + a self-blind-order pass. |
| **HEAVY** | irreversible, high-cost, adversarial, OR public-facing/publishable (it becomes someone's root) | full track + escalation artifacts + **`evidence-auditor` review before it's trusted**. |
**Escalation is one-way and automatic:** if irreversibility, a spend threshold, external publication, or a load-bearing claim graded Low-with-no-fallback appears mid-task → promote a tier and re-open the gate.

Also triage each load-bearing claim: **rootable** (primary source reachable → normal), **consilience-only** (no single root but independent lines → §Consilience), **unknowable** (neither → HARD-FAIL: may enter only as a labeled *assumption*, and the decision must be robust whether it's true or false).

## 2. Mode-selector (after triage, before researching)
First tag each artifact by **genre, not its title**: a peer-reviewed/registered study → Mode-A tools; a vendor/grey/practitioner artifact (whitepaper, marketing benchmark, forum post, analyst PDF) → Mode-B tools **even if it's called a "study."**

- **Mode A — Evidence synthesis:** appraise & synthesize others' *scientific* studies/reports. *(Woozle risk: continuing — amplifying a weak/echoed primary.)*
- **Mode B — Direct-source aggregation:** gather direct facts + practitioner testimony (specs, prices, benchmarks, reviews) into OUR dataset to drive a **decision** ("best architecture for X", "most cost-effective Y"). *(Woozle risk: both — echoed specs + bandwagon "popular ≠ best".)*
- **Mode C — Original primary research:** we generate NEW data with our own instrument. **C-internal** (a benchmark we run to decide → feeds a Mode-B matrix) vs **C-publishable** (intended to become a public root → full instrument-validity load). *(Woozle risk: originating — we could start one.)*

A mixed task decomposes into sub-tasks, each classified separately.

## 3. Per-track method (condensed — the fillable templates are at the bottom of this file)
**Mode A:** find the body of evidence (not one paper) → appraise each (risk-of-bias) → **collapse citations to independent origins** (effective-N ledger) → run **ACH** across the competing conclusions → grade the body (GRADE/SoF; **single-study cap = Moderate**; imprecision computed) → state our judgment + dissent.

**Mode B:** define the decision + **lock weighted criteria BEFORE scoring** (≤7 criteria, weights sum 100%, timestamped) → MoSCoW knockouts → gather facts+testimony → **verify every spec/price at the primary/vendor source** (hash + retrieval date + TTL) → score each option, tagging provenance per cell → **astroturf/independence screen** on testimony (weight by demonstrated hands-on use + independence) → **sensitivity/robustness** (±10–20% on weights; ROBUST/FRAGILE) → pre-mortem → graded recommendation.

**Mode C:** pre-register (question, DV, conditions, exact analysis, stopping rule) → design the instrument (avoid leading/double-barreled; validity/reliability) → **adversarial instrument review** ("what would make this produce a flattering-but-false result?") → pick the population + medium/channel to reach it (coverage/sampling/nonresponse — Total Survey Error) → pilot → refine → field → analyze the *pre-registered* way → publishable data is labeled with its method; C-internal data is labeled *"provisional — not collected under publishable controls."*

## 4. Consilience (when the origin is unreachable)
Independent lines converge → confidence — **but only if independent.** For each line, name its method/data/investigator AND its **error mode**; convergence counts only when the error modes are **disjoint** (default assumption: correlated, so argue it). Same-origin echoes are not lines.

## 5. The release gate (before anything external)
Publish a claim only when: root reached OR consilience argued; **root-veracity** assessed (not just reachability); **effective-N ≥ 2 independent origins** (or an explicit, logged single-source override for a fully-verified gold-standard primary — caps at Moderate otherwise); the **qualifier-drift diff** vs the origin's wording is empty (we didn't harden a hedge); dissent recorded; and the claim clears its tier's confidence floor. **HEAVY / publishable → `evidence-auditor` signs off first.** Anything failing stays internal, labeled.

## 6. Output format (analytic judgment, not a link dump)
BLUF (the judgment first) → the graded evidence (each load-bearing claim: our claim · source reliability×credibility · effective-N · root status · confidence) → **preserved dissent / strongest counter-case** → what would change the answer → the "so what". Label every line sourced-fact / assumption / our-inference.

## Tier defaults (starting config — tune from real runs via `AGENT-RETROS.md`)
Dual-grading: LITE none · STANDARD ≥10% sample · HEAVY all load-bearing. · Reviewer: distinct-role subagent + rules checks now; `evidence-auditor` for HEAVY; different model family later. · TTL: prices 7d · specs 90d · literature 12mo · security advisories 24h. · Single gold-standard source may reach High only via a logged reviewer override (else capped Moderate).

## Producer/reviewer
You (the producer) run this skill. For **HEAVY or publishable** work, a **separate reviewer must be independent of you** — invoke **`evidence-auditor`** (a distinct gate agent), never self-review. That independence is the point; a same-architecture self-check is correlated failure, not review.

---

# Artifact templates

Fillable templates for the `research-integrity` skill. Use the ones the task's tier and mode call for (proportionality — LITE tasks need only the triage card + a source-verification line + the report format; don't generate the whole set). Full catalog + rationale: `research-integrity-spec.md` §6.

---

## 0. Intake triage card *(all tasks)*
```
Task: <one line>
Stakes/reversibility tier: LITE | STANDARD | HEAVY   (escalation triggers seen: <none | ...>)
Mode: A (synthesis) | B (direct-source) | C-internal | C-publishable
Load-bearing claims + root-availability:
  - <claim> → rootable | consilience-only | unknowable(HARD-FAIL → assumption only)
Reviewer required (HEAVY/publishable)? yes → evidence-auditor | no
```

## 1. ACH matrix — Analysis of Competing Hypotheses *(Modes A, B)*
Rank by evidence *inconsistent* with each hypothesis, not consistent. Conclusion = the **least-disconfirmed**, plus what was rejected and why.
```
Evidence (reliability grade, root-ID) | Diagnosticity | H1 | H2 | H3
E1  (B2, root=doi:...)                 | high          | C  | I  | I
E2  (D4, root=vendor-blog)             | low           | C  | C  | N/A
...
Per-hypothesis  Inconsistent tally:      —   | 3  | 1  | 4
```
`C`=consistent, `I`=inconsistent, `N/A`=not applicable. High-consistency + zero-diagnosticity evidence (everyone echoes it) is formally worthless — flag it.

## 2. Admiralty source grid + anchored grade *(all)*
Grade the **source** and the **claim** separately.
```
Source reliability:  A completely reliable · B usually · C fairly · D not usually · E unreliable · F cannot judge
Claim credibility:   1 confirmed by independent sources · 2 probably true · 3 possibly · 4 doubtful · 5 improbable · 6 cannot judge
Record as {reliability}{credibility}, e.g. B2. Watch the A1/B2/C3 diagonal — over-clustering there is a bias smell.
```

## 3. GRADE / Summary-of-Findings profile *(Mode A)*
```
Claim/outcome | #studies & design | risk-of-bias | inconsistency | indirectness | imprecision(OIS/CI) | pub-bias | non-independence | qualifier-drift | effect + CI | CERTAINTY (High/Mod/Low/VeryLow)
```
Rules: **certainty = the lowest surviving domain** (bottleneck, not average). **Single study caps at Moderate.** One footnote per downgraded domain.

## 4. Citation-chain ledger + effective-N *(all)*
```
Claim: <text>
Citing node → what IT cites → hops-to-root → root type (primary data / method / bare assertion / dead-end) → reached origin? Y/N
  sourceA → cites sourceX → 2 → primary-dataset → Y
  sourceB → cites sourceX → 2 → (same origin)   → Y
  sourceC → own measurement → 0 → primary        → Y
RAW sources: 3   →   EFFECTIVE-N independent origins: 2   (sourceX-lineage, sourceC)
```

## 5. Independence audit (7 channels) *(all)*
A pair is independent only if **all** are "no":
```
Sources | same data? | same author/org? | one cites the other upstream? | same funder? | one propagated from the other? | shared model/training-corpus? | temporal cascade (later just echoes earlier)?
```
Channel #6 (shared-model/corpus) over-fires — treat as **flag-and-argue** for load-bearing claims, not auto-reject.

## 6. Qualifier-drift diff *(all — esp. before publishing)*
```
Origin wording:  "<verbatim, with its hedges/scope>"
Our wording:     "<ours>"
Modal/scope changes: <none = PASS | "may" → "does", "in one bank" → "companies", range → point>
```

## 7. Consilience worksheet *(when origin unreachable)*
```
Line | method | data | investigator | NAMED error mode | disjoint from other lines? (argue; default: correlated)
Convergent confidence only if ≥2 lines with argued-disjoint error modes.
```

## 8. Key Assumptions Check *(A, B, C)*
```
Assumption | why we believe it | confidence H/M/L | what would falsify it | still supported? | if false, does the conclusion collapse?
```

## 9. Mode-B decision matrix *(Mode B)*
Lock weights (timestamped) BEFORE any scoring. ≤7 criteria; weights sum to 100%.
```
Weights locked: <timestamp>
Criterion (weight%) | Option A (score 1–5, weighted, provenance-tier, source URL/hash) | Option B ... 
MoSCoW knockouts applied: <options eliminated + why>
Sensitivity: per-weight ±10/20% → rank stable? ROBUST | FRAGILE (which weight flips it)
Pre-mortem (T+12mo failure): <top risks + mitigations>
Recommendation + confidence + dissent:
```

## 10. Source-integrity scorecard + astroturf screen *(Mode B testimony)*
```
Source | hands-on tier | independence {organic / disclosed-incentivized / insider / affiliate / undisclosed→reject} | track record | reliability A–F | credibility 1–6
Astroturf red flags: near-duplicate wording · burst vs baseline · bimodal 5★/1★ · new-account cluster · co-review collusion · extreme sentiment + low detail · no verified purchase · undisclosed #ad
```

## 11. Vendor-fact verification + hash-vault *(Mode B, Lite)*
```
Claim | reviewer-reported value | PRIMARY-source value | URL | retrieval date | content hash | TTL/re-check date | status {verified / conflict / unverifiable / stale}
```

## 12. Pre-registration *(Mode C — lite version for C-internal)*
```
Status: pre-data | post-data(exploratory, labeled)
Question / hypothesis:
Dependent variable + exact operationalization:
Conditions & assignment (randomization?):
EXACT primary analysis (test, model, comparisons):
Outlier / exclusion rules (decided now):
Sample size + how derived (power):
Secondary / exploratory (labeled separately):
Instrument adversarial-review done? <what a hostile reviewer flagged + fixes>
```

## 13. Report structure (BLUF / Minto) *(all — the output)*
```
BLUF: <the judgment, one line, up front>
Basis: <graded evidence — each load-bearing claim: our claim · reliability×credibility · effective-N · root status · confidence>
Dissent / strongest counter-case: <preserved, not buried>
What would change this: <the load-bearing assumptions + sensitivities>
So what: <the decision/action it supports>
Every line tagged: [fact] / [assumption] / [our-inference]
```
