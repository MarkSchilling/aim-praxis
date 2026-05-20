# Agent Placement Philosophy

## The principle

Agents in Aim Praxis are placed at valves to widen them, at gates to enforce them, and at the rework register to learn from it. They are never placed at the aim, at acceptance, at fit validation, at release slicing, or at pattern interpretation — these remain human work.

This placement principle is what distinguishes Aim Praxis's approach to AI augmentation from approaches that treat agents as either threats or panaceas.

## Why placement matters

The conventional question is "should we use AI in software development?" — a yes/no question that produces unhelpful answers. The Aim Praxis question is "where, specifically, in the system should each kind of agent be placed?" — a structural question that produces actionable answers.

The placement determines what the agent does, what work it relieves humans of, and what work humans retain. Different placements produce different agentic systems.

## The four placement categories

### Agents at valves

Valves are the rates between stocks. An agent at a valve widens it — does the consistent, mechanical work that would otherwise constrain the rate.

The refinement agent operates at the detail-refinement valve, applying accumulated patterns to break down backbone tasks.

The workshopping agent operates at the story-workshopping valve, drafting Given-When-Then scenarios from refined tasks.

The glossary agent operates continuously across multiple valves, maintaining linguistic consistency in any text-producing flow.

### Agents at gates

Gates are deterministic checks at transition points. An agent at a gate enforces explicit criteria mechanically.

The ATDD Guardian operates at the ATDD gate, checking that acceptance criteria meet form requirements.

The CI/CD gate (the integration pipeline itself) enforces that integrated builds pass all required checks before deployment.

Gates do not exercise judgment; they enforce criteria. The deterministic property is what makes them trustworthy.

### Agents at sensing points

Sensing agents observe the environment for changes that might invalidate upstream assumptions.

The market signal agent watches competitive moves, regulatory changes, technology shifts, pricing dynamics — anything that might invalidate BMC assumptions.

The customer research agent synthesizes customer signals (support tickets, sales conversations, churn data) into patterns that might invalidate VPC fit assumptions.

The observability agent monitors production for issues that might invalidate the entire downstream chain.

Sensing agents produce findings for human interpretation. They do not decide what the findings mean.

### Agents at the rework register

The PDSA agent monitors the rework register for recurring patterns. It fires at the recurrence threshold (typically count ≥ 3) and proposes upstream changes.

The agent's output is a proposal, not a decision. Humans review proposals on a regular cadence (typically monthly).

The agent's role is pattern detection, which is well-suited to algorithmic processing. The interpretive judgment is human work.

## What agents never do

The methodology explicitly excludes agents from five categories of work:

**Aim setting.** What the product is for. The BMC layer's primary output. Setting an aim requires judgment about purpose that cannot be delegated.

**Fit validation.** Whether the value proposition actually serves the customer segment. Requires interpretation of qualitative customer signal that cannot be reduced to rules.

**Release slicing.** What ships first, what's in scope, what's deferred. Requires judgment about strategic priority and tradeoffs.

**Customer acceptance.** Whether the customer's actual problem was solved. The customer themselves is the judge; agents cannot stand in for them.

**Pattern interpretation.** What recurring failures mean. The PDSA agent detects patterns; humans interpret them. Different patterns require different responses, and the response choice requires understanding of context the agent cannot have.

## The escalation discipline

Every agent has explicit escalation triggers — conditions under which it must defer to humans rather than produce output. The escalation discipline is what keeps agents inside their competence.

Examples:

- The workshopping agent escalates when the refined task is too ambiguous to specify
- The coding agent escalates when acceptance tests are unclear or contradictory
- The PDSA agent escalates when a pattern is ambiguous rather than producing a confident proposal
- The customer research agent escalates when signals are conflicting rather than synthesizing them prematurely

An agent that always produces output trains the team to trust it. An agent that sometimes refuses trains the team to recognize when their inputs were inadequate. The refusal is a feature.

## The review discipline

Every agent output is reviewed. The review can be deterministic (a gate) or human (a person), but no agent output reaches a downstream stock without passing review.

This is the boundary that prevents the "chained agents" pathology — refinement agent feeds workshopping agent feeds coding agent, no human in the loop, the chain optimizes itself toward outputs that look correct to other agents and drifts from outputs humans would accept.

Every chain must be broken by a gate or a review. This sounds inefficient. It is the price of trust.

## Agents are workers

The methodology treats agents as workers, not as infrastructure. Each agent has:

- An operational definition (what it does)
- Inputs (what feeds it)
- Outputs (what it produces)
- Quality criteria (what counts as good output)
- Escalation triggers (when it must defer)
- Context requirements (what it needs to know)
- Boundary specifications (what it must not do)
- Performance metrics (how it is evaluated)

This is the same discipline applied to human workers. Agents that operate without these definitions drift; agents that operate with them are manageable.

## What this implies operationally

For Ship Audit specifically and for any application of Aim Praxis generally:

1. Build the agentic stack incrementally, in order of leverage. Foundational substrate first; gate agents second; valve agents third; sensing agents as needed.

2. Treat each agent as a product with version control, performance metrics, and explicit lifecycle.

3. Never chain agents without human or gate review between them.

4. Defend the human judgment zone actively. Pressure will mount to extend agents into judgment work. Resist.

5. Document agent behavior in operational definitions that can be reviewed and updated as the team learns what works.

## The Deming reading

Agents reduce common-cause variation in the work of the loops. They produce consistent outputs to consistent inputs, which is what you want for the mechanical aspects of the methodology. They do not reduce special-cause variation — the novel situations where judgment is required — because those are situations where the agent's training does not apply.

Place agents where common-cause variation dominates. Protect human judgment where special-cause variation dominates. The boundary between these is where the design of an agentic lifecycle succeeds or fails.

## What to read next

- `agents/refinement-agent.md`, `agents/workshopping-agent.md`, etc. — per-agent specifications
- `context/mcp-servers.md` — the substrate agents operate on
- `context/boundary-specifications.md` — the rails that keep agents safe
