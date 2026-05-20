# Stocks and Flows

## The concept

A stock is something that accumulates. A flow is the rate at which something moves into or out of a stock. Together, stocks and flows are the primary unit of analysis in systems thinking.

The bathtub metaphor is canonical. The water in the tub is a stock. The faucet is an inflow. The drain is an outflow. The water level at any moment is the result of the integral of inflows and outflows over time. If the inflow rate exceeds the outflow rate, the level rises. If the outflow exceeds the inflow, the level falls. If they balance, the level is stable.

This metaphor extends to any accumulation. Cash is a stock; revenue is an inflow; expense is an outflow. Customers are a stock; acquisition is an inflow; churn is an outflow. Code is a stock; commits are an inflow; deletions are an outflow.

## Why this matters for software development

Most software development thinking is in terms of activities (verbs): "we are writing code," "we are running tests," "we are deploying." Activities are flows. But every flow is changing the level of some stock, and the stock levels are what determine the system's behavior.

A team that thinks only about flows can be very busy without producing the stock-level changes they need. A team that thinks in stocks and flows can ask: which stock is too low? Which is too high? What flow is filling it too slowly? What flow is draining it too fast?

This is the diagnostic power that the activity-only view lacks.

## Examples in Aim Praxis

**Story map as bathtub.** The story map is a stock — an accumulation of stories at various levels of refinement. Five flows fill it: user discovery, blue-sky ideation, task identification, detail refinement, stakeholder input. Five flows drain it: release slicing, story workshopping, dev specification, scope depletion, product delivery. The story map's level rises when inflows exceed outflows; falls when outflows exceed inflows.

**The pack rat archetype.** When a team's inflow rate to the story map exceeds the outflow rate, the map accumulates discretionary stories. The backlog appears impressive but velocity does not change. This is pack rat syndrome, named for the household pattern that produces the same outcome.

**Working software as terminal stock.** Working software is the destination stock of the development system. It grows only from product delivery (one specific outflow from the story map, via the development pipeline). The other four outflows drain the map but do not yet produce value.

## Why most teams miss this

The activity-oriented view of software development is reinforced by every tool teams use. Jira shows tickets in motion; CI/CD pipelines show builds running; sprint reviews celebrate stories completed. The flows are everywhere visible; the stocks are not.

The discipline of asking "what is the level of this stock right now, and what is its rate of change?" requires deliberate effort. It is not how Jira reports, not how velocity charts work, not how standups are run. The stock-and-flow view has to be added.

Once added, it is hard to unsee. A team that has internalized stocks and flows can no longer look at a backlog without asking what's filling it and what's draining it.

## The leverage insight

The most important consequence of stock-and-flow thinking: leverage lives in the valves (rates), not the stocks (levels).

Teams routinely try to manage stocks directly. "We need to reduce our backlog." But the backlog is the integral of past inflows and outflows; you cannot reach into it and reduce it. You can only change the rates going forward. The leverage is in the valves: throttle the inflows, widen the outflows, and the stock level changes as a consequence.

This is why most attempts to "clean up the backlog" fail. They are operating on the stock when they need to be operating on the valves.

## Recognizing stocks and flows in practice

Stocks have units that include time integration: "200 stories," "$50,000 cash," "1,000 customers." You can take a snapshot of a stock at a moment.

Flows have units that include time division: "10 stories per week," "$10,000 revenue per month," "30 customer acquisitions per quarter." You cannot take a snapshot of a flow; you can only measure its rate over an interval.

A simple test: if you can ask "how much?" and get a number, it's a stock. If you can only ask "how fast?" and get a rate, it's a flow.

## Hidden stocks

Many of the most important stocks in a software development system are intangible and therefore easy to miss. Shared understanding is a stock. Team morale is a stock. Trust between engineering and product is a stock. Accumulated knowledge of the codebase is a stock.

These stocks have inflows (conversation, successful collaboration, learning) and outflows (turnover, conflict, forgetting). They are not tracked in any tool. They produce significant downstream effects on every visible metric.

Aim Praxis names some of these explicitly as compounding artifacts: the ubiquitous language glossary, the lessons learned library, the process capability statement. By making them version-controlled and queryable, the methodology converts them from invisible stocks into manageable ones.

## What to read next

- `concepts/02-aging-chains.md` — what happens when stocks are arranged in sequence
- `concepts/03-feedback-loops.md` — what happens when outputs become inputs
- `practices/story-mapping.md` — the bathtub model applied to a specific practice
