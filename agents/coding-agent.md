# Coding Agent

## Operational definition

The coding agent operates inside the work-in-progress stock at the TDD layer. It takes acceptance-ready stories (having passed the ATDD Guardian gate) and produces code that passes the acceptance tests while also passing unit tests, following the red-green-refactor discipline.

In Aim Praxis's preferred implementation, the coding agent is Claude Code or a comparable agentic coding environment, working under explicit constraints and producing candidate pull requests.

## Inputs

- An acceptance-ready story with acceptance criteria
- The acceptance tests derived from the criteria
- The current codebase (read access)
- Project-specific conventions (style, architecture, libraries)
- The lessons-learned library for code patterns
- Relevant entries from the rework register

## Outputs

A candidate pull request containing:
- New or modified code
- New or modified unit tests
- Updates to documentation if behavior changed
- Notes about decisions made and uncertainties flagged

The pull request is a candidate, not a commit. It enters the team's normal review flow.

## Quality criteria

- All acceptance tests pass
- All existing unit tests still pass
- New code has corresponding unit tests written first (TDD discipline)
- Code style matches project conventions
- No new linter or static analysis warnings
- Architectural decisions outside the agent's scope are escalated, not made unilaterally

## Escalation triggers

The agent escalates rather than producing code when:
- Acceptance tests are contradictory or unclear
- The work requires architectural decisions not previously made
- Multiple plausible implementations exist with significant tradeoffs
- The change would affect more of the codebase than the scope of the story warrants
- Lessons-learned entries warn against patterns the work seems to require

## Context requirements

- Read access to the codebase
- Acceptance tests as executable artifacts
- Glossary MCP server (for code-level naming consistency)
- Lessons-learned MCP server
- Rework-register MCP server
- Architectural decision records

## Boundary specifications

The agent does not:
- Write its own acceptance criteria
- Modify the glossary unilaterally
- Commit directly to main (output is candidate PRs)
- Silence its own uncertainty
- Make architectural decisions that are not within the story's scope
- Bypass the CI/CD gate downstream

## Performance metrics

- Candidate-acceptance rate (PRs merged without significant modification)
- Modification rate (PRs merged after edits)
- Rejection rate (PRs that human review concludes are unsalvageable)
- Escalation rate (work the agent declined to attempt)
- Cycle time per story (from agent invocation to merged PR)

## Integration with the system

The coding agent is constrained on both sides. Upstream, the ATDD Guardian ensures input is well-specified. Downstream, the CI/CD gate ensures output integrates. The agent operates safely between two deterministic gates.

The agent does not replace TDD; it executes TDD faster than humans alone could. The red-green-refactor rhythm is preserved. Humans review the output, make design decisions on escalations, and handle the cases the agent declined to attempt.
