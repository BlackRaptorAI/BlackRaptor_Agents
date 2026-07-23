# Changelog — BlackRaptor Advisory Council

All notable changes to the `blackraptor-council` plugin are recorded here.
Format loosely follows [Keep a Changelog](https://keepachangelog.com/).

## [1.2.0] — 2026-07-22

### Changed
- **`product-strategy` merged into the shared `product-manager`** and moved to the
  new `blackraptor-bridge` plugin (auto-installed as a dependency). The
  `council-orchestrator` still convenes it as the product/strategy anchor — every
  cross-reference in the seats, `COUNCIL.md`, and the Definition Brief now points to
  `product-manager`. Council seats 12 → 11.
- `plugin.json` now declares `"dependencies": ["blackraptor-bridge"]`; the bridge
  also brings the council its `evidence-auditor` gate.

## [1.1.0] — 2026-07-22

### Added — skills
- **`council`** — the plugin now ships a skill, not just agents. Say "convene the
  council" (or `/council`) to run the full challenge protocol: it grounds itself in
  `BUSINESS-CONTEXT.md`, frames the decision as a one-way/two-way door, delegates to
  the `council-orchestrator` sub-agent for independent parallel seat drafts +
  anonymized cross-review, enforces the output contract (steelman FOR/AGAINST,
  confidence-tagged evidence, mandatory "What You Lose"), and synthesizes without
  averaging. Self-contained under `skills/council/` with its `references/` bundle
  (`COUNCIL.md`, `business-context.md`, `definition-brief.md`). Brings the public
  port to full 9-skill parity with the golden source.

### Changed
- Plugin manifest declares `"skills": "./skills/"`.

## [1.0.0] — 2026-07-21

Initial public release of the Executive Advisory Council as a Claude Code plugin:
12 seats coordinated by the `council-orchestrator` under the challenge protocol.
