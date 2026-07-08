# Porting the Council to Other Platforms

The Council runs natively in **Claude Code / Cowork** — the agent files
are plain markdown and the runtime provides everything else. It can be
ported to any agent runtime that preserves the full mechanics. **It must
not be flattened into a single chat prompt** — that ships a degraded
council wearing the name, and we don't do that.

## What a faithful port MUST preserve

1. **Separated contexts.** Each seat runs as its own agent with its own
   context. One context window playing twelve roles is not a council.
2. **Independent parallel drafts.** Seats answer without seeing each
   other's drafts. Independence before synthesis prevents anchoring.
3. **Anonymized cross-review** on consequential questions: drafts
   circulate with seat identity stripped.
4. **The challenge protocol.** The orchestrator interrogates every draft
   (evidence, confidence, counter-case, falsifiability, customer, cost)
   and returns deficient work — before synthesis.
5. **Human-in-the-loop gates.** growth-engine's spend/claims approvals
   and ethics-governance's BLOCK verdicts must reach a human and halt
   until answered. If your runtime can't pause for a human, don't port
   the executor seat.
6. **The output contract** (`COUNCIL.md` §3), including "What You Lose"
   and confidence labels.
7. **Grounding.** Load `BUSINESS-CONTEXT.md` into every seat's context;
   refuse to run without it.

## How the pieces map

| This package | OpenAI Agents SDK | CrewAI | LangGraph |
|---|---|---|---|
| Agent .md body (below frontmatter) | Agent `instructions` | Agent role/goal/backstory + system prompt | Node system prompt |
| Frontmatter `tools` | Hosted/function tools (read-only + web search for advisors) | Tools list | Tool bindings |
| Frontmatter `model` tiering | Per-agent model choice | Per-agent LLM | Per-node model |
| council-orchestrator | Orchestrator agent + handoffs | Hierarchical process manager | Supervisor node + conditional edges |
| Independent drafts | Parallel runs, no shared thread | Async tasks, no context sharing | Parallel branches, merged after |
| HITL gates | Human approval tool / interrupt | Human-in-the-loop task | `interrupt()` before the gated node |

## Porting steps

1. Strip the YAML frontmatter from each agent file; the body is the
   system prompt (it is platform-agnostic by design).
2. Recreate the tool policy: advisors get read-only + web research;
   only growth-engine gets write/draft tools, behind a human gate.
3. Implement the orchestrator's flow: ground → select seats → context
   packets → parallel drafts → challenge protocol → (anonymized review)
   → synthesis → decision-ready view.
4. Keep model tiering: strongest model for council-orchestrator,
   finance, ethics-governance, fundraising-ir.
5. Test with a real question and check the output contract survived:
   steelman both ways, confidence labels, What You Lose, dissent
   register.

## What NOT to build

- A single-prompt "act as my board of advisors" version. One context
  cannot keep advisors honestly independent — the seats converge and the
  challenge protocol becomes self-review theater.
- A version where the orchestrator auto-decides. The human decides;
  that's load-bearing.
- A growth-engine that can spend or publish without a human approval
  step.

Share working ports back via GitHub (see CONTRIBUTING.md). Keep the
NOTICE attribution with every port.
