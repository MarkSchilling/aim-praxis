# Behavior-Driven Development

## What it is in Aim Praxis

Behavior-Driven Development (BDD), originating with Dan North's reframing of TDD around behavioral language and developed by Liz Keogh, Chris Matts, Gojko Adzic, and others, is treated in Aim Praxis as the fourth layer. It operates at the cycle time of days to weeks and is responsible for the behavioral specification of the system.

BDD's contribution is the discipline of expressing behavior in a vocabulary shared between business and engineering, and making that vocabulary executable through Given-When-Then scenarios.

## The systems reading

BDD operates on a tight aging chain:

**Examples** — concrete instances of behavior gathered from conversation. The raw material.

**Scenarios** — examples formalized into Given-When-Then structure. The central stock.

**Features** — scenarios grouped around coherent capabilities. Container stocks.

**Step definitions** — the executable code binding Given-When-Then phrases to system calls. The bridge between human-readable scenarios and machine-executable tests.

**Living documentation** — the rendered current state of passing scenarios. Emergent stock — not directly written, produced by the test suite passing.

**Test results** — the dynamic state of pass/fail. Oscillating stock; updates on every test run.

Plus a constraint stock that touches everything:

**Ubiquitous language** — the shared vocabulary. Maintained in version control, enforced at scenario-writing time. Slow-growing, foundational.

## What BDD catches

BDD catches behavioral specification drift — the system used to do X, now it does Y, and nobody noticed because no scenario covered the change. It catches it automatically, which is its signature property.

The standard TDD test suite catches what the developer thought to test. The BDD scenario suite catches what the team agreed the system should do. These are different things.

## What BDD does NOT catch

BDD catches drift between specified behavior and actual behavior. It does not catch:

- Whether the specification was wrong in the first place (ATDD's job)
- Whether the design degraded internally (TDD's job)
- Whether the product solves the wrong problem (VPC's job)
- Whether integration works (CI/CD's job)

BDD's coverage is specific to behavioral specification, and the layers around it cover the other concerns.

## The ubiquitous language as compounding artifact

The ubiquitous language is one of the five compounding artifacts. It is what bridges Story Mapping conversation to BDD scenarios to ATDD criteria to TDD code. Without active maintenance, the language drifts; scenarios use terms inconsistently; the system fragments.

The glossary agent operationalizes the maintenance: monitoring scenarios for terms not in the glossary, proposing additions, flagging inconsistent usage. The glossary itself is a versioned file in the repository.

## The structural property: textual and version-controlled

Every primary BDD stock is textual and version-controlled. Examples can be captured in conversation but ultimately get written down. Scenarios live in feature files. Step definitions live in code. Living documentation is generated from those files. The glossary is maintained in version control.

This means every BDD stock has an audit trail. This is something Story Mapping fundamentally cannot offer — sticky notes do not version-control themselves. The structural difference is why BDD scales to distributed teams and long-lived products in a way Story Mapping struggles to.

## Why most teams don't actually do BDD

Many teams say they do BDD but produce only the syntactic form (Given-When-Then) without the substance (ubiquitous language, conversation-first authoring, executable specifications). The result is scenarios that exist but don't reduce variation in behavior.

Aim Praxis treats the substance as load-bearing. The glossary agent enforces language; the workshopping agent enforces form; the ATDD Guardian enforces measurability. Without these supports, BDD degrades to syntactic theater.

## Cadence

BDD scenario authoring happens at feature start, typically weekly to bi-weekly. The scenarios are reviewed when they are written; they are executed continuously thereafter. The cycle of authoring is slower than the cycle of execution.

## Integration with ATDD

BDD scenarios become the acceptance criteria that ATDD agrees with the customer. The transition from BDD to ATDD is from "the team has specified this behavior" to "the customer has accepted these scenarios as the definition of done."

ATDD Guardian operates at this transition, enforcing that the acceptance criteria are measurable, falsifiable, and within process capability.

## What to read next

- `practices/atdd.md` — the layer below BDD
- `agents/workshopping-agent.md` — the agent that drafts scenarios
- `agents/glossary-agent.md` — the agent that maintains the language
