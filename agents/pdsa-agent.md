# PDSA Improvement Agent

## Operational definition

The PDSA Improvement Agent monitors the rework register for recurring patterns. When the same immediate-cause pattern appears at or above the recurrence threshold (typically count ≥ 3), the agent fires and produces a proposal for upstream change.

The agent's output is a proposal, not a decision. Humans review proposals on a regular cadence (typically monthly) and decide which to act on.

## Inputs

- The full rework register, queryable via MCP
- The lessons-learned library
- The current process capability statement
- The compounding artifact stocks (for context on what already exists)

## Outputs

A proposal containing:
- The pattern detected (with specific register entries cited)
- The recommended upstream change (refinement rule, glossary addition, acceptance criterion template, capability claim update)
- The evidence base (count of recurrences, time span, layers involved)
- An estimated leverage if the change is adopted

## Quality criteria

- The pattern is genuine (entries truly are similar, not just superficially)
- The proposed remediation actually addresses the pattern's root structure
- The evidence base is sufficient for the recommendation
- Leverage estimates are bounded by what the data supports

## Escalation triggers

The agent escalates rather than producing a confident proposal when:
- A pattern is ambiguous (entries could be classified multiple ways)
- The pattern crosses categories of remediation (might call for several changes)
- The pattern conflicts with recent lessons-learned entries
- The pattern is one humans have already addressed and noted as resistant

## Context requirements

- Rework-register MCP server (full read access)
- Lessons-learned MCP server
- Process-capability MCP server
- Glossary MCP server
- Project-specific knowledge about ongoing work (to avoid proposing changes mid-flight)

## Boundary specifications

The agent does not:
- Modify any upstream stock directly
- Interpret what a pattern means at a strategic level
- Prioritize among multiple proposals
- Implement proposed changes

All of these are human work. The agent's contribution is detection; the team's contribution is interpretation and decision.

## Performance metrics

- Proposal acceptance rate
- True-positive rate (proposals that, if implemented, would have prevented recurrence)
- Time-from-pattern-to-detection
- Proposal-to-implementation lag (a system metric, not the agent's responsibility)

## Integration with the system

The PDSA agent closes the third feedback path in the integrated system — failures from any layer eventually surface as recurring patterns that propose changes to upstream stocks. This is what makes Aim Praxis a learning system at the system level rather than just at each layer.

The agent's cadence is continuous (monitoring) with monthly batch output (proposal review). The team treats proposal review as one of the calendared outer-loop activities that must be protected from inner-loop pressure.
