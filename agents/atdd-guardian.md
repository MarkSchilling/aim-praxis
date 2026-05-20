# ATDD Guardian

## Operational definition

ATDD Guardian is the deterministic gate at the ATDD layer. It enforces explicit, measurable criteria on acceptance criteria mechanically. The gate does not exercise judgment; it checks criteria.

Mark Schilling has published an implementation as the `@schilling.mark.a/atdd-guardian` MCP server.

## Inputs

- Proposed acceptance criteria for a story
- The current ubiquitous language glossary
- The story being accepted (for context)

## Outputs

A pass/fail result with specific findings:
- Criteria pass: the gate allows the story to enter the development stock
- Criteria fail: the gate returns specific findings and blocks entry

## Gate criteria (illustrative)

- Each criterion references only terms in the glossary
- Each criterion specifies an observable outcome, not internal state
- Each criterion is measurable (a test can pass or fail based on it)
- Preconditions are stated explicitly
- The criterion is at story level, not unit level
- No criterion uses ambiguity-inducing words ("appropriate", "reasonable", "fast") without measurable thresholds

## The deterministic property

The gate's value is its determinism. It applies the same criteria the same way every time. There is no path for "this one is urgent" or "we'll fix the criteria later." The criteria are enforced uniformly.

Bypassing the gate creates rework that the rework register captures. Over time, the team learns that the gate is faster than the rework.

## Escalation

The gate does not escalate — it passes or fails. Failures contain enough information for a human to fix the input and resubmit. If a criterion seems unenforceable, the criterion itself is the wrong shape; the gate is correctly refusing it.

## Context requirements

- Glossary MCP server
- The story map (for context about parent backbone task)
- Process capability statement (for criteria that should reflect achievable thresholds)

## Boundary specifications

The gate does not:
- Author criteria (workshopping agent's job)
- Decide whether the customer should accept criteria (customer's job)
- Override its own checks
- Permit "in this case" exceptions

## Performance metrics

- First-pass rate (percentage of submissions that pass on first try)
- Mean number of resubmissions per accepted story
- Trend in first-pass rate over time (should improve as team learns)

## Integration with the system

ATDD Guardian is the bridge between the BDD/workshopping layer above and the TDD/coding layer below. Its pass result is the trigger that allows a story to enter coding. Its fail result blocks code work and routes the story back for refinement.
