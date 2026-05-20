# Compounding Artifacts

## The concept

A compounding artifact is a slow-moving stock that accumulates value over time and improves the system's capacity to do its work. Compounding artifacts are what distinguish a learning system from a delivery system.

A team without compounding artifacts produces software but does not get better at producing software. Each cycle starts from approximately the same capability level. A team with compounding artifacts produces software and accumulates institutional knowledge, which improves the next cycle's quality and reduces the next cycle's effort. Over time, the team's capability compounds.

## The five compounding artifacts

Aim Praxis names five compounding artifacts as first-class system components:

**Ubiquitous language glossary.** The team's shared vocabulary, in version control, enforced at scenario-writing time. Each new term proposed in a story-mapping session goes through brief review and lands in the glossary before appearing in scenarios. The glossary grows steadily as the team's domain understanding deepens. Drawn from Domain-Driven Design via BDD.

**Lessons learned library.** The team's accumulated patterns of what works and what doesn't. Each entry captures a pattern observed in practice, the conditions under which it applies, and the recommended response. Queryable by both agents and humans. The library grows from the rework register through the PDSA agent's pattern detection.

**Process capability statement.** The team's documented self-model of what it can reliably deliver, with what variance, in what timeframe. Used by ATDD to validate that acceptance criteria are within capability. Used by the BMC layer to ensure value propositions do not promise more than the system can deliver. The statement is updated as the team's actual capability shifts.

**Rework register.** The team's classified failure history. Each entry records what failed, which loop caught it, which loop should have caught it, and what change might prevent recurrence. The diagnostic instrument for system health. The PDSA agent monitors the register for recurring patterns.

**Metrics store.** The team's measurements at three levels: component output (stories shipped, tests passed), system output (working software in production), and aim alignment (user outcomes, business metric impact). The metrics store is queryable; the metrics are correlated; trends are visible across time.

## Why these specifically

Each of the five compounding artifacts addresses a different category of accumulation:

- The glossary accumulates **language** — how the team talks about its work
- Lessons learned accumulate **patterns** — how the team recognizes situations
- Process capability accumulates **self-knowledge** — what the team can reliably do
- The rework register accumulates **failure data** — what went wrong and where
- The metrics store accumulates **measurement** — what the system actually produces

Together, these five categories cover the team's institutional memory comprehensively. A team that maintains all five has a much richer self-model than a team that maintains none.

## How compounding works

The compounding property is not automatic. It requires active maintenance and active use.

**Active maintenance.** Each artifact has dedicated maintenance responsibility. The glossary agent monitors for new terms and proposes additions. The PDSA agent monitors the rework register for patterns. The metrics store is updated by the observability agent. Without maintenance, the artifacts decay.

**Active use.** Each artifact must be consulted in the work it informs. The workshopping agent queries the glossary when drafting scenarios. The refinement agent queries lessons learned when breaking down tasks. The BMC review consults the process capability statement when setting commitments. Without use, the artifacts become museum pieces.

The compounding effect comes from the cycle: artifact gets used, work produces new observations, observations get added to the artifact, the enriched artifact gets used again. Each cycle leaves the artifact slightly richer than before.

## The moat property

Compounding artifacts are the team's most defensible asset over the long term. Competitors can copy practices; they cannot copy accumulated context.

A new competitor can adopt Aim Praxis in a quarter. They cannot produce the glossary your team has built over two years of domain work. They cannot reproduce the lessons your team has captured from production incidents. They cannot reverse-engineer the process capability your team has documented. The artifacts are a moat that grows automatically with time, as long as maintenance is preserved.

This has strategic implications. The team's competitive advantage comes increasingly from the compounding artifacts and decreasingly from any individual practice or technology choice. Protecting and investing in the artifacts is therefore a strategic priority, not just an operational nice-to-have.

## Anti-patterns

**Documentation that nobody updates.** Many teams have wiki pages they call "lessons learned" that contain three entries from 2019. This is not a compounding artifact. A real lessons-learned library has entries from this month; the absence of recent entries is a signal that the artifact is dead.

**Glossaries that nobody enforces.** A glossary that exists but is not enforced at scenario-writing time will drift. Scenarios will use terms inconsistently; the glossary will be ignored; new terms will accumulate informally. The enforcement mechanism (the glossary agent or its human equivalent) is what makes the glossary actually compound.

**Metrics that nobody acts on.** A metrics store full of measurements that no one consults is overhead, not infrastructure. The compounding property requires that metrics be queried, correlated, and used to inform decisions. Otherwise the metrics are theater.

**Rework registers that classify everything as "developer error."** A register that attributes every failure to individual mistakes rather than system structure is using the artifact wrong. The point is to identify system-level patterns, which requires honest classification of where in the system the failure originated.

## Compounding artifacts as agent context

The compounding artifacts are also the substrate that makes agents effective. An agent without access to the glossary cannot enforce ubiquitous language. An agent without access to lessons learned cannot apply prior patterns. An agent without access to the rework register cannot detect recurring failures.

Each compounding artifact should be exposed via an MCP server so agents can query it programmatically. This is the integration that turns the artifacts from human-only references into shared resources between human and agent work.

## What to read next

- `concepts/07-the-rework-register.md` — the artifact at the center of the learning loop
- `context/mcp-servers.md` — how to expose the artifacts to agents
- `practices/bdd.md` — the practice that maintains the glossary most directly
