# Knowledge Files

Knowledge files are the static documents that travel with agents — the context they need to do their work correctly. Where MCP servers provide queryable data and skills provide procedural how-to, knowledge files provide the slow-moving facts about the project.

## What counts as a knowledge file

A knowledge file is:
- Static or slow-changing
- Authoritative within the project
- Relevant to multiple agents or sessions
- Suitable for inclusion in agent context

## Methodology-level knowledge files

### The system aim

The current articulation of what the system is for. This is the single most important knowledge file. Every agent that makes a tradeoff decision should refer to the aim.

For Aim Praxis itself, this lives in `docs/aim.md`. For a project applying Aim Praxis, the project has its own aim document.

### The current BMC

The team's current business model. Updated quarterly. Used by the market signal agent, the BMC review process, and the BMC layer of analysis generally.

### The current VPC

The team's current value proposition canvas. Updated quarterly or more often. Used by the customer research agent, the VPC review process, and any analysis touching the VPC layer.

### The current story map state

A snapshot of the story map at a point in time. The full state is queryable via Story Map MCP, but a snapshot serves as static knowledge for sessions where the live MCP isn't appropriate.

### Architectural decision records

The accumulated ADRs for the project. Each records context, decision, consequences, and alternatives considered. The coding agent should respect these decisions; the methodology itself has its own ADRs in `decisions/`.

### Style and convention guides

Coding style, documentation style, naming conventions. Slow-changing but project-specific. Used by the coding agent and the workshopping agent.

## Project-specific knowledge files

Beyond methodology-level files, each project accumulates its own:

- Domain glossary (the project's own ubiquitous language)
- Domain models and data structures
- Integration specifications for external systems
- Security and compliance requirements
- Performance requirements

These are not part of Aim Praxis proper but are part of any project applying it.

## How agents use knowledge files

The pattern: an agent invoked for a task receives in its context the knowledge files relevant to that task. The workshopping agent gets the glossary, the BDD conventions, the relevant feature file context. The coding agent gets the architectural decisions, the style guide, the relevant code area.

The discipline is to keep each file focused. A knowledge file that tries to cover everything ends up being too long for context and is ignored. A knowledge file that covers one specific concern can be loaded when relevant.

## Knowledge file maintenance

Like skills, knowledge files require maintenance. When the project's facts change, the files change. When the methodology evolves, the methodology-level files evolve with it.

The discipline parallels the glossary discipline: every significant change goes through review; minor updates (typo corrections, clarifications) can be handled less formally.

## Knowledge file storage

In version control, alongside the rest of the project. Discoverable by path conventions. Loadable by agents into context when relevant.

For Aim Praxis specifically, the methodology's own knowledge files are in this repository. For a project applying Aim Praxis, the project's knowledge files are in the project's repository.

## What to read next

- `context/mcp-servers.md` — the queryable data layer
- `context/skills.md` — the procedural layer
- `context/boundary-specifications.md` — the constraints layer
