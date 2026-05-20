# Feedback Loops

## The concept

A feedback loop is a cycle in which outputs of a system become inputs to itself. Loops are what make systems behave as systems rather than as collections of parts. Without feedback, a system runs once and stops. With feedback, the system's behavior depends not just on its inputs but on its own prior outputs.

Two types of feedback loops produce qualitatively different behaviors.

**Reinforcing loops** amplify. A small change grows. Compound interest is a reinforcing loop — interest on principal becomes additional principal, which produces more interest. Word-of-mouth growth is reinforcing — happy customers tell friends who become customers who tell more friends. Reinforcing loops produce exponential behavior, in either direction. A reinforcing loop running in the wrong direction is a death spiral.

**Balancing loops** stabilize. Departures from a target produce corrections back toward the target. A thermostat is a balancing loop — temperature departures trigger heating or cooling that returns the room to the setpoint. The human body's homeostasis is dozens of balancing loops operating simultaneously. Balancing loops produce stable equilibria.

A system's long-term behavior is determined by which loops dominate. A system with strong reinforcing loops grows or collapses. A system with strong balancing loops oscillates around an equilibrium. A system with both can exhibit complex behavior — growth phases, stabilization, decline — depending on which loops are active when.

## Why loops matter for software development

Most software development thinking is linear: requirements lead to design lead to code lead to tests lead to deployment. This linear view misses the feedback loops that actually determine team behavior.

Some feedback loops in a typical development team:

- The growth loop in the BMC: revenue funds key activities, which improve the value proposition, which attracts customers, which generates revenue. Reinforcing.
- The disappointment loop in the VPC: failed promises create new pains, which produce detractors, which damage reputation, which constrains growth. Reinforcing in the wrong direction.
- The rework loop: defects in production produce rework, which displaces new work, which slows feature delivery, which creates pressure for shortcuts, which produces more defects. Reinforcing in the wrong direction.
- The learning loop: rework feeds the lessons-learned stock, which improves refinement quality, which reduces future rework. Balancing (counteracts the rework loop).

The team's actual behavior emerges from the interactions of all these loops. A team with strong learning loops and weak rework loops improves over time. A team with strong rework loops and weak learning loops degrades over time. The same team with the same people can be on either trajectory depending on which loops are active.

## Loops in Aim Praxis

The methodology contains explicit feedback loops at multiple cycle times:

**BMC layer.** Three loops: growth (reinforcing), efficiency (balancing), learning (reinforcing when healthy, broken when stale).

**VPC layer.** Three loops: relief (reinforcing — pain drained creates retention), expectation (balancing — gains habituate, devaluing existing value), disappointment (reinforcing in the wrong direction — failed promises create detractors).

**Story Mapping layer.** The pack rat archetype is a reinforcing loop running in the wrong direction: when discovery feels good, more discovery happens, which fills the map faster than it drains, which produces backlog that feels like progress but isn't.

**Seven-layer integration.** Two upward feedback paths: value capture (right-side) returns revenue to the BMC; learning (left-side) returns observed outcomes to the VPC. The rework register is a third loop, closing the learning path through the compounding artifacts.

**PDSA cycles.** Every loop in Aim Praxis is a PDSA cycle at its own time scale. Plan an experiment (define the work), Do the experiment (perform it), Study the results (check what happened), Act on what was learned (update upstream stocks). Nested PDSA cycles at minute, day, week, month, and quarter scales.

## Recognizing loop pathologies

Several patterns of loop dysfunction recur across teams:

**Broken learning loop.** The team produces outputs but never gets feedback on whether the outputs served their intended purpose. Working software ships; nobody measures user outcomes. The reinforcing loop that would normally improve future work has no signal to reinforce against.

**Reinforcing-in-the-wrong-direction loops.** Pack rat in story mapping. Disappointment in VPC. Rework displacement in development. Each is a reinforcing loop producing accumulating damage. The intervention is not to "try harder"; it is to identify the loop structure and break the reinforcement.

**Missing balancing loops.** Growth without efficiency control produces unsustainable expansion. Learning without acting on lessons produces accumulated knowledge that no work benefits from. The balancing function has to exist somewhere; if it does not, the reinforcing loops run unchecked.

**Loop time-scale mismatch.** Fast inner loops with slow outer loops produces inner-loop dominance. The team optimizes what it can see and ignores what it cannot. The fix is not to make outer loops faster (they have to be slow for their function) but to defend the cadence at which they run.

## The five-loop architecture as a designed system

The seven practices of Aim Praxis, arranged as nested loops at different cycle times, form a designed system of feedback. Each loop catches errors at its own time scale that no other loop can see. Together they catch errors across seven orders of magnitude of time.

This is not an accident of how the practices evolved. Each practice was designed (by different people, at different times) to address a specific class of error. Aim Praxis recognizes that these classes of error are organized by cycle time, and that the practices are therefore mutually reinforcing rather than substitutable.

A team using only TDD has a strong inner balancing loop but no outer reinforcing loops. A team using only Story Mapping has rich upstream conversation but no mechanism for converting that into reliable execution. The full seven-loop architecture is the answer to "what would a complete feedback system for software development look like?"

## Loops and Deming's PDSA

Deming's PDSA is the canonical statement of a learning feedback loop. Plan a theory; Do an experiment; Study the results; Act on what was learned. The loop closes through "Act" updating the next "Plan."

Aim Praxis treats every loop as a PDSA cycle. At the BMC layer, plan a strategy; do a quarter's work; study the metrics; act on what was learned in the next strategy session. At the TDD layer, plan a test; do the implementation; study the test result; act on what was learned in the next test. Same logical structure; vastly different time constants.

The implication: PDSA is not a separate practice to bolt on. It is the underlying structure of every practice in the methodology. The discipline of running each loop as a deliberate PDSA cycle — not just as a habitual activity — is what makes the loops actually produce learning.

## What to read next

- `concepts/05-cycle-times.md` — why loops at different time scales catch different errors
- `concepts/06-compounding-artifacts.md` — what accumulates when learning loops work
- `system/archetypes.md` — recurring loop patterns and how to recognize them
