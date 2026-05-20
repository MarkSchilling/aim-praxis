# Wave 3 and Wave 4 Trigger Conditions

The Ship Audit migration completed Waves 1 (methodology backports) and 2 (skill updates) on 2026-05-20. Waves 3 (agentic skills) and 4 (MCP infrastructure) are deferred. This document specifies the conditions under which each component of those waves should begin, separating "premature" from "appropriate" by concrete, falsifiable thresholds.

The principle: build infrastructure when the human-mediated precursor becomes a measurable constraint, not before. Premature infrastructure produces costs without corresponding benefit and risks over-fitting to projected rather than observed requirements.

## Wave 3 — Agentic skills

### Deferral rationale

Wave 3 introduces agentic versions of work that is currently done by humans at release cadence. Manual at-release work is adequate while Ship Audit is below operational scale; the cost of building agentic versions exceeds the benefit they would deliver. Premature automation also risks encoding the wrong patterns — the human work is still discovering its own discipline.

### Component 1: Agentic Pattern Detection Skill

**Replaces:** The manual Pattern Candidate Scan step (Step 2 in `continuous-improvement`) introduced in Wave 2.

**Trigger condition:** Ship Audit's `artifacts/metrics-store.json` contains at least twenty completed story records. Below this threshold, the rework register does not contain enough signal to distinguish recurring patterns from coincidence; agentic detection would amplify noise rather than reduce it.

**First action when triggered:** Read the accumulated `pattern-candidates/r[N]-*.md` files. Identify which candidate patterns recurred and reached PDSA threshold, and which closed without recurrence. Use this human-validated history as the training signal for the agent's similarity scoring. Then specify the agent against `aim-praxis/agents/pdsa-agent.md` and build it against the rework register MCP (Wave 4 Component 2 below).

### Component 2: VPC Fit Assessment Skill

**Replaces:** Manual customer-signal review by humans.

**Trigger condition:** Ship Audit has paying customers generating support tickets, churn data, or sales-conversation transcripts. The customer research agent specified at `aim-praxis/agents/customer-research-agent.md` requires customer signal sources as inputs; until those signals exist in volume, the agent has nothing to synthesize.

**First action when triggered:** Build or configure the customer signal sources MCP server (Wave 4 Component 4 below). The skill cannot be built without that MCP because the skill's role is signal synthesis; the MCP is the signal source.

### Component 3: Implementing Gates 1, 2, 4

**Replaces:** Manual application of the gate criteria.

**Trigger conditions** (from Ship Audit's own phasing strategy in `shipaudit/.claude/skills/trusted-system-gates/SKILL.md`):

- **Gate 4 (Capability Declaration):** Ship Audit's `metrics-store.json` reaches the twenty-story threshold. Same threshold as Wave 3 Component 1.
- **Gates 1 (Assumption Clarity) and 2 (Coverage):** Ship Audit's first external client engagement or new market vertical. These gates have low value in a known domain; their cost-benefit ratio improves when domain assumptions are unvalidated.

**First action when triggered:**

- For Gate 4: build the process capability MCP server (Wave 4 Component 3 below), then implement the gate's Delivery Confidence Rating algorithm.
- For Gates 1 and 2: write the gate specifications in `aim-praxis/operations/gates.md` (extending the existing gate catalogue), then build the corresponding evaluation agents.

### Component 4: Reconciling 8-station and 7-layer models

**Resolves:** The structural ambiguity flagged in `examples/ship-audit/migration-audit.md` between Ship Audit's eight-station Software Factory model and Aim Praxis's seven-layer architecture.

**Trigger condition:** None operational. This is a methodology-design decision, not an operational dependency. The reconciliation should happen before Aim Praxis is published externally so the methodology presents a single canonical structural claim, but the decision is independent of Ship Audit's state.

**First action when triggered:** Write an ADR (likely ADR-005) that either folds the eight-station view into the methodology as a complementary frame or designates it a Ship-Audit-specific operational lens.

## Wave 4 — MCP infrastructure

### Deferral rationale

Each MCP server in Wave 4 corresponds to a specific Aim Praxis–specified resource (the glossary, the rework register, the process capability statement, customer signal sources). Building an MCP wrapper before the underlying resource is operationally load-bearing produces infrastructure without callers — premature optimization at the integration layer.

The principle: build the MCP when a second skill or agent needs to access the resource and the duplicated access cost becomes visible in the rework register or in human attention.

### Component 1: Glossary MCP server

**Wraps:** The ubiquitous language glossary (`ubiquitous-language.json` and `ubiquitous-language.md`).

**Trigger condition (proposed, requires confirmation):** Three or more rework register entries with `fail_type: "missing_term"` accumulate within a single release cycle. This indicates that reactive glossary maintenance is failing the workflow's pace — the team is rediscovering missing terms at Gate 3 Pass 2 failure time rather than during scenario authoring. Proactive lookup, which the MCP would enable, becomes the cheaper path at that point.

See the "Surfaced ambiguity" section below — this threshold is not derived from the migration audit.

**First action when triggered:** Specify the MCP interface (`glossary.lookup(term)`, `glossary.suggest_addition(term, context)`, `glossary.list_all()`). Build the MCP. Then update `bdd-specification`'s Step 3 (Validate Against Ubiquitous Language) to call the MCP instead of reading the file directly. The glossary agent specified at `aim-praxis/agents/glossary-agent.md` becomes implementable shortly afterward.

### Component 2: Rework register MCP wrapper

**Wraps:** `artifacts/rework-register.json` plus the semantic-similarity index over its diagnostic field. The injection mechanism is specified at `aim-praxis/concepts/07-the-rework-register.md` ("How the register compounds gate capability").

**Trigger condition:** Wave 3 Component 1 (Agentic Pattern Detection Skill) has been authorized. The agentic version requires programmatic access to the register and to similarity-indexed queries; the human-mediated Pattern Candidate Scan introduced in Wave 2 does not. Until Wave 3 Component 1 is triggered, no consumer needs this MCP.

**First action when triggered:** Specify the MCP interface (`rework_register.append(entry)`, `rework_register.query_similar(diagnostic_text, threshold)`, `rework_register.list_by_fail_type(type)`, `rework_register.get_candidates()`). Build the MCP. Update `continuous-improvement`'s Pattern Candidate Scan to read from the MCP instead of the file. The agentic Pattern Detection Skill then consumes the same MCP.

### Component 3: Process capability MCP server

**Wraps:** `artifacts/process-capability-statement.json` (does not yet exist in Ship Audit).

**Trigger condition:** Ship Audit's metrics-store has accumulated twenty or more story records (same threshold as Wave 3 Component 1 and Wave 3 Component 3 for Gate 4). At that point Gate 4 becomes implementable, and Gate 4 requires programmatic queries against the capability statement.

**First action when triggered:** First resolve Wave 4 Component 5 below — process capability statement governance is a prerequisite. Once governance is specified, build the MCP, then build Gate 4 on top of it.

### Component 4: Customer signal sources MCP

**Wraps:** Support ticket sources, churn data sources, sales-conversation transcript sources. Specifics depend on which tools Ship Audit is using by that point.

**Trigger condition:** Ship Audit has paying customers (same trigger as Wave 3 Component 2 — VPC Fit Assessment Skill). The customer signal MCP is required for that skill; before then, the MCP has no callers.

**First action when triggered:** Inventory the actual customer signal sources Ship Audit has at that time. Specify the MCP interface as a normalized signal stream (`signals.recent_support_volume(period)`, `signals.churn_events(period)`, `signals.sales_conversation_keywords(period)`). Build the MCP. Then build the VPC Fit Assessment Skill on top of it.

### Component 5: Process capability statement governance

**Resolves:** The methodology ambiguity flagged in the migration audit research — `aim-praxis/concepts/06-compounding-artifacts.md` names the process capability statement as a compounding artifact but does not specify ownership or maintenance cadence.

**Trigger condition:** Before Wave 4 Component 3 (Process capability MCP server) is built. This is a methodology-design decision that blocks the MCP work, not the other way around. If left unresolved, the MCP would expose an artifact with undefined governance, undermining its trustworthiness.

**First action when triggered:** Write an ADR that names the artifact's owner, the update cadence, and the conditions under which it changes. Then update `aim-praxis/concepts/06-compounding-artifacts.md` to reference the ADR.

## Cross-wave dependency map

Trigger conditions interlock. Read top-to-bottom to see what each event unlocks:

| Trigger event | Unlocks |
|---|---|
| Twenty-story threshold in `metrics-store.json` | Wave 3 Component 1 (Pattern Detection Skill); Wave 3 Component 3 (Gate 4); Wave 4 Component 3 (Process capability MCP — once governance resolved) |
| First paying customer | Wave 3 Component 2 (VPC Fit Assessment Skill); Wave 4 Component 4 (Customer signal sources MCP) |
| First external client / new market vertical | Wave 3 Component 3 (Gates 1, 2) |
| Three `missing_term` entries in a single release (proposed) | Wave 4 Component 1 (Glossary MCP) |
| Wave 3 Component 1 authorization | Wave 4 Component 2 (Rework register MCP) |
| Any time (methodology design) | Wave 3 Component 4 (8-station / 7-layer reconciliation); Wave 4 Component 5 (Capability statement governance) |

## Surfaced ambiguity

One trigger condition above is **not derived from the migration audit** and requires confirmation:

- **Glossary MCP — concrete threshold for "glossary becomes a constraint."** The audit (`examples/ship-audit/migration-audit.md`, Wave 4 section) identifies the glossary MCP as "highest leverage per build hour" and recommends building it first. The audit does not, however, specify *when* to build it.

  The proposed threshold above — three `missing_term` rework register entries within a single release cycle — translates a conversational hint into an operational condition. The number (three) and the window (single release) are working assumptions, not audit-derived facts.

  Alternative thresholds worth considering:
  - **Two or more distinct skills** reading `ubiquitous-language.md` directly (drift surface)
  - **The glossary agent specified at `aim-praxis/agents/glossary-agent.md`** becoming desired
  - **Total glossary size** crossing a threshold (e.g., 100+ terms) at which file-based lookup becomes the bottleneck

  Pick one (or compose them) before Wave 4 Component 1 begins.
