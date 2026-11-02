# User Guide — AN-chatNcodex-SubAgents-WorkFlow

This is the practical entry point for using the [canonical workflow](WORKFLOW.md) in an existing software repository, with **portable execution across Codex and Google Antigravity**.

## What this project does

ChatGPT performs architecture and **code-rich** implementation planning. The selected platform uses a primary agent as **orchestrator and implementer**: Codex may use Luna High, and Antigravity may use a verified Gemini Flash Medium-class model. Choose **dual-tier mode** (economical primary/workers plus optional stronger specialist) or **single-model mode** (same model for primary and parallel workers, no stronger tier).

The goal is end-to-end implementation of an approved GOAL without unnecessary model switches. When the user moves between platforms, the next agent resumes from a **portable execution checkpoint**, not the prior chat transcript. Agent configuration, permissions, and effective routing must be verified on each platform.

## 1. Choose repositories

- **Workflow manual:** https://github.com/Armoredweb/AN-chatNcodex-SubAgents-WorkFlow/blob/main/docs/WORKFLOW.md
- **Consumer repository:** your application/engine/backend repository; it contains actual source, architecture, and the planning folder, normally `plans/<plan-name>/`.
- **Original workflow:** reference only; do not copy old manual-switching procedures.

The workflow repository documents a method; it is not the place to store every consumer project's plans.

## 2. Set up ChatGPT planning

Create a ChatGPT Project for the **consumer project**. Give it the consumer repo and the canonical manual URL. Keep Project Instructions compact. This is a suggested bootstrap, not a replacement for the manual:

~~~text
You are the ChatGPT planning layer for this consumer software repository:
<OWNER/REPOSITORY> (branch: <BRANCH>).

Read the current canonical workflow at:
https://github.com/Armoredweb/AN-chatNcodex-SubAgents-WorkFlow/blob/main/docs/WORKFLOW.md

ChatGPT owns difficult architecture, repository inspection, research,
decomposition, Plan Parts, audits, platform-specific agent profiles,
and convergence review. Codex or Antigravity executes approved GOALs
from IMPLEMENTATION_HANDOFF.md. Delegate only when worthwhile.
Require minimal context; do not use manual ACTIVE_MODEL switching.

Treat current source and approved architecture as authoritative;
do not trust chat memory over current GitHub files.
Do not write plans until I approve implementation planning.
Ask before operations outside authorized scope.
Communicate with me in pt-BR; write technical plans in English.
~~~

Replace the placeholder repository/branch values with actual ones before use.

First-chat prompt:

~~~text
Read the current canonical workflow and verify my working repository,
branch, HEAD, and existing architecture. Brainstorm requirements with
me first. Do not create planning files or start implementation yet.
~~~

## 3. Brainstorm, approve, and prepare implementation

Discuss requirements and options with ChatGPT. It should inspect relevant current code, settle architecture, and build a compact `MASTER_PLAN.md` design before decomposition.

When ready, explicitly approve planning, for example:

~~~text
I approve the master-plan architecture and implementation planning.
You may write planning artifacts only inside plans/<plan-name>/.
Proceed with decomposition under the canonical workflow.
~~~

ChatGPT persists the master baseline and index and stops after the initial decomposition for your review. The next `continue` runs the **bidirectional Decomposition Audit Gate**, then later Plan Part expansion.

For substantial Plan Parts, ChatGPT should provide **as much verified, directly useful implementation code as practicable**—functions, interfaces, error handling, integrations, and detailed pseudocode—rather than shrinking the document at Luna's expense. More code-heavy Plan Parts are encouraged when that reduces later implementation reasoning. Specify **only named tests for the changed code and affected dependencies/consumers at the batch/GOAL boundary**; retain the cumulative suite as source code but never invoke it wholesale during implementation. After expansion it performs:
- **Pass A:** implementation-preserving optimization;
- **Pass B:** specialist minimization, Luna routing, and worthwhile parallelism;
- **Pass C:** cross-plan, current-source, and multi-agent consistency.

It then produces the platform-neutral `IMPLEMENTATION_HANDOFF.md` GOAL contract and initial execution checkpoint. Existing `CODEX_HANDOFF.md` files may be migrated as read-only compatibility pointers. No specialist should be scheduled merely because a task looks intimidating.

## 4. Select the platform/profile and bootstrap its agents

The approved index and `IMPLEMENTATION_HANDOFF.md` define the same GOALs and Expected Evidence for every platform. A **per-platform Agent Capability Matrix** records actual model IDs/effort where supported, or verified UI model label plus tier (not a fabricated pinned ID). The user selects **Codex or Antigravity**, then **dual-tier or single-model** mode.

For Codex: the primary Luna High can bootstrap `.codex/config.toml` and the necessary `.codex/agents/*.toml` roles, respecting existing files.

For Antigravity: select a compatible model such as **Gemini Flash Medium** in the installed App/CLI model selector; bootstrap only needed `.agents/agents/*.md` roles (Markdown + YAML). Their documented `model: flash | pro | inherit` values are **tiers**, not fixed model IDs. Antigravity can use shared `AGENTS.md`. Do **not** use deprecated legacy `.agents/workflows/` for new automation; reusable skills may live in `.agents/skills/` when actually needed.

Start in the consumer repository with a bounded first command:

~~~text
Read plans/<plan-name>/IMPLEMENTATION_HANDOFF.md and PLAN_INDEX.md.
Run the Agent Bootstrap and Compatibility Gate ONLY for the selected
platform and approved single-model or dual-tier profile.
Inspect current branch/HEAD, dirty files and existing configs; preserve
all user work and the other platform's agent definitions.
Verify the actual model/tier, subagent invocation, permissions and tools.
Checkpoint any required session restart. Do not start the GOAL yet.
~~~

Do not infer that a configured role successfully uses a chosen model solely from the existence of TOML/YAML. If a required capability is missing, select only an explicitly approved verified fallback or stop.

## 5. Execute a GOAL

After compatibility is verified, start the approved GOAL:

~~~text
Start GOAL G01 from the current IMPLEMENTATION_HANDOFF.md.
Use the verified primary implementer for my selected platform/profile.
Implement substantial coherent slices directly from prepared code;
delegate only useful independent work or justified hard blockers.
Select explicit test cases/files/packages for changed functionality and
its affected dependencies/consumers only; NEVER run the full suite in a GOAL.
Reuse valid passing results; on failure rerun only invalidated tests.
Do not use an unfiltered command or a broad-suite fallback.
Prove all Expected Evidence against the final relevant code state.
Stay inside approved architecture and write scope.
Do not ask me to switch models during the GOAL.
~~~

The primary implements larger coherent slices, optionally uses independent workers of the selected model, and escalates a verified hard problem in **Solve Only** mode only under a dual-tier profile. In single-model mode it must not invent an expensive specialist. **The full accumulated test suite must not be run during implementation, including at the end of a GOAL.** Select direct changed-module tests and impacted dependencies only. Earlier tests are limited to scoped foundational or high-risk dependencies. Passing results are not rerun unless their covered source, dependencies, selectors or relevant environment changed. A specialist can request specific additional context; Luna authorizes it only within already-approved limits.

GOALs may require a user action if the client must resume a paused session, request genuine permission, or resolve an architectural blocker. These are not manual model switches.

## 6. Switch platforms mid-GOAL, then complete and close the cycle

When usage capacity is unavailable or you want to change providers, stop concurrent writers and preserve the code plus a **compact** `IMPLEMENTATION_HANDOFF.md` checkpoint: repository/HEAD and dirty files, current GOAL, completed and remaining integrated slices, last still-valid tests, active subagents/worktrees/conflicts, chosen next profile and one exact next action. A checkpoint alone cannot transport uncommitted files to another computer; use the same working tree or an explicit commit/patch.

The user opens the other platform in the same consumer project and resumes with:

~~~text
Continue the approved GOAL from plans/<plan-name>/IMPLEMENTATION_HANDOFF.md.
Check real HEAD and uncommitted changes, ownership of any active writers,
completed work and tests still valid. Run the incoming platform's
Compatibility Gate, then continue only the next remaining slice.
Keep the plan and scope unchanged. Do not replay previous chat history.
~~~

Carry only still-valid outcomes and invalidated **targeted test selectors** into the next platform; switching does not trigger a full regression suite. A sudden limit can prevent the outgoing agent from updating its final checkpoint. The incoming agent must reconcile the last persisted checkpoint with the actual code and mark uncertain work as unverified, not discard or duplicate it. Switching is **user-initiated** and subject to each provider's rules; neither platform's in-memory session transfers automatically.

### Completion and closure

For each GOAL request a compact Execution Evidence summary: changed files, verified model routing when observable, subagent calls, **exact targeted selectors and results**, Expected Evidence, reusable passing evidence and real blockers. Do not invent token counts.

After implementation, return to ChatGPT for a **Convergence Check** against the approved baseline and current code, reusing relevant valid evidence. The growing suite remains available for a **separate post-implementation release/system validation gate** if requested or required; no GOAL or corrective loop triggers it automatically. ChatGPT prepares platform-neutral cleanup only after convergence, under `CLEANUP_HANDOFF.md`. Explicitly start the bounded **Cleanup GOAL** on a verified platform when ready; cleanup is never automatic.

## 7. Continuation and safety

At a new chat, read the current manual and smallest necessary persisted files: `PROJECT.md`, `CHAT_HANDOFF.md`, `MASTER_PLAN.md`, `PLAN_INDEX.md`, then only relevant parts. Use the current GitHub source instead of remembered state.

ChatGPT **Manual Mode** performs one coherent substantial operation per message; **Continuous Mode** is opt-in and risk-based. Use `CHAT_HANDOFF.md` for **planning-chat** continuity and `IMPLEMENTATION_HANDOFF.md` for **cross-platform implementation** continuity. Never substitute an old agent transcript for current Git state.

Respect platform, security, usage, and authorization limits. Minimal-context instructions are not a true filesystem sandbox; separate technical isolation may be required.

## License and references

The workflow is [CC BY 4.0](../LICENSE). For live Codex settings and caveats, consult links and the **Compatibility Gate** in [WORKFLOW.md](WORKFLOW.md). Do not copy example model identifiers without verification.
