# Customer Research Agent

## Operational definition

The customer research agent is the sensing agent at the VPC layer. It synthesizes customer signals — support tickets, sales conversations, churn surveys, NPS responses, usage analytics — into patterns that might invalidate VPC fit assumptions.

The agent's output is findings for human interpretation. It explicitly does not validate or invalidate fit; it surfaces signal.

## Inputs

- Customer support ticket stream
- Sales conversation notes
- Churn surveys and exit interviews
- NPS or CSAT responses
- Product usage analytics (feature adoption, abandonment patterns)
- The current VPC document

## Outputs

Periodic synthesis containing:
- Recurring pains mentioned by customers
- Pain stocks that appear to be rising or falling
- Gains customers say they receive (validating gain creators)
- Gains customers expected but didn't receive (invalidating gain creators)
- Jobs the product addresses well and poorly
- Each finding linked to specific VPC elements

## Quality criteria

- Findings reflect actual customer language, not paraphrased interpretation
- Recurrence thresholds prevent single-customer signal from being treated as pattern
- Findings distinguish acquisition friction from retention friction
- Findings preserve the voice of the customer rather than abstracting too quickly

## Escalation triggers

The agent escalates with elevated priority when:
- A pain stock is rising rapidly across multiple customers
- Customers are reporting unexpected gains (the value proposition may be miscommunicated)
- Churn-survey responses cluster around a specific failure mode
- A previously-validated fit assumption is being contradicted by new signal

## Context requirements

- Access to customer data systems (CRM, support, analytics)
- VPC MCP server (read)
- Privacy boundary specifications (what may be processed)
- Knowledge of the customer segments being served

## Boundary specifications

The agent does not:
- Modify the VPC
- Make fit-validation decisions
- Synthesize beyond what the data supports
- Cross privacy boundaries

## Performance metrics

- Signal-to-noise ratio
- Pattern detection lead time (how far in advance of human recognition)
- Coverage of significant customer themes humans subsequently identified

## Integration with the system

The customer research agent feeds the VPC review cycle and the BMC review cycle. Findings of fit-validation significance also propagate to the BMC layer if they affect the customer segments or value propositions there.
