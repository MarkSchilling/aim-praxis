# Gates

A gate is a deterministic check at a transition point that enforces explicit criteria. Gates pass or fail mechanically based on criteria; they do not exercise judgment.

This document specifies the gates in Aim Praxis and their criteria.

## Why gates

Gates concentrate variation control at specific points. Instead of every member of the team enforcing every criterion every time, the gate enforces criteria once, consistently, mechanically. This is Deming's discipline applied to software development workflow.

Gates also create the trust that enables agentic augmentation. An agent's output can be trusted because the gate downstream catches errors. Without gates, every agent output requires full human review; with gates, human review focuses on what the gate can't catch.

## The methodology's gates

### Story Mapping ratification gate

Criteria for elevating a Story Mapping session output from "session output" to "ratified release plan":
- All backbone tasks have user identification (who does this)
- All backbone tasks have outcome identification (what they accomplish)
- Release slices are identified (walking skeleton, MVP, subsequent)
- Each release slice produces a usable product
- Lessons-learned from prior releases have been consulted
- The session's outputs are version-controlled in the project

This gate is human-enforced, typically by a Story Mapping facilitator. It is the boundary between "we talked about it" and "we agreed on it."

### ATDD acceptance criterion gate (ATDD Guardian)

Criteria for elevating proposed acceptance criteria to accepted criteria ready for development:
- Each criterion references only glossary-approved terms
- Each criterion specifies an observable outcome, not internal state
- Each criterion is measurable
- Preconditions are stated explicitly
- The criterion is at story level, not unit level
- No criterion uses ambiguity-inducing words without measurable thresholds
- The criterion is within the team's process capability

This gate is mechanically enforced by ATDD Guardian (or equivalent). It is the boundary between "we discussed acceptance" and "the criteria are agreed and falsifiable."

Operational patterns for authoring criteria that pass this gate — and a catalogue of phrasings that produce divergence — are in "Criteria authoring patterns (ATDD gate)" below.

### TDD inner gate

Criteria for code to leave the work-in-progress stock:
- All new code has corresponding tests written first
- All tests pass
- Refactoring step has been completed (not just red-green)
- Code style matches project conventions
- No new linter or static analysis warnings

This gate is partially mechanical (linters, test runners) and partially human (the refactoring step). In agentic implementation, the coding agent self-enforces and humans review.

### CI/CD integration gate

Criteria for an integrated build to be promotable:
- All unit tests pass
- All acceptance tests pass
- All integration tests pass
- Static analysis produces no errors above threshold
- Security scans produce no critical findings
- Code coverage meets project threshold

This gate is fully mechanical. It is the gate most teams already have; the methodology's contribution is integrating its outputs with the rework register.

### CI/CD deployment gate

Criteria for a build to be deployed to production:
- The integration gate has passed
- Deployment dry-run succeeds
- Required approvals are in place (typically human)
- Rollback path is verified

This gate is partially mechanical and partially human (approvals).

### Observability rollback gate

Criteria for triggering automated rollback or human escalation:
- Error rate exceeds configured threshold
- Performance regresses beyond configured threshold
- Business metric movement exceeds configured threshold

This gate is mechanical for detection; rollback decisions remain human in most teams.

### PDSA proposal gate

Criteria for the PDSA agent to fire a proposal:
- Pattern recurrence at or above threshold (typically 3)
- Pattern entries are genuinely similar (not just superficially)
- Evidence base is sufficient
- A specific upstream remediation is identifiable

This gate is mechanical (count, similarity, evidence). The downstream review by humans is where interpretation happens.

## Gate adoption phasing

Adopting all gates simultaneously is overwhelming and produces gates without enforcement (an anti-pattern). Sequence gates by **leverage** and by **dependency on accumulated history**.

The principle: **gates that depend on history (metrics, capability data, rework patterns) cannot be adopted until that history exists.** Adopt them when the artifact thresholds they need are met, not before. Calendar-based phasing produces premature gates; artifact-state phasing produces gates that carry signal.

### The first gate

Adopt the ATDD acceptance criterion gate (ATDD Guardian) first. It has the highest leverage at the earliest stage: it catches completion ambiguity before any implementation work begins, eliminating the most expensive class of rework. This is consistent with `operations/operationalization-sequence.md` Phase 2.

### Gates that can follow immediately

Once the ATDD gate is operating, three more gates can be adopted in any order that suits the team:

- **Story Mapping ratification gate** — human-enforced, no infrastructure beyond facilitator discipline
- **TDD inner gate** — partially mechanical, requires the team to already practice TDD discipline; the gate enforces an existing practice, it does not introduce one
- **CI/CD integration gate** — most teams already have the underlying pipeline; the work is wiring its outputs into the rework register, not building the gate

None of these depend on accumulated history. They can be adopted as the team's capacity allows.

### Gates that require accumulated history

Three gates produce signal only after enough history accumulates and should be deferred until then:

- **CI/CD deployment gate** — needs stable deployment patterns and a verified rollback path
- **Observability rollback gate** — needs stable production baselines for the three thresholds (error rate, performance, business metric movement); premature adoption produces alert noise
- **PDSA proposal gate** — needs enough classified rework register entries that pattern recurrence at threshold (typically 3) is a meaningful signal rather than a coincidence

### The twenty-record threshold for actionable metrics

A gate's metrics are **informational until at least twenty story records exist in the metrics store.** Below that threshold, a gate's pass rate, rework rate, and recurrence patterns are noise. Process changes driven by them are likely to introduce variation rather than reduce it. This is a Deming-grounded sample-size discipline.

The number is a working heuristic, not a theorem. Domains with high story complexity may need more records before metrics stabilize. The principle — do not change the process from fewer records than can distinguish signal from noise — holds across projects.

### Project-specific gates

A team operating in an unvalidated domain (new market vertical, first external client) may benefit from gates Aim Praxis does not currently specify — for example, an assumption-clarity gate after BMC drafting, or a coverage gate verifying VPC↔backbone traceability. These are legitimate domain-specific extensions. When they recur across multiple projects, they become candidates for absorption into the methodology.

## Criteria authoring patterns (ATDD gate)

The ATDD acceptance criterion gate fails when two independent implementations of the same criterion would diverge in observable behavior. The root cause is almost always an unspecified code path — typically error handling for edge cases the Given does not cover.

The patterns below eliminate that divergence. They emerged from operating the gate against real criteria across the first dozen stories of a working implementation; documenting them here so that adopting teams do not have to rediscover them.

The principle: **pre-assert the outcome in the Given so no implementation can add defensive code on a path the criterion did not specify.**

### Pattern 1 — Pre-asserted expression Given

Use when: the criterion checks for the presence of a substring or evaluates a boolean expression.

Assert the expression result in the Given before the When evaluates it. Any implementation that adds a null guard, type check, or throws an error is adding dead code; two independent implementations will recognise this and converge on the direct call.

```gherkin
Given a string T
And T.includes('X') is true
When T.includes('X') is evaluated
Then the result is true
```

### Pattern 2 — Tautological Given for substring search

Use when: the When checks for a substring that must be present.

Add a Given that pre-asserts the substring before the When searches for it. The Given guarantees the Then is true before the When executes, so no implementation can diverge on the not-found case.

```gherkin
Given a string T that contains the substring 'X'
When T is searched for the substring 'X'
Then the substring 'X' is present in T
```

### Pattern 3 — Explicit boolean expression for multiple substrings

Use when: the criterion requires two substrings to be present simultaneously.

Encode both substrings in the Given AND as a single boolean expression in the When. The explicit `&&` locks the return type to boolean and eliminates throwing paths.

```gherkin
Given a string A that contains the substring 'X'
And A contains the substring 'Y'
When the expression (A.includes('X') && A.includes('Y')) is evaluated
Then the expression evaluates to true
```

### Pattern 4 — Line-by-line scan with pre-assertion

Use when: the criterion requires co-occurrence of two substrings on the same line.

Pre-assert the outcome in the Given; the When describes a deterministic scan algorithm. No divergence is possible.

```gherkin
Given a string T
And T contains the substring 'X'
And T contains the substring 'Y'
And at least one line of T contains both 'X' and 'Y'
When each line of T containing 'X' is checked for the simultaneous presence of 'Y'
Then at least one line in T contains both 'X' and 'Y'
```

### Phrasing rules

| Avoid | Use instead | Why |
|---|---|---|
| `a non-empty string T` | `a string T` | "non-empty" triggers null/undefined guards with divergent error messages |
| `a non-empty string T containing the source of X` | `a string T` | Descriptive prose triggers type-validation code |
| `When T is searched for 'X'` without a prior `And T contains 'X'` Given | Add `And T contains 'X'` to the Given | Divergence on "not found" handling |
| `Then both X and Y are present` | `When the expression (S.includes('X') && S.includes('Y')) is evaluated` | "Both present" triggers shape divergence (boolean vs object vs void) |

The catalogue will grow. New patterns get added as new classes of divergence are observed in operating gates. Treat the rework register as the source of truth for which patterns recur.

## Anti-patterns

**Gates with exceptions.** A gate that allows "in this case" exceptions is not a gate. It is a recommendation. Gates work because of their deterministic property; exceptions break the property.

**Gates without enforcement.** A documented gate that nobody actually runs is theater. Gates require infrastructure (test runners, linters, MCP servers, review processes) that actually run the checks.

**Gates that exercise judgment.** A gate that asks "is this good enough" is not a gate. It is a review. Gates apply explicit criteria mechanically.

**Gates without classification.** Gate failures should classify the failure to the loop that should have caught it. A failure caught by the CI/CD gate that should have been caught by TDD is a different signal from one caught at CI/CD that no upstream loop could have caught.

## Gate maintenance

Gates require maintenance as the team and the system evolve. New criteria get added as the team learns new failure modes. Old criteria get removed when they no longer apply.

The discipline parallels glossary maintenance: every change goes through review; the gate's criteria themselves are version-controlled.

## What to read next

- `agents/atdd-guardian.md` — the most articulated gate in the methodology
- `concepts/07-the-rework-register.md` — where gate failures are recorded
- `operations/operationalization-sequence.md` — when to establish each gate
