# Operationalization Sequence

This document specifies the order in which a team should adopt Aim Praxis. Adopting all seven practices simultaneously is overwhelming; adopting them in the wrong order produces dependencies that aren't yet satisfied. The sequence below has been tested informally and refined.

## Phase 0: Articulate the aim

Before adopting any practice, write down the system aim. One paragraph. What is the system for? Who does it serve? What would alignment look like?

This phase takes a few hours of focused work. The output is `docs/aim.md` for the project (parallel to Aim Praxis's own `docs/aim.md`).

A team that cannot articulate its aim cannot apply the methodology. The methodology aligns to an aim; without one, there is nothing to align to.

## Phase 1: Establish the substrate

Set up the foundational infrastructure that everything else relies on:

- Version control for the methodology artifacts (this repository pattern)
- An initial glossary, even minimal — a handful of terms with definitions
- An initial lessons-learned document, even empty — a place to add entries as they emerge
- An initial rework register, even empty — a place to classify failures
- An initial process capability statement, even tentative — current best understanding

Time estimate: one to two days.

Quit criteria: the substrate is ready when an agent or human can answer "where does this kind of artifact live?" for each compounding artifact.

## Phase 2: Set up the first gate

Implement the ATDD Guardian (or equivalent deterministic gate). This gate enforces the team's first hard quality boundary.

For Mark's team specifically, this means deploying `@schilling.mark.a/atdd-guardian` and integrating it into the team's workflow. For other teams, this means building or adopting a similar gate.

Time estimate: one to two weeks, including team adoption.

Quit criteria: the gate is operational and the team has accepted that bypassing it is not normal.

## Phase 3: Add the first agent (refinement)

The refinement agent is the lowest-risk introduction. It produces drafts that humans review; failures are caught in review. This phase establishes the pattern of human-in-the-loop agentic work.

Time estimate: two to four weeks, including refining the prompts and the team's review discipline.

Quit criteria: the refinement agent's pass-through rate is high enough that humans trust it for routine work, with confidence to escalate or override for non-routine work.

## Phase 4: Outer-loop scaffolding

Establish the cadences for Story Mapping, VPC review, and BMC review. These don't have to be perfect immediately; they have to be on the calendar and attended.

- Story Mapping: every 4-8 weeks
- VPC review: quarterly
- BMC review: quarterly

Time estimate: one cycle of each, so 3-6 months elapsed to have completed an instance of each.

Quit criteria: the team has completed at least one instance of each outer-loop activity and has produced the expected artifacts.

## Phase 5: Close the learning loop

Implement the PDSA agent monitoring the rework register. Establish monthly proposal review.

Time estimate: two to four weeks for the agent; ongoing for the review cadence.

Quit criteria: the team has reviewed at least two batches of proposals and has accepted at least one. The learning loop is closed when proposed changes are actually implemented.

## Phase 6: Add the remaining agents

In rough order of leverage:
- Workshopping agent
- Coding agent (integrated with existing TDD discipline)
- Glossary agent
- Customer research agent
- Market signal agent
- Observability agent

Each agent follows the same pattern: define operational specification, build/configure, integrate with review discipline, monitor performance.

Time estimate: weeks per agent, depending on integration complexity.

## Phase 7: Full system operation

The full system is operational when:
- All seven layers are in active use at appropriate cadences
- All five compounding artifacts have growing entries
- The rework register has classifications and active remediation
- The PDSA cycle is producing accepted proposals
- Agents are operating with clear boundaries and human review
- The team can describe what it's doing in terms of stocks, flows, and loops

Time estimate from Phase 0 to full operation: six to twelve months for a typical team, longer for larger organizations.

## What to do when the sequence breaks

If a phase doesn't work, do not skip ahead. Diagnose what's missing:

- Phase 0 broken: the team can't articulate its aim. Pause and work on this. The methodology has nothing to align to.
- Phase 1 broken: the substrate isn't established. Build the artifacts before adding agents that rely on them.
- Phase 2 broken: the gate is being bypassed. The team isn't ready for downstream agents.
- Phase 3 broken: humans aren't reviewing agent output meaningfully. The pattern of accountable human review hasn't been established.
- Phase 4 broken: outer-loop work is being skipped under pressure. The methodology will collapse to inner loops if this isn't fixed.
- Phase 5 broken: the rework register isn't being maintained. The learning loop is open.
- Phase 6 broken: specific agents aren't working. Treat each agent as its own project with its own diagnosis.

## What to read next

- `operations/cadences.md` — specific cadence recommendations
- `operations/gates.md` — gate criteria in detail
- `agents/placement-philosophy.md` — how to think about each agent introduction
