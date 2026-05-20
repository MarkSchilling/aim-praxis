# ADR-001: Naming the Methodology

**Status:** Accepted

**Date:** 2026-05-19

## Context

The methodology that became Aim Praxis evolved over multiple years of work, originally under the working name "Software Factory." As the methodology matured and the integration of Deming's SoPK, systems thinking, and the seven-practice stack became explicit, the working name began to feel inadequate.

Several specific problems with "Software Factory":
- "Factory" implies mass-production, which is the opposite of the methodology's commitment to context-sensitive judgment
- The Toyota Production System association is appropriate but the broader "factory" framing obscures the systems-thinking core
- Mark Schilling, the methodology's developer, was not personally excited about the name
- The name does not signal the methodology's intellectual seriousness or its philosophical lineage

A naming decision was needed that would honor the lineage, signal the substance, and feel right to use in writing, speaking, and identity.

## Decision

The methodology will be called **Aim Praxis**.

- **Aim** names the methodology's central organizing concept, drawn from Deming
- **Praxis** names its character as disciplined practice informed by theory, drawn from Aristotle

The full name is "Aim Praxis." It is pronounced "Aim PRAK-sis" (rhymes with "taxis"). It is written as two words, with both capitalized when used as a proper noun.

## Consequences

**What becomes easier:**

- Public communication has a name with intellectual weight and specific meaning
- The name signals the lineage to anyone familiar with Deming or with the Aristotelian tradition
- The name distinguishes the methodology from "yet another agile framework"
- Mark can use the name with personal conviction in his Substack, on calls, in writing

**What becomes harder:**

- Anyone unfamiliar with both "aim" (in Deming's specific sense) and "praxis" needs the term explained. This is a one-paragraph explanation, but it is required.
- Search engine discoverability requires the methodology to build presence; "Aim Praxis" is not a phrase people would search for unprompted
- The name's seriousness sets an expectation that the content must meet — it is not a name that excuses superficiality

## Alternatives considered

**Software Factory.** The original working name. Rejected as analyzed above.

**Praxis.** Alone. Rejected because "praxis" alone is generic; many methodologies in many fields use the word. The qualifier is what makes the name specific.

**Techne.** The Aristotelian alternative to praxis, naming productive craft rather than disciplined practice. Rejected because techne emphasizes the produced artifact while praxis emphasizes the practitioner's formation. The methodology's compounding artifacts produce both, but the practitioner-formation emphasis is closer to the methodology's intent.

**Phronesis.** Practical wisdom. Considered briefly. Rejected as too philosophical for the name; phronesis appears in the methodology's content (in the human judgment zone) but is too technical for the methodology's identity.

**Telos.** Purpose, end. Considered briefly. Rejected because telos is the goal-orientation; "aim" is the methodology's English term for the same idea, and English clarity beats Greek precision for the name.

**Aim-Driven Development.** Considered but rejected. The "-Driven Development" suffix has been used by BDD and TDD already, and the methodology is more than just driven by an aim — it is grounded in praxis as a character.

**Hypothesis-Driven System Development (HDSD).** A prior candidate from earlier conversations. Rejected because "hypothesis" is one part of the methodology (the PDSA learning aspect), not the whole, and "system development" is generic.

## References

- `docs/lineage.md` — the intellectual genealogy that informs the name
- `decisions/adr-002-praxis-vs-techne.md` — the deeper analysis of the praxis/techne choice
- Conversation transcript at `/mnt/transcripts/2026-05-19-18-29-52-aim-praxis-methodology-build.txt` — the discussion that led to the decision
