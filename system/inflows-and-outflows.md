# Inflows and Outflows

This document catalogs the major flows in the Aim Praxis system, organized by which stock they fill or drain. For visual reference, see `diagrams/02-story-map-bathtub.svg` and `diagrams/12-integrated-seven-practice.svg`.

## Story Map flows

### Inflows that fill the story map

**User discovery.** The flow of new insights gathered from observing and interviewing users. Fills the raw-ideas stock with grounded observations.

**Blue-sky ideation.** The process of imagining great possibilities without immediate regard for scope. Fills raw ideas with hypothetical possibilities.

**Task identification.** The naming of high-level verb phrases that tell the user's story left to right. Transforms raw ideas into backbone tasks.

**Detail refinement.** The breakdown of larger tasks into sub-tasks, exceptions, and details. Transforms backbone tasks into refined tasks.

**Stakeholder input.** Information from business choosers and customers regarding the "big why" — business goals, revenue outcomes, strategic constraints.

### Outflows that drain the story map

**Release slicing.** The decision-making flow that separates the map into prioritized increments (walking skeleton, MVP, subsequent releases).

**Story workshopping.** The process of reviewing requirements with developers and testers to create specific acceptance criteria. Drains refined tasks into acceptance-ready stories.

**Dev specification.** The rate at which functional requirements are handed off to development for active construction. Drains acceptance-ready stories into work in progress.

**Scope depletion.** The deliberate process of moving items out of scope to manage the system within time and resource constraints. Drains into the deferred map, not into nothing.

**Product delivery.** The final outflow where requirements are transformed into working software and verified.

## BMC flows

### Three primary flows that close the cycle

**Value creation flow.** Key partnerships and key resources combine through key activities to produce the value proposition. The production side of the business.

**Value delivery flow.** The value proposition reaches customer segments through channels, mediated by customer relationships. The distribution side.

**Value capture flow.** Customer segments generate revenue streams, which fund cost structure, which sustains key resources and activities. The closing loop.

## VPC flows

### Customer-side flows

**Failed-jobs flow.** Jobs that go badly fill the pain stock. Frustration, money wasted, time lost accumulate.

**Successful-jobs flow.** Jobs that go well fill the gain stock. Confidence, capability, status accumulate.

### Supplier-side valves

**Pain reliever flow.** Drains customer pain stocks faster than the customer could drain them alone. Mediated by products and services.

**Gain creator flow.** Fills customer gain stocks faster than the customer could fill them alone. Mediated by products and services.

## BDD flows

### Forward flows through the aging chain

- **Formalize:** examples → scenarios. Drives by conversation, captures by structuring as Given-When-Then.
- **Organize:** scenarios → features. Groups scenarios around coherent capabilities.
- **Implement:** scenarios → step definitions. Bridges human-readable to machine-executable.
- **Execute:** step definitions → test results. Continuous; runs on every change.
- **Render:** passing tests → living documentation. Emergent; produced by passes.

### Feedback flow

- **Defect:** failures → rework register. Failed scenarios become register entries.
- **Refine language:** patterns → glossary. The PDSA agent and humans propose glossary updates.

## The unified rework register flows

### Inflows from every layer

- BMC: invalidated strategic assumptions
- VPC: invalidated fit hypotheses
- Story Mapping: identified scope errors
- BDD: scenario ambiguities discovered in workshopping or execution
- ATDD: acceptance disagreements
- TDD: design issues surfaced in refactoring
- CI/CD: integration failures
- Observability: production incidents and user-outcome divergences

### Outflows that feed compounding artifacts

- Glossary additions (linguistic patterns)
- Lessons learned entries (procedural patterns)
- Process capability updates (capability patterns)
- Direct upstream changes (refinement rules, acceptance criteria templates, release-slice constraints)

## Diagnostic patterns

### Inflow rate exceeds outflow rate

The stock rises. Look for:
- Pack rat in story map (too much ideation, not enough delivery)
- Backlog accumulation in any stock (the constraint is downstream)
- Cash burn in BMC (revenue inflow < cost outflow)

### Outflow rate exceeds inflow rate

The stock falls. Look for:
- Premature drainage in story map (shipping ahead of shared understanding)
- Bug-driven engineering (rework outflow exceeding new-feature inflow)
- Customer churn exceeding acquisition in BMC

### Inflow disconnected from source

The stock fills but the contents are stale. Look for:
- BMC review without market signal updates
- Story map sessions without recent user research
- Glossary additions without grounded examples

### Outflow disconnected from destination

The stock drains but the destination doesn't receive. Look for:
- Working software outflows that don't produce user outcomes
- Lessons learned that don't influence future work
- PDSA proposals that don't update upstream stocks

## What to read next

- `system/sources-and-destinations.md` — where flows come from and go to
- `system/archetypes.md` — pathological flow patterns
- `practices/story-mapping.md` — the bathtub model applied
