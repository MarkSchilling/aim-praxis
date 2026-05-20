# Workshopping Agent

## Operational definition

The workshopping agent operates at the story-workshopping valve in the BDD layer. It takes refined tasks and drafts Given-When-Then scenarios that formalize the behavior into BDD-compatible specifications.

The agent's output is draft scenarios marked as agent-generated, presented for human review and customer collaboration.

## Inputs

- A refined task (from the Story Mapping layer)
- The current ubiquitous language glossary (via glossary MCP)
- The lessons-learned library (via lessons-learned MCP)
- Existing scenarios in the same feature area (for pattern consistency)
- BDD conventions specific to the project

## Outputs

Draft scenarios containing:
- Given-When-Then structure
- Preconditions, action, and observable outcome
- Reference to relevant glossary terms
- Flagged ambiguities requiring conversation

## Quality criteria

- Scenarios use only glossary-approved terminology
- Each scenario specifies an observable outcome, not internal state
- Preconditions are stated explicitly
- Edge cases identified by lessons-learned are covered with separate scenarios
- Scenarios are at story level, not at unit-test level

## Escalation triggers

The agent escalates when:
- The refined task uses terms not in the glossary
- The expected behavior is ambiguous or contradicts existing scenarios
- The outcome is not externally observable
- Acceptance criteria are not derivable without customer input

## Context requirements

- Glossary MCP server
- Lessons-learned MCP server
- Existing feature files in the project
- Current refined task and its parent backbone task
- Project-specific BDD conventions

## Boundary specifications

The agent does not:
- Author acceptance criteria unilaterally (those require customer agreement)
- Modify the glossary (escalates to glossary agent)
- Produce scenarios that test internal implementation
- Skip the ambiguity escalation

## Performance metrics

- Scenario acceptance rate
- Glossary compliance rate
- Ambiguity-detection accuracy (did the agent flag what humans would also flag)
- Coverage of edge cases identified post-hoc

## Integration with the system

Output feeds the ATDD layer as draft acceptance criteria. The ATDD Guardian then verifies the criteria meet form requirements. Customer agreement converts drafts into accepted criteria.
