# BlackRaptor Skills — Claude Cowork edition

**Claude Cowork** (on claude.ai) is *skills-centric*: it has no plugin marketplace,
doesn't read your machine's `~/.claude`, and has no sub-agent concept. So the
BlackRaptor **skills** work in Cowork, but the 24-agent dev team + 12-seat council
(sub-agents) are a **Claude Code** capability — see the [repo root](../) for those.

This folder holds **single-file, upload-ready** versions of the skills that work
well standalone in Cowork.

## How to add a skill to Cowork
1. Start a **Cowork** session on claude.ai.
2. Open **Customize → Skills** in the session (look for "Skills" / "Add skill" —
   the label shifts as the UI evolves).
3. **Add a skill** and give it the `SKILL.md` (or paste its contents). Grab the
   raw file from the links below.
4. Done — the skill auto-triggers on its description, exactly as in Claude Code.

## Upload-ready skills

| Skill | What it does | Raw file to upload |
|---|---|---|
| **research-integrity** *(self-contained — templates folded in)* | 3-mode research methodology: source × evidence grading, citation-independence (anti-woozle), root-to-mechanism, release gate | [`cowork/research-integrity.md`](https://raw.githubusercontent.com/BlackRaptorAI/BlackRaptor_Agents/main/cowork/research-integrity.md) |
| **excellence-pass** | the five behaviors that separate top-tier output from merely-correct, as a final pass before delivery | [`…/excellence-pass/SKILL.md`](https://raw.githubusercontent.com/BlackRaptorAI/BlackRaptor_Agents/main/development/claude/skills/excellence-pass/SKILL.md) |
| **gate-verdict-format** | the standard PASS/CONCERNS/FAIL verdict format for reviews | [`…/gate-verdict-format/SKILL.md`](https://raw.githubusercontent.com/BlackRaptorAI/BlackRaptor_Agents/main/development/claude/skills/gate-verdict-format/SKILL.md) |
| **stride-review** | STRIDE threat-modeling pass over a change's trust boundaries | [`…/stride-review/SKILL.md`](https://raw.githubusercontent.com/BlackRaptorAI/BlackRaptor_Agents/main/development/claude/skills/stride-review/SKILL.md) |
| **owasp-llm-checklist** | OWASP LLM Top-10 review lens for prompt/RAG/agent paths | [`…/owasp-llm-checklist/SKILL.md`](https://raw.githubusercontent.com/BlackRaptorAI/BlackRaptor_Agents/main/development/claude/skills/owasp-llm-checklist/SKILL.md) |
| **enforcement-liveness** | prove a control actually runs on the live path before certifying it | [`…/enforcement-liveness/SKILL.md`](https://raw.githubusercontent.com/BlackRaptorAI/BlackRaptor_Agents/main/development/claude/skills/enforcement-liveness/SKILL.md) |

> Only **research-integrity** needs the self-contained edition (it has companion
> templates); the rest are already single-file. Skills that assume a Claude Code
> repo/gate workflow (`change-record`, `expand-contract-migration`) are omitted —
> they add little in Cowork.

## Two limitations to know
- **No auto-update.** A manual upload is a snapshot; re-upload when a skill changes.
  The auto-updating path for Cowork is Anthropic's **official plugin catalog**
  (submission in progress) or **org-admin provisioning** — see the root README's
  install matrix.
- **Skills, not agents.** Cowork runs the *methodology skills*; the agent teams
  live in Claude Code (`/plugin marketplace add BlackRaptorAI/BlackRaptor_Agents`).
