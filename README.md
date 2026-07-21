# BlackRaptor Agents

**A complete, governed AI organization for Claude Code: a 24-agent development
team and a 12-seat executive advisory council, designed to work as one company
— agents advise, humans decide.**

Created by [Tom Hanks](https://tomhanks.pro) (BlackRaptor AI) ·
Battle-tested in production · Apache-2.0 ·
Contact: **GitHub issues and discussions only**

This repository consolidates the former `development-team-agents` and
`business-council-agents` repositories (both now archived, histories merged
here) into the single home for the full group.

## Install (Claude Code plugin marketplace)

Add this repo as a plugin marketplace, then install either team — or both:

```bash
/plugin marketplace add BlackRaptorAI/BlackRaptor_Agents
/plugin install blackraptor-dev-team@blackraptor-ai      # the 24-agent dev team + 8 skills
/plugin install blackraptor-council@blackraptor-ai       # the 12-seat advisory council
/reload-plugins
```

Installed agents and skills are namespaced (e.g. `blackraptor-dev-team:excellence-pass`)
and available in every project. Prefer to vendor the files into a single repo
instead? Each team also ships a classic installer — see [`development/`](development/)
and [`council/`](council/).

## The two teams

| | Team | Answers | Home |
|---|---|---|---|
| 🛠 | **Development team** — 24 specialist agents: architect, engineers, security, privacy, compliance, QA, ops, docs, and gate reviewers (incl. `evidence-auditor`, the research-integrity gate). Blocking gates hold the line; every sensitive change gets a signed Change Record. | *"Are we building the thing right?"* | [`development/`](development/) |
| 🏛 | **Executive Advisory Council** — 12 seats: product strategy, market insight, pricing, finance, GTM, revenue, growth, technology, people, ethics (with standing to block), fundraising — convened by an orchestrator whose **challenge protocol** stops unevidenced claims from ever reaching you. | *"Are we building the right company?"* | [`council/`](council/) |

Each directory is self-contained — its own README, install instructions, agent
files, and governance docs — and can be adopted independently. Together they
form one operating model:

```
                YOU (the human — decides, signs, owns)
                              │
              your Claude session (master orchestrator)
                    │                        │
             development team          advisory council
             (via its orchestrator)    (via council-orchestrator
                                        + challenge protocol)
```

**Agents advise, humans decide.** Development gates produce
Change-Record-ready verdicts (PASS / CONCERNS / FAIL) that a human signs;
council seats produce challenged, evidence-labeled advice with the counter-case
attached. No agent approves its own work; no claim reaches you unchallenged.

## Getting started

- Development team: [`development/README.md`](development/README.md) — quickstart, roster, tiered change governance, install script.
- Council: [`council/README.md`](council/README.md) — seat charters, the challenge protocol, Definition Brief templates, plugin package under [`council/dist/`](council/dist/).

## Provenance & roadmap

Extracted from a production platform where merge-to-main deploys straight to
production and one developer runs the whole show. The upstream deployment
continues to evolve; improvements flow here deliberately, not automatically.
Next scheduled port (by 2026-08-09): the org split introduced upstream on
2026-07-18 — a dedicated process-only `dev-orchestrator` (mirroring the
council's orchestrator), the principal architect refocused as a pure
architecture authority, formalized cross-agent collaboration working sessions,
and a customer-experience north star.

## License

Apache-2.0 (see [LICENSE](LICENSE) and [NOTICE](NOTICE)). The former
repositories' notices are preserved in their directories.
