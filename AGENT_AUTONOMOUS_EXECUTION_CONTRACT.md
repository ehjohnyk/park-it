# Repository Autonomous Execution Contract V3

Status: CANONICAL AGENT GOVERNANCE

This file governs HOW autonomous agents execute work. Repository-specific canonical status, roadmap, release-gates, security, migrations and product contracts remain authoritative for WHAT is built.

Before implementation establish `REPO_CONSISTENCY_GATE = PASS`: fetch/prune; compare GitHub/default branch with the actual local/workspace repo; inspect branch/HEAD/upstream, staged/unstaged/untracked work, local/remote-only commits, stashes/worktrees and relevant branches/PRs; preserve valid work; never destructive-reset/clean for convenience; establish canonical starting SHA. If the user's PC repo is inaccessible, report `LOCAL_PC_NOT_ACCESSIBLE`.

Audit repository reality before planning. Existing verified code/tests/runtime override stale docs; do not duplicate completed work.

This is a legacy repository. Before feature work use Plan/Megaplan to create `docs/agent/MASTER_EXECUTION_PLAN.md`, `GAP_LEDGER.md`, `SLICE_LEDGER.md` and `CURRENT_STATE.md` from actual runtime truth. Classify each dependency, external API, database path, UI flow, deployment assumption and test as CURRENT/STALE/BROKEN/MISSING.

Autonomous loop:
`AUDIT CURRENT DEFAULT BRANCH -> BOOT LEGACY APP -> DEPENDENCY/API SECURITY AUDIT -> BUILD MODERNIZATION PLAN -> PRESERVE PRODUCT BEHAVIOR -> IMPLEMENT VERTICAL SLICES -> LOCAL TESTS -> REAL RUNTIME -> VISIBLE E2E -> FIX/RETEST -> CANONICAL SERVER CI WHEN REQUIRED -> FIX UNTIL GREEN -> EVIDENCE -> UPDATE LEDGERS -> NEXT SLICE`.

After every COMPLETE slice record evidence/exact SHA, update canonical state, recompute dependencies, refresh repo state and continue automatically. A local external-provider blocker must not stop independent work.

HUMAN_REQUIRED is limited to genuine external blockers: unavailable API credential/entitlement, owner/policy approval, irreversible production operation, unavailable non-emulatable environment, non-derivable commercial/legal decision or material architecture conflict. Dependency upgrades, framework migration, DB migration, API adapter replacement, test failures and CI failures are not automatically HUMAN_REQUIRED.

No hardcoded success, fabricated parking availability/location/navigation evidence or stale external API behavior represented as current production truth. Prefer official supported provider APIs/sandboxes and clearly identify fixtures/emulators. User location/privacy and API-key handling must be explicit and safe.

## Canonical CI policy
The configured self-hosted/server CI is the PRIMARY canonical CI gate. GitHub Actions is not the default and must not be used merely to duplicate server validation or spend credits.

Each slice records `CI_REQUIRED`, `CI_PROFILE`, expected pipeline and exact completion gate. Required order when CI is required:
`IMPLEMENT -> LOCAL TESTS -> DB/INTEGRATION -> REAL RUNTIME -> E2E -> LOCALLY CLEAN -> SERVER CI -> ROOT-CAUSE/FIX FAILURE -> MINIMUM RERUN -> GREEN -> EVIDENCE -> COMPLETE`.

CI is not a debugger. Before each run execute strongest feasible unit/integration/provider-contract tests, DB checks, build/runtime, browser E2E and final diff audit. On failure inspect exact logs, fix locally, rerun relevant checks, then rerun only necessary CI scope. Never blind-rerun.

A CI-required slice cannot be COMPLETE while canonical CI is failing, skipped, unknown, stale or unexecuted. CI evidence is valid only for the exact tested SHA or proven immutable equivalent. Record CI system, run ID, exact SHA, profile, jobs, result and evidence location. A changed SHA requires new/equivalent validated evidence.

Default profiles: `FAST` = lint/static/unit/contract; `STANDARD` = FAST + integration + DB/build; `RUNTIME` = STANDARD + real stack/provider-test path + browser E2E; `RELEASE` = RUNTIME + full regression + security/privacy/release evidence.

GitHub Actions may run only when explicitly required or server CI cannot execute a required GitHub-specific gate. If server CI is not configured/reachable, record `CI_STATUS = NOT_CONFIGURED | UNAVAILABLE`, continue independent work and keep CI-required slices not COMPLETE.

A slice is COMPLETE only with real implementation, passing tests, safe data/API behavior, working runtime, required E2E, required exact-SHA canonical CI GREEN, evidence and accurate ledgers/docs. Project COMPLETE requires the intended parking flow end to end plus release CI.

## Park-It modernization/completion bootstrap — 2026-08-18
The current product concept is valuable but the implementation lineage is old: Node.js plus jQuery/MooTools, MongoDB, legacy Google Maps/Places/Directions patterns and polling-style availability. The last substantive code work predates modern dependency/API/security expectations. Do not continue by adding features directly on top of that stack before proving it still runs safely.

First autonomous program:
1. establish the actual default branch/local state and boot the current app in a clean isolated environment;
2. inventory package/runtime versions, known vulnerable/unsupported dependencies and dead build/start scripts;
3. inventory Google Maps/Places/Directions usage against currently supported official APIs without exposing API keys;
4. inspect MongoDB schema/data assumptions and determine a safe migration path;
5. capture the existing user-visible behavior as characterization tests before replacing internals;
6. choose the smallest maintainable modern architecture needed for the same mission rather than preserving jQuery/MooTools for historical reasons;
7. implement one real vertical flow: user location/search -> nearby parking source -> availability state -> selected parking detail -> navigation handoff, with explicit truth when live availability is unavailable;
8. add responsive UX, privacy/permission handling, provider failure/retry states, persistence where required, observability and browser E2E;
9. remove/deprecate obsolete paths only after the replacement has tests/evidence;
10. finish with production-like runtime and exact-SHA release CI.

Do not fake real-time parking availability if no authoritative source exists. Provider integrations may use official sandbox/test/fixture modes while clearly classified; source provenance and freshness must be visible in the data model.

Default objective: preserve the Park-It mission while replacing the obsolete technical foundation with a small, testable, real end-to-end parking product.
