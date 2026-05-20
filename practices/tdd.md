# Test-Driven Development

## What it is in Aim Praxis

Test-Driven Development (TDD), formalized by Kent Beck in *Test-Driven Development: By Example* (2002), is treated in Aim Praxis as the sixth layer. It operates at the cycle time of minutes and is responsible for unit-level design discipline.

TDD's contribution is the red-green-refactor cycle: write a failing test, write the minimum code to pass it, refactor for clarity. This rhythm produces code that is testable, regression-protected, and designed under pressure to be simple.

## The systems reading

TDD operates on three stocks within the work-in-progress stock:

**Failing tests** — the red phase. Tests that specify behavior the code does not yet exhibit.

**Passing tests** — the green phase. Tests that the code now passes. Accumulates monotonically as work proceeds.

**Refactored code** — the clean phase. Code that passes tests and has been improved structurally without changing behavior.

The valves between these stocks are implementation (red → green) and refactoring (green → clean).

## What TDD catches

TDD catches design degradation at the unit level — code that works but is hard to change, modules that are tightly coupled, abstractions that leak. None of the outer loops can see this; they only see external behavior.

TDD's signature property is that tests serve multiple purposes simultaneously: specification, verification, regression protection, and design feedback. The design feedback aspect is the most distinctive and the most often missed.

## What TDD does NOT catch

TDD does not catch:

- Whether the right tests are being written (ATDD's job — the customer's view)
- Whether the system as a whole behaves correctly (BDD's job — the behavioral specification)
- Whether integration works (CI/CD's job)
- Whether the product is for the right customer (VPC's job)
- Whether the business model is sound (BMC's job)

A team using only TDD has well-designed code that may solve the wrong problem.

## Tests as design pressure

The discipline of writing tests first creates design pressure that improves code structure. Code that is hard to test is usually hard to understand. Code that is easy to test is usually well-factored. The test-first rhythm makes this pressure continuous rather than periodic.

This is the property that makes TDD different from "write tests after." The tests-after pattern produces tests but does not produce the design pressure. The tests-first pattern is what makes the code itself better.

## The coding agent in the TDD layer

Aim Praxis places a coding agent inside the TDD layer. The agent's job is to take acceptance-ready stories (from ATDD) and produce code that passes the acceptance tests while also passing unit tests.

The agent is constrained by two gates: ATDD upstream (ensures the input story is well-specified) and CI/CD downstream (ensures the output integrates). The gates make the agent's output trustworthy.

The agent operates within the red-green-refactor rhythm. It does not bypass TDD; it executes TDD faster than humans alone could. The human's role shifts from typing code to reviewing the agent's output, making design decisions, and handling cases where the agent escalates uncertainty.

## What the coding agent should NOT do

Even with full capability, the coding agent should not:

- Write its own acceptance criteria (those come from ATDD)
- Modify the glossary unilaterally
- Commit directly to main (output is candidate PRs, not commits)
- Silence its own uncertainty

These boundaries are what keep the agent useful rather than dangerous. The coding agent that operates outside these boundaries becomes the inner-loop dominance pathology in agentic form.

## Cadence

TDD runs continuously within every coding session. The red-green-refactor cycle takes minutes. Multiple cycles happen per hour of focused work. The cadence is set by the work itself, not by external scheduling.

## Integration with CI/CD

TDD's clean code becomes the input that CI/CD integrates and deploys. The TDD test suite is one of the gates CI/CD enforces. A change cannot reach production if it breaks the unit tests.

## What to read next

- `practices/cicd.md` — the layer below TDD
- `practices/atdd.md` — the layer above TDD
- `agents/coding-agent.md` — the agent in the TDD layer
