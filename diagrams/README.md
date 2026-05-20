# Diagrams

This directory contains the SVG source for all diagrams generated during the methodology design conversation. Each diagram is referenced from one or more of the methodology documents.

## Index

### 00. Ship Audit overview
**File:** `00-ship-audit-overview.svg`
The initial stock-and-flow analysis of Ship Audit that started the methodology design conversation. Bonus diagram, not part of the formal 13.

### 01. Story Map aging chain
**File:** `01-story-map-aging-chain.svg`
Six stocks representing the maturation of information from raw ideas through refined stories to working software, with feedback loops via rework, lessons learned, and aim alignment. Referenced from `concepts/02-aging-chains.md` and `practices/story-mapping.md`.

### 02. Story Map bathtub
**File:** `02-story-map-bathtub.svg`
Five inflows fill the Story Map stock from the left; five outflows drain it toward working software on the right. Imbalance creates pack rat syndrome. Referenced from `practices/story-mapping.md` and `system/inflows-and-outflows.md`.

### 03. Detail refinement aging chain
**File:** `03-detail-refinement-aging-chain.svg`
Detail refinement reframed as a valve between two stocks (unrefined backbone → refined tasks) rather than as an external inflow. Referenced from `concepts/02-aging-chains.md`.

### 04. Inflow sources
**File:** `04-inflow-sources.svg`
The five sources that fill the Story Map: user reality, team imagination, business intent, market signals (all exogenous), and prior knowledge stocks (endogenous). Referenced from `system/sources-and-destinations.md`.

### 05. Outflow destinations
**File:** `05-outflow-destinations.svg`
The destinations of the five outflows: prioritized release backlogs, acceptance-ready stories, work in progress, future map / cut list, and working software. Plus the two further stocks working software feeds: user outcomes (exogenous) and rework register (endogenous feedback). Referenced from `system/sources-and-destinations.md`.

### 06. BDD stocks aging chain
**File:** `06-bdd-stocks-aging-chain.svg`
Examples flow through scenarios into executable step definitions, producing living documentation and verification state. Defects feed back upstream into language refinement. Referenced from `practices/bdd.md`.

### 07. Five-loop SDLC
**File:** `07-five-loop-sdlc.svg`
Five practices operating at different cycle times as nested loops: Story Mapping (outer) through CI/CD (inner). Each loop catches a class of error invisible to the others. Referenced from `concepts/04-the-seven-layers.md`.

### 08. Agentic SDLC
**File:** `08-agentic-sdlc.svg`
The SDLC with agents placed at valves and gates. Coral diamonds are agents; purple stocks are information; teal gates enforce quality. Human judgment zone preserved at aim, acceptance, release slicing, and pattern interpretation. Referenced from `agents/placement-philosophy.md`.

### 09. Agentic SDLC with coding agent
**File:** `09-agentic-sdlc-with-coding-agent.svg`
The agentic SDLC extended to include the coding agent in the TDD inner loop, constrained on both sides by ATDD Guardian upstream and CI/CD gate downstream. Referenced from `agents/coding-agent.md`.

### 10. Business Model Canvas as a system
**File:** `10-business-model-canvas-system.svg`
The nine canvas boxes arranged as stocks in a three-flow cycle (value creation, delivery, capture), with hidden stocks the canvas omits (operational knowledge, brand, customer goodwill, cash reserves) and the three implied loops (growth, efficiency, learning). Referenced from `practices/business-model-canvas.md`.

### 11. Value Proposition Canvas as a system
**File:** `11-value-proposition-canvas-system.svg`
Customer jobs drive pain and gain stocks; supplier products install valves that drain pains and fill gains. Hidden stocks (switching cost, trust, awareness, urgency) and three loops (relief, expectation, disappointment) made explicit. Referenced from `practices/value-proposition-canvas.md`.

### 12. Integrated seven-practice system
**File:** `12-integrated-seven-practice.svg`
Seven practices stacked as nested aging chains. Business model assumptions flow down through value proposition, story map, behavior, acceptance, code, and deployment. Value and learning flow back up. The full integrated picture. Referenced from `system/integrated-system.md` and `docs/methodology.md`.

### 13. Integrated seven-practice with agents
**File:** `13-integrated-seven-practice-with-agents.svg`
The full integrated system with all agents placed: market signal, customer research, refinement, workshopping, glossary, ATDD Guardian, coding agent, CI/CD gate, observability, PDSA. Human judgment zone explicitly preserved. The canonical reference diagram for Aim Praxis. Referenced from `system/integrated-system.md`, `agents/placement-philosophy.md`, and `docs/methodology.md`.

## Viewing

Each SVG can be viewed in any modern browser, in markdown previewers that support SVG, or in any image viewer. They are designed to work in both light and dark modes (using the Anthropic color ramps).

The diagrams have a fixed viewBox width of 680px optimized for inline display in chat-style interfaces. They scale fluidly for other display contexts.

## Source

These diagrams were generated during the Aim Praxis methodology design conversation on 2026-05-19. The full source for each (with comments and the conversation context) is preserved in `/mnt/transcripts/2026-05-19-18-29-52-aim-praxis-methodology-build.txt`.

## Updating

When the methodology evolves and diagrams need updating:

1. Update the corresponding SVG file
2. If the change is significant, archive the old version with a date suffix (e.g. `12-integrated-seven-practice-2026-05-19.svg`)
3. Update the description in this README
4. Update references in the documents that cite the diagram
