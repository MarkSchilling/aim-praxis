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
