# The Seven Layers

## The structural claim

Aim Praxis integrates seven practices into a single system of nested feedback loops. The layers, from outermost to innermost:

1. **Business Model Canvas (BMC)** — weeks to quarters
2. **Value Proposition Canvas (VPC)** — weeks to months
3. **Story Mapping** — weeks
4. **Behavior-Driven Development (BDD)** — days to weeks
5. **Acceptance Test-Driven Development (ATDD)** — days
6. **Test-Driven Development (TDD)** — minutes
7. **Continuous Integration / Continuous Deployment (CI/CD)** — seconds to hours

The order is not arbitrary. Each outer layer constrains what the inner layers do. Each inner layer feeds back to the outer layers. The structure is what makes the methodology a system rather than a collection of practices.

## Why this specific ordering

The ordering reflects two things: cycle time and authority over purpose.

**Cycle time.** Each layer operates at roughly an order of magnitude shorter cycle time than the layer above it. Quarter-scale strategy informs month-scale fit validation informs week-scale narrative structure informs day-scale behavioral specification informs day-scale story acceptance informs minute-scale unit design informs second-scale integration.

This multi-time-scale property is the methodology's defense against the variation that exists at different scales. Errors that take quarters to manifest get caught at the BMC level. Errors that take seconds to manifest get caught at CI/CD. A system that operated at only one cycle time could only catch one class of error.

**Authority over purpose.** The BMC layer sets the system aim — what the product is for. The VPC layer translates that aim into a value proposition for specific segments. Story Mapping decomposes the proposition into deliverable work. BDD specifies how the work should behave. ATDD agrees with the customer on what completion looks like. TDD codes against that agreement. CI/CD deploys the result.

Each layer inherits its purpose from the layer above. If the layers are arranged in any other order, this inheritance breaks. TDD cannot tell BDD what behaviors to specify; ATDD cannot tell the BMC what the product is for. The hierarchy of purpose runs from outer to inner, irreversibly.

## What each layer catches

Each layer in the hierarchy catches a class of error that the others cannot see.

**BMC catches direction error.** The product is heading the wrong way. The segment is wrong. The revenue model is wrong. No amount of inner-loop discipline can catch this. A team can be deploying continuously with perfect test coverage and still be building software for a market that doesn't exist.

**VPC catches fit error.** The product is heading toward the right segment but solving the wrong problem for them. The customer's actual pain is not what the product addresses. The gain creator does not produce the gain. This is invisible to Story Mapping and below because Story Mapping starts with the assumption that fit is established.

**Story Mapping catches scope error.** The work is structured in a way that delays value delivery. The release slices do not produce a usable product at any point until the very end. The opening game cannot be played because the walking skeleton was never identified.

**BDD catches behavioral drift.** The system used to do X, now it does Y, and nobody noticed because no scenario covered the change. The system's actual behavior diverges from its specified behavior, and the divergence is invisible without executable specifications.

**ATDD catches completion ambiguity.** Engineering thinks the story is done; the customer does not. The acceptance criteria were not specific enough; the customer's interpretation differs from engineering's interpretation. This is a different failure from behavioral drift; it is about agreement on what "done" means before code is written.

**TDD catches design degradation.** The code works but is hard to change. Modules are tightly coupled. Abstractions are leaky. The unit-level architecture is decaying even though external behavior is correct. None of the outer loops can see this; they only see external behavior.

**CI/CD catches integration failure.** The code works alone but does not work together. Environments drift. Deployment state is inconsistent. The unit-level work passes its own tests but the integrated system does not function. This is the loop with the shortest cycle time and the narrowest scope.

## Each layer alone is insufficient

The argument for the full seven-layer stack is that no subset is sufficient.

A team using only TDD has well-designed code that may solve the wrong problem.

A team using only BDD has behavioral specifications that may describe an unwanted product.

A team using only Story Mapping has a coherent narrative that may not produce deliverable software.

A team using only the VPC has a validated value proposition that may not become a product.

A team using only the BMC has a strategy that may not produce anything.

A team using only CI/CD ships continuously, ships fast, and may ship the wrong thing fast.

The seven layers together produce alignment at every cycle time simultaneously. Subsets produce alignment at some cycle times and drift at others.

## The inner-loop dominance pathology

Even teams that nominally adopt all seven layers tend to drift toward inner-loop dominance. The pattern is consistent across organizations:

CI/CD becomes the loop everyone cares about; deployment frequency is the proxy for quality.

TDD coverage becomes the proxy for engineering discipline.

ATDD becomes paperwork; stories get accepted in standups rather than demonstrated to customers.

BDD becomes vestigial; feature files exist but are not maintained.

Story Mapping becomes a thing that happened once at the start of the year.

BMC and VPC become artifacts that exist in some Confluence page and have not been updated in eighteen months.

The pattern is reinforced by the cadence mismatch — inner loops run continuously and feel productive; outer loops run rarely and feel like overhead. Under pressure, organizations cut what feels like overhead.

The defense is deliberate. Outer loops must be calendared, attended, and protected. The methodology's design assumes this defense; without it, the system collapses to its inner loops and the alignment property the system was designed to produce is lost.

## The diagnostic question

For any team running this lifecycle, the diagnostic question is: which of the seven layers is currently strongest, which is weakest, which feedback path is closed, and which is open?

The answers tell you where the system is producing variation, where it is catching variation, and where information is being lost.

A typical answer for a team that has not yet internalized Aim Praxis: TDD strong, CI/CD strong, ATDD inconsistent, BDD vestigial, Story Mapping done once a year, BMC and VPC haven't been touched since founding.

This diagnosis is the starting point for adopting the methodology. The work is to progressively strengthen the missing layers and close the open feedback paths until the system is whole.

## The Deming reading

Each layer reduces variation at its own time scale. The whole system reduces variation in every output the team produces, from quarterly business model decisions to minute-by-minute code commits. The compounding artifacts (glossary, lessons learned, process capability) accumulate institutional knowledge that makes the system increasingly capable over time.

This is what Deming meant by "appreciation for a system" applied to software development. The methodology is the operational definition of that appreciation.

## What to read next

- `concepts/05-cycle-times.md` — the multi-time-scale property in more depth
- `system/integrated-system.md` — the full integrated picture with diagram
- `practices/` — one document per layer
