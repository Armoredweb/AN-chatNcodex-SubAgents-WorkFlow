# AN-chatNcodex-SubAgents-WorkFlow

A ChatGPT-first planning and Codex multi-agent implementation workflow.

**ChatGPT performs the difficult thinking. Luna executes most of the implementation. Stronger specialists handle only justified residual complexity, with minimal delegated context.**

## What it does

- **ChatGPT plans code-first:** inspect current source, settle architecture and interfaces, design algorithms, and produce **substantial verified implementation code or detailed pseudocode** to reduce Luna's reasoning. Code-rich Plan Parts are welcome; brevity must never remove useful implementation detail.
- **Codex executes:** a Luna High primary agent orchestrates **and implements** each bounded GOAL; independent Luna workers are optional, not mandatory.
- **Specialists are exceptional:** a stronger model such as SOL High receives only a proven hard problem, preferably in **Solve Only** mode; **Scoped Implementation** is the fallback for a fragment Luna cannot safely implement.
- **Context stays deliberate:** minimal delegation packets, justified progressive context requests, explicit ownership, and no unnecessary full-history forks.
- **One autonomous GOAL:** implement coherent large batches and run **few essential tests at meaningful integration boundaries**. Reuse unaffected passing evidence, rerun only impacted tests after repairs, and complete without asking the user to switch models manually; stop at genuine authorization, safety, platform, or unresolved-blocker boundaries.

This is an independently maintained successor to [AN-chatNcodex-WorkFlow](https://github.com/Armoredweb/AN-chatNcodex-WorkFlow), not a synchronized fork. The original remains reference-only.

## Start here

- [Canonical operational manual](docs/WORKFLOW.md) — authoritative rules, gates, artifacts, and Codex delegation policy.
- [User guide (English)](docs/USER_GUIDE.md) — setup and practical commands.
- [Guia de uso (Português brasileiro)](docs/USER_GUIDE_PT-BR.md).

## Architecture

```text
User -> ChatGPT (approved architecture + implementation-ready planning)
     -> working GitHub repository (MASTER_PLAN, PLAN_INDEX, Plan Parts, handoffs)
     -> Codex: Luna High orchestrator and implementer
           |-> Luna workers only for worthwhile independent tasks
           |-> stronger specialist only for justified hard problems
     -> integration + Expected Evidence
     -> ChatGPT convergence review -> cycle closure
```

The *workflow repository* holds the instructions; each *consumer software repository* holds its own plans and, only after a validated bootstrap, project-local `AGENTS.md`, `.codex/config.toml`, and `.codex/agents/` as needed.

Exact model IDs, effort levels, platform capabilities, permission boundaries, and authorized fallbacks are verified during planning **and** rechecked during the Codex compatibility gate. Documentation alone is not proof that an installed client routes a specialist correctly.

## Governing principles

1. Implementation readiness through **code-forward complete plans**: prioritize useful code and precise pseudocode over aggressive document compression; shorten redundant prose, not the implementation.
2. No unnecessary specialist calls, repeated scans, artificial retries, or token-heavy context forwarding.
3. Parallelism only when dependencies, write ownership, integration, and shared state make it beneficial and safe.
4. Code and repository evidence outrank memory or obsolete notes. Approved requirements still govern convergence.
5. Authorization, product limits, and tests take precedence over speed or agent autonomy.

## License

[Creative Commons Attribution 4.0 International (CC BY 4.0)](LICENSE). Attribution: AN-chatNcodex-SubAgents-WorkFlow by Armoredweb.
