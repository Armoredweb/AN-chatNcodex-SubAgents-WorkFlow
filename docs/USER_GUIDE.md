# User Guide — AN-chatNcodex-SubAgents-WorkFlow

This is the practical entry point for using the [canonical workflow](WORKFLOW.md) in an existing software repository.

## What this project does

ChatGPT performs architecture and implementation planning. Codex uses a **Luna High primary agent as orchestrator and implementer**. It delegates worthwhile independent tasks to Luna workers and calls a stronger specialist (for example SOL High) only for proven hard problems, with a minimal context packet.

The goal is end-to-end implementation of an approved GOAL **without manually switching models**. Agent creation, permissions, and routing must be verified before execution.

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
decomposition, Plan Parts, audits, model/agent routing plans, and
convergence review. Codex Luna High executes approved GOALs and
delegates only when worthwhile. Require minimal context for every
subagent and do not use manual ACTIVE_MODEL switching.

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

For substantial Plan Parts ChatGPT supplies verified symbols, contracts, algorithms, ownership, code/pseudocode when useful, testing and Expected Evidence. After expansion it performs:
- **Pass A:** implementation-preserving optimization;
- **Pass B:** specialist minimization, Luna routing, and worthwhile parallelism;
- **Pass C:** cross-plan, current-source, and multi-agent consistency.

It then produces the `CODEX_HANDOFF.md` GOAL execution contract. No specialist should be scheduled merely because a task looks intimidating.

## 4. Confirm models, then bootstrap Codex

The final index/handoff names **exact model IDs, versions, effort, roles, allowed fallback, and verification date**. Role labels alone are insufficient; model availability varies by client and account.

Start Codex in the **consumer repository** and explicitly request the approved Agent Bootstrap/Compatibility Gate before starting G01. Example:

~~~text
Read CODEX_HANDOFF.md and the relevant PLAN_INDEX.md sections.
Verify repository/HEAD, client/version, current config and AGENTS.md.
Run Agent Bootstrap and Compatibility Gate ONLY.
Create or merge the approved .codex/agents definitions and config;
preserve all unrelated existing settings and user changes.
Verify model/effort routing and minimal-context delegation.
If a new session is required, checkpoint and tell me what to do next.
Do not begin implementation GOALs until compatibility is proven.
~~~

This may add a compact `AGENTS.md` and relevant project-local `.codex/config.toml` and `.codex/agents/*.toml` files in the **consumer** repository, subject to approved scope.

A static TOML file is not proof that the configured specialist model really ran. Validate the installed client and actual role invocation. If a required feature is unavailable, report it rather than silently changing models.

## 5. Execute a GOAL

After compatibility is verified, start the approved GOAL:

~~~text
Start GOAL G01 from the current CODEX_HANDOFF.md.
Luna is the primary orchestrator and implementer.
Implement directly by default; delegate only independent useful work
or justified hard blockers with minimal-context packets.
Integrate, test, and prove all Expected Evidence before reporting done.
Stay inside approved architecture and write scope.
Do not ask me to switch models during the GOAL.
~~~

Luna implements, optionally uses independent Luna workers, escalates a verified hard problem in **Solve Only** mode first, and performs integration/validation. A specialist can request specific additional context; Luna authorizes it only within already-approved limits.

GOALs may require a user action if the client must resume a paused session, request genuine permission, or resolve an architectural blocker. These are not manual model switches.

## 6. Check completion and close the cycle

For each GOAL request a compact Execution Evidence summary: changed files, verified model routing when observable, subagent calls, tests, Expected Evidence results, and real blockers. Do not invent token counts.

After implementation, return to ChatGPT for a **Convergence Check** against the approved baseline and current code. ChatGPT prepares cleanup only after convergence. Explicitly start the bounded **Cleanup GOAL** when ready; cleanup is never automatic.

## 7. Continuation and safety

At a new chat, read the current manual and smallest necessary persisted files: `PROJECT.md`, `CHAT_HANDOFF.md`, `MASTER_PLAN.md`, `PLAN_INDEX.md`, then only relevant parts. Use the current GitHub source instead of remembered state.

ChatGPT **Manual Mode** performs one coherent substantial operation per message; **Continuous Mode** is opt-in, risk-based, and does not use an arbitrary 12-operation countdown. Handoffs carry the exact baseline, phase, next action, blockers, and file pointers without transcripts.

Respect platform, security, usage, and authorization limits. Minimal-context instructions are not a true filesystem sandbox; separate technical isolation may be required.

## License and references

The workflow is [CC BY 4.0](../LICENSE). For live Codex settings and caveats, consult links and the **Compatibility Gate** in [WORKFLOW.md](WORKFLOW.md). Do not copy example model identifiers without verification.
