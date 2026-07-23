# BlackRaptor Agents

[![License: Apache 2.0](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](LICENSE)
[![Claude Code plugin](https://img.shields.io/badge/Claude_Code-add_marketplace-D97757?logo=anthropic&logoColor=white)](#install)
[![Agents](https://img.shields.io/badge/agents-23_dev_%2B_11_council_%2B_2_bridge-6E56CF)](#the-teams)
[![Skills](https://img.shields.io/badge/skills-9-2EA043)](development/claude/skills)

**A complete, governed AI organization for Claude Code: a 23-agent development
team and an 11-seat executive advisory council, joined by a shared bridge of
cross-cutting agents — designed to work as one company, agents advise, humans decide.**

Created by [Tom Hanks](https://tomhanks.pro) (BlackRaptor AI) ·
Battle-tested in production · Apache-2.0 ·
Contact: **GitHub issues and discussions only**

This repository consolidates the former `development-team-agents` and
`business-council-agents` repositories (both now archived, histories merged
here) into the single home for the full group.

## Install

**Claude Code (CLI / desktop / IDE)** — add this repo as a plugin marketplace, then install either team, or both. Installs at **user scope**, so it's available in **every project** on your machine:

```bash
/plugin marketplace add BlackRaptorAI/BlackRaptor_Agents
/plugin install blackraptor-dev-team@blackraptor-ai      # the 23-agent dev team + 7 skills
/plugin install blackraptor-council@blackraptor-ai       # the 11-seat advisory council + the /council skill
/reload-plugins
```

Either team **auto-installs the shared `blackraptor-bridge`** plugin — the
cross-cutting `product-manager` and `evidence-auditor` agents + the
`research-integrity` skill — so you don't install it directly. Agents and skills
are namespaced (e.g. `blackraptor-dev-team:excellence-pass`, `blackraptor-bridge:product-manager`).

> **Already had a team installed from before the bridge existed?** A `/plugin update`
> does **not** pull a newly-added dependency — only a fresh install does. So if you
> updated `blackraptor-dev-team` (≥ 1.4.0) or `blackraptor-council` (≥ 1.2.0) rather
> than installing them fresh, add the bridge once:
> ```bash
> /plugin install blackraptor-bridge@blackraptor-ai
> /reload-plugins
> ```
> Fresh installs (the commands above) pull it automatically — no extra step.

### Where it works today

| Surface | How to install | Status |
|---|---|---|
| **Claude Code** (CLI, IDE) | the `/plugin marketplace add` command above | ✅ **Available now** — user scope = every project |
| **Claude Desktop** (no terminal) | the GUI steps below — no typing required | ✅ Available now |
| **Any repo, vendored** | run each team's `install.sh` into your repo (see [`development/`](development/) · [`council/`](council/)) | ✅ Available now |
| **Claude Cowork** (individual, claude.ai) | via Anthropic's official plugin catalog | ⏳ **Submitted for curation** — Cowork has no self-serve marketplace yet |
| **Claude Cowork** (organization) | your org admin provisions it centrally (managed plugins/MCP) | ✅ Available to org admins now |

> **Note on Cowork:** Cowork is skills-centric and does not read a local `~/.claude` or support user-added marketplaces. Once curated into Anthropic's catalog, the **skills** (`research-integrity`, `excellence-pass`, gate reviews, …) sync automatically; the full sub-agent roster is primarily a Claude Code capability.

### Install in Claude Desktop (GUI, no commands)

There is no one-click install link yet (that arrives with Anthropic's official
plugin directory, [claude.com/plugins](https://claude.com/plugins), once this
marketplace is curated). Until then, in the **Claude Desktop** app:

1. Click **+** next to the prompt box → **Plugins**.
2. **Manage plugins** → **+** → **Add marketplace**.
3. Choose **GitHub repository** and enter `BlackRaptorAI/BlackRaptor_Agents`.
4. Back in the plugin browser, install **blackraptor-dev-team**,
   **blackraptor-council**, and/or **blackraptor-marketing** (the shared
   **blackraptor-bridge** comes automatically).
5. Restart the session (or `/reload-plugins`) to load them.

### Using the skills in Claude Cowork (today)

Until the catalog submission lands, you can add the skills manually: in a Cowork
session, open **Customize → Skills** and upload the `SKILL.md`. Upload-ready,
single-file versions (research-integrity has its templates folded in so nothing is
lost) + the exact steps and raw links are in **[`cowork/`](cowork/)**. Start with
**research-integrity** and **excellence-pass**.

## The teams

| | Team | Answers | Home |
|---|---|---|---|
| 🛠 | **Development team** — 23 specialist agents: architect, engineers, security, privacy, compliance, QA, ops, docs, and gate reviewers (incl. `completion-auditor`, which re-checks claimed-complete work against ground truth). Blocking gates hold the line; every sensitive change gets a signed Change Record. | *"Are we building the thing right?"* | [`development/`](development/) |
| 🏛 | **Executive Advisory Council** — 11 seats: market insight, pricing, finance, GTM, revenue, growth, technology, people, ethics (with standing to block), fundraising — convened by an orchestrator whose **challenge protocol** stops unevidenced claims from ever reaching you. | *"Are we building the right company?"* | [`council/`](council/) |
| 📣 | **Marketing team** — 15 world-class specialists + 9 skills: brand, naming/trademark research, market research, content, copy, creative, SEO/GEO, paid media, social/community, email/outbound, video, competitive intel, pricing, analytics, and a campaign coordinator — every external asset through a compliance-claims-gate; no autonomous sends, posts, or spend. | *"Are we telling the market the truth, well?"* | [`BlackRaptor_Agents_Marketing`](https://github.com/BlackRaptorAI/BlackRaptor_Agents_Marketing) (served via this marketplace) |
| 🌉 | **Shared bridge** — the cross-cutting roles that span both teams: `product-manager` (end-to-end product owner, from outcome thesis to buildable definition) and `evidence-auditor` (the adversarial gate over research/analysis), plus the `research-integrity` skill. **Auto-installed** with either team. | *"Does the build match the market, and is the evidence sound?"* | [`bridge/`](bridge/) |

Each directory is self-contained — its own README, install instructions, agent
files, and governance docs. The two teams can be adopted independently; the
bridge rides along with either. Together they form one operating model:

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
