# Changelog

All notable changes to **development-team-agents** are recorded here.
Format loosely follows [Keep a Changelog](https://keepachangelog.com/).

## [0.2.0] — 2026-07-03

This release grew the roster and hardened the agent *craft* — most of it
directly inspired by ideas from the wider Claude Code community. See the
**Credits & thanks** section below; these improvements exist because other
people published their work openly, and we're grateful for it.

### Added — agents
- **`red-team-reviewer`** — an adversarial, pre-penetration-test review agent:
  threat modeling, OWASP / abuse-case review, and *proof-of-vulnerability*
  tests written against your own code in a controlled test environment. It is
  read-only by design and explicitly **complements, never replaces, an
  independent human penetration test.** *(Role inspired by the
  `penetration-tester` / `security-auditor` roles common in public collections —
  see Credits.)*
- **`security-operations`** — runtime/operational security (SIEM, WAF, detection
  engineering, security incident response, secrets hygiene), distinct from
  build-time `security-architect`.
- **`technical-writer`** — owns as-built spec/code drift, API reference, and
  documentation quality. *(Identified as a roster gap by benchmarking against
  public role taxonomies — see Credits.)*

### Added — skills & tooling
- Reference **skills** extracted so agent prompts stay lean and multiple agents
  share one source: `stride-review`, `expand-contract-migration`,
  `owasp-llm-checklist`, `gate-verdict-format`. *(Progressive-disclosure-skills
  pattern — see Credits.)*
- **`agent-evals/`** — a proactive agent-quality convention (run a small fixed
  eval set when you change an agent definition) that pairs with the reactive
  `AGENT-RETROS.md` loop: evals prevent regressions, retros correct misses.
  *(Inspired by public agent-evaluation frameworks — see Credits.)*
- **`/red-team`** slash command to run the adversarial review on demand.

### Changed
- **Model-tiering** is now a documented, deliberate policy (deep-judgment agents
  on the strongest model, everyday builders on a mid tier, low-stakes work on a
  fast tier) rather than ad hoc. *(Multi-tier model strategy — see Credits.)*
- **Least-privilege tool permissions** audited across the roster: read-only
  reviewers carry only read/analysis tools; only builders get write/exec.
  `red-team-reviewer` was tightened to read-only after this audit caught it
  carrying shell access it did not need. *(Role-based tool-restriction
  convention — see Credits.)*

### Security
- **Tier-3 guard hook hardened.** Path matching is now case-insensitive (so a
  case variant like `.GitHub/` can't slip past on macOS/Windows) and resolves
  symlinks with `realpath` (so a symlink pointing at a protected file is
  caught). The docstring now states plainly that this hook is in-session
  accident-prevention and that the *enforcement of record* is server-side
  (branch protection + CODEOWNERS + the change-record-required CI check).
  Verified with a path-guard test harness.

### Notes
- Nothing here changes the governance core (Change Records, tier gates,
  fail-closed enforcement) — the differentiator of this kit. The additions are
  craft and coverage improvements layered on top.

---

## Credits & thanks

The 0.2.0 improvements came from **benchmarking this kit against the excellent
public Claude Code subagent collections**. Each idea below is credited to where
we found it, with a link to the source and our sincere thanks to the maintainers
and contributors — open-sourcing your work is what made these improvements
possible.

| Improvement in this release | Idea credited to | Source |
|---|---|---|
| Deliberate multi-tier model strategy (deep/everyday/fast) | **wshobson** and contributors — *agents* marketplace | https://github.com/wshobson/agents |
| Proactive agent-quality evaluation (the `agent-evals/` convention) | **wshobson** and contributors — the *PluginEval* quality framework | https://github.com/wshobson/agents |
| Progressive-disclosure **skills** (lean prompts, load knowledge on demand) | **wshobson** and contributors | https://github.com/wshobson/agents |
| Role-based **least-privilege tool restriction** (read-only reviewers, etc.) | **VoltAgent** and contributors — *awesome-claude-code-subagents* | https://github.com/VoltAgent/awesome-claude-code-subagents |
| Role taxonomy that surfaced our gaps (**technical-writer**, and the security roles behind **red-team-reviewer**) | **VoltAgent**, **0xfurai**, and the broader community catalogs | https://github.com/VoltAgent/awesome-claude-code-subagents · https://github.com/0xfurai/claude-code-subagents |
| Community index that made these collections discoverable | **hesreallyhim** — *awesome-claude-code* | https://github.com/hesreallyhim/awesome-claude-code |

**Thank you** to the maintainers and contributors of these projects. We adopted
your *ideas and conventions*, re-expressed for this governance-first kit; the
governance layer (Change Records, tier gates, enforcement) is our own
contribution back to the commons. If we've mis-credited an idea or missed a
source, please open an issue — we want attribution to be right.

## [0.1.0] — 2026-07-02

Initial public release: 16-agent governed team, Tier-3 path-guard hook,
`change-record-required` CI check, sparse CODEOWNERS two-person rule, the Change
Record system, and the agent-retro feedback loop. Extracted from production use.
