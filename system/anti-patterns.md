# System Anti-Patterns

System anti-patterns are recurring practices that produce predictable failures. They are the negative complement to `system/archetypes.md` — where archetypes describe emergent system behaviors over time, anti-patterns describe discrete practices that, when adopted, produce specific failure modes.

This document catalogues system-level anti-patterns (failures of cross-layer discipline). Local anti-patterns within a single practice or layer live with that practice — for example, gate-design anti-patterns are in `operations/gates.md`.

The list grows as new patterns are observed and confirmed through the rework register.

## Upstream layer bypass

**Pattern:** A request phrased as an imperative ("implement X", "build the audit feature", "show the dashboard") is matched directly to the innermost layer that contains the verb, skipping every upstream layer the work depends on.

**Symptoms:**

- Code is written for a feature that has no acceptance criteria, no scenarios, and no story map task
- The team discovers mid-implementation that the work does not match what the customer wanted
- Rework register entries cluster around features that lack upstream artifacts
- "Quick" features take longer than methodically structured ones because they get rebuilt after the gap is discovered
- Different engineers shipping similar features produce inconsistent results because there is no shared specification upstream

**Cause:** Imperative verbs ("implement", "build", "ship", "create") pattern-match strongly to the TDD/coding layer. Humans and agents both default to satisfying the imperative directly. The methodology's discipline of working from outer layers inward is overridden by the request's surface form.

**Intervention:** Require an explicit intake triage before any imperative request enters the work-in-progress stock. The triage checks, in order, that every upstream artifact exists: BMC, VPC, story map task, scenario, acceptance criteria, and any layer-specific outputs the feature requires. If any upstream artifact is missing, the request routes to that layer's work, not to coding.

The triage is mechanical, not judgmental. It does not ask "should we be doing this?" — it asks "does each upstream artifact exist?" A missing artifact reroutes the request without prejudice. The discipline is checking, not deciding.

In agentic implementations, the triage is encoded in the navigation skill or meta-skill (the equivalent of a "where am I in the system" question). In manual implementations, the triage is a team-level routing discipline at the request-intake point.
