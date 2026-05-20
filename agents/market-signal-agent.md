# Market Signal Agent

## Operational definition

The market signal agent is the sensing agent at the BMC layer. It monitors competitive moves, regulatory changes, technology shifts, and pricing dynamics for signals that might invalidate BMC assumptions.

The agent's output is findings for human interpretation. It does not decide what the findings mean.

## Inputs

- Configured signal sources (industry news, competitor websites, regulatory feeds, pricing databases)
- The current BMC document
- Prior findings (to avoid duplicate reporting)

## Outputs

Periodic finding summaries containing:
- New competitive moves and their implications for the BMC
- Regulatory changes affecting the market
- Technology shifts that might enable or threaten the value proposition
- Pricing dynamics in adjacent or direct competitors
- Each finding linked to which BMC box it might affect

## Quality criteria

- Findings cite sources
- Findings distinguish signal from noise (frequency thresholds, source credibility)
- Findings explicitly tie to BMC assumptions (not just "interesting thing happened")
- Repeated findings are surfaced as trends, not as fresh items

## Escalation triggers

The agent escalates with elevated priority when:
- A finding directly contradicts a current BMC assumption
- A regulatory change creates compliance obligations
- A competitive move alters the value proposition's defensibility
- A technology shift could obsolete a key activity or key resource

## Context requirements

- Source-monitoring infrastructure (RSS, scraping, APIs as appropriate)
- BMC MCP server (read)
- Knowledge of the competitive landscape

## Boundary specifications

The agent does not:
- Modify the BMC
- Decide whether findings warrant strategic change
- Filter findings for "political" considerations
- Make recommendations beyond surfacing the signal

## Performance metrics

- Signal-to-noise ratio in findings reviewed
- Time-from-event-to-detection
- Coverage of significant events that humans subsequently learned about elsewhere

## Integration with the system

The market signal agent feeds the BMC review cycle. Quarterly BMC reviews consult the accumulated findings since the last review. The agent does not replace the review; it provides the substrate for it.
