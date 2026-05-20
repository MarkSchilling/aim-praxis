# Observability Agent

## Operational definition

The observability agent operates at the CI/CD layer extension into production. It monitors error rates, performance, user behavior, and business metric impact, closing the learning loop from working software back to user outcomes.

The agent's output is observations for the rework register (when production issues emerge) and findings for the learning loop (when user outcomes diverge from expectations).

## Inputs

- Production telemetry (error rates, latency, throughput)
- User behavior analytics (feature usage, conversion funnels, abandonment)
- Business metrics (revenue impact, churn, expansion)
- The expected outcomes defined by the VPC and BMC layers

## Outputs

Continuous monitoring with discrete outputs:
- Rework register entries for production incidents
- Findings about feature usage divergent from expectation
- Performance regressions that pass CI/CD but degrade user experience
- Business metric movements correlated with deployments

## Quality criteria

- Rework register entries are classified to the loop that should have caught the failure
- Findings distinguish noise from signal (statistical thresholds)
- Performance regressions are tied to specific deployments
- Business metric correlations are reported with appropriate uncertainty

## Escalation triggers

The agent escalates with elevated priority when:
- Production error rates exceed configured thresholds
- A deployment correlates with a sharp business metric movement
- User behavior changes suggest a fit assumption is wrong
- A previously-working feature is showing degraded use

## Context requirements

- Production observability infrastructure (logs, metrics, traces)
- Analytics infrastructure (user behavior, business metrics)
- VPC and BMC documents (for expected outcomes)
- Deployment history (to correlate changes with effects)

## Boundary specifications

The agent does not:
- Take production action (does not roll back, redeploy, modify)
- Interpret what observations mean strategically
- Suppress findings that look "political"
- Cross privacy boundaries on user data

## Performance metrics

- Mean time to detection for production incidents
- False positive rate on metric movement alerts
- Coverage of findings humans subsequently identified

## Integration with the system

The observability agent is the mechanism that closes the third feedback path — user outcomes back to the VPC and BMC layers. Without observability, CI/CD only catches integration failure. With it, the system catches production-runtime failures and outcome divergences that connect back to outer-layer assumptions.

The agent's findings feed both the rework register (incidents) and the customer research stream (behavioral patterns). The combination is what makes the learning loop close automatically rather than depending on manual post-deployment analysis.
