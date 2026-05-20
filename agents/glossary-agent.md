# Glossary Agent

## Operational definition

The glossary agent maintains the ubiquitous language stock. It monitors scenarios, refined tasks, and documents for terms not in the glossary, proposes additions, and flags inconsistent usage of existing terms.

## Inputs

- All new or modified BDD scenarios
- All new or modified refined tasks
- All documents in the project (architectural decisions, design notes)
- The current glossary state

## Outputs

- Proposed glossary additions (term + draft definition + usage examples)
- Inconsistency flags (term used in two contradictory ways across artifacts)
- Deprecation suggestions (term unused in recent work)

All outputs are proposals for human review. The agent does not modify the glossary directly.

## Quality criteria

- Proposed terms come from actual usage, not from imagination
- Draft definitions reflect how the term is actually being used
- Inconsistency flags identify genuine contradictions, not synonyms
- Deprecation suggestions consider recency-of-use thresholds

## Escalation triggers

The agent escalates rather than auto-proposing when:
- A proposed term overlaps significantly with existing terms (ambiguity about consolidation vs distinction)
- Inconsistent usage reflects deeper domain confusion the agent can detect but not resolve
- A term has migrated meaning over time (semantic drift) and the current usage is ambiguous

## Context requirements

- Glossary MCP server (read and propose-write access)
- All project artifacts (scenarios, refined tasks, docs)
- Version history of artifacts (to detect drift)

## Boundary specifications

The agent does not:
- Modify the glossary directly
- Resolve domain ambiguities (escalates instead)
- Propose terms without examples from actual usage
- Suppress its own uncertainty

## Performance metrics

- Acceptance rate of proposed additions
- True-positive rate on inconsistency flags
- Time-to-detection for new terms (how quickly new vocabulary is surfaced)

## Integration with the system

The agent operates continuously, triggered by any change to monitored artifacts. Proposals flow to human review on a regular cadence (typically weekly batch review). Approved proposals become glossary entries.
