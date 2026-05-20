# Acceptance Test-Driven Development

## What it is in Aim Praxis

Acceptance Test-Driven Development (ATDD), with roots in the FIT tradition (Ward Cunningham) and developed by Lasse Koskela, Gojko Adzic, and others, is treated in Aim Praxis as the fifth layer. It operates at the cycle time of days and is responsible for story-level acceptance.

ATDD's contribution is the discipline of writing acceptance tests before code, with customer involvement in the test definition. The "three amigos" pattern of product, engineering, and testing collaborating on acceptance is the core practice.

## The systems reading

ATDD operates on three stocks:

**Acceptance criteria** — the customer-agreed conditions under which a story is considered complete. Negotiated; not unilaterally written by engineering.

**Acceptance tests** — the executable form of the criteria. Pass when criteria are met; fail when they are not.

**Demonstrably complete work** — stories that have passed acceptance and been signed off by the customer.

The valves between these stocks are workshopping (criteria → tests) and demonstration (tests → signoff).

## What ATDD catches

ATDD catches completion ambiguity — engineering thinks the story is done; the customer does not. The acceptance criteria were not specific enough; the customer's interpretation differs from engineering's.

This is a different failure from BDD's behavioral drift. BDD catches "the system used to do X, now it does Y." ATDD catches "engineering and customer disagree about what done means." Both are necessary; neither subsumes the other.

## The distinction from BDD

BDD and ATDD overlap in practice but differ in emphasis.

**BDD** is about behavioral specification — what the system should do, expressed in shared language, made executable. The author is typically the engineering team in collaboration with product.

**ATDD** is about customer acceptance — what counts as done from the customer's perspective, made testable. The author includes the customer, not just product and engineering.

In practice, BDD scenarios often serve as ATDD acceptance criteria, but they don't have to. A team can do BDD without ATDD (engineering writes scenarios, customer is not in the room) or ATDD without BDD (customer writes criteria in unstructured English, engineering translates to tests).

Aim Praxis distinguishes them because each catches errors the other can miss. BDD without ATDD produces precise specifications that may not match customer intent. ATDD without BDD produces customer-validated criteria that may not be consistently structured for execution.

## ATDD Guardian

ATDD Guardian is the deterministic gate at the ATDD layer. It enforces explicit criteria mechanically:

- Acceptance criteria must reference only terms in the ubiquitous language glossary
- Criteria must include observable outcomes, not internal state
- Criteria must be measurable (a test can pass or fail based on them)
- Criteria must specify preconditions explicitly

The gate is deterministic: it does not exercise judgment, only checks criteria. Mark Schilling has published an implementation as the `@schilling.mark.a/atdd-guardian` MCP server.

The deterministic property is what makes the gate trustworthy. An agent that exercises judgment about what is "good enough" introduces variation. An agent that mechanically checks criteria reduces variation.

## How to write acceptance criteria

The ATDD Guardian gate enforces structural properties on criteria. Five content rules govern what well-formed criteria look like at the practice level. They emerged from operating ATDD across a working implementation; documenting them so that adopting teams do not have to rediscover them through rework.

**Use concrete identifiers, not template variables.** A criterion that says "the system audits invoice `:id`" leaves two implementations free to interpret `:id` differently — what counts as a valid ID, what happens for absent or malformed IDs. Replace template variables with concrete identifiers and assert their existence in a precondition: "Given an invoice with ID `INV-001` exists; when the system audits invoice `INV-001`; then …". The Given establishes the state; the criterion references it concretely. Template variables in criteria are the most frequent class of ambiguity failure in practice.

**Split criteria that cross system boundaries.** A criterion that says "when I sign in with a federated identity provider" describes a flow spanning multiple systems (frontend, backend, identity provider). Two implementations will model the boundary differently and diverge. Write one criterion per system layer — a backend criterion describing the callback handling and token issuance, and a separate frontend criterion describing how the token is read and stored. The combined criterion is not precise; the per-layer pair is.

**Enumerate boundary cases explicitly.** "Rejects invalid input" is ambiguous — two implementations diverge on whether empty string, whitespace-only, null, and absent are all invalid or only some. State the cases: "Rejects an input that is empty, whitespace-only, absent, or does not satisfy `<specific rule>`." If the criterion intentionally applies only to a non-null, non-empty value, say so in the Given.

**Describe externally observable outcomes, not internal storage.** "The password is saved" is ambiguous — implementations diverge on plaintext versus hashed storage. "A password matching the submitted value cannot be retrieved in plaintext by anyone" is observable. Field names (`passwordHash`, `accessToken`, `userId`) in a criterion are a signal that the author is writing an implementation specification, not an acceptance criterion. Remove them and describe the externally observable guarantee instead.

**Criteria are test-layer-independent.** A criterion that prescribes a test framework, page object, or function signature is specifying the test, not the behavior. Criteria describe what should be true about the system; the test layer (end-to-end, integration, unit) and tooling are implementation choices made downstream in the TDD/ATDD workflow, not in the criterion. Remove references to test frameworks, page objects, function signatures, and return-value shapes from criterion text.

For Gherkin-level phrasing patterns that ensure criteria pass the ATDD Guardian's implementation-divergence check, see "Criteria authoring patterns (ATDD gate)" in `operations/gates.md`. The content rules above are about what a criterion says; the phrasing patterns are about how the Given/When/Then structure says it.

## The customer in the loop

ATDD's most distinctive feature, and the one most often skipped, is the customer's voice in defining "done." Teams that do not have direct customer access often substitute product management as a proxy. This works only if product management has genuine customer-fit insight; otherwise the proxy degrades the acceptance into engineering's own interpretation of what customers want.

Aim Praxis treats customer-in-the-loop as the ideal and product-as-proxy as a fallback that requires explicit awareness of the substitution.

## Cadence

Acceptance criteria are negotiated at story start, written down, and used as the test target throughout development. Demonstration happens at story completion. The cycle is per-story, typically several per week.

## Integration with TDD

ATDD's acceptance tests become the targets that TDD codes against. The TDD inner loop produces code that passes both unit tests (TDD's tests) and acceptance tests (ATDD's tests). The two test suites cover different concerns.

Without ATDD, TDD produces well-tested code that may not match what the customer wanted. Without TDD, ATDD produces customer-accepted features built on rotting foundations. Both are necessary.

## What to read next

- `practices/tdd.md` — the layer below ATDD
- `practices/bdd.md` — the layer above ATDD
- `agents/atdd-guardian.md` — the deterministic gate
