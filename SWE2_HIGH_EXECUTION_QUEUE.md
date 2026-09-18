# SWE-2 HIGH EXECUTION QUEUE

PROGRAM_END: 2026-10-15
PROJECT: PARK-IT
RULE: Audit the legacy application before modernization; preserve working behavior while replacing brittle/deprecated boundaries incrementally.

## ACTIVE
- Insert any current recovery/modernization closure here.

## READY
1. **PARK-SWE2-001 — Whole-App Recovery + Modern Runtime**
   - Objective: establish reproducible install/test/start, remove dead assumptions, secure configuration and create a reliable baseline.
2. **PARK-SWE2-002 — Parking Availability Model**
   - Objective: explicit availability state, freshness, provider/source abstraction, polling/reconnect and truthful stale/offline behavior.
3. **PARK-SWE2-003 — Nearest-Parking Routing Engine**
   - Objective: deterministic candidate ranking, route/distance integration, failure handling and testable navigation decisions.
4. **PARK-SWE2-004 — Map + Mobile UX Modernization**
   - Objective: customer-grade map/search/parking detail/route flow with responsive mobile browser E2E.
5. **PARK-SWE2-005 — Production/Staging Seal**
   - Objective: environment config, API-key hygiene, observability, deployment, browser E2E and hostile security/reliability audit.

## BLOCKED
- Real map/provider keys, authoritative parking feeds and public production deployment remain external/owner gates.

## COMPLETED
- Record package, PR, implementation SHA, CI SHA, merge SHA and evidence here.
