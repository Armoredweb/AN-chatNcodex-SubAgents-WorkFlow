# Canonical Workflow

This file is the single operational authority for **AN-chatNcodex-SubAgents-WorkFlow**. It defines the protocol used by ChatGPT to plan changes in a consumer software repository and by Codex to execute approved implementation GOALs.

The workflow repository defines the protocol; the consumer repository holds its own code, architecture, plans, and execution state. The Project Instructions used to **maintain this workflow** are not a substitute for the consumer-project protocol.

## 1. Purpose, boundaries, and operating principle

**ChatGPT does the difficult thinking. Luna performs most implementation. Stronger specialists address only justified residual complexity using the minimum necessary context.**

- ChatGPT owns architecture, research, source inspection, decomposition, detailed planning, consistency, specialist-minimization, approval preparation, convergence review, and cleanup preparation.
- Codex runs a **Luna High primary agent that is both orchestrator and implementer**. It implements directly by default, delegates independent work to Luna workers only when beneficial, and escalates real hard blockers to a more capable specialist.
- The workflow optimizes **implementation readiness per token** and the cost of achieving validated outcomes, not agent count, plan length, or unverified token estimates.
- A GOAL is an autonomous, bounded implementation mission; plan files do not define agent sessions, commits, or test boundaries.
- This protocol never authorizes bypassing product, account, safety, rate, security, or platform limits. A subagent is not an authorization bypass.

Do not assume that using more agents is faster or cheaper. Prefer direct implementation where the plan already supplies the solution.

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

Concise durable entry point: repository, branch/baseline, planning root/backend, authorized scope, phase, pointers to active artifacts, approved architecture baseline, and next responsible actor. No transcripts.

### MASTER_PLAN.md

Compact architectural backbone: outcome, requirements, behavior, invariants, non-goals, constraints, major components, dependencies, interfaces at the architectural level, compatibility and migration expectations, decisions needing user approval, and completion criteria.

Preserve `backup/MASTER_PLAN.original.md` as immutable approved semantic baseline when implementation planning begins. Git history alone does not replace the active-cycle semantic reference. If later explicit approval changes architecture, document the new approval and reconcile current canonical plans without covertly rewriting the original baseline.

### PLAN_INDEX.md

Dependency-oriented routing and traceability map: macroblocks, microsteps, ordered/parallel dependencies, Plan Part paths/status, cross-part invariants, Implementation Batches, GOALs, Expected Evidence, and an **Agent Capability Matrix**.

The matrix records exact verified model IDs/versions, effort, client/version/verification date, the primary role, Luna worker roles, permitted specialists, accepted fallbacks, routing constraints, and blocked/unverified features. Revalidate material runtime differences before execution. Never encode mutable model choices in Plan Part filenames.

Each GOAL entry identifies direct Luna ownership, parallel candidates, specialist triggers, delegation envelopes, integration, and validation. `UNASSIGNED` may exist during early decomposition only; none may remain at implementation handoff.

### Plan Parts

Filename/path describe stable work identity, not Luna/SOL assignment. A Plan Part has only the technical depth warranted by the mechanism, including as relevant:
- Goal and **current-to-target** behavior, verified repo base and real paths/symbols;
- fixed decisions, non-goals, invariants, types, state, ownership/lifetime, and contracts;
- interfaces, data flow, algorithms, concrete call sequences, pseudocode/code, and migration order;
- failure/retry/cancellation, races, persistence, resource/performance and cleanup behavior;
- dependencies, writable ownership, independent/parallel slices, integration boundaries;
- build/test/instrumentation actions and **objective Expected Evidence**;
- a proposed specialist trigger and minimal context only when justified.

Be explicit about proposed names versus existing symbols. Do not reproduce large source dumps or research transcripts.

### CHAT_HANDOFF.md

Compact operational checkpoint: verified baseline, phase, last completed unit, remaining work, blockers/decisions, context-safety state, exact next action and minimum files to reload. Include continuous/manual-mode state if relevant. Do not use a running conversation transcript or stale operation counter as authority.

### CODEX_HANDOFF.md

Final machine-facing implementation contract: verified repo/base, plan root/index, **approved exact Agent Capability Matrix**, bootstrap/compatibility requirements, ordered GOALs and foundational gates, scope and writes, delegation/parallel/escalation policy, validation and Expected Evidence, deviation reporting, and resume procedure.

Do **not** create or maintain a manual `ACTIVE_MODEL` switch variable. Planned model routing is configuration intent, not proof of active runtime model. Never silently rewrite a model selection based on history or an unverified agent report.

### CODEX_CLEAN_HANDOFF.md and CLEANUP_FINDINGS.md

After convergence, ChatGPT prepares a temporary, bounded Cleanup GOAL handoff: reconciliation rules, removal/preservation scope, build/cache policy, clean rebuild, and stop conditions. Luna executes it only after explicit user start. `CLEANUP_FINDINGS.md` is the concise surviving feedback artifact for real unresolved implementation divergences and durable architecture corrections, not a cleanup log.

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
5. Specify hard mechanisms concretely: types, transitions, ownership, data flow, algorithms and pseudocode/code where that removes Luna reasoning.
6. Define tests, migration, failure/concurrency cases, observability, integration, and objective Expected Evidence.
7. Mark independent work and potential specialist calls only when useful.

**Implementation Readiness Self-Check:** Can a Luna High implementer complete the part without inventing essential architecture, interfaces, algorithms, concurrency rules, migration sequencing, or acceptance criteria? Are current repo facts verified and dependencies consistent? Repair material gaps before marking expanded.

Plans must be the **shortest complete** actionable specification. Small complete files are good. For unusually large single parts, roughly 1,200–1,600 lines is a safety guide rather than a quota; modest 1,600–1,700 overage need not trigger redivision, but split by cohesive responsibility when readability or context safety warrants. Never inflate documents for a length target.

## 9. Final optimization and multi-agent consistency gates

After all required parts are expanded, perform the full gates in order. Checkpoint compaction is not a replacement.

### Pass A — implementation-preserving optimization

Remove filler, outdated rationale, duplicated descriptions, ambiguous choices, and avoidable planning left to Luna. Strengthen unverified contracts, algorithms, migration steps, race handling, pseudocode/code, and missing test evidence. Never remove a requirement or failure behavior just to save tokens.

### Pass B — Specialist Minimization and Agent Routing

Challenge **every** planned stronger-model call: can better source evidence, scope reduction, a concrete interface, algorithm, code snippet, or dependency resolution make Luna capable? Retain specialist calls only when a material residual difficulty remains. Decide **Solve Only** before **Scoped Implementation** unless the latter is clearly necessary.

Audit parallel slices for genuine independence, coordination cost, shared state, file ownership, and integration ordering. No automatic one-part-one-subagent or one-part-one-test mapping.

### Pass C — Cross-artifact Consistency Gate

Audit `MASTER_PLAN → PLAN_INDEX → Plan Parts → current repository` in both directions for requirements, interfaces, states, ownership, contracts, dependencies, migration, tests, and approved decisions. Add cross-agent checks: exact model routing, delegation inputs/outputs, allowed reads/writes, concurrent writes, integration, specialist permissions, and Expected Evidence.

Repair contradictions in the **owning canonical artifact** (architecture → master, decomposition/routing → index, mechanism → part), propagate downstream, then repeat until a complete clean pass or real blocker. Do not hide contradictions by patching handoffs alone.

### Final GOAL construction and handoff gate

Build meaningful Implementation Batches; mark foundational GOALs whose evidence gates dependent work. A GOAL may reference many Plan Parts. For each GOAL include:
- bounded mission, current-to-target delta, dependencies, authorized modifications;
- Luna direct steps, optional independent worker tasks and ownership;
- justified specialist triggers and smallest initial delegation packet;
- integration sequence, rollback/recovery rules, validation and Expected Evidence.

Confirm capability matrix and compatibility/bootstrap obligations, then persist `CODEX_HANDOFF.md`. The user explicitly starts the Codex implementation; planning approval is not implementation-start authorization.

## 10. Models, configuration, and actual capability checks

**Planning must record exact identifiers and effort.** Role names stay independent from model names. The intended default is **Luna High primary**, optionally **Luna High workers**, with **SOL High** or another verified stronger model for exceptional work.

As of the cited documentation snapshot, example Codex identifiers include `gpt-6-luna` and `gpt-6.1-sol`. Examples are **not permanent guarantees** of account availability, client routing, or effort support. Verify official docs during planning, record the date/client, and verify the installed runtime before GOAL execution. No silent model downgrade or substitution.

Current Codex documentation describes project-local agent role definitions under `.codex/agents/*.toml` and project configuration in `.codex/config.toml`, including `[agents]` keys for default subagent model/effort and a concurrency cap. The primary session's model must also be explicitly confirmed using supported session/client mechanisms.

### Agent Bootstrap and Compatibility Gate

Codex performs this bounded setup **before** starting implementation GOALs:
1. Verify consumer repo, branch/HEAD, plan files, current Codex client/version, workspace trust, and existing `AGENTS.md`, `.codex/config.toml`, and `.codex/agents/`. Preserve existing instructions and uncommitted changes.
2. Confirm model identifiers, availability/entitlements, accepted reasoning efforts, tool interface, features, sandbox/approval configuration, and client support for custom roles.
3. Create or merge **only the approved, necessary** project-local agent definitions; never replace user config wholesale or create unused roles. Add a compact `AGENTS.md` only when approved, limited to durable Codex operating guidance, while specific GOAL facts remain in handoff/index.
4. Set a conservative worker concurrency ceiling (often 2–3 workers initially; never assume a universal optimum). Prefer Luna defaults; explicitly specify specialists' models and reasoning effort. Do not confuse default settings with verified effective routing.
5. Validate parsing/discovery, perform a **minimal test invocation** for each required role, and confirm the actual model/effort from reliable client evidence where available. Verify necessary tools still work with minimal-context delegation and that permission constraints are understood.
6. If discovery requires a new session, stop bootstrap at a durable checkpoint and have the user start/resume in a fresh session; then verify again **before** beginning the GOAL. No manual mid-GOAL model switching.
7. Record verified outcomes, configuration paths, client version, limitations, and any blocked role in the implementation handoff. Recheck after a material update to client, models, session, or config, not before every trivial task.

If effective specialist routing cannot be confirmed, do **not** claim SOL ran or silently use Luna instead. Stop only the dependent operation, try an explicitly approved compatible alternative if verified, or report a real boundary. Feature availability varies by client and version.

### Configuration precedence and instruction discovery

Read applicable global/project `AGENTS.md`/`AGENTS.override.md` and Codex settings rather than overwriting them. Project-local configuration may depend on workspace trust. `AGENTS.md` instructions do not grant new filesystem permissions. A custom agent TOML controls the role; it does not by itself sandbox writes.

Before treating documented settings as supported in a given environment, inspect the actual installed client's help/config/schema and test the exact role.

## 11. Minimal Context Delegation protocol

Each subagent has an independent working context **only to the extent established by the actual spawn mode**. On supported Codex V2, spawning with `fork_turns: "none"` avoids copying the parent transcript; an unspecified mode may copy history. Verify syntax/behavior against the client's live tool schema. If tools are unavailable under clean forks, test the limitation and report an explicit fallback; never default to copying all history for convenience.

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
4. Integration owner, timing/order, merge plan, and tests.
5. Concurrency ceiling and stop/failure procedure.

Read-only exploration can overlap widely if useful. Write tasks require non-conflicting ownership and compatible shared resources. Different source files do **not** automatically mean independent tasks. Where practical, use isolated worktrees/branches for writes that cannot safely share a workspace; otherwise serialize.

Workers do not independently redesign architecture, modify another worker's files, overwrite user edits, or create unrelated commits. Prefer the primary Luna to integrate, review diffs, run integration tests, and produce coherent commits. If a worker fails, retain validated independent progress and repair the relevant boundary, not the whole GOAL.

## 13. Planned and dynamic specialist escalation

Default: Luna implements from the ChatGPT plan. A stronger specialist is an exceptional tool, never a routine reviewer of every file.

### Planned escalation

A Plan Part/GOAL may authorize a specialist for a narrowly defined difficult fragment with prerequisite evidence, minimal input contract, permitted model/effort, allowed reads/writes, and expected return. If the plan itself makes the fragment mechanical for Luna, remove the escalation in Pass B.

### Dynamic escalation

When Luna hits a blocker:
1. Classify ordinary build/test error, missing evidence, plan defect, platform/permission boundary, or genuinely difficult reasoning.
2. Perform bounded diagnosis and materially different repairs using available plan/source evidence; do not require a fixed number of artificial retries.
3. Escalate only when a durable blocker remains or the problem is demonstrably too difficult to solve safely at Luna's capability.
4. Send a minimal packet with repro, observed evidence, bounded attempts, and exact contract. Do not recreate the entire failed investigation.
5. Prefer **Solve Only**: specialist diagnoses and returns a precise patch/algorithm/contracts for Luna to implement and test.
6. Use **Scoped Implementation** only when Luna demonstrably cannot reliably implement the fragment; restrict changes to explicitly allowed paths and integrate through Luna.
7. If the result fails, provide only the **new evidence** to the same specialist when available; avoid an unbounded chain of fresh expensive agents.

No specialist may unilaterally alter approved architecture, ownership, safety constraints, authorization scope, or a foundational contract. For a real plan contradiction, pause the affected dependent work and return to ChatGPT/user for an approved correction. Avoid indefinite retries, busy waiting, and silent fallbacks.

## 14. Autonomous GOAL execution

Starting a GOAL is a user action. Once started and compatible:
1. Luna reads the persisted `CODEX_HANDOFF.md`, current `PLAN_INDEX.md`, and relevant Plan Parts (not all parts by default), checks source/HEAD and permitted files.
2. Verify prerequisites and foundational Expected Evidence, identify direct versus parallel work, and start implementing **without gratuitous pauses**.
3. Use prepared interfaces, algorithms, and pseudocode/code; do not reopen settled architecture.
4. Delegate only independent tasks or justified specialist problems; manage progressive context and safely integrate.
5. Validate relevant intermediate invariants when needed, then run the GOAL's final build/tests/instrumentation and **Expected Evidence**.
6. Report deviations, evidence, changes, and blockers concisely, persisting only durable state. Complete the GOAL when its acceptance contract is met.

Do not stop merely because a compiler error or test failure appears. Do stop at genuine authorization/security/platform limits, unresolvable specialist or tool failure, invalid architecture, or impossible acceptance evidence. Do not promise background continuation or automatic resumption of a paused session.

A user-triggered `continue` or equivalent client resume may be required after an actual pause or new-session bootstrap. Restart from the durable handoff, recheck source and config, and avoid repeating validated work. A model preference expressed in an old conversation does not change the client's selected model.

## 15. Tests, Expected Evidence, and observability

Every GOAL declares **Expected Evidence** that actually proves the requested behavior. Existing test suite success alone is insufficient if no test or observation exercises the intended invariant.

Possible evidence: targeted unit/integration tests, clean build, API/ABI shape, migration result, runtime state, deterministic repro, measured performance threshold, or verified generated artifacts. Make validation proportional to risk. Foundational GOALs must validate before dependent work begins.

At GOAL completion produce a compact **Execution Evidence** summary:
- GOAL ID and verified base/result commit or working-tree state;
- actual verified primary model/effort if observable and specialist model if invoked;
- counts/purposes of Luna workers and specialist invocations, with Solve Only vs Scoped Implementation;
- changed files, integration result, targeted tests and Expected Evidence verdict;
- material deviations, unresolved blockers, and any reliable usage metrics **only if actually exposed by the client**.

Do not fabricate token totals, effort routing, or benchmark numbers. Do not keep large logs or full agent transcripts unless needed to reproduce a real failure. Compare overall GOAL cost/quality, not just specialist-call counts.

## 16. Convergence review after implementation

After a completed implementation batch, ChatGPT freshly compares **current repository code and test evidence** with the approved master/index/Plan Parts.

Classify any mismatch as missing, partial, contradictory, unrequested, or an approved requirement change. For material divergences, create bounded corrective GOALs with Expected Evidence; do not silently accept code as the new requirement. Re-run targeted convergence checks until intended behavior is supported by evidence or a genuine blocker/user decision remains.

Preserve observed bugs or hot-path problems outside approved scope as concise follow-up findings, not opportunistic undocumented changes.

## 17. Cycle Closure and cleanup

Convergence success allows **Cleanup Preparation**, not immediate cleanup execution.

ChatGPT resolves architecture/documentation reconciliation, dead-legacy classification, preservation/deletion boundaries, local generated/build state handling, and clean-rebuild evidence. It creates `CODEX_CLEAN_HANDOFF.md` for a single bounded Luna Cleanup GOAL with no architectural decisions left to invent.

Stop and require explicit user start for cleanup. Luna:
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

At handoff persist `CHAT_HANDOFF.md`, synchronize `PROJECT.md`/`PLAN_INDEX.md` pointers and verified baseline, and finish with a populated copyable continuation prompt: repo/branch/HEAD, plan root, phase, last completed unit, next exact action, files to read, blockers, mode, and current manual URL. No placeholders, transcript, or obsolete history.

## 19. Maintaining and evolving this protocol

The *maintenance* repository is `Armoredweb/AN-chatNcodex-SubAgents-WorkFlow`. Its docs are English-first, with a pt-BR user guide. The original `Armoredweb/AN-chatNcodex-WorkFlow` is reference-only, never synchronized automatically.

When changing this manual: verify target repository/branch/HEAD, read the current manual and relevant source docs, get user approval for new architecture and write scope, edit the owning section, update both guides/README as needed, inspect contradictions, commit coherent changes, and verify remote persistence. Do not create unnecessary templates or unchecked agent TOMLs in this repository. Test examples in a consumer project before publishing reusable configuration examples.

### External references and version sensitivity

These are documentation references, not a claim that an actual local client was tested:

- [Codex subagents](https://developers.openai.com/codex/subagents)
- [Codex configuration reference](https://developers.openai.com/codex/config-reference)
- [Codex project instructions with AGENTS.md](https://developers.openai.com/codex/guides/agents-md)
- [Codex hooks](https://developers.openai.com/codex/hooks)
- [Codex multi-agent implementation](https://github.com/openai/codex)

The names, keys, and behavior described here were checked against public documentation/code on **2026-10-30**. Revalidate before creating consumer-project configuration; interfaces and models may change.
