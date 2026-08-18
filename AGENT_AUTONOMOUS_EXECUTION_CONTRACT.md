# Repository Autonomous Execution Contract V1

Status: CANONICAL AGENT GOVERNANCE

This file governs HOW autonomous agents execute work here. Repository-specific canonical status, roadmap, release-gate, security, migration and `NEXT_*` documents remain authoritative for WHAT is built.

Before implementation establish `REPO_CONSISTENCY_GATE = PASS`: fetch/prune; compare GitHub/default branch with the actual local/workspace repository; inspect branch/HEAD/upstream, staged/unstaged/untracked changes, local-only/remote-only commits, stashes/worktrees and relevant branches/PRs; preserve valid work; never destructive-reset/clean for convenience; establish the canonical starting SHA. If the user's PC repo is inaccessible, state `LOCAL_PC_NOT_ACCESSIBLE` rather than claiming verification.

Audit current code/tests/migrations/docs/runtime/CI before assuming roadmap gaps. Repository reality overrides stale plans; do not duplicate verified work. For major multi-slice work first use read-only `Plan`/`Megaplan` (or equivalent) to create/update `docs/agent/MASTER_EXECUTION_PLAN.md`, `docs/agent/GAP_LEDGER.md`, `docs/agent/SLICE_LEDGER.md`, and `docs/agent/CURRENT_STATE.md`. The plan must define dependency-aware slices, invariants, affected components, migrations/APIs/runtime impact, tests, real E2E, risks, HUMAN_REQUIRED actions and exact completion gates. Planning is not completion; then switch to Agent/Autonomous execution without approval between normal slices.

Autonomous loop:
`AUDIT CURRENT DEFAULT BRANCH -> SELECT NEXT UNBLOCKED SLICE -> PLAN -> IMPLEMENT -> LOCAL TESTS -> REAL RUNTIME -> E2E -> FIX -> RETEST -> EVIDENCE -> MATURE CI -> UPDATE LEDGERS -> NEXT SLICE`

After every COMPLETE slice record evidence/SHA, update ledgers/current state, recompute dependencies, refresh canonical repo state and continue automatically.

HUMAN_REQUIRED is limited to genuine external blockers: unavailable credential/API entitlement; owner/policy-required approval; irreversible production operation; external environment unavailable without safe emulation; non-derivable product/legal/commercial decision; or material architecture conflict with equally valid incompatible outcomes. Coding decisions, test failures, merge conflicts, migration details, refactors and CI failures are not automatically HUMAN_REQUIRED.

No hardcoded success, fabricated evidence, fake external transactions or mocks represented as production. Use official real sandbox/test APIs where available; otherwise clearly identified emulator/realistic mock. Visible state must have a real derivation path.

CI is regression protection, not the debugger. Before CI run strongest feasible focused/broad local tests, DB/migration/contract/integration checks, real runtime with applicable services, visible E2E/golden path and final diff/repo audit. Root-cause/fix failures and restart invalidated golden paths. Prefer one mature CI run per completed slice; avoid blind reruns/speculative pushes.

Preserve unrelated work; use coherent slice branches/PRs where expected; one master plan is not one giant commit. Merge automatically only when policy/permissions allow and every machine-verifiable gate passes; otherwise expose only the precise owner-only gate.

COMPLETE requires real implementation, passing relevant tests, safe data/migrations, working runtime, required E2E, evidence, accurate ledgers/docs, no known in-scope blocker and required CI green. Project COMPLETE requires all required slices integrated plus a final production-like golden path.

Statuses: `REPO_CONSISTENCY_GATE = PASS | BLOCKED`; `SLICE_STATUS = READY | ACTIVE | BLOCKED | COMPLETE`; `PROJECT_STATUS = ACTIVE | BLOCKED | RELEASE_CANDIDATE | COMPLETE`; `HUMAN_REQUIRED = NONE | <precise external action>`.

Default objective: maximum safe autonomy, minimum human coordination, preserved repository truth, runtime correctness, security, evidence quality and CI credits.
