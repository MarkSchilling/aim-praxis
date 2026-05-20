# Aim Praxis

**Pronunciation:** Aim PRAK-sis (rhymes with "taxis")

Aim Praxis is a software development methodology grounded in W. Edwards Deming's System of Profound Knowledge and broader systems thinking. It treats software development as a system whose properties emerge from feedback at every cycle time — from minute-by-minute code commits to quarter-by-quarter strategy — and it preserves human judgment at the specific points where judgment about purpose is required.

The methodology integrates seven practices as nested feedback loops: Business Model Canvas, Value Proposition Canvas, Story Mapping, Behavior-Driven Development, Acceptance Test-Driven Development, Test-Driven Development, and Continuous Integration / Continuous Deployment. Each loop operates at its own cycle time on its own stocks of information. Each catches a class of error invisible to the others. Together they form a control system that produces software aligned with stated intentions.

Aim Praxis is grounded in the conviction, from Deming, that 94% of failures belong to the system rather than the individual. Its central organizing concept is the *system aim* — the purpose toward which every practice in the methodology orients. The name reflects this: *Aim* names the methodology's orientation; *Praxis* names its character as disciplined practice informed by theory.

## Intellectual lineage

Aim Praxis draws on multiple traditions:

- W. Edwards Deming's System of Profound Knowledge — *Out of the Crisis*, *The New Economics*
- Systems thinking — Forrester, Meadows (*Thinking in Systems*), Senge (*The Fifth Discipline*)
- Lean and Toyota Production System — Ohno, Womack and Jones
- Story Mapping — Patton's *User Story Mapping*
- BDD — North, Adzic's *Specification by Example*
- ATDD — Koskela and the FIT tradition
- TDD — Beck's *Test-Driven Development*
- CI/CD — Humble and Farley's *Continuous Delivery*
- Philosophical tradition — Aristotle on praxis and phronesis, Aquinas, Dallas Willard

See `docs/lineage.md` for the detailed genealogy.

## Repository organization

- `docs/` — core methodology documents: aim, full methodology, lineage, glossary
- `concepts/` — foundational concepts (stocks and flows, aging chains, feedback loops, the seven layers, cycle times, compounding artifacts, the rework register)
- `practices/` — one document per integrated practice
- `system/` — the integrated view: how the practices form one system
- `agents/` — agentic augmentation: placement philosophy and per-agent specifications
- `context/` — the substrate that makes agents work: MCP servers, skills, knowledge files, boundary specifications
- `operations/` — putting the methodology to work: sequence, cadences, gates, monetization
- `diagrams/` — every diagram, as SVG source
- `decisions/` — architecture decision records for the methodology itself
- `examples/` — worked applications (Ship Audit will be the first)

## Suggested reading order

For someone encountering Aim Praxis for the first time:

1. `docs/aim.md` — what the methodology is for
2. `concepts/01-stocks-and-flows.md` — the analytical vocabulary
3. `concepts/04-the-seven-layers.md` — the structural claim
4. `system/integrated-system.md` — how it all fits together
5. `agents/placement-philosophy.md` — how agents fit in
6. `operations/operationalization-sequence.md` — how to actually adopt it

## Status

Aim Praxis is under active development. The methodology is being consolidated from research, design work, and application to a working SaaS product (Ship Audit). The repository is the canonical source of truth as the methodology evolves.

This is not yet a published external methodology. It is the working substrate from which publications, tooling, and consulting offerings will eventually be derived.

## License

Apache License 2.0 — see `LICENSE`.
