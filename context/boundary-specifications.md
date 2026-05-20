# Boundary Specifications

Boundary specifications are the explicit prohibitions and escalation triggers that prevent agents from operating outside their competence. Every agent has boundary specifications; they are the rails that keep agents safe.

This document specifies the boundary discipline as a methodology-level concern, and lists boundaries that apply across multiple agents.

## Why boundaries matter

Agents without boundaries optimize for producing output. They will produce something for any input. The pathology is silent failure: an agent that should have refused produces a confident-looking answer that is wrong.

Boundary specifications convert silent failure into visible refusal. The agent that refuses produces no output but produces signal: "this input is outside what I can reliably handle." The team's response is to fix the input, not to consume the wrong output.

The discipline parallels Deming's stopping the line. Defects are caught at the source rather than passed downstream.

## Universal boundaries (apply to all agents)

### No modification of upstream stocks

Agents at any layer do not modify stocks at higher layers. The refinement agent does not modify the backbone. The workshopping agent does not modify refined tasks. The coding agent does not modify acceptance criteria. The PDSA agent does not modify the lessons-learned library directly.

The principle: upstream stocks belong to upstream loops. Downstream agents read from them but do not write to them. Writes happen through the layer that owns the stock.

### Explicit uncertainty markers

Agents that produce output must distinguish what they are confident about from what they are uncertain about. Silencing uncertainty produces overconfident output that humans cannot evaluate.

The standard pattern: confident output flows normally; uncertain output is flagged with explicit markers ("[uncertain: ...]") that humans can search for and review.

### No bypassing of downstream gates

Agents do not produce output that bypasses gates designed to catch their errors. The coding agent does not commit directly to main; output flows through CI/CD. The workshopping agent does not produce scenarios that skip ATDD Guardian; output flows through the gate.

### No making of decisions in the human judgment zone

Five categories of decision are explicitly off-limits to agents:
- Aim setting
- Fit validation
- Release slicing
- Customer acceptance
- Pattern interpretation

An agent that finds itself producing output in these categories should escalate. Producing output anyway violates the methodology's foundational division of labor.

## Layer-specific boundaries

### BMC layer

- Agents at this layer (market signal agent) sense but do not propose strategy changes
- Strategic decisions remain human
- BMC document modifications require human approval

### VPC layer

- Agents at this layer (customer research agent) synthesize but do not validate fit
- Fit decisions remain human
- VPC document modifications require human approval

### Story Mapping layer

- Refinement agent proposes; humans accept
- Release slicing is not agent work
- Story-map modifications go through human review

### BDD layer

- Workshopping agent drafts scenarios; humans review
- Glossary modifications go through human review
- Living documentation is generated, not authored

### ATDD layer

- ATDD Guardian is deterministic; it does not exercise judgment
- Acceptance criteria are negotiated with humans (and customers)
- Acceptance signoff is human work

### TDD layer

- Coding agent produces PRs; humans review and merge
- Architectural decisions outside the story's scope escalate
- Direct commits to main are prohibited

### CI/CD layer

- Observability agent observes; it does not take production action
- Rollback decisions are human
- Production access for the agent is read-only

## Escalation patterns

Every boundary has a corresponding escalation pattern. When the agent encounters a situation at or beyond a boundary, the agent:

1. Identifies the boundary that applies
2. Produces an explanation of why output cannot be safely produced
3. Suggests what would need to change for the agent to proceed
4. Routes the question to the appropriate human

The escalation is not failure; it is correct behavior. Teams that train agents to never escalate produce agents that fail silently.

## Boundary maintenance

Boundary specifications, like other compounding artifacts, accumulate over time. As the team learns what agents handle well and where they fail, the boundaries get refined.

Common pattern: a failure surfaces in the rework register; the PDSA agent detects a recurring pattern; analysis reveals the pattern stems from an agent producing output beyond its competence; the remediation is a new or strengthened boundary specification.

This is how the methodology becomes safer over time. The boundaries don't get written once and forgotten; they evolve with the team's experience.

## What to read next

- `agents/placement-philosophy.md` — the principles boundaries operationalize
- `context/mcp-servers.md`, `context/skills.md`, `context/knowledge-files.md` — what boundaries constrain
- `concepts/07-the-rework-register.md` — the source of boundary-update signal
