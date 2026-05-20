# Glossary: The Ubiquitous Language of Aim Praxis

This is the canonical vocabulary of the methodology itself. Every term here has a specific meaning within Aim Praxis, and that meaning is what the methodology means by the term wherever it appears.

This glossary is itself a compounding artifact — it grows as the methodology develops, and it is the reference that all other documents in the repository should be consistent with.

## Core terms

**Aim**
The purpose a system serves. In Aim Praxis, every loop is judged by alignment with the system aim. Drawn from Deming. Distinct from "goal" (a specific target) or "objective" (a measurable outcome) — the aim is what the system is *for*.

**Aging chain**
A sequence of stocks where information matures through transformation. Each stock represents a higher-resolution or more-refined state of the same underlying information. The story map is an aging chain (raw ideas → backbone → refined tasks → release slices). The seven-layer methodology is an aging chain at a higher level.

**Agent**
A software component that performs work autonomously within boundaries defined by the system. Distinguished from a tool (which a human directs) by its capacity to operate within an operational definition and produce reviewable outputs.

**Archetype**
A recurring pattern of system behavior that produces predictable outcomes. Pack rat, inner-loop dominance, limits to growth, fixes that fail, shifting the burden. Recognizing archetypes is how practitioners diagnose system pathologies.

**Boundary**
The line distinguishing what is inside the system (and therefore subject to intervention) from what is outside (and therefore treated as input or output). Boundaries are deliberate analytical choices, not natural facts.

**Cadence**
The rhythm at which a loop runs. Different loops have different cadences. CI/CD is continuous; TDD is per-change; ATDD is per-story; BDD is per-feature; Story Mapping is calendared (every N weeks); BMC review is quarterly. The set of cadences across all loops is the methodology's calendar.

**Common-cause variation**
Variation built into the system, present in the normal operation of the system. Deming's term. Responding to common-cause variation as if it were special cause makes the system worse.

**Compounding artifact**
A slow-moving stock that accumulates value over time and improves the system's capacity to do its work. Glossary, lessons learned, process capability, rework register, metrics store. The artifacts that distinguish a learning system from a delivery system.

**Cycle time**
The period required for one full traversal of a loop. Multi-time-scale systems have loops at multiple cycle times. A healthy system has appropriate variation reduction at every cycle time it operates at.

**Endogenous**
Inside the system boundary; subject to the team's intervention. Distinguished from exogenous (outside the boundary; treated as input or output). The endogenous/exogenous distinction depends on where the boundary is drawn.

**Exogenous**
Outside the system boundary; treated as input or output rather than subject to intervention. User outcomes, market signals, regulatory changes are typically exogenous for a development team.

**Feedback loop**
A cycle where outputs of the system become inputs to itself. Reinforcing loops amplify; balancing loops stabilize. Healthy systems have appropriate feedback at every cycle time.

**Flow**
A rate at which something moves between stocks or transforms within a stock. Flows have direction and magnitude. Flows are governed by valves.

**Gate**
A deterministic check at a transition point that enforces explicit criteria. Gates pass or fail mechanically based on criteria; they do not exercise judgment. ATDD Guardian is a gate. CI/CD's build pipeline is a gate.

**Human judgment zone**
The set of decisions in the methodology that must remain human: aim setting, fit validation, release slicing, customer acceptance, pattern interpretation, and review of agent outputs. The methodology's design preserves human judgment at these points specifically.

**Inner loop**
A loop with a short cycle time, typically operating on detailed work. TDD and CI/CD are inner loops. Inner loops catch correctness errors but not direction errors.

**Inner-loop dominance**
The pathology in which a team collapses toward inner loops (because they feel productive) and lets outer loops atrophy. The most common failure mode of teams that have nominally adopted the full seven-practice stack.

**Lessons learned**
A compounding artifact: the team's accumulated patterns of what works and what does not. Queryable by agents (via MCP server) and humans. Distinct from documentation in that it captures *patterns*, not procedures.

**Loop**
See "feedback loop."

**Outer loop**
A loop with a long cycle time, typically operating on strategy or direction. BMC and VPC are outer loops. Outer loops catch direction errors but not unit-level errors.

**Pack rat**
A system archetype: the story map (or any planning artifact) accumulates discretionary items faster than the team can refine and deliver them. The level rises; throughput does not. Named for the hoarding pattern that produces the same outcome in households.

**PDSA cycle**
Plan-Do-Study-Act. Deming's name for the basic cycle of learning. Plan an experiment; Do the experiment; Study the results; Act on what was learned. Every loop in Aim Praxis is a PDSA cycle at its own time scale.

**Phronesis**
Practical wisdom — the capacity to act well in specific situations where no rule could specify in advance what to do. Aristotle's term. The virtue preserved in the human judgment zone.

**Praxis**
Practice informed by theory; action emerging from understanding; disciplined practice that integrates intellectual rigor with operational discipline. The methodology's name reflects this character.

**Process capability**
A compounding artifact: the team's documented self-model of what it can reliably deliver, with what variance, in what timeframe. Used by ATDD and BMC layers to ensure promises do not exceed capability.

**Refined task**
A backbone task that has been decomposed into sub-tasks, exceptions, and details. The output of detail refinement. The input to scenario authoring.

**Rework register**
A compounding artifact: the team's classified failure history. Each entry records what failed, which loop caught it, which loop should have caught it, and what change might prevent recurrence. The diagnostic instrument for system health.

**Skill**
Procedural knowledge captured in a form usable by agents. A skill says "when asked to do X, follow this procedure, consult these resources, produce output in this form." Distinct from a tool (which provides capability) and from knowledge (which provides facts).

**Sopk**
System of Profound Knowledge. Deming's four-lens framework: appreciation for a system, knowledge of variation, theory of knowledge, psychology.

**Special-cause variation**
Variation caused by something outside the normal operation of the system. Deming's term. Responding to special-cause variation as if it were common cause misses the opportunity to learn from the disturbance.

**Stock**
An accumulation of something in the system. Stocks have levels that change over time. Information stocks (glossary, lessons learned), work stocks (in-progress code), and value stocks (working software) are all stocks. Distinct from flows, which are rates.

**System aim**
See "aim."

**Trusted system gate**
A gate that enforces criteria the team has agreed to trust. ATDD Guardian is a trusted system gate for acceptance criteria. The CI/CD pipeline is a trusted system gate for integration.

**Ubiquitous language**
A compounding artifact: the shared vocabulary of the team and its domain. Maintained in version control, enforced at scenario-writing time, queryable by agents. Drawn from domain-driven design via BDD.

**Valve**
A regulatable rate; the leverage points in a stock-and-flow system. Inflows and outflows are governed by valves. Most agent placements in Aim Praxis are at valves, widening them by handling consistent work mechanically.

## Practice-specific terms

**Acceptance criteria**
The conditions under which a story is considered complete by the customer. Negotiated between product, engineering, and customer; verified by acceptance tests. The unit of agreement at the ATDD layer.

**Acceptance test**
An executable test corresponding to acceptance criteria. Passes when the criteria are met; fails when they are not. The bridge between customer agreement and engineering verification.

**Backbone**
The high-level activities and tasks that tell the user's journey through the product. The structural ribs of a story map. Drawn from Patton.

**BDD scenario**
A structured behavioral specification in Given-When-Then form. Given specifies preconditions; When specifies the action; Then specifies the observable outcome. Drawn from North.

**Customer segment**
A group of customers with shared jobs, pains, and gains. The unit of analysis at the VPC layer. Distinct from "user" — segments are economic units, users are interaction units.

**Examples**
Concrete instances of behavior gathered from conversation. The raw material of BDD. Drawn from Adzic's "specification by example."

**Gain creator**
A supplier-side valve that fills a customer's gain stock faster than the customer could fill it alone. Drawn from VPC.

**Job to be done**
What a customer is trying to accomplish. Continuous demand on the customer's attention and resources. The customer-side flow that fills either the pain stock or the gain stock depending on how well the job goes.

**Pain reliever**
A supplier-side valve that drains a customer's pain stock faster than the customer could drain it alone. Drawn from VPC.

**Release slice**
A coherent subset of the story map that can be shipped as a usable product. The MVP, the walking skeleton, the next release. Drawn from Patton.

**Story**
A unit of customer-facing work, typically expressed as "as a [user], I want [capability], so that [benefit]." The unit of work at the ATDD layer. Distinct from a task (engineering unit) or a feature (capability grouping).

**Value proposition**
The supplier-side description of what the product offers. Composed of products and services, pain relievers, and gain creators. The central stock of the VPC.

## Agent-specific terms

**Boundary specification**
The explicit prohibition and escalation rules that prevent an agent from operating outside its competence. Every agent has boundary specifications; they are the rails that keep the agent safe.

**Coding agent**
The agent that operates inside the work-in-progress stock at the TDD layer. Writes code against acceptance tests. Output is a candidate, not a commit. Constrained by ATDD gate upstream and CI/CD gate downstream.

**Customer research agent**
The sensing agent at the VPC layer. Monitors customer signals (support tickets, sales conversations, churn data) for patterns that might invalidate fit assumptions. Output is findings for human interpretation.

**Glossary agent**
The maintenance agent for the ubiquitous language. Monitors scenarios and documents for terms not in the glossary, proposes additions, flags inconsistent usage. Output is proposed glossary diffs.

**Market signal agent**
The sensing agent at the BMC layer. Monitors competitive moves, regulatory changes, technology shifts, and pricing dynamics. Output is findings for human interpretation.

**MCP server**
Model Context Protocol server. The canonical mechanism for tool context — gives agents access to systems they could not otherwise reach. ATDD Guardian is published as an MCP server.

**Observability agent**
The agent at the CI/CD layer that monitors production. Watches error rates, performance, user behavior, business metric impact. Closes the learning loop by feeding observations back upstream.

**PDSA agent**
The pattern-detection agent that monitors the rework register. Fires at recurrence threshold (count ≥ 3). Output is proposals for upstream changes, reviewed by humans.

**Refinement agent**
The agent at the detail refinement valve. Takes unrefined backbone tasks and proposes sub-tasks, exceptions, and details. Constrained by lessons learned and glossary. Output is reviewable refinement.

**Workshopping agent**
The agent at the story workshopping valve. Takes refined tasks and drafts Given-When-Then scenarios. Constrained by glossary and BDD conventions. Output is scenarios for human review.

## How to extend this glossary

When a new term appears in methodology work, the question is whether it has a specific meaning within Aim Praxis or whether it inherits its general English meaning. If specific, add it here. If general, do not — the glossary is for terms that carry methodology-specific meaning.

The discipline: when in doubt, define. A glossary entry that exists is cheap to consult. A missing glossary entry produces inconsistent usage that compounds over time.
