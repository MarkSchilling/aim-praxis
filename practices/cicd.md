# Continuous Integration / Continuous Deployment

## What it is in Aim Praxis

Continuous Integration / Continuous Deployment (CI/CD), articulated by Jez Humble and David Farley in *Continuous Delivery* (2010), is treated in Aim Praxis as the seventh and innermost layer. It operates at the cycle time of seconds to hours and is responsible for integration and deployment.

CI/CD's contribution is the discipline of keeping the main branch always deployable and the system always in a known integrated state. Long release cycles are recognized as a hiding place for problems; continuous integration surfaces them immediately.

## The systems reading

CI/CD operates on three stocks:

**Integrated build** — the system in its current integrated state, with all tests green

**Deployed artifact** — the build in deployable form, having passed all pipeline checks

**Working software** — the deployed artifact running in production, observable by users

The valves are integration (clean code → integrated build), deployment (integrated build → deployed artifact), and production (deployed artifact → working software).

## What CI/CD catches

CI/CD catches integration failure — code that works alone but does not work together. Environments drift; deployment state is inconsistent; the unit-level work passes its own tests but the integrated system does not function.

This is the loop with the shortest cycle time and the narrowest scope. It catches things no other loop can see because no other loop operates at this time scale or this granularity.

## The observability extension

Standard CI/CD focuses on the build-and-deploy side: get clean code into production. Aim Praxis extends CI/CD with an observability function that operates on the production side: what happens after the artifact is deployed.

The observability agent watches error rates, performance regressions, user behavior changes, business metric impact. Its output feeds the rework register (when production issues emerge) and the learning loop (when user outcomes diverge from expectations).

Without observability, CI/CD only catches integration failure. With observability, CI/CD catches integration failure plus the production-runtime failures that integration testing cannot reach.

## The CI/CD gate

The CI/CD gate is deterministic: it does not exercise judgment, only enforces explicit criteria.

- All unit tests pass
- All acceptance tests pass
- All integration tests pass
- Static analysis produces no errors
- Security scans produce no critical findings
- Deployment dry-run succeeds

A change that fails any criterion does not reach production. The gate has no override path for "this one is urgent" — the criteria are enforced uniformly. Bypassing the gate is what creates production incidents that the team has to remediate.

## What CI/CD does NOT catch

CI/CD catches integration and deployment failure. It does not catch:

- Whether the deployed system serves users well (observability extension's job, feeding back to outer layers)
- Whether the code internally degraded (TDD's job)
- Whether the behavior matches specification (BDD's job)
- Whether the customer agrees the work is done (ATDD's job)
- Whether the work is the right work (Story Mapping, VPC, BMC)

A team with strong CI/CD and weak outer loops ships continuously, ships fast, and may ship the wrong thing fast.

## The learning loop extension

Aim Praxis treats the observability agent as the mechanism that closes the learning loop from production back to the VPC layer. User outcomes observed in production become signal that validates or invalidates fit assumptions.

This is the loop most commonly broken in real-world systems. Teams ship continuously but do not observe outcomes; or they observe technical metrics but not user outcomes; or they observe user outcomes but do not feed them back to strategy. The observability agent's job is to make this loop close automatically rather than requiring manual effort.

## Cadence

CI/CD runs on every commit. The pipeline executes in minutes; observability runs continuously. The cadence is set by code-change rate, not by external scheduling.

## Integration with the rework register

Every CI/CD gate failure is a candidate for the rework register. The classification is which loop should have caught the failure that CI/CD caught — typically TDD (for unit issues) or integration test gaps (a CI/CD-internal issue) or environmental drift (an infrastructure issue).

Over time, the pattern of CI/CD-caught failures reveals where the team's upstream gates are weakest.

## What to read next

- `concepts/07-the-rework-register.md` — how CI/CD failures feed system learning
- `agents/observability-agent.md` — the agent that extends CI/CD to production
- `practices/tdd.md` — the layer above CI/CD
