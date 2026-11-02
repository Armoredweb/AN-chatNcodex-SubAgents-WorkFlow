# Canonical Workflow

This file is the single operational authority for **AN-chatNcodex-SubAgents-WorkFlow**. It defines the protocol used by ChatGPT to plan changes in a consumer software repository and by a **selected, compatible implementation platform** (initially Codex or Google Antigravity) to execute approved GOALs. Plans and execution checkpoints are platform-neutral; platform-specific agent files are adapters.

The workflow repository defines the protocol; the consumer repository holds its own code, architecture, plans, and execution state. The Project Instructions used to **maintain this workflow** are not a substitute for the consumer-project protocol.

## 1. Purpose, boundaries, and operating principle

**ChatGPT does the difficult thinking. An economical primary agent performs most implementation. Stronger specialists address only justified residual complexity, using the minimum necessary context.**

- ChatGPT owns architecture, research, source inspection, decomposition, detailed planning, consistency, specialist-minimization, approval preparation, convergence review, and cleanup preparation **independent of implementation platform**.
- The selected platform runs a **primary agent that both orchestrates and implements**. For Codex, prefer Luna High; for Antigravity, a verified Gemini Flash Medium-class configuration is a candidate. These are profiles, not permanent model names.
- Support both **dual-tier mode** (economical primary/parallel workers plus optional stronger specialist) and **single-model mode** (same selected model for primary and parallel workers, no stronger specialist configured or assumed). Direct implementation remains the default in either mode.
- The workflow optimizes **implementation readiness and useful implementation code produced by ChatGPT**, shifting complex reasoning away from the implementation platform. Favor code/pseudocode-rich plans over superficially short plans; minimize redundant prose and expensive rediscovery, not useful technical content.
- Execute **coherent implementation batches with few, high-value validation gates**; do not require a new test or a test run for every Plan Part or microstep.
- A GOAL is an autonomous, bounded implementation mission; plan files do not define agent sessions, commits, or test boundaries.
- This protocol never authorizes bypassing product, account, safety, rate, security, or platform limits. A subagent is not an authorization bypass.

Do not assume that using more agents is faster or cheaper. Prefer direct implementation where the plan already supplies the solution. A user-authorized platform switch preserves approved scope, evidence, and progress; it does not authorize bypassing providers' usage policies or sharing credentials.

## 2. Authority and evidence precedence

For **current software facts**, use:
1. Current verified consumer-repository source, configuration, and active architecture.
2. The approved semantic baseline and latest canonical architectural decisions.
3. Latest applicable Plan Parts and the dependency index.
4. Earlier plans and historical notes, only as supporting evidence.

For **procedure**, this manual is authoritative. For a consumer project's **approved requirements**, the canonical plan governs intended outcomes even when current code diverges. During convergence, current code is evidence of implementation state, not automatic permission to discard a requirement.

Project Instructions are a compact bootstrap, not a duplicate manual. Never promote chat memory, a previous tool result, an old model-selection statement, or an agent's self-description above freshly inspected artifacts or actual client behavior.

Distinguish: **existing** files and symbols, **verified external** facts, **proposed** interfaces, and **untested** configuration.

When already inspecting relevant source, note material bugs, stale paths, unnecessary hot-path work, or architecture contradictions in that scope. Do not expand into unrelated repository audits without a reason.

## 3. Starting, restoring, and refreshing a planning session

At the beginning of a new or continuation ChatGPT chat:
1. Read this document from the current workflow repository.
2. Identify the *consumer* repository, branch, and approved write scope; verify repository and HEAD.
3. Determine whether this is a new cycle or a continuation.
4. On continuation read the persisted `PROJECT.md` and `CHAT_HANDOFF.md` first, then `MASTER_PLAN.md` and `PLAN_INDEX.md`; inventory remaining files without loading them all.
5. Load only Plan Parts and source files needed for the next bounded operation.
6. If `CLEANUP_FINDINGS.md` survives a closed cycle, reconcile live findings into the new plan.
7. Re-read relevant manual sections before major phase transitions or implementation handoff.

Do not invent a missing manual, repository, branch, file, status, or decision. On tool failure, record what could not be verified. A new chat reconstructs state from GitHub, not conversation history.

## 4. Scope approval and persistent storage

Brainstorming and architecture exploration do not imply permission to write code or create plan files. **Require explicit user approval before transitioning from brainstorm/master-plan discussion to implementation planning.**

For each consumer cycle, use an existing planning convention or `plans/<plan-name>/`. GitHub is the recommended persistent backend; Library is a fallback only if access is unavailable or the user prefers it. Record backend, branch/base, plan root, and authorized write boundaries in `PROJECT.md`.

Explain that planning writes create Git commits. Permission to edit planning files does **not** automatically authorize modifying application source, unrelated paths, existing agent configuration, or the reference workflow. A subsequent explicit GOAL start with an approved scope authorizes the corresponding code/configuration changes, subject to any additional platform approval.

Prefer one coherent commit for a bounded related planning update, with safe synchronization of index/handoff. Avoid micro-commits, but do not batch unrelated changes, postpone required checkpoints, overwrite concurrent edits, or force-push to reduce commit count. Re-read the branch head before writes and confirm commit persistence.

## 5. Planning artifact contracts

Keep artifacts distinct; create a document only when its phase requires it. The location and status of each live artifact must be discoverable from `PROJECT.md`.

### PROJECT.md

Concise durable entry point: repository, branch/baseline, planning root/backend, authorized scope, phase, pointers to active artifacts (including the **portable implementation handoff** when applicable), approved architecture baseline, and next responsible actor. No transcripts.

### MASTER_PLAN.md

Compact architectural backbone: outcome, requirements, behavior, invariants, non-goals, constraints, major components, dependencies, interfaces at the architectural level, compatibility and migration expectations, decisions needing user approval, and completion criteria.

Preserve `backup/MASTER_PLAN.original.md` as immutable approved semantic baseline when implementation planning begins. Git history alone does not replace the active-cycle semantic reference. If later explicit approval changes architecture, document the new approval and reconcile current canonical plans without covertly rewriting the original baseline.

### PLAN_INDEX.md

Dependency-oriented routing and traceability map: macroblocks, microsteps, ordered/parallel dependencies, Plan Part paths/status, cross-part invariants, Implementation Batches, GOALs, Expected Evidence, and an **Agent Capability Matrix**.

The matrix is **platform-profiled**: for each supported platform, record primary, worker and optional specialist roles, exact model IDs/versions and effort **when the interface exposes them**, otherwise the verified selector name/tier and its resolution limitation; client/surface/version, verification date, permitted fallbacks, routing constraints, and unavailable features. Include `single-model` and `dual-tier` modes and platform-specific parallelism limits. Never invent exact IDs from display labels or assume tiers map to fixed versions. Revalidate material runtime differences before execution. Never encode models, platforms, or mutable assignments in Plan Part filenames.

Each GOAL entry identifies direct Luna ownership, parallel candidates, specialist triggers, delegation envelopes, integration, **batch-level validation boundaries**, the essential affected-test set and reusable prior evidence. `UNASSIGNED` may exist during early decomposition only; none may remain at implementation handoff.

### Plan Parts

Filename/path describe stable work identity, not Luna/SOL assignment. A Plan Part must be **code-forward**, with enough implementation-ready technical content for an economical primary implementer to build mechanisms instead of reasoning them out again. Include, as relevant:
- Goal and **current-to-target** behavior, verified repo base and real paths/symbols;
- fixed decisions, non-goals, invariants, types, state, ownership/lifetime, and contracts;
- **substantial concrete source code, function bodies, interfaces, implementation skeletons, or detailed executable-style pseudocode** for non-trivial mechanisms, including algorithms, call sequences, data flow, and migration order;
- failure/retry/cancellation, races, persistence, resource/performance and cleanup behavior expressed in the proposed implementation where useful;
- dependencies, writable ownership, independent/parallel slices, integration boundaries;
- **essential** build/test/instrumentation procedures and objective Expected Evidence **at shared batch/GOAL validation boundaries**, not an automatic test per part;
- a proposed specialist trigger and minimal context only when justified.

**Default toward more useful implementation code, not less.** If ChatGPT has enough verified source and decisions to draft a correct implementation, provide it. Prefer code that can be adapted or implemented directly over prose describing what Luna should invent. Use precise pseudocode when exact source would require unverified APIs or would lock in an unjustified detail. Explain integration points, ownership, and assumptions. Code volume is not itself a goal: omit boilerplate, existing unchanged code, speculative unverified implementations, and irrelevant examples.

Be explicit about proposed names versus existing symbols. Avoid large *unchanged* source dumps and research transcripts; substantial **new implementation code** is encouraged. A longer, code-dense Plan Part is preferable to a short narrative that transfers difficult work to Luna.

### CHAT_HANDOFF.md

Compact operational checkpoint: verified baseline, phase, last completed unit, remaining work, blockers/decisions, context-safety state, exact next action and minimum files to reload. Include continuous/manual-mode state if relevant. Do not use a running conversation transcript or stale operation counter as authority.

### IMPLEMENTATION_HANDOFF.md — portable execution authority

The **single canonical implementation handoff** for new planning cycles. It contains both:
1. **Approved stable contract:** verified repo/base, plan root/index, platform-neutral GOAL order and foundational gates, approved Agent Capability Matrix (per-platform profiles and single/dual-tier modes), allowed writes, delegation, escalation and testing/Expected Evidence rules.
2. **Compact mutable execution checkpoint:** active/last platform and selected model profile, current GOAL, completed and remaining coherent steps, active/pending work, exact code baseline and dirty working-tree provenance, relevant tests and evidence validity, pending integration/locks/worktrees, blockers, and **one precise next safe action**. Update this small section at meaningful checkpoints and before switching platforms, not for every microstep.

`IMPLEMENTATION_HANDOFF.md` is the **sole portable source for current implementation state**. `PLAN_INDEX.md` owns the approved task graph; `CHAT_HANDOFF.md` owns ChatGPT conversation continuity. Never duplicate mutable implementation state in either. For pre-existing cycles, `CODEX_HANDOFF.md` may remain as a **read-only compatibility pointer** to the canonical portable handoff; migrate its active state once and avoid parallel authorities.

Do **not** create or maintain a manual `ACTIVE_MODEL` switch variable. The active **platform/profile** recorded at a user-authorized handoff is a verified routing choice, not permission to change UI model selection or proof of the effective model. Never infer an active platform from stale chat or agent claims.

### CLEANUP_HANDOFF.md and CLEANUP_FINDINGS.md

After convergence, ChatGPT prepares a temporary, bounded, platform-neutral Cleanup GOAL handoff: reconciliation rules, removal/preservation scope, build/cache policy, clean rebuild, and stop conditions. The selected compatible primary agent executes it only after explicit user start. An older `CODEX_CLEAN_HANDOFF.md` can be treated as a compatibility source during migration, not a second active authority. `CLEANUP_FINDINGS.md` is the concise surviving feedback artifact for real unresolved implementation divergences and durable architecture corrections, not a cleanup log.

## 6. Brainstorm and master-plan approval gate

ChatGPT compares requirements and design alternatives, inspects source when relevant, and resolves decisions with the user. Keep the MASTER_PLAN concise; avoid premature Plan Part expansion. Cite external sources only when they materially drive a choice.

When the user explicitly approves implementation planning:
1. Confirm consumer repository/base and planning write scope.
2. Persist `PROJECT.md`, the approved `MASTER_PLAN.md`, and immutable `backup/MASTER_PLAN.original.md`.
3. Begin the index/decomposition stage.
4. Preserve open questions requiring true user authority; do not invent decisions to avoid asking.

Routine technical choices that follow an approved architecture can be resolved in planning without repeated user approval.

## 7. Decomposition and the bidirectional audit gate

Decompose the approved master into coherent macroblocks, microsteps, dependencies, outputs, cross-domain contracts, and provisional neutral Plan Part paths. Preliminary roles are **Luna direct**, **Luna parallel**, **specialist candidate**, or **UNASSIGNED**.

At the **first completed decomposition**, persist the index and stop for a user checkpoint even if Continuous Mode is enabled. This checkpoint allows review of broad scope before detailed expansion. One subsequent user continuation authorizes the audit and following approved planning work; it is not a demand to approve every microstep.

### Decomposition Audit Gate

Before expansion:
1. Fresh-read persisted `MASTER_PLAN.md` and `PLAN_INDEX.md`.
2. Trace **every** implementation-relevant requirement, decision, invariant, non-goal affecting scope, compatibility expectation, and dependency *forward* to index work or an explicit no-work reason.
3. Trace **every** material index item *backward* to approved intent or verified current-source necessity.
4. Check missing bridges, ordering, duplicated ownership, parallel dependencies, overfragmentation, and agent-neutral paths.
5. Repair at the owning artifact, persist coherently, and re-read both from GitHub for another complete pass.
6. Advance only after a full clean pass or stop at a real blocker.

Do not fragment one conceptual audit into separate operations for every paragraph or Plan Part. A complete bounded audit plus necessary internal checks is one top-level operation unless the scope genuinely requires subdivision.

## 8. Plan expansion, research, and readiness

For each substantial Plan Part:
1. Verify relevant current source, functions, interfaces, schemas, and tests directly.
2. Confirm upstream/downstream contracts, ownership, and approved decisions.
3. Perform **targeted current external research** when comparable solutions, standards, or changing platform capabilities can materially affect the design; examine the actual sources and trade-offs. Do not create decorative research requirements for trivial repository-local work.
4. Resolve meaningful alternatives in ChatGPT, recording only implementation-relevant reasoning and sources.
5. **Write the implementation before merely describing it** when enough source evidence exists: provide concrete data types, function signatures and bodies, sequences, error handling, and integration code where useful; otherwise give sufficiently precise pseudocode with explicit assumptions. Do not remove working implementation detail to make a Plan Part shorter.
6. Specify migration, failure/concurrency cases, observability, integration, and the **smallest essential shared validation set** proving the relevant GOAL/batch outcomes. Avoid creating or running tests for each Plan Part by default.
7. Mark independent work and potential specialist calls only when useful.

### Code-first planning policy

ChatGPT should do as much of the hard coding and algorithm design as is safely possible **during planning**. A rich Plan Part may include multiple proposed functions or implementation fragments, not merely headings and short bullet points. Proactively add code when it eliminates Luna implementation decisions or likely specialist calls. Check proposed code against current types, APIs, ownership and surrounding call sites; label unverified fragments explicitly and replace invented APIs with precise integration contracts or pseudocode.

Prioritize **(1) correctness and applicable contracts, (2) code/pseudocode completeness for difficult behavior, (3) clear integration instructions, (4) concise explanatory prose**. Do not optimize for low line counts at the expense of useful code. No arbitrary minimum code quota; never pad with boilerplate or rewrite working unchanged source simply to enlarge a plan.

**Implementation Readiness Self-Check:** Could a verified economical primary agent in **each supported platform profile** use the included code/pseudocode directly, without reinventing hard algorithms, architecture, interfaces, ownership, concurrency, or sequencing? Have useful concrete implementations been omitted solely to keep the document short? Are repo facts and dependencies verified and batch-level acceptance evidence clear? Repair any material gap before marking expanded.

A file's line count is a **context-safety and maintainability indicator, not a brevity target**. The former ~1,200–1,600-line guidance may prompt a safety check, but a coherent, code-heavy file exceeding it is acceptable. Split by meaningful responsibility only when readability, dependencies, or context capacity require it; preserve complete implementation fragments and cross-part contracts.

## 9. Final optimization and multi-agent consistency gates

After all required parts are expanded, perform the full gates in order. Checkpoint compaction is not a replacement.

### Pass A — implementation-preserving optimization

Remove filler, outdated rationale, duplicated explanations, ambiguous choices, and avoidable planning left to the economical primary agent. **Increase actionable code density**: add missing concrete implementations, function bodies, algorithms, migration steps, race/error handling, and pseudocode where verified source permits. Do **not** compress or remove useful implementation code just to shrink the plan. Consolidate redundant test instructions into shared GOAL/batch validation without removing essential evidence or failure behavior.

### Pass B — Specialist Minimization and Agent Routing

Challenge **every** planned stronger-model call: can better source evidence, scope reduction, a concrete interface, algorithm, code snippet, or dependency resolution make the economical primary agent capable? Retain specialist calls only when a material residual difficulty remains **in the selected dual-tier profile**. A single-model profile has no automatic stronger-model escalation; a true capability blocker requires explicit user approval to change mode/profile/platform. Decide **Solve Only** before **Scoped Implementation** unless the latter is clearly necessary.

Audit parallel slices for genuine independence, coordination cost, shared state, file ownership, and integration ordering. No automatic one-part-one-subagent or one-part-one-test mapping.

### Pass C — Cross-artifact Consistency Gate

Audit `MASTER_PLAN → PLAN_INDEX → Plan Parts → current repository` in both directions for requirements, interfaces, states, ownership, contracts, dependencies, migration, tests, and approved decisions. Add cross-agent checks: **platform-neutral contracts**, profile-specific effective model/tier routing, delegation inputs/outputs, allowed reads/writes, concurrent writes, integration, specialist permissions, **cross-platform checkpoint/resume**, and Expected Evidence.

Repair contradictions in the **owning canonical artifact** (architecture → master, decomposition/routing → index, mechanism → part), propagate downstream, then repeat until a complete clean pass or real blocker. Do not hide contradictions by patching handoffs alone.

### Final GOAL construction and handoff gate

Build meaningful Implementation Batches; mark foundational GOALs whose evidence gates dependent work. A GOAL may reference many Plan Parts. For each GOAL include:
- bounded mission, current-to-target delta, dependencies, authorized modifications;
- direct primary-agent steps, optional independent worker tasks and ownership;
- justified specialist triggers and smallest initial delegation packet **only in a supported dual-tier profile**;
- integration sequence, rollback/recovery rules, **a substantial implementation batch followed by few essential tests at its meaningful boundary**, and Expected Evidence. Include earlier tests only for justified risk/foundational gates; identify which previously passing checks remain valid unless affected code/dependencies change.

Confirm the per-platform capability matrix and compatibility/bootstrap obligations, then persist `IMPLEMENTATION_HANDOFF.md` as the shared execution contract and initial checkpoint. The user explicitly selects a platform/profile and starts implementation; planning approval is not implementation-start authorization.

## 10. Platform profiles, agent configuration, and compatibility

**Plan once; adapt execution per platform.** Keep roles independent of vendor/model names. The supported baseline platforms are **Codex** and **Google Antigravity**, with room for future adapters after research and validation. User selects one platform/profile for a running session; moving between profiles is explicit and checkpoint-driven.

### Runtime role profiles

- **Dual-tier:** economical primary implementer and economical parallel workers, with an optional stronger specialist used only for justified hard problems. Codex candidate: Luna High primary/workers and SOL High specialist. Antigravity candidate: a verified **Gemini Flash Medium**-class primary/parallel configuration and a verified more capable model/tier for specialists.
- **Single-model:** one verified model for the primary implementer **and workers**. Parallelism may use clones or explicitly configured same-model agents; no specialist tier is assumed. If a genuinely difficult fragment exceeds this profile, return a blocker or request explicit approval for a profile/platform change.
- **Model identifiers:** Plan exact IDs/versions and reasoning effort **when supported by the surface**. Otherwise record the exact UI label, tier, available effort, and `effective_model_unverified` rather than inventing an ID. A named Gemini Flash variant can change; verify current available models and user entitlements at bootstrap.

The stable Plan Parts must not depend on platform tools, prompt syntax, agent IDs, vendor-specific model strengths, or live session state. The capability matrix describes how the same GOAL is executed on each platform.

### Codex adapter

Codex uses project-local `.codex/agents/*.toml`, relevant `.codex/config.toml` agent settings, and applicable `AGENTS.md`. Verify workspace trust, model/effort support, discovery and spawn routing in the actual CLI/IDE/App; examples such as `gpt-6-luna` and `gpt-6.1-sol` are version-sensitive, not guarantees. Prefer context-clean subagent spawning when supported and verified; follow §11 for minimal delegation.

### Antigravity adapter

Official Antigravity App/CLI docs (checked 2026-11-02) describe workspace custom subagents in `.agents/agents/<name>.md` or `.agents/agents/<name>/agent.md`, Markdown with YAML frontmatter. The documented **subagent** `model` field accepts `inherit`, `flash`, or `pro`: these are **tiers**, not pinned underlying model/version IDs. The actual primary model and thinking level are selected through the supported client model selector; confirm and record its effective label. Current available models include Flash Medium options; availability changes by account, surface and date.

Antigravity supports `invoke_subagent`, clean subagent contexts, and workspace policies `inherit`, `branch` (isolated Git worktree), or `share` where exposed. Test context, tools, worktree behavior and integration in the installed client. **Do not** assume `.codex/agents/*.toml` is consumed by Antigravity or translate TOML fields into unsupported YAML options.

Antigravity reads `AGENTS.md`/ `GEMINI.md` and `.agents/rules/*.md` according to its discovery rules. Keep shared `AGENTS.md` minimal to avoid duplicating handoff/plan content; do not clobber pre-existing rules. If detailed reusable instructions are necessary, prefer documented `.agents/skills/<name>/SKILL.md` patterns rather than obsolete `.agents/workflows/` (legacy IDE workflows stopped being indexed after 2026-10-19). Neither skills nor global rules are required just to perform a portability handoff.

**Do not conflate** the Antigravity IDE, App, CLI, SDK, or managed Gemini API agent: a feature or model-selection API documented for one surface does not prove the others implement it. Verify the user's actual chosen surface.

### Platform-specific Agent Bootstrap and Compatibility Gate

For the user-selected platform, before GOAL start or after a cross-platform transfer:
1. Verify repo, branch/HEAD, working tree, current handoff, approved write scope, installed client/surface/version, workspace trust, permissions and relevant pre-existing config.
2. Inspect **only that platform's** instruction/config files and effective model selection. Preserve all unrelated existing files and configurations, including the other platform's agent files.
3. Bootstrap only roles necessary for the selected profile: Codex `.codex/...`; Antigravity `.agents/agents/...`; shared `AGENTS.md` only when authorized. Never create unused specialist definitions in single-model mode.
4. Validate schema/discovery, necessary tools, sandbox/approval behavior, concurrency cap, and a small real role invocation if needed. Confirm effective model/effort where observable; distinguish verified identifiers, UI labels and unresolved model-tier mappings.
5. Confirm the selected platform can read the portable handoff and complete at least a non-destructive resume readiness check. If an agent requires new session/config reload, checkpoint and request the user to resume explicitly.
6. Record platform, profile, effective capabilities, restrictions, test outcome and next step in `IMPLEMENTATION_HANDOFF.md`. Rerun compatibility only after platform switch or meaningful changes, not every step.

If routing is uncertain, **do not claim** a stronger model was invoked or silently substitute another tier. Ask for approval of a verified fallback or pause only dependent work. Agent config files and prompt rules are **not** filesystem sandboxes; use actual permission/worktree isolation where needed.

### Shared rules and precedence

Review applicable `AGENTS.md`, `GEMINI.md`, `AGENTS.override.md`, global/project rules and local platform config rather than overwriting them. The canonical work plan and portable handoff own the GOAL contract; vendor-specific rules contain minimal operational instructions only. Do not let conflicting platform adapters silently revise approved architecture, model/profile, test policy, or scope.

## 11. Minimal Context Delegation protocol

Each subagent has a separate context **to the extent established by the actual platform/spawn mode**. On supported Codex V2, `fork_turns: "none"` can avoid copying parent history; an unspecified mode may copy history. Antigravity custom subagents are documented as starting with clean context. Validate actual spawn behavior and tool availability in the chosen client. If tools are unavailable in a clean context, report the limitation; never forward complete histories by default.

Each dispatch must contain **only**:
- task/role and why delegation is justified;
- GOAL and bounded desired result;
- exact relevant Plan Part sections/contracts and verified repository paths/symbols;
- concise observed failure/diagnosis if applicable;
- allowed reads and writes, prohibited scope, and shared-state constraints;
- expected deliverable and validation criteria;
- progressive context request procedure.

Do not forward complete chat histories, whole plans, unrelated modules, large logs, or raw research. Source references should be precise enough that a subagent does not need to rediscover ownership.

**Progressive context:** the subagent requests the specific additional file, symbol, or evidence and explains why its current packet is insufficient. Luna may approve necessary operational expansion **within previously approved architectural and permission boundaries**. If approval would change architecture, unrelated write scope, security posture, or user authorization, stop and escalate to the user/ChatGPT.

A scope instruction is **not enforced filesystem isolation**. Agents may share tools, permissions, and workspace. Use actual sandbox/worktrees or external enforcement when strict isolation is required. Hooks may optionally add defense in depth after validation; do not claim they enforce all tool paths.

Subagent returns are compact and actionable: root cause or result, precise change/solution, relevant changed files, tests/evidence, limitations, and any unresolved request. The parent retains integration ownership.

## 12. Parallelism, file ownership, and integration

The primary Luna decides whether parallelism actually improves the mission. Parallel work is useful for disjoint subsystems, independent investigations, or independent read-only reviews; trivial or tightly coupled tasks remain direct.

Before spawning workers, record:
1. Dependency prerequisites and immutable upstream contracts.
2. File/module ownership and allowed writes.
3. Shared state: generated files, caches, databases, test fixtures, build directories, ports, locks, and migrations.
4. Integration owner, timing/order, merge plan, and a **shared post-integration validation boundary** rather than a test run per worker or Plan Part.
5. Concurrency ceiling and stop/failure procedure.

Read-only exploration can overlap widely if useful. Write tasks require non-conflicting ownership and compatible shared resources. Different source files do **not** automatically mean independent tasks. Where practical, use isolated worktrees/branches for writes that cannot safely share a workspace; otherwise serialize.

Workers do not independently redesign architecture, modify another worker's files, overwrite user edits, or create unrelated commits. Prefer the primary Luna to integrate, review diffs, run integration tests, and produce coherent commits. If a worker fails, retain validated independent progress and repair the relevant boundary, not the whole GOAL.

## 13. Planned and dynamic specialist escalation

Default: the selected profile's primary agent implements from the ChatGPT plan. A stronger specialist is **optional in dual-tier mode** and exceptional, never a routine reviewer of every file. Single-model mode has no automatic capability escalation; use its primary model also for worthwhile parallel workers.

### Planned escalation

A Plan Part/GOAL may authorize a specialist for a narrowly defined difficult fragment with prerequisite evidence, minimal input contract, permitted model/effort, allowed reads/writes, and expected return. If the plan itself makes the fragment mechanical for Luna, remove the escalation in Pass B.

### Dynamic escalation

When the active primary agent in a **dual-tier profile** hits a blocker:
1. Classify ordinary build/test error, missing evidence, plan defect, platform/permission boundary, or genuinely difficult reasoning.
2. Perform bounded diagnosis and materially different repairs using available plan/source evidence; do not require a fixed number of artificial retries.
3. Escalate only when a durable blocker remains or the problem is demonstrably too difficult to solve safely at Luna's capability.
4. Send a minimal packet with repro, observed evidence, bounded attempts, and exact contract. Do not recreate the entire failed investigation.
5. Prefer **Solve Only**: specialist diagnoses and returns a precise patch/algorithm/contracts for Luna to implement and test.
6. Use **Scoped Implementation** only when Luna demonstrably cannot reliably implement the fragment; restrict changes to explicitly allowed paths and integrate through Luna.
7. If the result fails, provide only the **new evidence** to the same specialist when available; avoid an unbounded chain of fresh expensive agents.

No specialist may unilaterally alter approved architecture, ownership, safety constraints, authorization scope, or a foundational contract. For a real plan contradiction, pause the affected dependent work and return to ChatGPT/user for an approved correction. In **single-model mode**, use bounded primary-agent diagnosis; if it cannot progress, checkpoint and request an approved change instead of silently invoking a stronger tier. Avoid indefinite retries, busy waiting, and silent fallbacks.

## 14. Autonomous GOAL execution

Starting a GOAL is a user action. Once started with a verified platform/profile:
1. The **active primary implementer** reads `IMPLEMENTATION_HANDOFF.md`, relevant `PLAN_INDEX.md` and Plan Parts (not all by default), confirms repo/HEAD/working tree and its authorized scope.
2. Recover only the **remaining** coherent steps and prerequisites from the portable checkpoint; verify that previously marked completed work is reflected in code and still-valid Expected Evidence. Do not redo settled work.
3. **Implement substantial coherent slices using Plan Parts' code/pseudocode**; do not reopen settled architecture or test each microstep.
4. Delegate useful independent work under the current profile. In dual-tier mode, escalate hard blockers when justified. In single-model mode, do not fabricate a stronger specialist.
5. Run the **minimum necessary post-batch/GOAL validation** proving Expected Evidence; earlier checks only for foundational, destructive, high-risk, or diagnostic necessity.
6. After a failure, repair and rerun failed/impacted checks rather than restarting an unaffected full suite.
7. At **meaningful durable boundaries** (completed integration slice, validated foundational milestone, before a planned platform switch, or when an interruption is foreseeable), update the **small mutable execution checkpoint**. Do not record every edit or generate ceremonial commits.
8. Report final evidence/changes/blockers concisely, preserving a verified next action if unfinished. A GOAL completes only when its acceptance contract is met.

Do not stop merely for ordinary build/test errors. Do stop at authorization/security/platform boundaries, an invalid architecture, or a genuine unresolved blocker. A user-triggered resume/new session may be needed after a provider limit or compatibility setup. **A new platform resumes from persisted repository state, not from the previous platform's conversation or subagent state.** It must not automatically claim still-running writes, uncommitted worktrees, or unknown tests as completed.

## 15. Tests, Expected Evidence, and observability

Every GOAL declares **Expected Evidence** that actually proves the requested behavior. Evidence can be targeted unit/integration tests, a build, API/ABI inspection, migration state, runtime behavior, deterministic reproduction, a measurement, or verified generated artifacts. Existing tests can satisfy new requirements when they genuinely cover the behavior; do not add redundant tests solely because a new Plan Part exists.

### Test planning: essential coverage, not per-part accumulation

- **Plan testing at meaningful Implementation Batch/GOAL boundaries.** Favor larger coherent implementation slices, then a small, decisive validation set at the end. A Plan Part, microstep, subagent return, or individual file change does not automatically trigger its own test run.
- **Do not prescribe, generate, or execute a new test for every Plan Part.** Select the minimum combination of existing and new checks needed to prove the approved Expected Evidence and critical invariants. Add tests for missing meaningful coverage, not for ritual completeness.
- **Early checks are exceptions** when necessary to prove a foundational contract before dependents, prevent costly propagation of a serious fault, validate a destructive migration, or de-risk concurrency/security/data-loss behavior. A quick compiler/type check may also be useful to unblock implementation. Do not turn these exceptions into an always-on per-edit loop.
- **Reuse passing results only while still valid.** A result must identify the tested code/commit or working-tree state, test version, relevant dependencies/configuration, and environment assumptions where material. If none of the covered source, transitive dependencies, build/test configuration, generated state, or runtime conditions that affect the check have changed, do not rerun it merely because another test was added elsewhere.
- **Invalidate affected evidence, not everything.** Changes in tested code or its relevant dependencies, shared infrastructure, toolchain/configuration, or test behavior require the impacted tests to be rerun; changes outside that impact boundary do not. When impact cannot be established reliably, run the minimum broader regression set needed to restore confidence.
- **Failure-driven loop:** first run the selected end-of-batch checks; diagnose failures, repair, rerun the failed/affected checks, and repeat only while producing material progress. Do not restart the full suite after every fix. Before declaring the GOAL done, confirm each required Expected Evidence result applies to the **final relevant code state**.
- **Broader clean validation** belongs at real integration/release/convergence boundaries when cross-cutting changes justify it, and at the explicit clean rebuild gate of Cycle Closure. Preserve safety-critical or mandatory project tests despite the preference for fewer runs.

Do not confuse **fewer runs** with **weaker evidence**. Record the selected validation boundary and evidence validity in the index/handoff; no continuously growing cumulative test checklist.

### Execution Evidence

At GOAL completion produce a compact **Execution Evidence** summary:
- GOAL ID and verified base/result commit or working-tree state;
- platform and actual verified primary model/effort if observable, and specialist model/tier if invoked;
- counts/purposes of parallel workers and optional specialist invocations, with Solve Only vs Scoped Implementation;
- changed files, integration result, targeted tests and Expected Evidence verdict;
- material deviations, unresolved blockers, and any reliable usage metrics **only if actually exposed by the client**.

Do not fabricate token totals, effort routing, or benchmark numbers. Do not keep large logs or full agent transcripts unless needed to reproduce a real failure. Compare overall GOAL cost/quality, not just specialist-call counts.

## 16. Convergence review after implementation

After a completed implementation batch, ChatGPT freshly compares **current repository code and test evidence** with the approved master/index/Plan Parts.

Classify any mismatch as missing, partial, contradictory, unrequested, or an approved requirement change. For material divergences, create bounded corrective GOALs with Expected Evidence; do not silently accept code as the new requirement. **Inspect and reuse still-valid passing evidence first.** Re-run checks only for changed/impacted areas, invalid evidence, or an uncovered required behavior, until intended behavior is supported or a genuine blocker/user decision remains.

Preserve observed bugs or hot-path problems outside approved scope as concise follow-up findings, not opportunistic undocumented changes.

## 17. Cycle Closure and cleanup

Convergence success allows **Cleanup Preparation**, not immediate cleanup execution.

ChatGPT resolves architecture/documentation reconciliation, dead-legacy classification, preservation/deletion boundaries, local generated/build state handling, and clean-rebuild evidence. It creates `CLEANUP_HANDOFF.md` for a single bounded, **platform-neutral** Cleanup GOAL with no architectural decisions left to invent.

Stop and require explicit user start for cleanup. The compatible selected primary agent:
1. Revalidates current code and approved final contract.
2. Reconciles permanent documentation without erasing intended behavior.
3. Removes only approved completed planning, obsolete paths, and classified generated residue.
4. Validates from a clean build/test state.
5. Removes temporary cleanup handoff when complete.
6. Preserves only concise live `CLEANUP_FINDINGS.md` for the next planning cycle.

Do not delete unclassified files, active architecture, or user work. A clean build failure or material divergence is a blocker or finding, not a reason to erase evidence.

The cycle is: **Plan → Implement → Converge → Clean → feed findings into the next Plan**.

## 18. Context safety, checkpoints, and handoffs

Context safety is independent of line count or tool limits. Before substantial reasoning/source/research work judge:
- **SAFE:** execute a bounded operation.
- **CAUTION:** finish the current coherent operation and checkpoint; avoid starting another major one without reassessment.
- **HANDOFF:** persist state and provide an exact continuation prompt; do not begin further substantial work.

Use observable evidence (conversation length, loaded source, failure patterns, incomplete responses, latency, contradictory recollections). There is no reliable universal remaining-context counter.

**Manual Mode:** default: perform one coherent substantial planning operation per user invocation and report the result. Do not split one bounded audit, related correction, or commit into ritual micro-steps.

**Continuous Mode:** opt-in; perform successive bounded operations while SAFE, checkpointing at meaningful changes and honoring the mandatory first-decomposition user checkpoint. There is **no copied 3×4 or 12-operation quota**. Use risk-based context checks rather than automatic small artificial blocks. Stop when a genuine user decision/approval is needed, a platform boundary appears, or Context Safety requires handoff; this does not mean asynchronous or background operation.

For **ChatGPT planning-session continuity**, persist `CHAT_HANDOFF.md`, synchronize `PROJECT.md`/`PLAN_INDEX.md` pointers and verified baseline, and finish with a populated copyable continuation prompt: repo/branch/HEAD, plan root, phase, last completed unit, next exact action, files to read, blockers, mode, and current manual URL. No placeholders, transcript, or obsolete history.

For **implementation-provider switches**, use the separate canonical `IMPLEMENTATION_HANDOFF.md` contract in §19. Never rely on `CHAT_HANDOFF.md` or a Codex/Antigravity conversation to transmit the live implementation state.

## 19. Portable implementation handoff and platform switching

The user may deliberately switch implementation platforms during an unfinished GOAL, including when usage allowance is exhausted on one platform. The goal remains **one approved mission** with the same contracts, permissions, decomposition and Expected Evidence, regardless of which supported platform executes the remaining work. Platform selection does not change ChatGPT's planning authority or permit evasion of a provider's restrictions.

### Canonical execution checkpoint (minimal state, not transcript)

The **single** `IMPLEMENTATION_HANDOFF.md` in the consumer plan root must contain a stable execution contract (see §5) plus a **small, current checkpoint** with these fields:

| Field | Required meaning |
| --- | --- |
| `schema_version`, `checkpoint_id`, `updated_at` | Versioned, unambiguous checkpoint identity (UTC when recorded); do not assume a time alone orders concurrent writes. |
| `repository`, `branch`, `base_commit`, `observed_HEAD` | Verified source provenance. Note whether changes were actually pushed and which workspace is authoritative. |
| `platform_from`, `platform_to`, `profile`, `effective_model` | Last known platform and user-selected next platform/profile; mark unverified selections explicitly, not as runtime facts. |
| `goal_id`, `goal_status`, `completed_slices`, `remaining_slices` | Current scope and only the material implementation slices already integrated versus remaining. |
| `worktree_state`, `pending_integrations` | Uncommitted changed/untracked files, staged content, worktree/branch paths if relevant, ongoing worker ownership, conflicts and any unmerged patches. |
| `evidence`, `invalidated_evidence` | Last valid test/Expected Evidence entries and the code/config/dependency baseline they prove; known failures and affected retest scope. |
| `blocking_issue`, `next_action` | One concise current blocker and **one executable next safe action**, pointing to exact Plan Parts/files. |
| `transfer_state` | `ACTIVE`, `HANDOFF_READY`, `RESUMING`, `BLOCKED` or `DONE`, with writer ownership and incomplete-transfer notes. |

Omit empty/irrelevant fields and resolved history, previous failed approaches, huge diffs/logs, transcripts, old agents, and repetitive test listings. Reference Git commits, changed file paths, small diffs, or external test artifacts when needed; do not paste entire files into the checkpoint.

### Safe handoff protocol

1. **Prepare on the outgoing platform when possible.** At a meaningful boundary, stop launching subagents, receive or terminate active work, and integrate/record each worker's outcomes. Quiesce active writers. For an abrupt usage-limit interruption, acknowledge that a final checkpoint may be impossible; the incoming platform reconstructs **only uncertain state** from the last checkpoint and real repository/working-tree evidence.
2. **Preserve implementation bytes.** Prefer a coherent checkpoint commit for integrated source and the small handoff update **when safe and authorized**. If files remain uncommitted, list affected paths and ensure the incoming platform can access the same physical worktree or an explicitly exported patch. A Markdown handoff does **not** transfer unstaged files, ignored assets, unpushed commits, private build artifacts, or worktrees between devices.
3. **User selects the next platform/profile.** Never silently switch accounts or providers, or automatically start another provider to work around usage restrictions. The user launches/resumes the new client's session in the repository and authorizes the current GOAL continuation.
4. **Incoming platform verifies** plan root, canonical handoff, branch/HEAD, uncommitted changes/patches, missing generated state, existing writer processes/subagents and outstanding integration. Do not overwrite working files or change branches in a way that loses progress. If parent and child writers may both continue, obtain exclusive ownership or stop until the ambiguity is resolved.
5. **Run only the incoming platform adapter's Compatibility Gate** (§10). Reuse verified model role/config when valid; do not rewrite the other platform's adapter or regenerate all agent files. If the chosen platform cannot safely meet a mandatory capability, request explicit approval for a supported fallback or stop.
6. **Resume exactly once.** Change checkpoint to `RESUMING` then `ACTIVE` only after obtaining writer ownership and verifying the current code state. Complete **only remaining slices**. Previously passing tests remain valid under §15's dependency and environment rules; run only invalidated/affected checks.
7. **Checkpoint after subsequent coherent milestones** and before another intentional switch. Finish at `DONE` only when all GOAL Expected Evidence is valid against the final relevant state.

Avoid excessive checkpoint commits and status churn; durable state must be sufficient for recovery, not a detailed execution diary. If the old platform was interrupted mid-step, assume that slice is **unverified**, inspect existing diffs and tests, and continue safely instead of discarding or blindly repeating work.

### Cross-platform resume prompt contract

A fresh client needs only a concise user instruction such as:

```text
Continue the approved GOAL from plans/<plan-name>/IMPLEMENTATION_HANDOFF.md.
Verify current HEAD and working-tree changes, current writer ownership,
completed vs pending slices, and validity of existing Expected Evidence.
Use the selected platform's verified agent profile and its compatibility gate.
Resume the exact next safe action without replaying past work.
Preserve approved scope. Update only the compact execution checkpoint.
```

No system can guarantee continuity of a running agent's internal thoughts, live in-memory state, session permissions, or unpersisted buffers. The contract guarantees **recoverable project progress to the extent it was persisted and verified**, not transparent migration of execution.

### External research notes

As checked **2026-11-02**: Antigravity documentation distinguishes the App, CLI, IDE and SDK; its custom subagents support Markdown/YAML, clean context and optional isolated worktrees, with `flash`/`pro`/ `inherit` tier selection; Gemini Flash Medium labels vary over time. Legacy Antigravity IDE workflows were deprecated effective 2026-10-19. Reverify features/model names on the actual installed surface before generating files or claiming model routing.

## 20. Maintaining and evolving this protocol

The *maintenance* repository is `Armoredweb/AN-chatNcodex-SubAgents-WorkFlow`. Its docs are English-first, with a pt-BR user guide. The original `Armoredweb/AN-chatNcodex-WorkFlow` is reference-only, never synchronized automatically.

When changing this manual: verify target repository/branch/HEAD, read the current manual and relevant source docs, get user approval for new architecture and write scope, edit the owning section, update both guides/README as needed, inspect contradictions, commit coherent changes, and verify remote persistence. Do not create unnecessary templates or unchecked agent TOMLs in this repository. Test examples in a consumer project before publishing reusable configuration examples.

### External references and version sensitivity

These are documentation references, not a claim that an actual local client was tested:

- [Codex subagents](https://developers.openai.com/codex/subagents)
- [Codex configuration reference](https://developers.openai.com/codex/config-reference)
- [Codex project instructions with AGENTS.md](https://developers.openai.com/codex/guides/agents-md)
- [Codex hooks](https://developers.openai.com/codex/hooks)
- [Codex multi-agent implementation](https://github.com/openai/codex)
- [Antigravity custom subagents](https://antigravity.google/docs/subagents)
- [Antigravity model selector](https://antigravity.google/docs/models)
- [Antigravity rules and AGENTS.md](https://antigravity.google/docs/rules)
- [Antigravity migration from workflows to skills](https://antigravity.google/docs/migration/workflows-to-skills)

Codex details derive from the prior **2026-10-30** documentation inspection; Antigravity platform details were examined on **2026-11-02**. Neither provider was tested in the user's actual local client. Revalidate before creating consumer-project configuration; interfaces, limits and models may change.
