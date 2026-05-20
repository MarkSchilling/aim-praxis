# The Integrated System

## The unified view

Aim Praxis integrates seven practices into one continuous stock-and-flow system. This document presents the integrated view. For per-practice depth, see the documents in `practices/`. For the foundational concepts, see `concepts/`.

The integrated system is visualized in `diagrams/12-integrated-seven-practice.svg` (without agents) and `diagrams/13-integrated-seven-practice-with-agents.svg` (with agentic augmentation).

## The vertical structure

Seven layers stack in a specific order, from outermost to innermost:

1. BMC layer (weeks to quarters): aim and segments, value flows, revenue and cost
2. VPC layer (weeks to months): customer jobs, value proposition, fit validation
3. Story Mapping layer (weeks): backbone, refined tasks, release slices
4. BDD layer (days to weeks): examples, scenarios, living documentation
5. ATDD layer (days): acceptance criteria, acceptance tests, demonstrably complete
6. TDD layer (minutes): failing tests, passing tests, refactored code
7. CI/CD layer (seconds to hours): integrated build, deployed artifact, working software

The order is not arbitrary. Each layer's output becomes the next layer's input. The ordering is the conservation law of the system — information cannot skip a layer without losing fidelity.

## The downward flow

Information flows from outer layers to inner layers through valves:

- BMC's value flows define VPC's customer jobs to address
- VPC's validated fit becomes the user journey Story Mapping decomposes
- Story Mapping's refined tasks become BDD's examples for formalization
- BDD's scenarios become ATDD's acceptance criteria for agreement
- ATDD's executable gates become TDD's targets for coding
- TDD's clean code becomes CI/CD's input for integration
- CI/CD's working software produces user outcomes

Each transition is a valve. Each valve has a rate. The slowest valve sets the system's throughput.

## The upward feedback

Two upward feedback paths close the system:

**Value capture (right-side return).** Revenue from working software returns to the BMC layer, funding the next cycle of business model investment. This is the loop that makes the system financially sustainable.

**Learning (left-side return).** Observed user outcomes return to the VPC layer, validating or invalidating fit assumptions. This is the loop that makes the system epistemologically honest.

A business with the first loop but not the second is profitable but fragile; it makes money until its assumptions break. A business with the second loop but not the first is honest but unsustainable; it learns until the cash runs out. Both loops have to close.

## The third feedback path

A third feedback path runs through the rework register:

- Failures from every layer flow into the unified register
- The register classifies failures by which loop caught them and which should have
- The PDSA agent monitors the register for recurring patterns
- The PDSA agent proposes upstream changes
- Humans review and approve
- Approved changes update the compounding artifacts (glossary, lessons learned, process capability)
- Updated artifacts feed back into every layer

This is what makes the system a learning system rather than just a delivery system.

## The compounding artifacts

Three slow stocks accumulate over time and improve every layer:

- **Ubiquitous glossary** — shared language enforced at scenario-writing time
- **Process capability** — documented self-model of what the team can deliver
- **Lessons learned** — pattern library queryable by agents and humans

Plus the **rework register** as the diagnostic instrument and the **metrics store** as the measurement infrastructure.

These five artifacts together constitute the team's institutional memory. They distinguish a learning system from a delivery system. A team that maintains them has a competitive moat that grows automatically with time.

## The boundary

Most of the system is inside the team's boundary — under their control. Some elements are on the boundary or outside it:

**Inside the boundary:** all seven practice layers, the compounding artifacts, the rework register, the agents.

**On the boundary:** the customer-facing artifacts (value proposition, customer segments, acceptance criteria as agreed with customers).

**Outside the boundary:** user outcomes, market signals, regulatory environment, competitive moves.

The boundary is a deliberate analytical choice. Aim Praxis recommends drawing it to include everything the team can influence and excluding everything they can only observe. Pulling it too narrow blinds the team to where leverage lives. Pulling it too wide produces wishful thinking about influence the team doesn't actually have.

## What each layer catches

The defense of the full seven-layer stack is that each layer catches errors invisible to the others:

- BMC catches direction error
- VPC catches fit error
- Story Mapping catches scope error
- BDD catches behavioral drift
- ATDD catches completion ambiguity
- TDD catches design degradation
- CI/CD catches integration failure
- Observability extension catches production-runtime failure

A subset of layers catches a subset of errors. The full stack is the only architecture that catches all of them.

## The diagnostic question

For any team running this lifecycle: which layer is currently strongest, which weakest, which feedback path is closed, which is open?

A typical answer for a team that has not yet internalized Aim Praxis: TDD strong, CI/CD strong, ATDD inconsistent, BDD vestigial, Story Mapping done once a year, BMC and VPC haven't been touched since founding.

The diagnosis is the starting point for adopting the methodology. The work is progressively strengthening missing layers and closing open feedback paths until the system is whole.

## What to read next

- `system/archetypes.md` — recurring failure patterns to watch for
- `operations/operationalization-sequence.md` — how to adopt the methodology
- `agents/placement-philosophy.md` — how agents fit into the integrated system
