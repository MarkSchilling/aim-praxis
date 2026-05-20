# Aging Chains

## The concept

An aging chain is a sequence of stocks where information matures through transformation. Each stock represents a higher-resolution or more-refined state of the same underlying information. The valves between stocks are the transformations that convert one state to the next.

The canonical example outside software is human age cohorts. Children become adolescents become young adults become middle-aged adults become elders. Each is a stock. Aging is the flow between stocks. The chain captures the structure of how the same population matures over time.

In software development, information aging chains are everywhere once you look for them. Raw ideas mature into backbone tasks mature into refined tasks mature into acceptance-ready stories mature into code mature into deployed software. The same underlying intent moves through progressively more concrete representations.

## Why aging chains matter

The aging-chain structure has three consequences that the simpler stock-and-flow framing does not surface as cleanly.

First, **throughput is set by the slowest valve, not the largest stock**. If detail refinement is slow, no amount of upstream raw ideas will produce more refined tasks. The constraint is at the slowest transformation, and the bottleneck moves the system regardless of where work piles up.

Second, **filling a stock upstream of the constraint does nothing**. Brainstorming more raw ideas when the refinement valve is the bottleneck just raises the raw-ideas stock level. The team feels productive (generating ideas) but the system's throughput is unchanged.

Third, **the chain has direction**. Information flows downstream; it cannot skip a stock. Trying to convert raw ideas directly into code skips refinement, workshopping, acceptance, and unit testing. The skipped stocks are precisely where errors get caught. The discipline of the chain is to let information mature through every stock.

## Aging chains in Aim Praxis

**The story map aging chain.** Raw ideas → backbone → refined tasks. Detail refinement transforms backbone into refined tasks. The chain at this level is internal to Story Mapping practice.

**The development aging chain.** Refined tasks → acceptance-ready stories → in-progress work → integrated build → working software. Each transition is a valve operated by a specific practice (workshopping, dev specification, integration, deployment).

**The seven-layer aging chain.** BMC value flows → VPC validated fit → Story Map refined tasks → BDD scenarios → ATDD criteria → TDD code → CI/CD working software. The whole methodology is an aging chain at a higher level of abstraction.

The fractal property is deliberate. Aging chains at one scale contain aging chains at finer scales. The same diagnostic discipline applies at every scale: where is the slowest valve, what stock is piling up, where is information being filled into stocks upstream of the constraint?

## Theory of Constraints applied

Eli Goldratt's Theory of Constraints maps directly onto aging-chain diagnosis. The five focusing steps:

1. **Identify the constraint.** Which valve is the slowest? Where is the stock rising while the downstream stock waits?
2. **Exploit the constraint.** Make sure the constraint valve is operating at full capacity — no idle time, no quality compromises that produce rework.
3. **Subordinate everything else.** Throttle upstream valves so they do not overwhelm the constraint. Avoid optimizing non-constraint valves; the improvements have no system-level effect.
4. **Elevate the constraint.** If steps 1-3 are insufficient, add capacity to the constraint (more people, better tooling, agents).
5. **Repeat.** Once the original constraint is no longer the constraint, identify the new one.

Aim Praxis treats this as the operating discipline. The rework register identifies where work piles up. The team's interventions are organized around relieving the current constraint, not around generic improvement.

## What aging chains reveal that other models hide

The standard agile narrative is "ship value continuously" — a flow-focused view. The standard lean narrative is "eliminate waste" — also flow-focused. Both miss the structural fact that information must traverse a sequence of stocks, and that the system's behavior is determined by where in the chain the constraint sits.

A team optimizing for flow at every step can still produce a backlog crisis if the inflow valve is wider than the outflow valve. A team eliminating waste at every step can still ship the wrong product if the upstream stocks (BMC, VPC) are stale. The aging-chain view shows where these failures come from in a way that the flow-only views do not.

## Detail refinement as an aging-chain valve

Detail refinement is a particularly instructive valve to examine. In standard story-mapping practice, refinement is treated as an inflow to the story map — something that adds detail to existing tasks. The aging-chain view reveals that refinement is actually a valve between two stocks: unrefined backbone tasks and refined tasks.

This reframing has practical consequences. If refinement is treated as an inflow, the response to a slow system is "do more refinement," which feels like adding work. If refinement is treated as a valve between stocks, the response is "what's constraining the rate at which backbone tasks become refined tasks?" — which directs attention to glossary clarity, lessons-learned access, and team capacity rather than to brute-force more refinement sessions.

The pattern generalizes. Whenever a methodology treats something as a "flow" or "activity," it's worth asking what stocks it sits between. The answer usually clarifies the intervention.

## The compounding artifacts as a parallel chain

The aging chain analysis applies to the compounding artifacts as well. Lessons learned begins as observation; matures into pattern; matures into rule; matures into automated check. Each stage is a stock. Each transition is a valve. The slowest valve in the compounding artifacts chain determines how quickly the team's learning produces operational improvement.

For most teams, the slowest valve is "pattern to rule" — recognizing that a pattern exists is easier than codifying a rule. Or "rule to automated check" — writing the rule is easier than embedding it in a gate. Identifying these constraints is how the methodology gets better at getting better.

## What to read next

- `concepts/03-feedback-loops.md` — what happens when chains feed back into themselves
- `concepts/04-the-seven-layers.md` — the methodology's primary aging chain
- `system/integrated-system.md` — all aging chains integrated into one diagram
