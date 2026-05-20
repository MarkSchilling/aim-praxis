# Story Mapping

## What it is in Aim Praxis

Story Mapping, developed by Jeff Patton, is treated in Aim Praxis as the third layer from the outside. It operates at the cycle time of weeks and is responsible for the narrative structure of the user's journey through the product.

Patton's contribution is the recognition that user stories alone lose the narrative coherence that makes a product comprehensible. The story map preserves the journey while still permitting the granularity that agile delivery requires.

The standard story map has activities arranged left-to-right along a backbone, with tasks hanging down as ribs, and release slices identified horizontally. Aim Praxis reads this as an aging chain of intangible stocks.

## The systems reading

The story map is not one stock but several, arranged as an aging chain:

**Raw ideas** — the initial reservoir of brainstormed possibilities

**Backbone tasks** — high-level activities organized in narrative flow

**Refined tasks** — backbone tasks decomposed into sub-tasks, exceptions, and details

**Release slices** — coherent subsets ready for delivery as MVP, walking skeleton, or subsequent releases

The transformations between these stocks are valves: task identification, detail refinement, release slicing.

## The bathtub model

The story map as a whole behaves like a bathtub with multiple inflows and outflows.

**Five inflows fill it:**
- User discovery
- Blue-sky ideation
- Task identification
- Detail refinement
- Stakeholder input

**Five outflows drain it:**
- Release slicing
- Story workshopping
- Dev specification
- Scope depletion
- Product delivery

The level rises when inflows exceed outflows; falls when outflows exceed inflows.

## The pack rat archetype

When inflow rate exceeds outflow rate, the map accumulates discretionary stories faster than the team can refine and deliver them. The level rises; backlog appears impressive; velocity does not change. This is pack rat syndrome.

The leverage point is in the valves: throttle inflows (especially blue-sky ideation) or widen outflows (slicing, scope depletion). Pumping discovery harder while outflows are constant is the most common mistake.

## Scope depletion as legitimate outflow

Scope depletion — moving items "out of scope" — is colored amber because it does not produce value. It preserves throughput by removing items. Treating it as failure produces pack rat syndrome. Treating it as flow regulation is SoPK.

Items moved out of scope are not destroyed; they are parked in a deferred map that can be re-drained later if conditions change. The deferred map is itself a stock.

## What the story map catches

The story map catches scope error — the work is structured in a way that delays value delivery. The release slices do not produce a usable product at any point until the very end. The opening game cannot be played because the walking skeleton was never identified.

## Sources and destinations

Inflows come from five sources, four of which are exogenous (outside the team's boundary):

- User reality (exogenous): observed behavior, pains, workflows
- Team imagination (exogenous): tacit knowledge, analogies, hunches
- Business intent (exogenous): strategy, revenue goals, constraints
- Market signals (exogenous): competitor moves, regulatory shifts
- Prior knowledge stocks (endogenous): glossary, lessons learned, capability claims

Outflows go to internal staging stocks (release backlogs, acceptance-ready stories, work in progress, working software) and ultimately to user outcomes (exogenous).

The endogenous source is what makes a learning system. Without it, every map starts from scratch and the team rediscovers the same details each cycle.

## Cadence

Recommended cadence: every release-slice boundary, typically every 4-8 weeks. The story map is not a one-time artifact. It is the team's current articulation of the user's journey, updated as the team learns.

## Integration with BDD

The story map's refined tasks become the examples that BDD formalizes into scenarios. The workshopping valve at the BDD layer drains refined tasks and produces acceptance-ready stories with Given-When-Then scenarios.

## What to read next

- `practices/bdd.md` — the layer below Story Mapping
- `system/inflows-and-outflows.md` — detailed analysis of the bathtub
- `diagrams/02-story-map-bathtub.svg` — the visualization
