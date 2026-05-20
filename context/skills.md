# Skills

Skills are procedural knowledge captured in a form usable by agents. Where MCP servers expose data, skills capture *how* to do something. A skill says: when asked to do X, follow this procedure, consult these resources, produce output in this form.

This document specifies the skills the methodology relies on.

## What is a skill

A skill is distinct from:

- A **tool** (which provides a capability — write file, query MCP)
- **Knowledge** (which provides facts — what a term means)
- **Context** (which provides situation — what we're working on)

A skill is the procedural overlay: given the tools, knowledge, and context, here is how to actually do the work.

In Anthropic's Claude infrastructure, skills are markdown documents at well-known paths that get surfaced to agents when relevant. The same pattern applies in any agentic system; the storage is implementation-specific.

## Methodology-level skills

### Story refinement skill

Procedural knowledge for decomposing backbone tasks into refined tasks. Includes:
- Standard task taxonomy (CRUD operations, error paths, edge cases)
- Decomposition checklist (have you considered exceptions, has the user's actual journey been preserved)
- Quality criteria for refined tasks
- Escalation patterns

Used by: refinement agent.

### Scenario authoring skill

Procedural knowledge for writing Given-When-Then scenarios. Includes:
- Standard scenario structure
- Common patterns (CRUD, validation, error handling, async behavior)
- Anti-patterns to avoid (testing internal state, ambiguous outcomes)
- Glossary-compliance check

Used by: workshopping agent.

### Acceptance criterion authoring skill

Procedural knowledge for writing measurable acceptance criteria. Includes:
- Required structure (preconditions, action, observable outcome)
- Common measurability traps and how to avoid them
- How to handle non-functional criteria (performance, security)
- Customer-collaboration patterns

Used by: workshopping agent (drafts), ATDD Guardian (checks).

### Code generation skill

Procedural knowledge for writing code that passes acceptance tests in this project. Includes:
- Project-specific conventions
- Architectural patterns to follow
- Anti-patterns from the lessons-learned library
- TDD rhythm discipline (red-green-refactor)
- Escalation patterns for architectural decisions

Used by: coding agent.

### Pattern detection skill

Procedural knowledge for detecting recurring patterns in the rework register. Includes:
- Similarity criteria for grouping entries
- Threshold rules for triggering proposals
- Evidence-base construction
- Proposal authoring patterns

Used by: PDSA agent.

### VPC fit assessment skill

Procedural knowledge for synthesizing customer signal into VPC-relevant patterns. Includes:
- Pain-stock rising/falling detection
- Gain-creator validation patterns
- Job-completion success detection
- Signal-vs-noise thresholds

Used by: customer research agent.

## Project-specific skills

Beyond methodology-level skills, each project will accumulate skills specific to its domain. Ship Audit, for example, will have:

- Carrier invoice parsing skill
- Audit rule application skill
- Claim packaging skill
- SMB customer communication skill

These project-specific skills are not part of the methodology proper but are part of the methodology's application in a specific context.

## Skill maintenance

Skills, like all compounding artifacts, require maintenance. When the team learns something new about how to do work, the skill is updated. When the methodology evolves, the skills evolve with it.

The PDSA agent's proposals often translate into skill updates. A recurring pattern of mistakes in scenario authoring becomes a check added to the scenario-authoring skill. A recurring pattern of code mistakes becomes a guardrail added to the code-generation skill.

## Skill versioning

Like MCP server schemas, skills should be versioned. An agent following version 1 of a skill should not silently break when version 2 is deployed. The skill versioning is part of the discipline.

## Where skills live

In a Claude-based implementation, skills live at well-known paths (typically `/skills/<name>/SKILL.md`). Other implementations may use different storage; the principle is that skills are discoverable, versioned, and queryable by the agents that need them.

For Aim Praxis specifically, skills should be in version control alongside the rest of the methodology artifacts. They are not separate from the project; they are part of the project's documentation.

## What to read next

- `context/mcp-servers.md` — the data layer skills operate over
- `context/knowledge-files.md` — the static knowledge skills reference
- `context/boundary-specifications.md` — the rails skills should respect
