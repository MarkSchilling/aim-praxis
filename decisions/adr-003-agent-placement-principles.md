# ADR-003: Agent Placement Principles

**Status:** Accepted

**Date:** 2026-05-19

## Context

Aim Praxis is designed for an era when AI agents can perform consistent, mechanical work that would otherwise require human attention. The methodology had to make explicit design decisions about where agents belong in the system and where they explicitly do not belong.

Three approaches were considered:

1. **Agents everywhere.** Use agents at every point where they can produce output. Maximizes the leverage of AI; risks the methodology becoming dependent on agent quality and prone to silent drift.

2. **Agents nowhere.** Keep the methodology entirely human-driven. Avoids agentic risks; misses the leverage that agents can provide for consistent mechanical work.

3. **Agents at specific structural points.** Place agents where they widen valves or enforce gates; preserve human judgment at points where judgment about purpose is required.

The third approach was chosen and required articulation of the placement principles.

## Decision

Agents in Aim Praxis are placed at:

1. **Valves** to widen them (refinement agent at detail refinement, workshopping agent at scenario authoring)
2. **Gates** to enforce them (ATDD Guardian at acceptance criteria, CI/CD gate at integration)
3. **The rework register** to learn from it (PDSA agent for pattern detection)
4. **Sensing points** to observe the environment (market signal agent, customer research agent, observability agent)
5. **Inside specific work-in-progress stocks** (coding agent inside the TDD loop, glossary agent across multiple text-producing flows)

Agents are explicitly **not** placed at:

1. **Aim setting** — what the product is for
2. **Fit validation** — whether the value proposition serves the customer
3. **Release slicing** — what ships first
4. **Customer acceptance** — whether the work solves the customer's actual problem
5. **Pattern interpretation** — what recurring failures mean strategically

Every agent has explicit boundary specifications and escalation triggers. Every agent output is reviewed (either by a gate or by a human). No agent chain operates without a human or gate review between agents.

## The principle behind the placement

The placement reflects Deming's distinction between common-cause and special-cause variation, applied to agentic work:

- **Common-cause variation** is built into the system; consistent mechanical work reduces it; agents are well-suited
- **Special-cause variation** requires judgment about novel situations; rules don't apply; humans are well-suited

Agent placements address common-cause variation in the loops. Human placements address special-cause variation that requires interpretation, judgment, or strategic choice.

This is also Aristotle's distinction between techne (skilled production, well-suited to agents within their training) and phronesis (practical wisdom in specific situations, irreducibly human).

## Consequences

**What becomes easier:**

- The methodology has principled answers to "should we use AI for this?" — yes if it's a valve or gate that benefits from consistent work; no if it's judgment about purpose
- Each agent has a defined role with boundaries and metrics
- The methodology defends itself against "AI will do everything" hype with a structural argument

**What becomes harder:**

- The methodology requires explicit boundary specifications, escalation triggers, and review processes for each agent — significant operational discipline
- Pressure will mount to extend agents into the human judgment zone; resistance to this pressure is ongoing work
- Teams adopting the methodology need to understand the placement philosophy, not just adopt the agents mechanically

## Alternatives considered

**Agents at every valve and at every gate, including judgment points.** Maximum agentic leverage. Rejected because it produces silent drift — agents producing confident-looking output where humans should be exercising judgment, with the team unable to see the drift until significant rework accumulates.

**Agents only at gates, not at valves.** Conservative approach. Rejected because it leaves consistent mechanical work (refinement, scenario authoring) to humans, wasting human attention on work that doesn't require it.

**Agents only at specific layers (e.g., only at TDD and below).** Considered as a phased approach. Adopted as the *adoption sequence* (Phase 3 introduces only the refinement agent; later phases add others) but not as the final state. The final state is agents at every appropriate structural point across all layers.

**No explicit boundary specifications, relying on agent training to constrain behavior.** Rejected because it makes agent failures invisible. Explicit boundaries produce visible escalation rather than silent overreach.

## References

- `agents/placement-philosophy.md` — the full elaboration of these principles
- `context/boundary-specifications.md` — the boundary discipline
- `concepts/03-feedback-loops.md` — the structural understanding agents operate within
- Deming, *The New Economics* — the variation framework underlying the placement principle
