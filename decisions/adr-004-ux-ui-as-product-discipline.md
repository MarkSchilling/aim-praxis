# ADR-004: UX/UI as Product Discipline, Not Methodology Layer

**Status:** Accepted

**Date:** 2026-05-20

## Context

Ship Audit's existing skills include UX research, UX design, and UI design. The migration audit (`examples/ship-audit/migration-audit.md`) raised the question of whether to fold these into Aim Praxis as additional layers or treat them as out-of-scope product discipline.

Three options were on the table:

1. Fold UX research, UX design, and UI design into Aim Praxis as additional layers
2. Declare UX/UI as legitimate product-level discipline, out of methodology scope
3. Defer the decision and leave Aim Praxis silent

A decision was required because silence produces drift between the methodology and a working implementation.

## Decision

UX/UI is treated as a legitimate product-level discipline that produces inputs to multiple Aim Praxis layers (VPC, Story Mapping, BDD, ATDD), but is not itself part of the methodology.

Aim Praxis defines the integration points — what UX/UI artifacts feed which methodology layers — without prescribing how UX/UI work is done. The choice of UX/UI methodology (lean UX, design thinking, double-diamond, in-house frameworks) is left to the adopting team.

## The integration points

UX/UI artifacts feed Aim Praxis layers at four specific points:

- **VPC** receives personas, mental models, and journey maps. These are the inputs that ground customer jobs, pains, and gains in research rather than assumption.
- **Story Mapping** receives personas and journey maps. The backbone of activities derives from journey maps; personas referenced by name appear in task definitions.
- **BDD** receives information architecture, interaction patterns, and screen flows. Scenario authoring references these as the behavioral substrate the system is being specified against.
- **ATDD** receives acceptance targets from screen flows. The observable outcomes that acceptance criteria reference often originate as UI specifications.

These integration points are Aim Praxis's contribution to the boundary. The work *upstream* of each point — how personas are researched, how IA is structured, how screen flows are designed — belongs to the UX/UI discipline and is governed by its own methodology.

## Consequences

**What becomes easier:**

- The seven-layer architecture stays clean. The structural claim that each layer catches a distinct error class is preserved.
- The methodology stays teachable. Seven layers with distinct error classes is a coherent claim; ten layers, three of which serve a different function, would not be.
- UX/UI practitioners can use Aim Praxis without feeling colonized. The methodology respects an independent tradition rather than absorbing it.
- Aim Praxis applies cleanly to non-UI software (API-only systems, batch pipelines, embedded systems, infrastructure tooling). Hard-coding UX/UI as layers would have made the methodology UI-specific.

**What becomes harder:**

- Readers must understand that Aim Praxis is one of multiple disciplines that contribute to good software, not the totality. The methodology's scope is narrower than a complete product methodology.
- Teams adopting Aim Praxis for UI-heavy products must integrate a separate UX/UI methodology. Aim Praxis does not provide one.

## Alternatives considered

**Option A — Fold UX research, UX design, and UI design into Aim Praxis as additional layers.** Rejected because UX/UI is a mature independent tradition that Aim Praxis cannot honestly absorb without overreach. The seven-layer architecture is structured around distinct error classes caught by distinct feedback loops; UX/UI work produces inputs to multiple layers but does not itself constitute a feedback loop with a distinct error class of its own. Adopting Option A would dilute both the structural claim and the boundary respect Aim Praxis owes to adjacent disciplines.

**Option C — Defer the decision and leave Aim Praxis silent.** Rejected because the decision is about scope, not application, and additional Ship Audit work will not resolve the scope question. Silence would produce ongoing drift between the methodology and a working implementation, with neither being wrong but neither being settled.

## A note on the pattern

This decision parallels the methodology's treatment of database design, security engineering, and other disciplines that interact with software development without being subsumed by it. Each of these disciplines produces inputs that flow into Aim Praxis layers (security requirements inform BDD scenarios; data model decisions inform TDD design); none is itself a layer. The same logic that keeps database design and security engineering outside the methodology keeps UX/UI outside as well.

## References

- `examples/ship-audit/migration-audit.md` — the audit that surfaced the question
- `concepts/04-the-seven-layers.md` — the structural claim being preserved
- `docs/aim.md` — the methodology's articulation of scope
- `decisions/adr-003-agent-placement-principles.md` — the related discipline of explicit scope (what agents do and do not do)
