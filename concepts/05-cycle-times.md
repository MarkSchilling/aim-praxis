# Cycle Times

## The concept

Cycle time is the period required for one full traversal of a feedback loop. Different loops operate at different cycle times. A healthy system has appropriate variation reduction at every cycle time it runs at.

Variation that takes a minute to manifest must be caught by a loop with a cycle time of a minute or less. Variation that takes a quarter to manifest must be caught by a loop with a cycle time of a quarter or less. A system with only short-cycle loops misses long-cycle variation. A system with only long-cycle loops misses short-cycle variation.

## The multi-time-scale property

Aim Praxis is explicitly a multi-time-scale system. The seven layers operate at cycle times spanning seven orders of magnitude:

- CI/CD: seconds to hours
- TDD: minutes
- ATDD: days
- BDD: days to weeks
- Story Mapping: weeks
- VPC: weeks to months
- BMC: weeks to quarters

This range is the methodology's signature property. No prior methodology I know of explicitly designs for all seven scales.

## Why teams collapse toward fast loops

The pathology is consistent: under pressure, teams collapse toward inner loops. Three reasons drive this.

**Visibility.** Inner-loop work produces immediately visible output. A passing test, a deployed build, a closed ticket. Outer-loop work produces output that pays off later (a refined strategy, a validated fit, a coherent release plan). Visible output competes with invisible output under measurement pressure.

**Cycle rhythm.** Inner loops feel rhythmic and productive. Outer loops feel sporadic and slow. The rhythmic work feels like progress; the sporadic work feels like overhead.

**Career incentives.** Engineers are evaluated on inner-loop output (code shipped, tests written, builds deployed). Strategy work and customer-fit validation are not in most engineers' performance reviews. The incentive system reinforces the visibility bias.

The defense: outer-loop work must be deliberately calendared, attended, and protected. Without explicit defense, the gravity of the system pulls inward.

## Cadence as a design choice

The cadence at which each loop runs is itself a design choice. Aim Praxis recommends specific cadences:

- **CI/CD:** on every commit
- **TDD:** within every coding session
- **ATDD:** at every story completion (typically per-story, several per week)
- **BDD:** at every feature start (typically per-feature, weekly to bi-weekly)
- **Story Mapping:** every release-slice boundary, typically every 4-8 weeks
- **VPC review:** quarterly, or whenever significant customer signal accumulates
- **BMC review:** quarterly, with annual strategic overhaul

These cadences are recommendations, not mandates. The principle is that each loop's cadence must match the rate at which its class of error manifests. Faster than necessary wastes effort; slower than necessary lets errors accumulate.

## The conservation of attention

A team has finite attention. Each loop's cadence consumes attention proportional to its cycle time and depth. The total attention budget across all seven loops must fit within the team's capacity.

A team with 2 engineers cannot run the BMC, VPC, Story Mapping, BDD, ATDD, TDD, and CI/CD loops with the same depth as a team of 50 engineers. The cadences must be adjusted to the team's actual capacity. The principle is that all seven loops must run; the depth of each at any given cadence scales with team capacity.

For a solo founder, this often means abbreviated outer-loop cycles (a one-hour BMC review every two months rather than a multi-day strategic offsite) rather than skipping the outer loops entirely.

## What to read next

- `concepts/04-the-seven-layers.md` — the seven loops and what each catches
- `operations/cadences.md` — specific cadence recommendations
- `system/archetypes.md` — pathologies that emerge when cadences are mismatched
