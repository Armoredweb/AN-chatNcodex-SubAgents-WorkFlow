# Canonical Workflow

This file is the single operational authority for **AN-chatNcodex-SubAgents-WorkFlow**. It defines the protocol used by ChatGPT to plan changes in a consumer software repository and by a **selected, compatible implementation platform** (initially Codex or Google Antigravity) to execute approved GOALs. Plans and execution checkpoints are platform-neutral; platform-specific agent files are adapters.

The workflow repository defines the protocol; the consumer repository holds its own code, architecture, plans, and execution state. The Project Instructions used to **maintain this workflow** are not a substitute for the consumer-project protocol.

## 1. Purpose, boundaries, and operating principle

**ChatGPT does the difficult thinking. An economical primary agent performs most implementation. Stronger specialists address only justified residual complexity, using the minimum necessary context.**

- ChatGPT owns architecture, research, source inspection, decomposition, detailed planning, consistency, specialist-minimization, approval preparation, convergence review, and cleanup preparation **independent of implementation platform**.
- The selected platform runs a **primary agent that both orchestrates and implements**. For Codex, prefer Luna High; for Antigravity, a verified Gemini Flash Medium-class configuration is a candidate. These are profiles, not permanent model names.
- Support both **dual-tier mode** (economical primary/parallel workers plus optional stronger specialist) and **single-model mode** (same selected model for primary and parallel workers, no stronger specialist configured or assumed). Direct implementation remains the default in either mode.
- The workflow optimizes **implementation readiness and useful implementation code produced by ChatGPT**, shifting complex reasoning away from the implementation platform. Favor code/pseudocode-rich plans over superficially short plans; minimize redundant prose and expensive rediscovery, not useful technical content.
- **Orchestrate independent work proactively.** When multiple authorized, dependency-ready implementation slices or GOALs can proceed safely, the primary agent should normally delegate useful simple implementations to economical parallel workers and focus more of its time on routing, contracts, integration, and critical-path work; it may still implement directly when that is better.
- **Route by capability proactively.** In verified dual-tier mode, delegate image/screenshot interpretation and genuinely high-risk or very complex fragments to an appropriately capable specialist before mistakes accumulate, not only after repeated failures. Always send a precise minimal evidence/context packet.
- Execute **coherent implementation batches with selective, high-value validation**. The test repository may grow cumulatively, but during implementation run **only tests directly related to the active changes and their affected dependencies/consumers**—never the whole accumulated suite.
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

Each GOAL entry identifies primary-implementer ownership, **intra-GOAL parallel slices and cross-GOAL concurrency candidates**, prerequisites/critical-path gates, worker write ownership and shared-resource conflicts, optional dual-tier **proactive visual/high-risk/complexity routing** and blocker triggers, minimum delegation packets, integration, **batch-level selective validation boundaries**, relevant test selectors/dependency impact, plus reusable previously passing evidence. There is no cumulative per-GOAL list of all historical tests. `UNASSIGNED` may exist during early decomposition only; none may remain at implementation handoff.

### Plan Parts

Filename/path describe stable work identity, not Luna/SOL assignment. A Plan Part must be **code-forward**, with enough implementation-ready technical content for an economical primary implementer to build mechanisms instead of reasoning them out again. Include, as relevant:
- Goal and **current-to-target** behavior, verified repo base and real paths/symbols;
- fixed decisions, non-goals, invariants, types, state, ownership/lifetime, and contracts;
- **substantial concrete source code, function bodies, interfaces, implementation skeletons, or detailed executable-style pseudocode** for non-trivial mechanisms, including algorithms, call sequences, data flow, and migration order;
- failure/retry/cancellation, races, persistence, resource/performance and cleanup behavior expressed in the proposed implementation where useful;
- dependencies, writable ownership, **cross-component and cross-GOAL independence**, safe parallel slices, critical-path dependencies, isolation requirements, integration boundaries;
- **essential scoped test targets/commands**, impacted dependencies, and objective Expected Evidence **at shared batch/GOAL validation boundaries**; do not request the full project test suite or an automatic test per part;
- **proactive specialist/visual-review triggers** for objectively difficult, high-risk, or perception-heavy tasks plus a minimal evidence/context envelope when justified; dynamic blocker escalation remains a fallback.

**Default toward more useful implementation code, not less.** If ChatGPT has enough verified source and decisions to draft a correct implementation, provide it. Prefer code that can be adapted or implemented directly over prose describing what the primary implementer should invent. Use precise pseudocode when exact source would require unverified APIs or would lock in an unjustified detail. Explain integration points, ownership, and assumptions. Code volume is not itself a goal: omit boilerplate, existing unchanged code, speculative unverified implementations, and irrelevant examples.

Be explicit about proposed names versus existing symbols. Avoid large *unchanged* source dumps and research transcripts; substantial **new implementation code** is encouraged. A longer, code-dense Plan Part is preferable to a short narrative that transfers difficult work to the primary implementer.

### CHAT_HANDOFF.md

Compact operational checkpoint: verified baseline, phase, last completed unit, remaining work, blockers/decisions, context-safety state, exact next action and minimum files to reload. Include continuous/manual-mode state if relevant. Do not use a running conversation transcript or stale operation counter as authority.

### IMPLEMENTATION_HANDOFF.md — portable execution authority

The **single canonical implementation handoff** for new planning cycles. It contains both:
1. **Approved stable contract:** verified repo/base, plan root/index, platform-neutral **GOAL dependency graph and explicitly authorized runnable GOAL set** (including allowed concurrency), foundational gates, approved Agent Capability Matrix (per-platform profiles and single/dual-tier modes), allowed writes, task/capability routing, delegation, escalation and selective testing/Expected Evidence rules.
2. **Compact mutable execution checkpoint:** active/last platform and model profile, **active GOAL set** with concise per-GOAL completed/running/remaining slices, integration owner and in-flight workers/worktrees, exact code baseline and dirty working-tree provenance, relevant tests/evidence validity, conflicts/locks, blockers, and **one next safe action per active GOAL or critical integration boundary**. Update this small section at meaningful checkpoints and before switching platforms, not for every microstep.

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

Decompose the approved master into coherent macroblocks, microsteps, dependencies, outputs, cross-domain contracts, and provisional neutral Plan Part paths. Identify the **critical path and independently runnable components**, including safe cross-GOAL concurrency. Preliminary roles are **primary direct/integration**, **economical parallel implementation worker**, **proactive visual/high-risk/complex specialist candidate** (dual-tier only), or **UNASSIGNED**. Serial order in the index must encode real dependencies, not merely the order in which plans were written.

At the **first completed decomposition**, persist the index and stop for a user checkpoint even if Continuous Mode is enabled. This checkpoint allows review of broad scope before detailed expansion. One subsequent user continuation authorizes the audit and following approved planning work; it is not a demand to approve every microstep.

### Decomposition Audit Gate

Before expansion:
1. Fresh-read persisted `MASTER_PLAN.md` and `PLAN_INDEX.md`.
2. Trace **every** implementation-relevant requirement, decision, invariant, non-goal affecting scope, compatibility expectation, and dependency *forward* to index work or an explicit no-work reason.
3. Trace **every** material index item *backward* to approved intent or verified current-source necessity.
4. Check missing bridges, **false dependencies that serialize independent GOALs**, missing safe parallel opportunities, ordering, duplicated ownership, shared-resource risks, overfragmentation, and agent-neutral paths.
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
6. Specify migration, failure/concurrency cases, observability, integration, and the **smallest explicitly selected affected-test set** proving the relevant GOAL/batch outcomes. Existing test suites may accumulate as permanent project assets, but do not add per-part run requirements or include unrelated historical tests in a GOAL.
7. Mark **ready-in-parallel work both within a GOAL and across independent approved GOALs**; classify implementation roles by simple/independent versus visual/complex/high-risk capability. Specify the smallest useful specialist evidence package when needed.

### Code-first planning policy

ChatGPT should do as much of the hard coding and algorithm design as is safely possible **during planning**. A rich Plan Part may include multiple proposed functions or implementation fragments, not merely headings and short bullet points. Proactively add code when it eliminates implementation decisions for economical primary models or avoids likely specialist calls. Check proposed code against current types, APIs, ownership and surrounding call sites; label unverified fragments explicitly and replace invented APIs with precise integration contracts or pseudocode.

Prioritize **(1) correctness and applicable contracts, (2) code/pseudocode completeness for difficult behavior, (3) clear integration instructions, (4) concise explanatory prose**. Do not optimize for low line counts at the expense of useful code. No arbitrary minimum code quota; never pad with boilerplate or rewrite working unchanged source simply to enlarge a plan.

**Implementation Readiness Self-Check:** Could a verified economical primary agent in **each supported platform profile** use the included code/pseudocode directly, without reinventing hard algorithms, architecture, interfaces, ownership, concurrency, or sequencing? Have useful concrete implementations been omitted solely to keep the document short? Are repo facts and dependencies verified and batch-level acceptance evidence clear? Repair any material gap before marking expanded.

A file's line count is a **context-safety and maintainability indicator, not a brevity target**. The former ~1,200–1,600-line guidance may prompt a safety check, but a coherent, code-heavy file exceeding it is acceptable. Split by meaningful responsibility only when readability, dependencies, or context capacity require it; preserve complete implementation fragments and cross-part contracts.

## 9. Final optimization and multi-agent consistency gates

After all required parts are expanded, perform the full gates in order. Checkpoint compaction is not a replacement.

### Pass A — implementation-preserving optimization

Remove filler, outdated rationale, duplicated explanations, ambiguous choices, and avoidable planning left to the economical primary agent. **Increase actionable code density**: add missing concrete implementations, function bodies, algorithms, migration steps, race/error handling, and pseudocode where verified source permits. Do **not** compress or remove useful implementation code just to shrink the plan. Consolidate redundant test instructions into **selective, affected-code GOAL/batch validation**; eliminate accidental full-suite commands and repeated execution of still-valid historical tests without removing essential evidence or failure behavior.

### Pass B — Specialist Minimization and Agent Routing

Challenge **every** planned stronger-model call against actual required capability and consequences of error. Better source evidence, scope reduction, algorithms, code or pseudocode should remove avoidable expensive calls, **but do not force an economical model to perform perceptually difficult screenshot/image analysis or genuinely high-risk/complex implementation** merely to minimize specialist count. In a verified dual-tier profile, retain **proactive** specialist analysis/implementation where the quality or failure cost justifies it; also retain justified blocker escalation. A single-model profile has no automatic stronger-model escalation; a true capability blocker requires explicit user approval to change mode/profile/platform. Decide **Solve Only** before **Scoped Implementation** unless the latter is clearly necessary.

Audit **ready GOALs and independent slices across GOAL boundaries**, not just parallel work inside one GOAL. Challenge avoidable serial execution and preferentially route useful simple implementation to economical workers so the primary orchestrates/integrates and implements critical-path or tightly coupled work. Check dependencies, context overhead, files, shared state, worktrees, concurrent resource limits, integration order and tests. No one-part-one-subagent or one-part-one-test mapping. Concurrent agents must not launch overlapping suites or compete for shared test resources.

### Pass C — Cross-artifact Consistency Gate

Audit `MASTER_PLAN → PLAN_INDEX → Plan Parts → current repository` in both directions for requirements, interfaces, states, ownership, contracts, dependencies, migration, **test impact mappings and exact selective test selectors**, and approved decisions. Add cross-agent checks: **platform-neutral contracts**, planned GOAL readiness/concurrency (no false dependencies), **visual artifact accessibility and specialist suitability**, proactive high-risk routing, profile-specific effective model/tier, minimal delegation envelopes, shared write ownership, integration, permissions, **multi-GOAL cross-platform checkpoint/resume**, and Expected Evidence.

Repair contradictions in the **owning canonical artifact** (architecture → master, decomposition/routing → index, mechanism → part), propagate downstream, then repeat until a complete clean pass or real blocker. Do not hide contradictions by patching handoffs alone.

### Final GOAL construction and handoff gate

Build meaningful Implementation Batches; mark foundational GOALs whose evidence gates dependent work. A GOAL may reference many Plan Parts. For each GOAL include:
- bounded mission, current-to-target delta, dependencies, authorized modifications;
- **parallel-ready GOAL/slice prerequisites**, worktree/shared-resource ownership, direct primary critical-path/integration work, and delegated simple independent implementation tasks;
- **proactive visual/complex/high-risk specialist assignments** plus justified blocker triggers and the smallest initial **artifact-aware** delegation packet **only in a supported dual-tier profile**;
- integration sequence, rollback/recovery rules, **a substantial implementation batch followed by only its changed/affected tests at a meaningful boundary**, and Expected Evidence. Provide exact selective test targets/commands where known, including direct dependencies and impacted consumers. List earlier tests only for justified risk/foundational gates; do **not** include or run the whole accumulated suite during any implementation GOAL.

Confirm the per-platform capability matrix and compatibility/bootstrap obligations, then persist `IMPLEMENTATION_HANDOFF.md` as the shared execution contract and initial checkpoint. **Explicitly label which GOALs may run concurrently** and which require validated predecessors. The user selects a platform/profile and authorizes the implementation GOAL(s) or a bounded batch/queue: approval to start **one** GOAL does not automatically authorize starting all others.

## 10. Platform profiles, agent configuration, and compatibility

**Plan once; adapt execution per platform.** Keep roles independent of vendor/model names. The supported baseline platforms are **Codex** and **Google Antigravity**, with room for future adapters after research and validation. User selects one platform/profile for a running session; moving between profiles is explicit and checkpoint-driven.

### Runtime role profiles

- **Dual-tier:** economical primary implementer and economical parallel workers, with an optional stronger specialist used only for justified hard problems. Codex candidate: Luna High primary/workers and SOL High specialist. Antigravity candidate: a verified **Gemini Flash Medium**-class primary/parallel configuration and a verified more capable model/tier for specialists.
- **Single-model:** one verified model for the primary implementer **and workers**. Parallelism may use clones or explicitly configured same-model agents; no stronger specialist tier is assumed. The agent still proactively delegates safe parallel tasks. If a visually demanding, high-risk, or complex fragment exceeds this profile's actual capabilities, request an approved profile/platform change or report a blocker; never silently invoke a stronger tier.
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
4. Validate schema/discovery, necessary tools, sandbox/approval behavior, concurrency cap, and a small real role invocation if needed. **Verify actual agent support for accessing image artifacts/screenshots**, not merely that the underlying model is advertised as multimodal. Confirm effective model/effort where observable; distinguish verified identifiers, UI labels and unresolved model-tier mappings.
5. Confirm the selected platform can read the portable handoff and complete at least a non-destructive resume readiness check. If an agent requires new session/config reload, checkpoint and request the user to resume explicitly.
6. Record platform, profile, effective capabilities, restrictions, test outcome and next step in `IMPLEMENTATION_HANDOFF.md`. Rerun compatibility only after platform switch or meaningful changes, not every step.

If routing is uncertain, **do not claim** a stronger model was invoked or silently substitute another tier. Ask for approval of a verified fallback or pause only dependent work. Agent config files and prompt rules are **not** filesystem sandboxes; use actual permission/worktree isolation where needed.

### Shared rules and precedence

Review applicable `AGENTS.md`, `GEMINI.md`, `AGENTS.override.md`, global/project rules and local platform config rather than overwriting them. The canonical work plan and portable handoff own the GOAL contract; vendor-specific rules contain minimal operational instructions only. At bootstrap, where supported, give the primary a **short durable instruction to scan the ready GOAL/slice graph, dispatch independent economical workers proactively, route verified visual/high-risk work by capability, and integrate results**. Do not copy all planning documents into agent configurations. Do not let conflicting platform adapters silently revise approved architecture, model/profile, test policy, or scope.

## 11. Minimal Context Delegation protocol

Each subagent has a separate context **to the extent established by the actual platform/spawn mode**. On supported Codex V2, `fork_turns: "none"` can avoid copying parent history; an unspecified mode may copy history. Antigravity custom subagents are documented as starting with clean context. Validate actual spawn behavior and tool availability in the chosen client. If tools are unavailable in a clean context, report the limitation; never forward complete histories by default.

Each dispatch must contain **only**:
- task/role and why delegation is justified;
- GOAL and bounded desired result;
- exact relevant Plan Part sections/contracts and verified repository paths/symbols;
- **for visual work, the actual accessible image/screenshot artifact path or supported attachment reference, affected UI state/frame/region, expected-versus-observed behavior, and a precise visual question** (a primary agent's text summary is not a substitute for seeing the image);
- concise observed failure/diagnosis if applicable;
- allowed reads and writes, prohibited scope, and shared-state constraints;
- expected deliverable and validation criteria;
- progressive context request procedure.

Do not forward complete chat histories, whole plans, unrelated modules, large logs, or raw research. Source references should be precise enough that a subagent does not need to rediscover ownership. **For implementation workers**, supply the concrete proposed code/interfaces and allowed files so they can write directly. **For specialists**, provide the real minimal image/reproduction/contract and restrict unrelated reads; use native artifact handles instead of inflating prompts with image encodings when supported.

**Progressive context:** the subagent requests the specific additional file, symbol, or evidence and explains why its current packet is insufficient. The primary implementer may approve necessary operational expansion **within previously approved architectural and permission boundaries**. If approval would change architecture, unrelated write scope, security posture, or user authorization, stop and escalate to the user/ChatGPT.

A scope instruction is **not enforced filesystem isolation**. Agents may share tools, permissions, and workspace. Use actual sandbox/worktrees or external enforcement when strict isolation is required. Hooks may optionally add defense in depth after validation; do not claim they enforce all tool paths.

Subagent returns are compact and actionable: root cause or result, precise change/solution, relevant changed files, **for visual findings exact screen region and observed discrepancy**, scoped tests/evidence, limitations, and any unresolved request. The parent retains integration ownership. Avoid a second specialist pass unless the result is materially ambiguous, the artifact changed, or the risk requires independent verification.

## 12. Proactive parallel orchestration, GOAL scheduling, and integration

**Orchestrator-first when concurrency is useful:** the primary agent is not required to personally implement every available task. For two or more non-trivial **independent ready** slices, preferentially spawn economical implementation workers while the primary coordinates contracts, dependency readiness, integration, outstanding high-risk decisions, and the critical path. The primary may also implement an independent critical-path/tightly coupled slice while workers execute elsewhere. Avoid both extremes: serially implementing everything alone, or spawning agents for negligible work whose setup/coordination costs exceed the benefit.

### Two levels of parallelism

1. **Within one authorized GOAL:** dispatch independent components or steps concurrently if their interfaces and file ownership are stable.
2. **Across multiple authorized GOALs:** dispatch GOALs in parallel **only if the user has explicitly authorized the implementation batch/GOAL set** and their prerequisites, write ownership, and shared-resource gates allow it. An order in the index is not automatically a dependency; an architectural/foundational dependency is a hard gate until its evidence is valid. Never start unapproved GOALs just because they are ready.

At each meaningful dispatch boundary, classify available work:
- **Economical worker implementation:** simple, bounded, well-planned coding in independent components; use two or more concurrent workers when their expected time savings exceed context/coordination overhead.
- **Primary direct work:** integration, shared contracts, critical-path changes, conflict resolution, or a small/serial task best completed immediately.
- **Proactive capable specialist:** actual image/screenshot perception, non-trivial visual layout diagnosis, very complex algorithms, or high-risk contracts/implementation under §13 and a verified dual-tier profile.
- **Blocked/serial:** missing approvals, unmet prerequisites, shared writes/resources without safe isolation, unsupported capabilities or uncertain integration.

### Ready-work scheduler (normative pseudocode)

```text
authorized := user_approved_goals_or_batch
ready := tasks_in(authorized) where prerequisites_have_valid_evidence
for task in ready:
    if shared_write_or_runtime_conflict(task): serialize_or_isolate(task)
    else if verified_visual_or_high_risk_specialist_needed(task):
        route_narrow_specialist_task(task)    // dual-tier only, per §13
    else if independent_substantial_work(task) and worker_capacity_available:
        dispatch_economical_worker(task, minimal_context_packet)
    else:
        primary_implements_or_integrates(task)

as_workers_finish:
    collect_compact_evidence_and_diffs()
    integrate_with_exclusive_write_ownership()
    run_only_affected_selective_tests()
    mark_dependency_ready_only_after_required_evidence()
    dispatch_newly_ready_authorized_tasks()
```

This is a **continuous ready-queue**, not a one-time decision at GOAL start. Reassess after a completed dependency, worker return, integration, blocker removal, or newly available independent task. Reuse an idle suitable worker where supported instead of unnecessarily starting a fresh session.

### Safe concurrent writes and cost controls

Before dispatch, establish each task's immutable upstream contracts, exact writable paths, generated files, database/migration state, build outputs/caches, ports, tests, worktree/branch owner, and integration order. **Different files are not necessarily independent.** Use isolated worktrees or branches when required and supported; otherwise serialize conflicting writers. Worker scopes in prompts are not technical sandboxes.

The primary is the **single integration/commit coordinator**. Workers should not independently change foundational contracts, merge conflicting branches, or create unrelated commits. Merge/apply only verified worker outputs; protect pre-existing user changes. Coordinate selective test runs so workers do not run conflicting or duplicate suites. Prefer a **single scoped post-integration validation** for related worker outputs, plus earlier targeted checks only at real foundational/safety boundaries (§15).

Choose concurrency based on actual task independence, expected elapsed time, available workers, resource contention and measured context/token overhead; **do not use a fixed agent count as a goal**. A few economical workers may accelerate simple modules; more workers are not automatically better. Keep parent context lean: worker task packets and terse results, not full logs or transcripts. On a failed worker, preserve unrelated validated progress and repair the affected slice.

## 13. Capability-aware proactive specialist routing and escalation

The primary **must evaluate task difficulty and evidence modality before attempting the work**, not only after it fails. In a verified **dual-tier** profile, it may proactively route a genuinely demanding fragment to a stronger specialist when the expected improvement in correctness, perception or risk reduction justifies cost. The goal is **minimum total time/tokens to a correct result**, not minimum specialist calls.

### Proactive specialist triggers

- **Visual perception and UI inspection:** a real screenshot, rendered UI, image composition, visual regression, alignment, layering, clipping, missing/doubled elements, color or shader artifact, animation frame, or comparison with an approved visual target, **when subtle visual differences matter**. Prefer a vision-capable stronger agent that can access the original image/capture. The primary can do routine obvious checks; do not escalate every trivial screenshot.
- **High-risk work:** security/authentication boundaries, irreversible persistence or migrations, update-signing/security-sensitive distribution, complex synchronization/data races, memory safety, or other work where a subtle error has material cost. Request a focused pre-implementation risk/contract review or direct scoped implementation if justified.
- **Very complex work:** tightly coupled algorithms, difficult cross-component state and ownership, performance-sensitive synchronization, nuanced platform compatibility, or mechanisms where a strong specialist is likely to avoid expensive redesign/retries.
- **Demonstrated blocker:** a hard issue that remains after bounded, materially different primary-agent diagnoses; ordinary compile/test failures are not triggers.

The plan/index should **preidentify** high-risk, visual and difficult fragments and specify timing, image/artifact access, minimal contracts and expected specialist return. The primary may add a new justified narrow call when real execution reveals a task's visual/risk/complexity demands; it must not expand approved architecture, permissions, or user scope.

### Specialist task modes

1. **Visual Review / Diagnose Only (preferred for perception):** inspect the actual accessible image(s) or screenshot(s), compare to the stated expected state, identify precise regions/differences and likely causes, and return an actionable verdict with confidence/uncertainty and relevant source symbols if known. The primary or economical worker implements and performs a **targeted new capture/verification** when the image changes.
2. **Solve Only (preferred for complex logic/risk):** examine a tightly bounded problem and return precise architecture-compatible algorithms, code/pseudocode, patch instructions, failure analysis or risk mitigations for the primary/worker to implement.
3. **Scoped Implementation:** specialist directly implements the hard fragment when direct execution by economical agents is unlikely to be reliable or would cause expensive iteration. Define exact read/write ownership, interfaces and integration checks beforehand.

**Visual handoff must actually include or grant access to the source image.** Provide the artifact path/reference, UI/view resolution and state, frame/viewport/region where possible, expected outcome and a focused question. Do not send only a cheap model's textual description or ask the specialist to search the entire repository for a screenshot. Check model **and client/tool** image-input support before dispatch. For browser-only captures, use a verified supported browser/image tool; if no agent can receive the pixels, report the limitation or obtain the missing artifact, never fabricate visual analysis.

A stronger specialist is not required to review every visual iteration or all code. One high-value narrow pass is usually better than repeated generic audits. Reserve additional review for material new evidence, changed imagery, unresolved ambiguity, or a genuine safety gate. Return concrete findings and file/symbol references; primary integrates outcomes and owns selective tests (§15).

### Dynamic escalation and bounded recovery

When an unforeseen blocker appears:
1. Identify whether it is routine implementation failure, missing information, unsupported tool/image capability, an architectural contradiction, or true high-complexity/high-risk work.
2. Attempt bounded diagnosis and meaningful distinct repairs when appropriate; **do not wait through artificial retries** if risk or perceptual difficulty is already clear.
3. Select the smallest suitable specialist role and preferred mode; send the precise reproduction, observed evidence, attempted approaches that matter, exact paths, contracts, expected result, and allowed writes.
4. If the result fails, send **only new evidence** to the same agent when possible; avoid indefinite escalation loops or repeatedly re-reading the repository.
5. If specialist capability or permission is unavailable, checkpoint the affected task and request an approved fallback while unrelated authorized work may continue safely.

**Single-model mode:** proactively parallelize independent work with same-model workers, but **do not silently invoke a stronger tier**. The primary may use any verified vision capability of the selected single model; if its capability is insufficient for a required visual/high-risk contract, request user-approved profile/platform change or report a blocker. Avoid pretending that routing alone upgrades perception.

No specialist may unilaterally modify approved architecture, scope, security rules or foundational contracts. Escalate a genuine architectural change to ChatGPT/user, not to the specialist's discretion.

## 14. Autonomous GOAL and authorized batch execution

Starting implementation is a user action. **The user may authorize one GOAL or a bounded GOAL batch/queue.** Once the selected platform/profile is verified, the primary may coordinate **multiple approved independent GOALs at the same time**, without user prompts between their normal internal stages. Authorization to start only G01 is **not** authorization to start G02.

1. Read `IMPLEMENTATION_HANDOFF.md`, the GOAL dependency graph in `PLAN_INDEX.md`, and **only** relevant Plan Parts. Verify branch/HEAD, current worktrees and approved concurrent GOAL set.
2. Recover remaining tasks, already integrated work, still-valid Expected Evidence and unresolved worker states. **Do not replay completed work** or automatically assume an interrupted worker finished.
3. **Build the ready task queue across authorized GOALs** (§12). Validate true dependency/foundational gates. Dispatch useful simple independent implementations to economical workers **proactively**, without serializing all components through the primary. The primary coordinates, integrates and may implement critical-path or tightly coupled work concurrently.
4. **Route before mistakes:** in dual-tier mode, call a verified strong visual reviewer for subtle image/screenshot work or a capable specialist for clearly high-risk/very complex fragments (§13). Prefer precise Review/Solve Only where sufficient; use narrowly scoped specialist implementation when justified.
5. Integrate worker outputs under exclusive ownership and run **only explicitly selected tests of affected code and its dependencies/consumers** (§15). No full suite at GOAL completion or between parallel GOALs. On failures, repair and rerun only invalidated selectors; preserve valid evidence for other work.
6. Mark a GOAL or dependency done **only** when its own acceptance contract is proven. Unblock newly ready authorized GOALs immediately when it is safe; do not wait for unrelated GOALs to finish merely to advance independent work.
7. Persist a compact **multi-GOAL execution checkpoint** at meaningful integrated milestones, before a platform switch or likely interruption: active/blocked/finished GOALs, worker ownership/worktrees, integrated commits/dirty state, still-valid evidence and next ready action(s). Avoid a microstep log and gratuitous commits.
8. Report each completed GOAL's changes, focused evidence and remaining blockers concisely. Keep other independent, authorized work progressing if an isolated task is blocked; stop at genuine safety/approval/platform boundaries.

Do not automatically escalate a routine compile/test failure or add unapproved GOALs. Context and usage limits still apply; a new platform resumes from persisted repo/handoff state, **not** internal agent memories or old sessions. Preserve exclusive writers and check whether screenshots/artifacts and uncommitted branches are actually available before resuming visual or parallel work.

## 15. Selective implementation testing, Expected Evidence, and observability

**Fundamental separation:** the project's test suite is **cumulative as source code**, but test **execution during implementation is selective**. Existing tests remain available for final system/release validation. An implementation GOAL must never automatically execute the entire repository-wide test suite, regardless of how many historical tests have accumulated.

Every GOAL defines **Expected Evidence** that proves its requested behavior. Evidence may come from scoped unit/integration tests, isolated component checks, a targeted build/type-check, API/ABI verification, migration state, runtime inspection, measured behavior, or other objectively observable results. Reuse existing coverage instead of duplicating tests; add a new test only when needed to demonstrate meaningful missing behavior.

### Scoped test selection — mandatory for every implementation GOAL

1. **Determine actual changes first** for the relevant **worker slice, integrated GOAL, or independent GOAL group**, not the whole repository. Build a small impact map from edited/added modules, public interfaces, changed test code, relevant generated artifacts, shared contracts, and transitive dependencies/consumers that could be affected.
2. **Select test targets explicitly.** Run only tests for the changed functionality plus tests for genuinely affected dependencies/integration boundaries. Prefer named test cases, files, packages, modules, fixtures or filtered integration scenarios. Never select all test directories simply because the suite exists.
3. **Choose a meaningful coordinated validation boundary.** Favor implementing and integrating a coherent large slice before running selected tests. Multiple parallel worker outputs affecting the same component should share one scoped integration check, not competing duplicate runs. A Plan Part, microstep, subagent delivery, commit or single file edit does not by itself mandate a test run.
4. **Check command scope before launching.** Use known test filters or package/target arguments. Avoid unfiltered project-wide commands such as `pytest`, `cargo test`, `go test ./...`, `ctest` without selection, `npm test` scripts that invoke every package, or equivalent commands **unless a specific filtered invocation has been verified**. Review script aliases and task runners to ensure that a seemingly targeted command does not launch the whole suite.
5. **Never use full-suite fallback during implementation.** If impact is uncertain, inspect only enough dependency edges to choose a **conservative but targeted subset**. If no reliable selective runner exists, use a justified isolated check or record unverified evidence/a genuine blocker. Do not silently run the entire suite to compensate for missing selectors.
6. **Rerun only invalidated tests.** On failure, diagnose and fix, then rerun failed tests and any other selectors affected by the fix. Previously passing tests remain valid if their covered code, transitive dependencies, test definitions, generated state, toolchain/configuration and material environment have not changed. New tests added elsewhere do not invalidate unrelated passing evidence.
7. **Prove the final state.** A GOAL is complete only when the selected relevant Expected Evidence holds for its final affected code state. Do not append a full-suite regression run at GOAL completion. If a mandated or safety-critical gate requires extra coverage, select its relevant targeted checks; if only a full suite can satisfy a non-negotiable external gate, report the boundary rather than violating the GOAL policy.

### Cumulative test library and final comprehensive verification

- Continue preserving and adding **useful automated tests** over the project's lifetime. The accumulated test suite is an asset, **not** an execution queue that every agent must replay.
- Reserve a **complete-suite run, if desired or required**, for a separately defined **post-implementation system/release validation gate**, after the relevant implementation GOALs have ended. It is **not** part of routine GOAL execution, per-batch checks, every commit, every new test, or automatic recovery. A final release gate may run the entire suite once when its scope and cost are explicitly accepted; a clean build alone does not imply a full test sweep.
- Existing organizational CI, branch protection or security-mandated checks still apply. Do not modify/disable such checks without authorization. Identify unavoidable automatically triggered broad CI and distinguish it from **agent-invoked** testing; report its cost/constraints instead of hiding it or repeatedly triggering it.
- The only standing early exceptions are **scoped** checks for foundational contracts, destructive migrations, concurrency/security/data-loss risks or an actual debugging need. Exceptions never authorize running unrelated tests during a GOAL.

### Efficient evidence and cross-platform reuse

The index/handoff should hold **only** selectors for the currently active authorized GOALs, observed outcomes, relevant source/commit or dirty-state provenance, material test/config/environment dependencies, and invalidations. Do not maintain a growing ledger of historical test commands or repeated logs. When switching between Codex and Antigravity, the incoming agent compares real code/configuration with these provenance notes and executes **only newly invalidated/affected selectors**, never the entire suite as a resume ritual.

### Execution Evidence

At GOAL completion report briefly:
- GOAL ID (including simultaneous approved GOALs, if any) and verified base/result commit or working-tree state;
- platform and verified primary model/effort if observable, and specialist tier if used;
- counts/purposes of economical parallel workers, **proactive visual/high-risk/complex specialist invocations**, and any blocker-driven escalations, without claiming token savings without measurement;
- changed files, integration result, **exact selective tests/checks run and their outcomes**, and Expected Evidence verdict;
- previously passing checks reused with valid provenance, material gaps/blockers, and only reliable usage metrics actually exposed by the client.

Do not fabricate tokens, benchmark values, model routing, or test results. Do not include transcripts or large logs unless needed for a reproducible failure. Evaluate total GOAL completion cost and quality, not suite size or number of test runs.

## 16. Convergence review after implementation

After a completed implementation batch, ChatGPT freshly compares **current repository code and test evidence** with the approved master/index/Plan Parts.

Classify any mismatch as missing, partial, contradictory, unrequested, or an approved requirement change. For material divergences, create bounded corrective GOALs with Expected Evidence; do not silently accept code as the new requirement. **Inspect and reuse still-valid passing evidence first.** During corrective implementation GOALs, run **only selected changed/affected test targets**, not the full suite. Broader end-to-end verification, if chosen, belongs to the separate post-implementation validation gate rather than repeated corrective loops.

Preserve observed bugs or hot-path problems outside approved scope as concise follow-up findings, not opportunistic undocumented changes.

## 17. Cycle Closure and cleanup

Convergence success allows **Cleanup Preparation**, not immediate cleanup execution.

ChatGPT resolves architecture/documentation reconciliation, dead-legacy classification, preservation/deletion boundaries, local generated/build state handling, and clean-rebuild evidence. It creates `CLEANUP_HANDOFF.md` for a single bounded, **platform-neutral** Cleanup GOAL with no architectural decisions left to invent.

Stop and require explicit user start for cleanup. The compatible selected primary agent:
1. Revalidates current code and approved final contract.
2. Reconciles permanent documentation without erasing intended behavior.
3. Removes only approved completed planning, obsolete paths, and classified generated residue.
4. Validates from a clean build plus **the essential scoped cleanup/integration checks**. This does not automatically invoke the cumulative full suite; any comprehensive suite run belongs to the separately agreed post-implementation system/release gate.
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

The user may deliberately switch implementation platforms during **one unfinished GOAL or an explicitly authorized parallel GOAL batch**, including when usage allowance is exhausted on one platform. **Each GOAL keeps its own approved mission, status, dependencies and Expected Evidence** across the platform switch; concurrent GOALs remain separate missions under the same bounded authorization and canonical checkpoint. Platform selection does not change ChatGPT's planning authority or permit evasion of a provider's restrictions.

### Canonical execution checkpoint (minimal state, not transcript)

The **single** `IMPLEMENTATION_HANDOFF.md` in the consumer plan root must contain a stable execution contract (see §5) plus a **small, current checkpoint** with these fields:

| Field | Required meaning |
| --- | --- |
| `schema_version`, `checkpoint_id`, `updated_at` | Versioned, unambiguous checkpoint identity (UTC when recorded); do not assume a time alone orders concurrent writes. |
| `repository`, `branch`, `base_commit`, `observed_HEAD` | Verified source provenance. Note whether changes were actually pushed and which workspace is authoritative. |
| `platform_from`, `platform_to`, `profile`, `effective_model` | Last known platform and user-selected next platform/profile; mark unverified selections explicitly, not as runtime facts. |
| `authorized_goals`, `active_goals`, `goal_status`, `completed_slices`, `remaining_slices` | **Per-GOAL compact status** for the user-approved batch: ready/running/blocked/done, validated prerequisites, integrated slices and remaining work. Never silently add GOALs. |
| `worktree_state`, `pending_integrations` | Uncommitted changed/untracked files, staged content, **per-worker/GOAL ownership and isolation**, worktree/branch paths, active image/artifact paths and availability where material, conflicts and any unmerged patches. |
| `evidence`, `invalidated_evidence` | Compact, still-valid Expected Evidence and **only the affected test selectors**, with relevant code/config/dependency provenance; no cumulative historical suite log. |
| `blocking_issue`, `next_actions` | Only material blockers and **one executable next safe action per active GOAL or shared integration gate**, pointing to exact Plan Parts/files; no microstep history. |
| `transfer_state` | `ACTIVE`, `HANDOFF_READY`, `RESUMING`, `BLOCKED` or `DONE`, with writer ownership and incomplete-transfer notes. |

Omit empty/irrelevant fields and resolved history, previous failed approaches, huge diffs/logs, transcripts, old agents, and repetitive test listings. Reference Git commits, changed file paths, small diffs, or external test artifacts when needed; do not paste entire files into the checkpoint.

### Safe handoff protocol

1. **Prepare on the outgoing platform when possible.** At a meaningful boundary, stop launching subagents, receive or terminate active work, and integrate/record each worker's outcomes. Quiesce active writers. For an abrupt usage-limit interruption, acknowledge that a final checkpoint may be impossible; the incoming platform reconstructs **only uncertain state** from the last checkpoint and real repository/working-tree evidence.
2. **Preserve implementation bytes.** Prefer a coherent checkpoint commit for integrated source and the small handoff update **when safe and authorized**. If files remain uncommitted, list affected paths and ensure the incoming platform can access the same physical worktree or an explicitly exported patch. A Markdown handoff does **not** transfer unstaged files, ignored assets, unpushed commits, private build artifacts, or worktrees between devices.
3. **User selects the next platform/profile.** Never silently switch accounts or providers, or automatically start another provider to work around usage restrictions. The user launches/resumes the new client's session in the repository and authorizes continuation of **the previously approved GOAL or bounded GOAL batch**, without expanding its scope.
4. **Incoming platform verifies** plan root, canonical handoff, **all authorized active GOALs and their prerequisites**, branch/HEAD, uncommitted changes/patches, **accessible screenshots/visual artifacts**, missing generated state, existing writer processes/subagents and outstanding integration. Do not overwrite working files or change branches in a way that loses progress. If parent and child writers may both continue, obtain exclusive ownership or stop until the ambiguity is resolved.
5. **Run only the incoming platform adapter's Compatibility Gate** (§10). Reuse verified model role/config when valid; do not rewrite the other platform's adapter or regenerate all agent files. If the chosen platform cannot safely meet a mandatory capability, request explicit approval for a supported fallback or stop.
6. **Resume exactly once.** Change checkpoint to `RESUMING` then `ACTIVE` only after obtaining writer ownership and verifying the current code state. Reconstruct a ready queue from **only the already authorized GOAL set**, complete **only remaining slices**, and preserve safe concurrent ownership. Previously passing tests remain valid under §15's dependency and environment rules; run only invalidated/affected named tests **and never the full suite as a platform-resume check**.
7. **Checkpoint after subsequent coherent milestones** and before another intentional switch. Finish at `DONE` only when all GOAL Expected Evidence is valid against the final relevant state.

Avoid excessive checkpoint commits and status churn; durable state must be sufficient for recovery, not a detailed execution diary. If the old platform was interrupted mid-step, assume that slice is **unverified**, inspect existing diffs and tests, and continue safely instead of discarding or blindly repeating work.

### Cross-platform resume prompt contract

A fresh client needs only a concise user instruction such as:

```text
Continue the approved GOAL from plans/<plan-name>/IMPLEMENTATION_HANDOFF.md.
Verify current HEAD and working-tree changes, current writer ownership,
completed vs pending slices, and validity of existing Expected Evidence.
Use the selected platform's verified agent profile and its compatibility gate.
Resume the ready queue for **only the previously authorized GOALs**,
dispatch independent work when safely parallelizable, and route genuine
visual/high-risk work to a verified capable specialist if permitted.
Do not replay completed work. Preserve write ownership and approved scope.
Update only the compact execution checkpoint.
```

No system can guarantee continuity of a running agent's internal thoughts, live in-memory state, session permissions, or unpersisted buffers. The contract guarantees **recoverable project progress to the extent it was persisted and verified**, not transparent migration of execution.

### External research notes

As checked **2026-11-02**: Antigravity documentation distinguishes the App, CLI, IDE and SDK; its custom subagents support Markdown/YAML, clean context and optional isolated worktrees, with `flash`/`pro`/`inherit` tier selection; Gemini Flash Medium labels vary over time. As of **2026-11-04**, official Codex guidance supports prompting local clients to delegate and shows that agents have independent work/context but consume extra resources; Antigravity documents concurrent custom agents, worktree isolation and screenshot/browser tooling on **specific surfaces**. Verify actual multimodal access before delegating image review. Legacy Antigravity IDE workflows were deprecated effective 2026-10-19. Reverify features/model names on the actual installed surface before generating files or claiming model routing.

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
- [Antigravity browser screenshot capture](https://antigravity.google/docs/screenshots)
- [Antigravity built-in browser agent and surface limitations](https://antigravity.google/docs/commands/browser)
- [Antigravity model selector](https://antigravity.google/docs/models)
- [Antigravity rules and AGENTS.md](https://antigravity.google/docs/rules)
- [Antigravity migration from workflows to skills](https://antigravity.google/docs/migration/workflows-to-skills)

Codex details derive from the prior **2026-10-30** documentation inspection; Antigravity platform details were examined on **2026-11-02**. Neither provider was tested in the user's actual local client. Revalidate before creating consumer-project configuration; interfaces, limits and models may change.
