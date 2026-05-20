# System Archetypes

System archetypes are recurring patterns of system behavior that produce predictable outcomes. Recognizing archetypes is how practitioners diagnose pathologies and intervene effectively.

This document catalogs the archetypes most relevant to Aim Praxis.

## Pack rat

**Pattern:** Inflow rate to a planning stock (typically the story map) exceeds outflow rate. The stock accumulates faster than the team can drain it.

**Symptoms:**
- Backlog grows quarter over quarter without corresponding velocity increase
- Discovery and brainstorming sessions feel productive
- Items in the backlog get stale; nobody can summarize what's in it
- Periodic backlog grooming sessions become Sisyphean

**Cause:** Inflows feel generative and morally good; outflows like scope depletion feel like failure. The inflow valves run wide-open by default; the outflow valves stay throttled.

**Intervention:** Throttle inflows (especially blue-sky ideation) or widen outflows (especially scope depletion). Treating scope depletion as a legitimate first-class outflow is the key cultural shift.

## Inner-loop dominance

**Pattern:** Under pressure, teams collapse toward inner loops (TDD, CI/CD) and let outer loops (Story Mapping, BMC) atrophy.

**Symptoms:**
- Deploy frequency is high and growing; outer-loop ceremonies happen rarely or not at all
- BMC and VPC documents haven't been updated in 18 months
- Story Mapping sessions are remembered as "the workshop we did once"
- Engineering can describe what they're building this sprint but not what it's for
- Customer outcomes are not measured; deployment count is the primary success metric

**Cause:** Inner-loop work is visible and rhythmic; outer-loop work is invisible and sporadic. Career incentives reinforce visible output. Under pressure, organizations cut what feels like overhead.

**Intervention:** Outer loops must be calendared, attended, and protected. Make outer-loop work visible (Story Mapping sessions on the calendar, BMC review with required attendance). Make outer-loop output legible (the methodology repository, decisions documented, lessons learned tracked).

## Premature drainage

**Pattern:** Outflows run ahead of inflows. The stock empties; the team ships quickly but with poor shared understanding.

**Symptoms:**
- Stories ship that nobody can explain why they shipped
- Customer-facing artifacts contradict each other
- Engineers work on tasks they don't understand the purpose of
- Rework rate is high because work didn't reflect actual intent

**Cause:** Pressure to ship overrides the discipline of building shared understanding first. The opposite of pack rat — both are failure modes.

**Intervention:** Slow down. Story Mapping is upstream of delivery for a reason. Scenario authoring is upstream of code for a reason. The healthy state is matched rates with adequate stock level for shared understanding to remain coherent.

## Pathological reinforcing loop (death spiral)

**Pattern:** A reinforcing loop running in the wrong direction. Small departures amplify into large ones.

**Examples:**

- **Disappointment death spiral:** Failed promises create new pains, which produce detractors, which damage reputation, which reduces acquisition, which forces shortcuts to maintain revenue, which produces more failed promises.

- **Rework death spiral:** Defects in production produce rework, which displaces new work, which slows feature delivery, which creates pressure for shortcuts, which produces more defects.

- **Trust death spiral:** Team trust degrades, communication suffers, mistakes increase, blame is assigned, trust degrades further.

**Symptoms:** Things are getting worse. The team has noticed; interventions don't seem to help; each fix creates new problems.

**Intervention:** Find the loop structure and break the reinforcement. "Try harder" doesn't work because the loop's gain is what amplifies the effort into damage. The intervention is structural — change what feeds the loop, change what the loop produces, or change the connection between them.

## Fixes that fail

**Pattern:** Quick fixes that address symptoms produce delayed consequences that make the underlying problem worse.

**Examples:**

- Bypass the ATDD gate "this one time" to ship faster → creates rework that displaces planned work → more pressure to bypass gates → quality erodes
- Skip the BDD scenario authoring because "we know what we're building" → produces ambiguity in implementation → causes acceptance disputes → more rework

**Symptoms:** Recurring problems. The team has dealt with the same issue multiple times in different forms.

**Intervention:** Resist the quick fix. The cost of the discipline is less than the cost of accumulated bypass. The rework register is the diagnostic — recurring failures of similar type signal a fix-that-fails pattern.

## Shifting the burden

**Pattern:** A symptomatic solution displaces the fundamental solution. The symptomatic solution works in the short term but erodes the capacity to apply the fundamental solution.

**Examples:**

- Hire more engineers to ship more features rather than improving the process → the larger team produces more rework with the same broken process → "we need more engineers"
- Use AI agents to bypass the discipline of clear specifications → the agents produce code that approximately matches intent → "we need better agents"

**Symptoms:** Repeated escalation of the symptomatic solution. The fundamental solution is talked about but not invested in.

**Intervention:** Name the displacement explicitly. The discipline is to invest in the fundamental solution even when the symptomatic solution would feel more productive. This is hard precisely because the symptomatic solution does work in the short term.

## Limits to growth

**Pattern:** A reinforcing loop produces growth until some external constraint slows it. Continued investment in the loop produces no continued growth.

**Examples:**

- Adding more ideation produces no more deliverable software once refinement is the constraint
- Improving CI/CD speed produces no more user value once acceptance ambiguity is the constraint
- Expanding marketing produces no more revenue once value proposition fit is the constraint

**Symptoms:** Investments stop producing returns. The growth slope flattens.

**Intervention:** Find the constraint. Apply the Theory of Constraints discipline — identify, exploit, subordinate, elevate. Pumping the previously-effective lever harder is wasted effort; the leverage has moved elsewhere.

## Tragedy of the commons (within the team)

**Pattern:** A shared resource gets degraded by individual rational behavior. Each individual maximizes their own use; the shared resource depletes.

**Examples:**

- The team's attention budget gets fragmented by each subteam demanding meetings
- The codebase gets degraded by each engineer optimizing for their own velocity
- The glossary gets confused by each subteam introducing their own terms

**Symptoms:** Shared resources are degrading despite no individual doing anything wrong.

**Intervention:** Make the shared resource explicit and assign maintenance ownership. The glossary agent owns glossary maintenance. The system steward owns system health. Without explicit ownership, the commons degrade by default.

## Diagnostic discipline

The discipline of using archetypes:

1. **Observe the pattern.** Things are getting worse, or stuck, or in some recognizable failure mode.
2. **Match to an archetype.** Which of the known patterns does this resemble?
3. **Find the loop structure.** The archetype names the structure; the team identifies its specific instance.
4. **Intervene at the structure.** Not at the symptom.
5. **Verify the intervention.** Did the pattern change?

This is essentially the PDSA cycle applied to system pathologies. It is also Deming's discipline of distinguishing common-cause from special-cause variation applied to behavioral patterns.

## What to read next

- `concepts/03-feedback-loops.md` — the underlying mechanics
- `system/integrated-system.md` — the system in which archetypes manifest
- `operations/operationalization-sequence.md` — how to avoid creating archetypes during adoption
