# AN-chatNcodex-SubAgents-WorkFlow

A ChatGPT-first, **platform-portable** planning and multi-agent implementation workflow for **Codex and Google Antigravity**.

**ChatGPT performs the difficult thinking. A verified economical primary agent implements and orchestrates. Optional stronger specialists handle only justified residual complexity with minimal delegated context.**

## What it does

- **ChatGPT plans code-first:** inspect current source, settle architecture and interfaces, design algorithms, and produce **substantial verified implementation code or detailed pseudocode** to reduce Luna's reasoning. Code-rich Plan Parts are welcome; brevity must never remove useful implementation detail.
- **Portable execution:** Codex can use Luna High; Antigravity can use a verified Gemini Flash Medium-class agent. The primary model both orchestrates **and implements** each bounded GOAL.
- **Adaptive orchestration:** the primary dynamically schedules useful independent work **within and across user-authorized GOALs**, delegating simple implementation to economical parallel workers while coordinating/integrating and optionally implementing critical-path tasks.
- **Capability-aware specialists:** dual-tier mode proactively routes **subtle screenshot/image inspection, visual composition, high-risk contracts and unusually complex fragments** to a verified stronger agent with actual artifacts, exact file references and minimal context. Prefer **Visual Review / Solve Only**; **Scoped Implementation** is a bounded fallback. Single-model mode uses the same model for primary and parallel workers.
- **Context stays deliberate:** precise task and file/symbol references, relevant code and **actual image artifacts for visual analysis**, justified progressive context requests, explicit ownership, and no unnecessary full-history forks.
- **Selective GOAL testing:** keep a growing, cumulative repository test suite, but during implementation execute **only explicitly targeted tests of changed code and affected dependencies/consumers**. Never run the entire suite in a GOAL—even at completion—or repeat unaffected passing tests. A compact `IMPLEMENTATION_HANDOFF.md` preserves current evidence and the next safe action across platforms.

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
           |-> primary orchestrates ready approved GOALs + critical path
           |-> economical workers implement independent GOALs/components
           |-> capable visual/high-risk/complex specialist in dual-tier mode
     -> integration + Expected Evidence
     -> user-initiated switch -> resume remaining GOAL from checkpoint
     -> ChatGPT convergence review -> cycle closure
```

The *workflow repository* holds the instructions; each *consumer software repository* holds its own plans and portable `IMPLEMENTATION_HANDOFF.md`. Validated platform adapters may add shared `AGENTS.md`, Codex `.codex/config.toml` / `.codex/agents/`, or Antigravity `.agents/agents/` as needed. Do not overwrite one platform's agent definitions when switching.

Model IDs where supported, otherwise effective UI labels and agent tiers, effort, platform capabilities, permissions and fallbacks are verified during planning **and** in each platform's compatibility gate. A successful checkpoint transfers verified *project state*, not in-memory conversations or uncommitted files across machines.

## Governing principles

1. Implementation readiness through **code-forward complete plans**: prioritize useful code and precise pseudocode over aggressive document compression; shorten redundant prose, not the implementation.
2. No unnecessary specialist calls, repeated scans, artificial retries, or token-heavy context forwarding; single-model operation is supported.
3. **Proactive parallel implementation** for genuinely independent authorized GOALs/components; coordinate dependencies, write ownership, shared resources and scoped test runs without serializing unrelated work.
4. Code and repository evidence outrank memory or obsolete notes. Approved requirements still govern convergence.
5. User-controlled platform switching preserves implementation progress and valid targeted test evidence. Comprehensive suite execution, if needed, is a **separate post-implementation validation gate**, never a routine GOAL step. Respect authorization and provider limits.

## License

[Creative Commons Attribution 4.0 International (CC BY 4.0)](LICENSE). Attribution: AN-chatNcodex-SubAgents-WorkFlow by Armoredweb.
