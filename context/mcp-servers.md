# MCP Servers

Model Context Protocol servers are the canonical mechanism by which agents access the compounding artifacts and operational stocks of an Aim Praxis implementation. This document specifies the servers the methodology requires.

## Why MCP

MCP gives agents typed, versioned access to systems they could not otherwise reach. Without MCP, agents work from whatever happens to be in their context window. With MCP, agents query authoritative stores and receive structured responses.

For Aim Praxis, MCP is what makes the compounding artifacts useful to agents rather than just to humans. A glossary in a markdown file is human-readable. The same glossary behind an MCP server is queryable by the workshopping agent, the coding agent, and the glossary agent itself.

## Required servers

### Glossary MCP

Exposes the ubiquitous language stock. Read operations: lookup term, list terms, suggest related terms. Write operations (proposal only): propose new term, propose update, propose deprecation. All writes go through human review before taking effect.

Schema: term, definition, examples, status (proposed/active/deprecated), last-modified, related-terms.

Used by: workshopping agent, coding agent, glossary agent, refinement agent, ATDD Guardian.

### Rework Register MCP

Exposes the unified failure history. Read operations: query by classification, query by time window, query by pattern. Write operations: record new failure, update remediation status. The PDSA agent reads from this; humans and observability agent write to it.

Schema: failure ID, immediate cause, classification (loop caught / loop should have caught), proposed remediation, status, related entries.

Used by: PDSA agent, refinement agent (for prior patterns), coding agent (for warnings).

### Lessons Learned MCP

Exposes the pattern library. Read operations: lookup by context, query by relevance, full-text search. Write operations: propose new lesson (typically from PDSA agent or human after retrospective).

Schema: pattern description, conditions of application, recommended response, evidence base, related rework entries.

Used by: refinement agent, workshopping agent, coding agent, PDSA agent.

### Process Capability MCP

Exposes the team's documented capability claims. Read operations: lookup capability for a given work type, list current claims. Write operations: propose capability update (typically from observed metrics).

Schema: capability statement, conditions, current performance distribution, last validation date.

Used by: ATDD Guardian (to check criteria against capability), BMC review (to check commitments against capability), refinement agent (to inform decomposition).

### Story Map MCP

Exposes the current story map state. Read operations: full map, by backbone, by release slice, by refinement status. Write operations: typically driven by human Story Mapping sessions; agents propose refinements that humans accept.

Schema: backbone tasks, refined tasks, release slices, status, refinement history.

Used by: refinement agent, workshopping agent, coding agent (for narrative context).

### Metrics Store MCP

Exposes the team's measurements at three levels: component output, system output, aim alignment. Read operations: query by metric, by time window, with correlation. Write operations: automated from observability infrastructure.

Schema: metric, value, time, category (component/system/aim), source.

Used by: BMC and VPC review processes, PDSA agent (for evidence base), observability agent (writes).

## Optional servers

### BMC MCP and VPC MCP

For teams that want their canvas documents to be agent-queryable rather than just human-readable. Useful for the market signal agent and customer research agent to tie findings to specific BMC/VPC elements.

### Architectural Decisions MCP

For projects with significant architectural history. Exposes ADRs queryable by topic and by date. Useful for the coding agent to respect prior decisions.

## Implementation notes

The methodology does not prescribe specific MCP server implementations. Some teams may build custom servers; others may use existing tools that expose MCP interfaces. The interface contracts are what matter; the implementation is local.

Mark Schilling has published one such server: `@schilling.mark.a/atdd-guardian`, which serves as both the ATDD gate and a reference for how MCP servers in Aim Praxis are structured.

## Versioning discipline

MCP servers in production should version their schemas. Agents written against version 1 should not break when version 2 is deployed. The same compounding-artifact discipline that applies to the data also applies to the interfaces.

## What to read next

- `context/skills.md` — the procedural knowledge that complements MCP-exposed data
- `context/knowledge-files.md` — the documents that travel with agents
- `agents/placement-philosophy.md` — how agents use these servers
