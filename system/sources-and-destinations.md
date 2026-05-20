# Sources and Destinations

This document catalogs where the system's inflows come from and where its outflows go. The analysis distinguishes exogenous sources/destinations (outside the team's boundary) from endogenous ones (inside the boundary). For visual reference, see `diagrams/04-inflow-sources.svg` and `diagrams/05-outflow-destinations.svg`.

## Sources of inflows

Every inflow has a source. Naming the sources clarifies the system boundary and where the team depends on the world.

### Exogenous sources (outside the boundary)

**User reality.** The actual lives, workflows, pains, and unmet needs of the people who use (or might use) the product. The team can sample this through research; the team cannot produce it. Drains via user discovery and stakeholder input into raw ideas and stakeholder concerns.

**Team imagination.** Tacit knowledge, analogies, hunches, possibilities the team can imagine. Bounded by the team's experience and exhaustible within a session. Drains via blue-sky ideation into raw ideas.

**Business intent.** Strategy, revenue goals, constraints from leadership, the "big why." Small in volume but high in authority. Drains via stakeholder input into both raw ideas and the BMC's aim statement.

**Market signals.** Competitor moves, regulatory shifts, technology shifts, pricing dynamics. Arrive on an external clock the team doesn't set. Drains via discovery and stakeholder input into raw ideas and reshapes business intent.

### Endogenous sources (inside the boundary)

**Prior knowledge stocks.** Glossary, lessons learned, capability claims accumulated from past work. The endogenous source is what makes a learning system. Flows into detail refinement (informing how tasks decompose), workshopping (informing how scenarios are written), and the coding agent (informing how code is structured).

### Source dynamics

Each source has different dynamics that affect inflow rate:

- **User reality** is essentially infinite but expensive to sample (requires research)
- **Team imagination** is bounded and runs into diminishing returns within a session
- **Business intent** is small and over-sampling produces noise
- **Market signals** arrive on an external clock the team doesn't set
- **Prior knowledge stocks** grow as a function of past cycles

These different dynamics mean inflow rates are not independent levers. Pumping discovery harder when user reality has been thoroughly sampled produces diminishing returns. Generating more business intent than the strategy can absorb produces noise. Each source has its own appropriate sampling rate.

### Diagnostic question for sources

For any inflow that feels stuck, ask whether:
- The **source stock** is depleted (no more signal available)
- The **sampling mechanism** is broken (signal exists but isn't being collected)
- The **inflow valve** is throttled (signal is collected but isn't entering the system)

Three different problems, three different remedies. Teams often try to solve them with the wrong intervention.

## Destinations of outflows

Every outflow has a destination. Naming the destinations clarifies what the system produces and where value accumulates.

### Destinations within the team boundary

**Prioritized release backlogs (MVP, walking skeleton).** Drained by release slicing. Internal staging stock.

**Acceptance-ready stories.** Drained by story workshopping. Internal staging stock.

**Work in progress.** Drained by dev specification. Internal staging stock.

**Future map / cut list.** Drained by scope depletion. Items deferred, not destroyed. Internal staging stock that can be re-drained later.

**Working software.** Drained by product delivery. The team's terminal internal stock.

### Destinations outside the team boundary

**User outcomes.** The only exogenous destination. Where value actually leaves the system and produces effects in the world. The destination that justifies the whole system.

### The asymmetry

Internal destinations are easy to measure (story counts, deployment counts, code coverage). User outcomes are hard to measure (behavior change, problem reduction, satisfaction).

Teams over-optimize what they can count, accumulating internal stocks while the only exogenous destination — the one that justifies the system — goes unmeasured. Deming's measurement hierarchy applies here verbatim: component output is not system output is not aim alignment.

### Working software has two destinations

This is the conservation insight that turns a delivery pipeline into a learning system:

- **Intended destination:** working software → user outcomes (exogenous, where value leaves)
- **Unintended destination:** working software → rework register (endogenous, where problems return)

Without the second destination explicitly modeled, the system looks like an arrow. With it, the system is a cycle. A team that doesn't track the rework register sees only the forward flow and never learns.

### Diagnostic question for destinations

For any outflow that feels slow, ask whether:
- The **destination stock** is full (downstream backed up)
- The **receiving capacity** is constrained (destination can't absorb at the rate of outflow)
- The **outflow valve** itself is throttled (production constrained, not destination)

Most "we can't ship faster" complaints are destination-stock-full problems (work in progress is overflowing because product delivery valve is narrow), not outflow-valve problems (the team is capable of writing more code).

## The complete conservation picture

Putting sources and destinations together: the system has four exogenous sources (user reality, team imagination, business intent, market signals), one endogenous source (prior knowledge stocks), several internal destinations (release backlogs, acceptance-ready, work in progress, future map, working software), one exogenous destination (user outcomes), and one feedback destination (rework register).

The conservation property: every flow connects to identified sources and destinations. There are no "miraculous" flows that appear from nowhere or disappear into nothing. This conservation is what makes the system analyzable.

## What to read next

- `system/inflows-and-outflows.md` — the flows themselves in detail
- `system/integrated-system.md` — the complete integrated picture
- `concepts/01-stocks-and-flows.md` — the analytical vocabulary
