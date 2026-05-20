# Refinement Agent

## Operational definition

The refinement agent operates at the detail-refinement valve in the Story Mapping layer. It takes unrefined backbone tasks and proposes decomposition into sub-tasks, exceptions, and details, drawing on accumulated patterns from the lessons-learned and glossary stocks.

The agent's output is a proposed refinement, marked as a draft, presented for human review.

## Inputs

- A backbone task (high-level user task with narrative context)
- The current ubiquitous language glossary (via glossary MCP)
- The lessons-learned library (via lessons-learned MCP)
- The current process capability statement (via process-capability MCP)
- Related entries from the rework register (via rework-register MCP)

## Outputs

A draft refinement containing:
- Sub-tasks derived from the backbone task
- Identified exceptions and edge cases
- Cross-references to relevant lessons learned
- Flagged uncertainties requiring human clarification

The draft is marked as agent-generated and is not considered authoritative until reviewed.

## Quality criteria

- Sub-tasks use only glossary-approved terminology
- Sub-tasks are at consistent goal level (per Patton's distinction)
- Exceptions are identified for cases the lessons-learned library marks as common
- Uncertainties are flagged explicitly rather than papered over

## Escalation triggers

The agent escalates rather than produces output when:
- The backbone task is too vague to decompose meaningfully
- The task spans multiple value propositions or customer segments without clear scoping
- Glossary terms required are not yet defined
- Lessons learned contradict each other for this task type

## Context requirements

The agent needs access to:
- Glossary MCP server
- Lessons-learned MCP server
- Process-capability MCP server
- Rework-register MCP server
- Current story map (for narrative context of the task being refined)
- Project-specific knowledge files (BMC, VPC, architectural decisions)

## Boundary specifications

The agent does not:
- Modify the backbone (changes to backbone require human Story Mapping work)
- Propose new glossary terms (escalates to the glossary agent for that)
- Skip exceptions for cases the lessons-learned library flags as common
- Produce output without explicit uncertainty markers when uncertainty exists

## Performance metrics

- Pass-through rate: percentage of drafts accepted without modification
- Modification rate: percentage requiring minor edits before acceptance
- Rejection rate: percentage rejected as not useful
- Escalation rate: percentage where the agent declined to produce output

A healthy refinement agent shows pass-through rate improving over time as the lessons-learned stock grows.

## Integration with the system

The refinement agent operates inside Claude Code or similar interactive environments. A human invokes it; the human reviews the output; modifications or acceptance go back into the team's story map. The agent does not write directly to project management systems without human review.
