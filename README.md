# AN-chatNcodex-SubAgents-WorkFlow

A ChatGPT-first, **platform-portable** planning and multi-agent implementation workflow for **Codex and Google Antigravity**.

**ChatGPT performs the difficult thinking. A verified economical primary agent implements and orchestrates. Optional stronger specialists handle only justified residual complexity with minimal delegated context.**

## What it does

- **ChatGPT plans code-first:** inspect current source, settle architecture and interfaces, design algorithms, and produce **substantial verified implementation code or detailed pseudocode** to reduce Luna's reasoning. Code-rich Plan Parts are welcome; brevity must never remove useful implementation detail.
- **Portable execution:** Codex can use Luna High; Antigravity can use a verified Gemini Flash Medium-class agent. The primary model both orchestrates **and implements** each bounded GOAL.
- **Configurable model modes:** dual-tier (economical primary/workers plus optional stronger specialist) or single-model (same model for primary and parallel workers). Specialists are exceptional and prefer **Solve Only**; **Scoped Implementation** is a bounded fallback.
- **Context stays deliberate:** minimal delegation packets, justified progressive context requests, explicit ownership, and no unnecessary full-history forks.
- **Portable GOAL continuity:** implement coherent batches with **few essential tests at integration boundaries**, reusing still-valid evidence. A compact `IMPLEMENTATION_HANDOFF.md` records verified progress and the next safe action so a user-selected platform can resume an unfinished GOAL without replaying the old session.

This is an independently maintained successor to [AN-chatNcodex-WorkFlow](https://github.com/Armoredweb/AN-chatNcodex-WorkFlow), not a synchronized fork. The original remains reference-only.

## Start here

- [Canonical operational manual](docs/WORKFLOW.md) — authoritative rules, gates, artifacts, and Codex delegation policy.
- [User guide (English)](docs/USER_GUIDE.md) — setup and practical commands.
- [Guia de uso (Português brasileiro)](docs/USER_GUIDE_PT-BR.md).

## Architecture

```text
User -> ChatGPT (approved architecture + code-rich portable planning)
     -> working GitHub repository (MASTER_PLAN, PLAN_INDEX, Plan Parts)
     -> IMPLEMENTATION_HANDOFF.md (approved GOAL + current checkpoint)
     -> selected platform: Codex or Antigravity
           |-> primary implementer/orchestrator (economical or single-model)
           |-> parallel workers only when useful
           |-> optional stronger specialist only in dual-tier mode
     -> integration + Expected Evidence
     -> user-initiated switch -> resume remaining GOAL from checkpoint
     -> ChatGPT convergence review -> cycle closure
```

The *workflow repository* holds the instructions; each *consumer software repository* holds its own plans and portable `IMPLEMENTATION_HANDOFF.md`. Validated platform adapters may add shared `AGENTS.md`, Codex `.codex/config.toml` / `.codex/agents/`, or Antigravity `.agents/agents/` as needed. Do not overwrite one platform's agent definitions when switching.

Model IDs where supported, otherwise effective UI labels and agent tiers, effort, platform capabilities, permissions and fallbacks are verified during planning **and** in each platform's compatibility gate. A successful checkpoint transfers verified *project state*, not in-memory conversations or uncommitted files across machines.

## Governing principles

1. Implementation readiness through **code-forward complete plans**: prioritize useful code and precise pseudocode over aggressive document compression; shorten redundant prose, not the implementation.
2. No unnecessary specialist calls, repeated scans, artificial retries, or token-heavy context forwarding; single-model operation is supported.
3. Parallelism only when dependencies, write ownership, integration, and shared state make it beneficial and safe.
4. Code and repository evidence outrank memory or obsolete notes. Approved requirements still govern convergence.
5. User-controlled platform switching preserves implementation progress and respects authorization, provider limits, and valid test evidence.

## License

[Creative Commons Attribution 4.0 International (CC BY 4.0)](LICENSE). Attribution: AN-chatNcodex-SubAgents-WorkFlow by Armoredweb.
