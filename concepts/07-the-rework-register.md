# The Rework Register

## The concept

The rework register is the team's classified failure history. Every failure in the system flows into the register, classified by which loop caught it, which loop should have caught it, what the immediate cause was, and what change might prevent recurrence.

The register is one of the five compounding artifacts. It is also the methodology's primary diagnostic instrument. A team that maintains a healthy rework register can answer questions about its system that no other artifact supports.

## Why a unified register

Most teams have multiple, disconnected failure-tracking systems: a bug tracker for code defects, a postmortem document for incidents, a retrospective for process issues, a customer complaint log for product issues. Each system captures part of the failure picture; none captures the whole.

The unified rework register collects failures from every layer of the seven-layer system into a single classified store. This makes cross-layer patterns visible. A recurring production issue that traces back to a BDD ambiguity that traces back to a VPC assumption that was never validated — that pattern is invisible in any single layer's failure tracking but obvious in a unified register.

## The classification scheme

Each register entry captures:

**Which loop caught the failure.** CI/CD, TDD, ATDD, BDD, Story Mapping, VPC, or BMC. This is where the failure was detected.

**Which loop should have caught it.** Often a different loop from the one that actually did. A production incident caught by observability might "belong" to TDD (a unit-test gap) or to BDD (a behavioral scenario gap) or to ATDD (an acceptance criterion that did not specify the case).

**The immediate cause.** What happened, in concrete terms. Not "the system failed" but "the import-CSV function threw an exception when the file contained a UTF-8 byte order mark."

**The proposed remediation.** What change to upstream stocks or valves would prevent recurrence. A new acceptance criterion. A glossary addition. A refinement rule. A lessons-learned entry.

**Status.** Open, in remediation, closed. The register tracks both individual failures and the team's response.

## How the register supports learning

The compounding property of the register comes from its query patterns. Each query produces different insights.

**Query by "which loop should have caught it."** Reveals where the team's gates are weakest. If many production incidents should have been caught by TDD, the unit test discipline needs strengthening. If many failures should have been caught by BDD, the scenario coverage is thin.

**Query by immediate cause similarity.** Reveals recurring patterns. The PDSA agent fires when the same pattern of immediate cause appears three or more times. The threshold filters noise from signal.

**Query by classification stability.** Reveals diagnostic clarity. If failures are consistently re-classified as the team's understanding deepens, the team is learning. If classifications are stable from the start, the team is either confident or not looking hard enough.

**Query by remediation outcome.** Reveals what kinds of upstream change actually prevent recurrence. Over time, the team learns which interventions are effective.

## The PDSA agent's role

The PDSA agent monitors the register continuously. When a pattern of immediate cause appears three or more times across recent entries, the agent fires. The output is a proposal: this pattern has recurred; here is the recommended upstream change; here is the evidence base.

The proposal goes to humans for review. The agent does not implement the change. The human decision is whether the pattern is real, whether the proposed remediation is correct, and whether the cost of the remediation is justified by the recurrence rate.

This human-in-the-loop pattern is deliberate. Pattern detection is something agents do well; pattern interpretation is something humans do well. The register and the PDSA agent together produce candidates for human decision; they do not replace the decision.

## The register as audit trail

A side effect of the unified register is that it becomes the team's audit trail for system health over time. Trends become visible: failures are increasing or decreasing, certain categories are growing or shrinking, certain layers are improving or degrading.

This audit trail is also useful externally. A team that can show a quarterly trend of declining failure rates with documented upstream changes has evidence of a working improvement system. A team that can only show postmortems for major incidents has reactive evidence.

## Anti-patterns

**Blame-classified register.** Some teams classify failures by who caused them rather than where in the system they originated. This violates Deming's central insight that 94% of failures belong to the system. A register that names individuals is being used wrong.

**Bug-tracker as register.** Bug trackers capture defects in code. They do not capture failures in upstream artifacts (a refined task that was unclear, a scenario that was ambiguous, a fit assumption that was wrong). A bug tracker is a subset of a register; the register must include the upstream artifacts.

**Write-once register.** Some teams record failures but never re-query the register. Without querying, the register is just storage. The value is in the queries, not the entries.

**No remediation tracking.** A register that records failures but does not track what was done about them is half a register. The remediation side is what closes the learning loop.

## The register's place in the integrated system

In the integrated seven-layer diagram, the rework register sits at the bottom, receiving inputs from every layer and feeding the compounding artifacts. This placement is structural: the register is the single point where failure information from across the system converges, and it is the source from which system-level learning radiates.

Without the register, the seven-layer system has feedback at each layer but no integration across layers. With the register, the system can learn about itself at the system level — not just about its components.

## What to read next

- `concepts/06-compounding-artifacts.md` — how the register relates to the other artifacts
- `agents/pdsa-agent.md` — the agent that monitors the register
- `context/mcp-servers.md` — how to expose the register to agents
