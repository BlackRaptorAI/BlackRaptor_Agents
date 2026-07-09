# The Executive Advisory Council

**A tough, evidence-driven team of AI advisor agents that helps you build
the right company.**

Created by [Tom Hanks](https://tomhanks.pro) (BlackRaptor AI) ·
Battle-tested building Paragon Energy · Contact: **GitHub issues and
discussions only**

Twelve advisor seats — product strategy, market insight, pricing, finance,
go-to-market, revenue, growth, technology & data, people, ethics & legal,
fundraising — convened by an orchestrator that challenges every input
before it reaches you. The Council argues in front of you and hands you
decision-ready views with the disagreement preserved. **You decide; it
advises.** Read [VISION.md](VISION.md) for why this exists and what makes
it different.

## What's in the box

```
business-council-agents/
├── COUNCIL.md              # The charter — binding rules for every seat
├── VISION.md               # Why this exists, strengths, intended use
├── agents/                 # 12 advisor agent definitions
│   ├── council-orchestrator.md   # Convener + challenge protocol (start here)
│   ├── product-strategy.md       # What to build, for whom, why it wins
│   ├── market-insight.md         # Market truth + customer ground truth
│   ├── pricing-strategy.md       # Packaging, pricing, offer economics
│   ├── finance.md                # Unit economics, capital, "is it worth it"
│   ├── ethics-governance.md      # Ethics, governance & legal counsel (can BLOCK)
│   ├── gtm-strategy.md           # Positioning, story, channels, sales motion
│   ├── revenue.md                # GTM execution, the number (CRO)
│   ├── growth-engine.md          # Demand execution (the only executor; HITL-gated)
│   ├── technology-strategy.md    # Business tech + data truth-finding
│   ├── people-org.md             # Hiring, org design, culture
│   └── fundraising-ir.md         # Raising capital + investor relations
├── templates/
│   ├── definition-brief.md       # The handoff artifact to your dev team
│   └── business-context.md       # REQUIRED grounding — fill this in first
└── docs/
    └── PORTING.md          # Running the Council outside Claude Code
```

## Quickstart (Claude Code / Cowork)

1. Copy `agents/*.md` into your project's `.claude/agents/` directory.
2. Copy `COUNCIL.md` and `templates/` into your project root.
3. **Fill in `BUSINESS-CONTEXT.md`** from `templates/business-context.md`.
   This is not optional — a council that doesn't know your company gives
   conventional wisdom, and the orchestrator refuses to convene without it.
4. Ask: *"Convene the council on ..."* — the orchestrator selects seats,
   enforces the challenge protocol, and returns a decision-ready view.

## Start lean — don't activate all twelve

Add seats as your company earns them (`COUNCIL.md` §5). Start with the
orchestrator, the core four (product, market, pricing, finance), and
ethics-governance. A council of twelve consulted on "do ten customers want
this?" is theater. Copy only the agent files for active seats if you want
the discipline enforced by absence.

## What makes this different

- **No sycophancy, structurally.** Independent parallel drafts, anonymized
  cross-review, a challenge protocol every input must survive, and
  adversarial mode for consequential calls. Not "be critical" as a vibe —
  mechanisms.
- **Balanced evidence, always.** Confidence labels on claims, steelman
  for/against, a mandatory "What You Lose" cost in every recommendation,
  and dissent preserved on the record.
- **Customer-focused by charter.** Every seat optimizes for world-class
  customer experience and loyalty — checked against real voice-of-customer
  evidence, never an imagined customer.
- **A human decides.** Consequential calls carry a human signature. The
  one executing seat (growth-engine) runs behind human-in-the-loop
  approval and ethics review.

## Model assignments (tiered by decision stakes)

Each agent's frontmatter assigns the Claude model best suited to its seat.
The council tiers by **decision stakes** — how expensive a subtle
reasoning failure is, and how reversible the resulting decision — not by
task volume:

| Tier | Seats | Why |
|---|---|---|
| **Opus** | `council-orchestrator`, `finance`, `ethics-governance`, `fundraising-ir` | Highest judgment stakes: the orchestrator synthesizes disagreement (a subtle failure corrupts everything downstream); finance owns capital allocation and downside math; ethics-governance holds legal judgment and BLOCK authority; fundraising-ir analyzes terms where a missed nuance costs equity. |
| **Sonnet** | `product-strategy`, `market-insight`, `pricing-strategy`, `gtm-strategy`, `revenue`, `growth-engine`, `technology-strategy`, `people-org` | Analysis and strategy seats: strong reasoning over sources and frameworks, invoked frequently, cost-efficient. |

There is deliberately no cheaper volume tier: every council output is
advice a CEO may act on, so the quality floor is uniform. Assignments are
coaching records — if a seat under-reasons in practice, promote it (one
line in its frontmatter). Ports should preserve the tiering with their
vendor's equivalents (see [docs/PORTING.md](docs/PORTING.md)).

## Requirements & platforms

The Council's potency comes from its mechanics (independent drafts,
anonymized review, challenge protocol), which require an **agent runtime**
— Claude Code or Cowork natively, or a faithful port (OpenAI Agents SDK,
CrewAI, LangGraph): see [docs/PORTING.md](docs/PORTING.md). **There is
deliberately no single-prompt "chat mode"** — one chat window cannot keep
five advisors honestly independent, and we don't ship degraded versions.

## Honest limits

An AI council models the world; it is not the world. It gives you rigor,
structure, memory, and tireless challenge — genuinely valuable and rare —
but internal coherence is not external truth. Use it to think harder and
decide better, then go get ground truth: real customers, real dollars,
real market signal. The agents are not lawyers, accountants, or investment
advisors, and they will tell you when licensed professionals are required.

## Companion project: development-team-agents

The Council answers *"are we building the right company?"* Its companion,
**[development-team-agents](https://github.com/BlackRaptorAI/development-team-agents)**,
answers the question downstream of it: *"are we building the thing right?"*
— a governed AI development team (architect, engineers, security,
compliance, QA, and blocking review gates) battle-tested on production
energy-monitoring infrastructure.

The two teams connect through one artifact: the Council's signed
**Definition Brief** (`templates/definition-brief.md`) is the input the
development team builds against. Same operating philosophy (advise →
decide → enforce, preserved dissent, a human signs), same license, same
authors. Run both and you have the full loop: decide what and why, then
build it right.

## Contributing & contact

Improvements welcome — see [CONTRIBUTING.md](CONTRIBUTING.md). Keep the
attribution (NOTICE) and a link back to this repository with any copy,
port, or derivative. **All contact is through GitHub** — issues for bugs
and gaps, discussions for ideas and results. No other channel is
monitored.

## License

Released under the Apache License 2.0 (see [LICENSE](LICENSE)) — the same
license as our development-team-agents companion. Use it, adapt it, build
on it, commercially or not; the [NOTICE](NOTICE) attribution travels with
every copy, port, and derivative.
