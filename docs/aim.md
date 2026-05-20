# The Aim of Aim Praxis

## The aim, in one sentence

Aim Praxis exists to help organizations and individuals build software that aligns with their stated intentions across every cycle time, from minute-by-minute commits to quarter-by-quarter strategy.

## The aim, expanded

Alignment is the methodology's central concept. Software that is fast but solves the wrong problem is misaligned with strategy. Software that solves the right problem but ships unreliably is misaligned with operational reality. Software that ships reliably but rots internally is misaligned with the team's future capacity. Software that is internally sound but does not change what users can do is misaligned with the world it claims to serve. Each of these is a failure of alignment at a specific cycle time, and each is invisible to practices that operate only at other cycle times.

Aim Praxis treats alignment as something that must be produced at every cycle time simultaneously. The methodology arranges seven practices as nested feedback loops, each catching a class of misalignment the others cannot see. The whole produces software that is aligned at every scale, not just at the scale most visible to the team in any given moment.

## What success looks like

A team operating Aim Praxis successfully exhibits the following properties:

- The team can describe its current work in terms of the system aim, and the description is concrete enough to be falsifiable
- The team can identify which loops are currently healthy, which are stressed, and which are silently broken
- The team's compounding artifacts (glossary, lessons learned, process capability) grow steadily and are referenced in current work
- The rework register classifies failures by which loop caught them, making system-level patterns visible
- Human judgment is concentrated at aim setting, fit validation, release slicing, customer acceptance, and pattern interpretation — not dispersed across mechanical work
- Agents handle the mechanical work that consistent execution requires, freeing human attention for judgment
- The team can explain its methodology to a new member in terms of stocks, flows, valves, and loops — not just in terms of practices and ceremonies

## What failure looks like

A team that has adopted Aim Praxis vocabulary but not its substance exhibits the following pathologies:

- Inner-loop dominance: TDD and CI/CD run continuously while Story Mapping and BMC review happen once and atrophy
- Pack rat accumulation: the story map fills with ideas faster than the team can refine and deliver them
- Vestigial outer loops: BMC and VPC documents exist but are not updated and no longer inform decisions
- Disconnected metrics: the team measures component output (stories shipped) without measuring system output (working software in production) or aim alignment (user outcomes)
- Agentic substitution: agents do work that should remain human, particularly around acceptance and pattern interpretation
- Rework without learning: the rework register fills with defects but is not analyzed for patterns
- Lost glossary: the ubiquitous language stock degrades because no agent or practice maintains it

A team in these states is using Aim Praxis as branding rather than as a system. The methodology has been adopted nominally; the substance has been lost.

## The aim is recursive

Aim Praxis is itself a methodology that must be aligned with its own aim. This document is the operational definition the methodology applies to itself. Every change to the methodology must be evaluated against this aim. Changes that improve alignment between built software and stated intentions are improvements; changes that compromise alignment in service of other goods are not.

This recursion is deliberate. A methodology that cannot apply its own discipline to itself cannot claim the discipline it asks of its practitioners.

## What this aim deliberately excludes

Aim Praxis is not a methodology for:

- Maximizing development velocity at the expense of alignment
- Producing software faster regardless of whether it serves the intended purpose
- Substituting agents for human judgment about purpose
- Replacing strategic thinking with operational discipline
- Producing software that meets explicit requirements while failing to serve unstated but real needs

These exclusions matter because they distinguish Aim Praxis from methodologies that share its vocabulary but optimize for different ends. Many agile methodologies are velocity-optimized; many lean methodologies are waste-elimination-optimized; many DevOps practices are deployability-optimized. Aim Praxis is alignment-optimized, and alignment sometimes requires moving slower, accepting waste, or deploying less frequently than other optimizations would suggest.

## The audience this aim serves

Aim Praxis is for builders who treat software development as a system whose properties emerge from feedback rather than as a sequence of tasks. It is for teams willing to invest in outer-loop discipline even when inner-loop work feels more productive. It is for organizations whose stated intentions are worth aligning with — which is to say, organizations that have thought seriously about what they are for.

The methodology will not help organizations whose stated intentions are themselves incoherent or unspoken. It is not a substitute for the work of clarifying what the work is for. It is the discipline that, given a clear aim, produces software that serves that aim across every cycle time the work actually happens at.
