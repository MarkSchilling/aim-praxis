# Cadences

This document specifies the recommended cadences for each loop in Aim Praxis. Cadences are the design choice that determines how often each loop runs and therefore how quickly each class of error gets caught.

## The cadence table

| Loop | Cadence | Calendared or continuous |
|------|---------|--------------------------|
| BMC review | Quarterly, with annual strategic overhaul | Calendared |
| VPC review | Quarterly, or when customer signal accumulates | Calendared |
| Story Mapping | Every 4-8 weeks (every release boundary) | Calendared |
| BDD scenario authoring | Per feature, typically weekly to bi-weekly | Calendared at feature start |
| ATDD criteria authoring | Per story, multiple per week | Triggered by story start |
| TDD red-green-refactor | Per coding change, minutes | Continuous during coding |
| CI/CD | Per commit | Continuous |
| Observability monitoring | Continuous | Continuous |
| Rework register review (with PDSA agent) | Monthly | Calendared |
| Glossary review | Weekly batch (proposals from agent) | Calendared |
| Lessons-learned review | Monthly or after significant events | Calendared |

## Why these specific cadences

Each cadence reflects the rate at which its class of error manifests.

**BMC errors manifest slowly.** Strategic direction errors take quarters or years to become visible. Quarterly review catches them at the appropriate cycle time.

**VPC errors manifest medium-slowly.** Fit errors take weeks to months of customer signal to surface clearly. Quarterly with signal-driven exceptions catches them.

**Story Mapping errors manifest at release boundaries.** Scope errors become visible when releases ship. Every 4-8 weeks (the typical release cadence) catches them.

**BDD errors manifest at feature boundaries.** Behavioral specifications stay valid until features change. Per-feature authoring keeps specifications current.

**ATDD errors manifest per story.** Acceptance ambiguities surface story by story. Per-story authoring catches them at the right grain.

**TDD errors manifest per coding change.** Design degradation happens as code is written. Minute-scale rhythm catches it.

**CI/CD errors manifest per commit.** Integration failures emerge when code combines. Per-commit pipeline catches them.

**Observability findings emerge continuously in production.** No appropriate batch cadence; continuous monitoring catches them.

**Rework register patterns emerge over weeks.** Three recurrences of a pattern take time to accumulate. Monthly review matches the pattern emergence rate.

## Cadence and team size

The cadences above are appropriate for typical small to medium teams. Adjustments for size:

**Solo founder.** Reduce outer-loop depth (a one-hour BMC review every two months rather than a multi-day offsite) but keep all loops on the calendar. The discipline matters more than the depth.

**Larger teams.** Outer-loop cadences may stay the same but require more participants. Inner-loop cadences remain per-individual.

**Distributed teams.** All cadences require explicit scheduling rather than relying on co-located rhythms. The calendaring discipline becomes more important, not less.

## The conservation of attention

A team has finite attention. The total attention budget across all loops must fit within team capacity. If the recommended cadences would consume more than the team has, the recommendation is to reduce depth, not to skip loops.

Skipping an outer loop entirely produces blind spots. Reducing its depth produces partial coverage, which is better than nothing.

## Cadence enforcement

The biggest threat to cadences is inner-loop pressure. When sprint deadlines compete with quarterly review, the quarterly review tends to get postponed. When production incidents compete with monthly PDSA review, the PDSA review gets postponed.

The defense:

- Calendared cadences on the team's actual calendar
- Visible attendance — outer-loop work happens with the team in the room
- Documented outputs — each loop produces artifacts that prove it happened
- Periodic check — does the calendar reflect the methodology's cadence requirements

A team where outer-loop reviews keep getting postponed has slid into inner-loop dominance. The remediation is to restore the calendar.

## The asymmetry

Inner-loop cadences enforce themselves through visible mechanics — pipelines fail, tests stop, commits don't merge. Outer-loop cadences enforce themselves only through deliberate practice.

This asymmetry is what makes outer loops vulnerable to atrophy. The methodology compensates by making outer-loop cadences explicit and calendared. Without that compensation, the system runs at inner cadences only.

## What to read next

- `concepts/05-cycle-times.md` — why multi-time-scale operation matters
- `operations/gates.md` — the criteria each cadence enforces
- `operations/operationalization-sequence.md` — how to establish cadences in adoption
