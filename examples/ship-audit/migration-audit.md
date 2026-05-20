# Ship Audit → Aim Praxis Migration Audit

**Status:** Audit only. No skills modified, no methodology documents modified.
**Date:** 2026-05-19
**Scope:** 15 skills in `shipaudit/.claude/skills/` against the methodology in `aim-praxis/`.
**Ship Audit completion estimate:** one-third built, two-thirds remaining.

---

## Preamble: a structural mismatch to name before reading further

Aim Praxis and Ship Audit's skills folder are not the same artifact at different completeness levels. They are different *units of decomposition*.

- **Aim Praxis** (`context/skills.md`) defines **six canonical skills** at the points where **agents need procedural knowledge**: Story Refinement, Scenario Authoring, Acceptance Criterion Authoring, Code Generation, Pattern Detection, VPC Fit Assessment. The methodology treats most layer work (BMC creation, VPC drafting, story mapping, CI/CD pipeline design, customer acceptance) as **human activity** that does not require a skill artifact.
- **Ship Audit's skills folder** decomposes the entire production system into **15 skills**, including ones for human-driven layers (product-strategy, story-mapping, cicd-pipeline, ux-research, ux-design). Several Ship Audit skills are procedural job aids for humans, not agent-support skills.

This is a **judgment call to surface, not a misalignment to fix**: the two repositories are answering different questions. Aim Praxis answers "where does an agent belong and what does it need?" Ship Audit answers "what does Claude need to know to help me at every step of the process?"

Treat this audit accordingly. Many Ship Audit skills have no Aim Praxis counterpart because Aim Praxis does not call for a skill at that point. That is not necessarily drift — it is a difference in artifact scope.

---

## Section 1 — Existing skills inventory

### Mapping table

| # | Skill | One-sentence description | Closest Aim Praxis layer | Alignment |
|---|---|---|---|---|
| 1 | `atdd-workflow` | Implements features outside-in via RED-GREEN-REFACTOR cycles until acceptance tests pass. | ATDD + TDD (collapsed) | Partially aligned |
| 2 | `bdd-specification` | Translates story map tasks into Gherkin feature files with example mapping and glossary validation. | BDD + ATDD (acceptance criterion authoring) | Aligned |
| 3 | `cicd-pipeline` | Defines the automated commit→deploy path: stages, environment promotion, deployment, rollback. | CI/CD | Aligned |
| 4 | `clean-code` | Decision tree for which SOLID/patterns apply during REFACTOR phase. | TDD (refactor) | Aligned |
| 5 | `continuous-improvement` | Post-release Deming-grounded measurement, root-cause analysis, and skill-update feedback loop. | Cross-cutting (PDSA + rework register + lessons-learned + metrics store) | Partially aligned |
| 6 | `marketing-review` | Validates every customer-facing claim is truthful, substantiated, and compliant before code ships. | No counterpart (cross-cutting quality gate) | Misaligned (in scope sense) |
| 7 | `product-strategy` | Creates and maintains BMC and VPC as foundation documents for downstream skills. | BMC + VPC | Partially aligned |
| 8 | `shipping-invoice-audit` | Domain expertise for parcel carrier invoice auditing (UPS/FedEx/USPS). | Out-of-scope (product domain) | N/A |
| 9 | `software-factory` | Meta-skill navigation guide for the eight-station production system. | Cross-cutting (process governance) | Misaligned (structurally adds a layer Aim Praxis does not name) |
| 10 | `story-mapping` | Organizes VPC Customer Jobs into backbone, walking skeleton, tasks, and releases. | Story Mapping | Aligned |
| 11 | `trusted-system-gates` | Standard work for autonomous gate enforcement (Gate 3 active; 1, 2, 4 deferred). | Cross-cutting (gates) | Partially aligned |
| 12 | `ui-design-system` | Single source of truth for tokens, layout, typography, components, accessibility. | No counterpart | Misaligned (in scope sense) |
| 13 | `ui-design-workflow` | Translates Gherkin scenarios into screen flows, components, and acceptance targets. | No counterpart (UX/UI is not an Aim Praxis layer) | Misaligned (in scope sense) |
| 14 | `ux-design` | IA, interaction patterns, usability evaluation, onboarding before screens are designed. | No counterpart | Misaligned (in scope sense) |
| 15 | `ux-research` | Personas, mental models, journey maps; updates VPC with research findings. | Feeds VPC (no Aim Praxis layer of its own) | Partially aligned |

**Vocabulary on "alignment":**
- **Aligned** = produces the same output Aim Praxis would call for at that layer, with the same boundary discipline.
- **Partially aligned** = overlaps but diverges in specific ways noted below.
- **Misaligned** = produces different output, operates on different principles, or exists where Aim Praxis has no layer at all.
- **N/A** = product domain logic, not methodology-relevant.

### Per-skill divergence notes

**1. `atdd-workflow` — partially aligned.** The skill collapses Aim Praxis layers 5 (ATDD) and 6 (TDD) into a single outside-in workflow. Aim Praxis treats these as **distinct error-catching loops** (`concepts/04-the-seven-layers.md`): ATDD catches completion ambiguity at days cycle time; TDD catches design degradation at minutes cycle time. Each maintains separate compounding artifacts (acceptance criteria library vs unit test suite). The collapse loses the methodology's claim that the two loops catch different errors. **Operationally**, the skill is internally coherent — RED for AT, then nested RGR for unit tests — but it does not produce the separate "acceptance criteria library" artifact Aim Praxis names. The criteria live inside `.feature` files and `bdd-specification` owns them, which is fine, but the audit chain Aim Praxis assumes (criteria → tests → demonstrably-complete) is not visible as three distinct stocks.

**5. `continuous-improvement` — partially aligned.** This skill is doing the work Aim Praxis assigns to *four* separate elements: the PDSA agent (`agents/pdsa-agent.md`), the rework register (`concepts/07-the-rework-register.md`), the lessons-learned library (`concepts/06-compounding-artifacts.md`), and the metrics store. In Ship Audit, this is one skill executed by humans on a release cadence. Aim Praxis specifies it as agentic + continuous + multi-artifact. **The Ship Audit version is operationally complete for current scale**; the divergence is that Aim Praxis assumes recurrence-threshold pattern detection (≥3 occurrences) fires automatically, while Ship Audit's pattern detection is human-eyeball at release time. This is fine for now and a deliberate Phase 1 choice — but the gap should be named, because as Ship Audit grows past 20 stories, the human-eyeball loop will lose patterns that span multiple releases.

**6. `marketing-review` — misaligned (scope).** No Aim Praxis counterpart. The methodology does not specify a customer-facing-claim validation gate. This is a Ship Audit invention. **Judgment call:** it is operationally valuable and methodologically reasonable — preventing unsubstantiated claims from reaching production is a legitimate gate before implementation — but it is not in Aim Praxis. Either (a) Aim Praxis should absorb it as a cross-cutting "Claim Integrity Gate" or (b) it should remain a Ship Audit-specific extension. The choice depends on whether Aim Praxis intends to govern marketing copy or only the engineering production system.

**7. `product-strategy` — partially aligned.** The skill produces both BMC and VPC documents, which Aim Praxis treats as two distinct layer artifacts. Bundling them in one skill is operationally fine; the misalignment is that **Aim Praxis specifies the BMC layer maintains the BMC; the VPC layer maintains the VPC**, with VPC fit validation as a separate human-decision boundary (`agents/placement-philosophy.md` — fit validation is one of five human judgment zones). `product-strategy` puts both behind one skill without distinguishing the validation boundary. The alignment check at `references/canvas-alignment.md` is good and resembles Aim Praxis' coupling between layers, but the validation-vs-synthesis distinction is fuzzed.

**9. `software-factory` — misaligned (structurally).** Adds an "eight-station production system" abstraction (Strategy, Research, Planning, Specification, UX Design, UI Design, Implementation, Delivery, plus Improvement) that **Aim Praxis does not name**. Aim Praxis has seven nested loops at seven cycle times. Ship Audit has eight sequential stations. These are different mental models of the same work: nested feedback loops vs sequential value stream. **The station model emphasizes hand-off discipline (good); it obscures cycle-time heterogeneity (cost).** The intake-triage discipline in `software-factory` is valuable operational knowledge (see Section 3) that prevents bypassing upstream artifacts — that is genuine, hard-won wisdom worth preserving in either model. But the station decomposition itself is a Ship Audit choice, not an Aim Praxis claim.

**11. `trusted-system-gates` — partially aligned.** Aim Praxis names seven gates (`operations/gates.md`); Ship Audit has implemented one (Gate 3 — Ambiguity) and explicitly defers Gates 1, 2, and 4. This is deliberate phasing, not contradiction. **The divergence worth noting** is that Ship Audit's Gate 3 implementation has accreted operational knowledge (Pass 1/Pass 2 architecture, criteria phrasing patterns, rework register injection via semantic similarity) that goes substantially beyond what `operations/gates.md` documents. This is the most important "old wisdom" finding in Section 3.

**12, 13, 14. `ui-design-system`, `ui-design-workflow`, `ux-design` — misaligned (scope).** Aim Praxis has no UX or UI Design layers. The methodology assumes user-facing decisions emerge from Story Mapping narrative fidelity and BDD scenarios. Ship Audit has separated UX and UI into discrete stations with three dedicated skills. **Judgment call:** this is the cleanest case of Ship Audit extending beyond the methodology. Whether it represents missing methodology (Aim Praxis should add layers) or appropriate product-level customization (UX/UI skills stay in Ship Audit, not in Aim Praxis) is an open architectural question.

**15. `ux-research` — partially aligned.** Aim Praxis does not have a UX Research layer — research feeds VPC, where the customer research agent synthesizes signals. `ux-research` in Ship Audit produces personas, mental models, and journey maps as artifacts, then updates the VPC. The function is mostly compatible with Aim Praxis' "customer research agent" vision, but the boundary is different: in Aim Praxis, customer research **synthesizes** signals for human VPC validation; in Ship Audit's `ux-research`, the skill **writes back to VPC directly** (Step 4). This crosses the synthesis-vs-validation line Aim Praxis is careful to preserve (`agents/placement-philosophy.md` — fit validation is human work).

---

## Section 2 — Missing skills

The six canonical agent-support skills in `aim-praxis/context/skills.md` map as follows:

| Aim Praxis canonical skill | Aim Praxis layer | Status in Ship Audit | Notes |
|---|---|---|---|
| Story Refinement Skill | Story Mapping (detail-refinement valve) | **PARTIALLY PRESENT** | Folded into `story-mapping` (Step 3 "Break Activities into Tasks" + `references/task-template.md` sizing rules + "Update Story Map" workflow). The work exists; it is not surfaced as a distinct entry point for the ongoing refinement valve, only as part of the initial mapping workflow. Same structural collapse pattern as `atdd-workflow` (ATDD+TDD bundled). |
| Scenario Authoring Skill | BDD | **PRESENT** as `bdd-specification` | Aligned. |
| Acceptance Criterion Authoring Skill | ATDD | **PARTIALLY PRESENT** | Mixed into `bdd-specification` (which writes AC into `.feature` files) and validated by `trusted-system-gates` Gate 3. No standalone AC authoring skill. |
| Code Generation Skill | TDD | **PRESENT** as `atdd-workflow` | Aligned in function; bundles ATDD and TDD as noted above. |
| Pattern Detection Skill | Cross-layer (PDSA, reads rework register) | **PARTIALLY PRESENT** | `continuous-improvement` does pattern detection manually at release time. No agentic, threshold-fired version exists. |
| VPC Fit Assessment Skill | VPC | **MISSING** | `ux-research` is research-and-write, not signal synthesis. No skill watches customer signals (support tickets, churn, sales conversations) for VPC-pain-stock-rising patterns. |

### What the remaining two-thirds of Ship Audit would benefit from

- **Surfacing the refinement workflow inside `story-mapping`**: As Ship Audit's backbone fills out, refining backbone tasks into actionable refined tasks becomes a recurring high-cost activity. The procedural knowledge already exists in `references/task-template.md` (sizing rules) — what is missing is a distinct entry point that fires when a backbone task comes due for refinement, separate from the initial-mapping workflow. Delivered as a `story-mapping` refactor (new Workflow Decision branch + reference doc), not as a new skill. Highest near-term leverage.
- **Pattern Detection Skill (agentic)**: As `rework-register.json` grows, manual eyeball pattern detection at release time will miss cross-release patterns. An agentic version that fires when ≥3 similar entries accumulate would catch what humans miss. Medium-term leverage.
- **VPC Fit Assessment Skill**: Required once Ship Audit has paying customers generating support/churn signal. Until then, premature.

---

## Section 3 — Old wisdom worth preserving

These are the highest-value findings of the audit: operational knowledge encoded in Ship Audit's skills that **the Aim Praxis methodology does not yet articulate**. Each represents a gap in the methodology that the working implementation has already solved.

### 3.1 Gate 3 criteria phrasing patterns (HIGHEST VALUE)
**Location:** `shipaudit/.claude/skills/trusted-system-gates/SKILL.md:154-227`
**What Ship Audit knows:** Four specific phrasing patterns to eliminate Pass 1 implementation divergence — Pre-asserted Expression Given, Tautological Given for Substring, Explicit Boolean Expression for Multiple Substrings, Line-by-Line Scan with Pre-Assertion. These are hard-won from running Gate 3 across the first dozen stories.
**What the methodology misses:** `aim-praxis/operations/gates.md` describes the ATDD Guardian gate's *function* (validate criteria for ambiguity) but provides no catalog of phrasing patterns that produce divergence-free criteria. Any team adopting Aim Praxis would rediscover these patterns from scratch.
**Recommendation:** These belong in `aim-praxis/operations/gates.md` under a "Criteria Phrasing — Patterns That Pass Gate 3" section.

### 3.2 Rework register as compounding knowledge artifact (HIGH VALUE)
**Location:** `shipaudit/.claude/skills/trusted-system-gates/SKILL.md:236-246`
**What Ship Audit knows:** The rework register is implemented as `artifacts/rework-register.json` indexed by criterion type and domain. Failures are injected into future Gate 3 Evaluation Agent context via semantic similarity matching. The gate becomes progressively harder to fool as it accumulates failure modes — a self-improving compounding artifact.
**What the methodology misses:** `aim-praxis/concepts/07-the-rework-register.md` treats the rework register as a classification/audit mechanism. It does not specify the "injection into future gate context" pattern that makes the artifact actively compound the gate's capability. This is the operational definition of "compounding" the methodology asserts but does not detail.
**Recommendation:** Aim Praxis should absorb this mechanism into the concept doc and reference it from the gate doc.

### 3.3 RGR cycle granularity and commit discipline (HIGH VALUE)
**Location:** `shipaudit/.claude/skills/atdd-workflow/SKILL.md:142-158`
**What Ship Audit knows:** Each RGR cycle produces at minimum two commits (RED test, GREEN code), with separate refactor commits only for structural changes. Batch-committing destroys "Signal 4 (RGR cycle granularity)" and prevents process measurement. Pre-push: `tsc --noEmit && npm test --bail`. One feature per PR. Structural refactors in separate PRs.
**What the methodology misses:** `aim-praxis/practices/tdd.md` and `practices/cicd.md` do not specify commit granularity as a measurement-enabling discipline. The methodology cares about cycle times but does not mandate the artifact (commit-level granularity) that makes cycle time measurable.
**Recommendation:** Add to `aim-praxis/practices/tdd.md` as a measurement prerequisite.

### 3.4 Intake triage to prevent station bypass (HIGH VALUE)
**Location:** `shipaudit/.claude/skills/software-factory/SKILL.md:13-45`
**What Ship Audit knows:** Mandatory intake triage before every imperative request: Does task file exist? Feature file? UI? Screen flow? Marketing review? Root cause: `imperative-request-station-bypass.md` RCA — humans (and Claude) pattern-match "implement" to coding and skip upstream artifacts.
**What the methodology misses:** Aim Praxis describes the seven layers and their hand-offs but does not articulate the *anti-pattern* of bypassing upstream layers. The methodology assumes the layers will be respected; Ship Audit learned the hard way that they must be enforced via explicit triage.
**Recommendation:** Add to `aim-praxis/system/integrated-system.md` or as a new `system/anti-patterns.md` doc.

### 3.5 Nine signals taxonomy for measurement (MEDIUM VALUE)
**Location:** `shipaudit/.claude/skills/continuous-improvement/SKILL.md` and `references/measurement.md`
**What Ship Audit knows:** Nine specific signals computable from existing artifacts without new instrumentation, each with healthy thresholds. Critical caveat: metrics are informational until 20 story records (sample size discipline).
**What the methodology misses:** `aim-praxis/concepts/06-compounding-artifacts.md` names the metrics store but does not specify the signals or the sample-size threshold for treating metrics as actionable. The 20-story rule is Deming-grounded sample size discipline that the methodology should make explicit.
**Recommendation:** Add to `aim-praxis/concepts/06-compounding-artifacts.md` (metrics store section).

### 3.6 Marketing-review claim taxonomy and substantiation tree (MEDIUM VALUE — scope-dependent)
**Location:** `shipaudit/.claude/skills/marketing-review/SKILL.md` and references
**What Ship Audit knows:** Six-category claim taxonomy (performance, social proof, comparative, capability, trust signal, pricing) with a Verified/Estimated/Unsubstantiated decision tree and per-category substantiation procedure. Fabricated testimonials always removed (never reframed). Cost of fixing false claim doubles at each downstream station.
**What the methodology misses:** Nothing — because Aim Praxis does not currently claim governance over customer-facing copy. **Judgment call:** if Aim Praxis intends to be a complete production methodology (engineering + product + marketing), this is methodology-level wisdom worth absorbing. If it intends to govern only the engineering production system, this stays a Ship Audit-specific extension.

### 3.7 AC patterns from RCA ACT-002-rework (HIGH VALUE)
**Location:** `shipaudit/.claude/skills/bdd-specification/SKILL.md:84-104`
**What Ship Audit knows:** Five concrete rules learned from rework on ACT-002:
- Template variables (`:id`) prohibited in endpoint paths; reference concrete IDs from prior Given.
- Multi-system flow rule: one criterion per system layer when AC crosses frontend/backend boundary.
- Input validation: enumerate boundary cases explicitly (empty, whitespace, null, undefined).
- Observable state rule: describe what user/external system observes, not internal storage.
- Test-layer rule: ACs describe behavior, not test tool/framework.
**What the methodology misses:** `aim-praxis/practices/atdd.md` does not enumerate these. They are exactly the patterns Aim Praxis would call out in an Acceptance Criterion Authoring Skill, but no such skill artifact exists in the methodology yet.
**Recommendation:** Either (a) backport into `practices/atdd.md` or (b) draft a canonical "Acceptance Criterion Authoring Skill" specification incorporating them.

### 3.8 Threshold-based gate phasing strategy (MEDIUM VALUE)
**Location:** `shipaudit/.claude/skills/trusted-system-gates/SKILL.md:250-281`
**What Ship Audit knows:** Don't enforce all gates from day one. Phase 1: Gate 3 only (Ambiguity). Phase 2: Gates 1 (Assumption Clarity) and 4 (Capability Declaration), arriving at the **20-story-record threshold** in `metrics-store.json`. Phase 3: Gate 2 (Coverage), arriving at first external client or new market vertical. The thresholds are concrete and tied to artifact state, not calendar time.
**What the methodology has and misses:** `aim-praxis/operations/operationalization-sequence.md` documents **macro-level adoption phasing** (Phase 0 aim → Phase 1 substrate → Phase 2 first gate [ATDD Guardian] → Phase 3 first agent → ...). It names the ATDD Guardian as the first gate. **What it does not document** is the sequence for the other six gates from `operations/gates.md` after the ATDD Guardian, threshold-based phasing rules, or the "informational until 20 story records" sample-size discipline. The methodology has the general principle; Ship Audit has the gate-specific thresholds.
**Recommendation:** Add a "Gate Adoption Phasing" section to `aim-praxis/operations/gates.md` (not to `operationalization-sequence.md` — that doc covers macro-phasing across the whole methodology; gate-specific phasing belongs with the gates themselves). The new section should specify which gates follow ATDD Guardian, in what order, gated by what artifact thresholds.

---

## Section 4 — Sequenced recommendation

### Constraints (restated for traceability)
- Ship Audit must keep shipping.
- Two-thirds of Ship Audit's build remains.
- Do not recommend rewriting all skills at once.
- Identify near-term-leverage updates vs deferrable ones.
- Flag infrastructure dependencies.

### Wave 1 — Methodology backport (do before next major Ship Audit feature)

These changes are *only to Aim Praxis*, not to Ship Audit's skills. They preserve hard-won Ship Audit wisdom into the methodology source of truth so it survives the next migration and benefits anyone else adopting Aim Praxis. **No Ship Audit work is blocked. No infrastructure dependencies.**

1. **Backport Gate 3 criteria phrasing patterns** into `aim-praxis/operations/gates.md`. Lift Section 3.1 above verbatim. (Highest leverage; reflects most expensive learning.)
2. **Backport rework register injection mechanism** into `aim-praxis/concepts/07-the-rework-register.md`. (Section 3.2.)
3. **Backport intake-triage anti-pattern** into either `system/integrated-system.md` or a new `system/anti-patterns.md`. (Section 3.4.)
4. **Backport AC patterns from ACT-002-rework** into `aim-praxis/practices/atdd.md`. (Section 3.7.)
5. **Document the UX/UI architectural decision.** Either fold UX Research and UX/UI Design into Aim Praxis as layers, or write an ADR (`decisions/adr-004-ux-ui-as-product-level-extensions.md`) declaring them out-of-methodology-scope. The current state — Ship Audit has them, Aim Praxis is silent — is the worst of both worlds.

### Wave 2 — Ship Audit skill updates that benefit the next chunk of build

Targeted skill updates that materially improve Ship Audit's velocity over the next third of the build. Order matters; later items depend on earlier.

1. **Refactor `story-mapping` to surface the refinement workflow as a distinct entry point.** The procedural knowledge for task decomposition already exists in `references/task-template.md` (sizing/splitting rules). What is missing is a Workflow Decision branch that fires when a backbone task comes due for refinement, separate from the initial-mapping workflow. Delivery shape: add a third branch to the existing "Workflow Decision" section (alongside "Create" and "Update") and a `references/refinement.md` doc that scopes the valve work. Cheaper and lower-risk than a new skill, and avoids the structural collapse Aim Praxis warns about by making the two activities distinguishable at the skill's entry point. **Infrastructure:** none required.
2. **Update `bdd-specification` SKILL.md to reference the Aim Praxis methodology** (lineage statement). Low-effort, high-clarity. Helps future contributors understand why the Gate 3 patterns are non-negotiable.
3. **Update `continuous-improvement` to log pattern-detection candidates** as it scans the rework register, even before the agentic version exists. Lays groundwork for Wave 4.

### Wave 3 — Defer until Ship Audit ships

These are valuable but not load-bearing for the next two-thirds of build. Defer to avoid scope creep.

1. **Building agentic Pattern Detection Skill.** Manual at-release detection is adequate until past 20 stories. Premature automation here delivers no measurable benefit.
2. **Building VPC Fit Assessment Skill.** Requires customer signal sources (support tickets, churn data, sales conversation logs) that only exist once Ship Audit has paying customers. Premature.
3. **Implementing Gates 1, 2, 4.** Already deferred by Ship Audit's own phasing strategy. Phase 2 arrives at 20-story threshold; Phase 3 at first external client. Honor the phasing.
4. **Reconciling `software-factory`'s eight-station model with Aim Praxis' seven-layer model.** Both are operationally workable. The reconciliation is a methodology-design decision, not a Ship Audit delivery dependency.

### Wave 4 — Infrastructure (MCP servers and agents that don't yet exist)

Aim Praxis methodology references several MCP servers and agents that **are not yet implemented**. Building them too early wastes capacity; not building them blocks Wave 1's higher-order goals. Recommended build order, highest leverage first:

| MCP / Agent | Why first | Aim Praxis reference |
|---|---|---|
| **1. Glossary MCP server** | Multiple Ship Audit skills (`bdd-specification`, `atdd-workflow`, `clean-code`, `trusted-system-gates` Pass 2) already read `ubiquitous-language.md`. An MCP wrapper would unify access, enable the glossary agent Aim Praxis specifies, and simplify Gate 3 Pass 2. **Highest leverage per build hour.** | `context/skills.md`, `agents/glossary-agent.md` |
| **2. Rework register MCP wrapper** | Ship Audit already has `artifacts/rework-register.json` as a file. Wrapping it as an MCP enables the PDSA agent's pattern detection without changing the underlying artifact. Unlocks Wave 3 item 1 when ready. | `agents/pdsa-agent.md`, `concepts/07-the-rework-register.md` |
| **3. Process capability MCP server** | Required for the Aim Praxis-specified Gate 4 (Capability Declaration). Ship Audit defers Gate 4 to Phase 2 (20 stories). Build this when Phase 2 approaches, not before. | `operations/gates.md`, `context/skills.md` |
| **4. Customer signal sources MCP** | Required for VPC Fit Assessment Skill. Defer until paying customers exist. | `agents/customer-research-agent.md` |
| **5. Process capability statement governance** | Aim Praxis names the artifact but does not specify ownership/cadence (this is listed as ambiguity #5 in the Aim Praxis research brief). Resolve before building Gate 4. | `operations/gates.md`, `concepts/06-compounding-artifacts.md` |

### Cross-cutting recommendation

**Do not rewrite Ship Audit skills wholesale to match Aim Praxis vocabulary.** The skills work. They have proven themselves through running Gate 3 and shipping the first third. The methodology should absorb Ship Audit's wisdom (Wave 1) before Ship Audit conforms to the methodology's vocabulary. **Bottom-up flow first, top-down conformance later.** This mirrors Aim Praxis' own Deming-grounded principle that the system, not the individual, produces outcomes — and the system has already worked.

---

## Ambiguities flagged (not resolved)

These are open questions surfaced by the audit that I have not silently resolved. Each is a judgment call that the human (you) should make.

1. **Scope of Aim Praxis vs Ship Audit.** Does Aim Praxis govern only the engineering production system, or the full product system including marketing copy and UX/UI? This determines whether `marketing-review`, `ui-design-system`, `ui-design-workflow`, `ux-design` are "missing from the methodology" or "appropriately out of scope."
2. **Granularity of "skill" as an artifact.** Aim Praxis defines 6 agent-support skills; Ship Audit defines 15 process-stage skills. Should Aim Praxis adopt Ship Audit's broader skill granularity, or should Ship Audit narrow its skill set to match Aim Praxis' more restrictive definition?
3. **Customer research synthesis vs validation boundary in `ux-research`.** `ux-research` Step 4 writes back to VPC directly. Aim Praxis specifies that synthesis is agentic but VPC validation is human work (`agents/placement-philosophy.md`). Is `ux-research` crossing the line, or is "research findings flow back" within synthesis scope?
4. **ATDD/TDD collapse in `atdd-workflow`.** Bundling outside-in (ATDD) and inside-out (TDD) cycles in one skill is operationally clean but loses the methodology's two-error-classes claim. Is this a feature or a defect?
5. **Eight-station vs seven-layer mental models.** Both are operationally usable. Should they coexist (Aim Praxis as theoretical frame, software-factory as operational frame), or should one absorb the other?

---

## Audit summary

- **15 skills examined**: 5 aligned, 6 partially aligned, 4 misaligned (mostly in scope sense, not in operation).
- **6 canonical Aim Praxis skills examined**: 2 fully present, 3 partially present, 1 missing.
- **8 cases of "old wisdom" identified** — operational knowledge Ship Audit holds that Aim Praxis does not yet articulate.
- **5 open ambiguities flagged** — judgment calls for the human.
- **4 build waves recommended** — methodology backport first, targeted skill additions next, deferred work last, infrastructure interleaved.

**The single most important finding:** Section 3.1 (Gate 3 phrasing patterns). This is the most expensive lesson Ship Audit has paid for, and it currently lives nowhere in the methodology.
