# Aim Praxis: The Methodology

This is the master document of Aim Praxis. It synthesizes the foundational concepts, the seven practices, the integrated system view, and the agentic augmentation into a single coherent statement of what the methodology is and how it works.

For deeper treatment of any specific topic, see the linked documents in `concepts/`, `practices/`, `system/`, and `agents/`.

## The central claim

Software development is a system. Like any system, it has stocks (accumulations of information and work), flows (rates of change between stocks), feedback loops (cycles where outputs become inputs), and a system aim (the purpose the system serves). The behavior a software development team produces — both the software it ships and the rate at which it ships — emerges from the structure of this system, not from the individual capabilities of its members.

This claim has practical consequences. If 94% of failures belong to the system rather than the individual, as Deming argued, then improving software development requires improving the system, not exhorting individuals to try harder. Aim Praxis is the discipline of treating software development this way.

## The systems-thinking foundation

Aim Praxis rests on five concepts from systems thinking, each developed in its own document in `concepts/`:

**Stocks and flows.** Every artifact in a development process is either a stock (something that accumulates) or a flow (a rate at which something changes). A story map is a stock; refinement is a flow. Acceptance criteria are a stock; workshopping is a flow. Code is a stock; commits are a flow. Recognizing this distinction is the first move of systems analysis.

**Aging chains.** Information matures through a series of stocks, each representing a higher-resolution or more-refined state. Raw ideas mature into backbone tasks mature into refined tasks mature into acceptance-ready stories mature into code mature into deployed software. The maturation happens through valves (controlled rates of transformation). The slowest valve sets the system's throughput.

**Feedback loops.** Outputs of the system become inputs to itself. Reinforcing loops amplify; balancing loops stabilize. Healthy systems have appropriate feedback at every cycle time. Pathological systems have feedback that produces unintended behavior — pack rat syndrome, inner-loop dominance, fixes that fail.

**Cycle times.** Different parts of a system operate at different rates. A healthy system has variation reduction at every cycle time, from seconds (CI/CD) to quarters (BMC review). A system that operates at only one cycle time catches only one class of error.

**Compounding artifacts.** Some stocks grow slowly over time and improve the system's capacity to do its work. A ubiquitous language glossary, a lessons-learned library, a process capability statement, a rework register. These are what make a learning system different from a delivery system.

## The Deming foundation

Aim Praxis equally rests on four concepts from Deming's System of Profound Knowledge:

**Appreciation for a system.** A system is more than the sum of its parts; its behavior emerges from the relationships between parts. Optimizing individual parts without understanding the whole produces local improvements that degrade global performance.

**Knowledge of variation.** Variation in outputs has two causes: common cause (built into the system) and special cause (external disturbances). The two require different responses. Reacting to common-cause variation as if it were special cause makes the system worse.

**Theory of knowledge.** Improvement requires prediction; prediction requires theory; theory must be tested through PDSA (Plan-Do-Study-Act) cycles. Operational definitions make theory testable.

**Psychology.** People are intrinsically motivated; extrinsic motivators (rewards, punishments) degrade intrinsic motivation. The system should be designed so that doing good work and doing the right work are the same thing.

## The seven practices

Aim Praxis integrates seven practices, each operating at its own cycle time on its own stocks. See `practices/` for the detailed treatment of each.

**Business Model Canvas (BMC)** — weeks to quarters. Operates on the stocks that define what the business is: aim and segments, value flows, revenue and cost. Catches direction error — the product is heading the wrong way.

**Value Proposition Canvas (VPC)** — weeks to months. Operates on the supplier-customer interface: customer jobs, pains and gains, supplier products, pain relievers, gain creators. Catches fit error — the product solves the wrong problem for the segment.

**Story Mapping** — weeks. Operates on the narrative structure: backbone tasks, refined tasks, release slices. Catches scope error — the work is structured in a way that delays value delivery.

**Behavior-Driven Development (BDD)** — days to weeks. Operates on behavioral specification: examples, scenarios, features, ubiquitous language. Catches specification drift — the system used to do X, now it does Y, and nobody noticed.

**Acceptance Test-Driven Development (ATDD)** — days. Operates on story-level acceptance: criteria, acceptance tests, demonstrably-complete work. Catches completion ambiguity — engineering thinks it is done, the customer does not.

**Test-Driven Development (TDD)** — minutes. Operates on unit-level design: failing tests, passing tests, refactored code. Catches design degradation — code works but is hard to change.

**Continuous Integration / Continuous Deployment (CI/CD)** — seconds to hours. Operates on integration and deployment: integrated builds, deployed artifacts, working software. Catches integration failure — code works alone but not together.

## The integration

The seven practices are not independent. Each layer's output is the next layer's input. BMC's value flows define VPC's customer jobs. VPC's validated fit defines Story Mapping's user journey. Story Mapping's refined tasks become BDD's examples. BDD's scenarios become ATDD's acceptance criteria. ATDD's executable gates become TDD's coding targets. TDD's clean code becomes CI/CD's integration input. CI/CD's working software produces user outcomes.

Two upward feedback paths close the system. Value capture returns revenue to the BMC layer, funding continued operation. Learning returns observed outcomes to the VPC layer, validating or invalidating fit assumptions.

A third feedback path runs through the rework register. Failures from every layer flow into a unified register, classified by which loop caught them and which should have. The PDSA Improvement Agent monitors the register for recurring patterns and proposes upstream changes.

See `system/integrated-system.md` for the full integration with diagrams.

## The agentic augmentation

Aim Praxis is designed for an era when AI agents can perform consistent, mechanical work that would otherwise require human attention. The methodology places agents at specific points where they widen valves, enforce gates, or learn from accumulated artifacts. It explicitly preserves human judgment at the points where judgment about purpose is required.

The placement principles:

- Agents at valves to widen them (refinement agent, workshopping agent)
- Agents at gates to enforce them (ATDD Guardian, CI/CD gates)
- Agents at the rework register to learn from it (PDSA agent)
- Agents at observation points to sense changes (market signal agent, customer research agent, observability agent)
- Agents inside specific work-in-progress stocks (coding agent, glossary agent)

The exclusions:

- No agent at aim setting — humans decide what the product is for
- No agent at fit validation — humans interpret whether the proposition serves the customer
- No agent at release slicing — humans decide what ships first
- No agent at customer acceptance — humans confirm that the customer's actual problem was solved
- No agent at pattern interpretation — humans decide what failures mean

See `agents/placement-philosophy.md` and the per-agent documents for detailed specifications.

## The compounding artifacts

Aim Praxis treats certain stocks as the system's institutional memory and capacity-building infrastructure:

- **Ubiquitous language glossary** — the team's shared vocabulary, maintained in version control, enforced at scenario-writing time
- **Lessons learned** — the team's accumulated patterns of what works and what doesn't, queryable by agents and humans
- **Process capability statement** — the team's documented self-model of what it can reliably deliver
- **Rework register** — the team's classified failure history, the diagnostic instrument for system health
- **Metrics store** — the team's measurements at three levels: component output, system output, aim alignment

These artifacts grow slowly but compound. A team that operates Aim Praxis for two years has accumulated context that a new team cannot replicate without doing the same work. This compounding is the methodology's deepest contribution to a team's long-term capacity.

## The recursive property

Aim Praxis applies to itself. The methodology is a system; its own development is governed by the methodology's principles. The repository at `aim-praxis/` is the methodology's own primary stock. The lessons learned from applying the methodology accumulate in its lessons-learned document. The decisions about the methodology's evolution are tracked in architecture decision records. The methodology improves through PDSA cycles applied to itself.

This recursion is what distinguishes Aim Praxis from methodologies that are static prescriptions. It is a living system that updates itself based on its own application.

## What to read next

For a new reader, the natural next documents are:

1. `docs/lineage.md` — the intellectual genealogy of the methodology
2. `concepts/04-the-seven-layers.md` — the structural claim made concrete
3. `system/integrated-system.md` — the full integrated picture
4. `operations/operationalization-sequence.md` — how to actually adopt the methodology

For someone evaluating the methodology against alternatives:

- `decisions/adr-001-naming-the-methodology.md` — why "Aim Praxis" and not "Agile Plus" or similar
- `practices/bdd.md` and `practices/tdd.md` — how Aim Praxis treats two practices most teams think they already do
- `agents/placement-philosophy.md` — how Aim Praxis differs from "let AI do everything" approaches
