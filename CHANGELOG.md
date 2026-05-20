# Changelog

All notable changes to Aim Praxis will be documented here.

The format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [Unreleased]

### Added
- Initial repository structure
- Core documents: aim, methodology overview, lineage, glossary
- Foundational concepts: stocks and flows, aging chains, feedback loops, the seven layers, cycle times, compounding artifacts, the rework register
- Per-practice documents for BMC, VPC, Story Mapping, BDD, ATDD, TDD, CI/CD
- Integrated system documentation
- Agent placement philosophy and per-agent specifications
- Context engineering: MCP servers, skills, knowledge files, boundary specifications
- Operations: sequence, cadences, gates, monetization paths
- All thirteen diagrams from the methodology design conversation, in SVG format
- Initial architecture decision records (naming, praxis vs techne, agent placement)

### Notes
- Methodology consolidated from research and design work through May 2026
- Repository established as the canonical source of truth for the methodology

## [2026-05-20] — Ship Audit migration session

### Added
- `examples/ship-audit/migration-audit.md` — comparison of Aim Praxis against the Ship Audit working implementation, identifying alignment, drift, and operational wisdom worth absorbing back into the methodology
- `decisions/adr-004-ux-ui-as-product-discipline.md` — declares UX/UI a product discipline that produces inputs to Aim Praxis layers (VPC, Story Mapping, BDD, ATDD), not a layer of the methodology itself
- `system/anti-patterns.md` — new catalogue of system-level anti-patterns, opening with the upstream-layer-bypass pattern (Ship Audit's intake-triage discipline, generalized)
- `examples/ship-audit/wave-3-4-trigger-conditions.md` — concrete, falsifiable trigger conditions for deferred Waves 3 (agentic skills) and 4 (MCP infrastructure)

### Changed
- `concepts/07-the-rework-register.md` — added "How the register compounds gate capability" section, articulating the in-band feedback mechanism (semantic-similarity injection into gate evaluation context) that makes the register an operational compounding artifact rather than just classified storage
- `practices/atdd.md` — added "How to write acceptance criteria" section with five content rules: concrete identifiers, system-boundary split, boundary-case enumeration, observable outcomes, and test-layer independence
- `operations/gates.md` — added "Gate adoption phasing" section (sequence + the twenty-record threshold for actionable metrics) and "Criteria authoring patterns (ATDD gate)" section (four Gherkin phrasing patterns that eliminate Pass 1 implementation divergence)

### Notes

This session is the methodology's first demonstration of its recursive property. The Ship Audit migration audit identified eight cases where the working implementation had accreted operational wisdom that the methodology did not yet articulate. Five of those — register injection, AC content rules, Gate 3 phrasing patterns, gate adoption phasing, and the upstream-layer-bypass anti-pattern — were backported into the methodology source of truth in this session. Ship Audit's lessons-learned loop closed into Aim Praxis through the same mechanism the methodology specifies for its own internal learning: identify the pattern, classify the failure or gap, route the remediation to the upstream artifact that should have prevented it. The methodology evolved by being used.

Wave 2 of the migration (three skill updates in Ship Audit's repository: methodology lineage in `bdd-specification`, the Refine Task workflow in `story-mapping`, the Pattern Candidate Scan step in `continuous-improvement`) landed on Ship Audit's main on the same day, completing the migration's near-term scope.

Waves 3 (agentic skills) and 4 (MCP infrastructure) are deferred pending the operational triggers specified in `examples/ship-audit/wave-3-4-trigger-conditions.md`. The principle: build infrastructure when the human-mediated precursor becomes a measurable constraint, not before. In the meantime, the manual precursors (release-time pattern-candidate scanning, file-based glossary lookup, human gate review) are sufficient.
