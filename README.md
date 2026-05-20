# Aim Praxis

**Pronunciation:** Aim PRAK-sis

A software development methodology that treats building software as a system, grounded in Deming's System of Profound Knowledge and broader systems thinking.

## Why this exists

Most software methodologies optimize for one cycle time. Agile optimizes for weekly delivery. DevOps optimizes for deployment frequency. TDD optimizes for unit-level design. Each is correct at its own scale, and each leaves the other scales unaddressed.

A team that deploys continuously can still be building software for a market that doesn't exist. A team with perfect unit tests can still ship features that don't solve the customer's actual problem. A team with a beautiful story map can still produce code that's hard to change.

The error each methodology catches is invisible to the others. The methodology that catches them all at once doesn't exist — yet.

Aim Praxis is the integration of seven existing practices into one system, organized by the structural insight that they form a stack of nested feedback loops at different cycle times. Each loop catches errors invisible to the others. Together they produce software aligned with stated intentions at every scale the work actually happens at.

## What it is

[Same as above]

## What's different

[Same as above]

## Worked example: Ship Audit

The methodology is being applied to Ship Audit, a SaaS product for SMB e-commerce shipping invoice auditing. Ship Audit's development is the methodology's first proof. See [`examples/ship-audit/`](examples/ship-audit/) for the worked case study — system aim, BMC and VPC evolution, story map development, glossary growth, rework register patterns, and the compounding artifacts as they accumulated.

This is not a methodology built in the abstract. It's the methodology I've found I needed to build a SaaS product as a solo founder while preserving the discipline that forty years of consulting taught me matters for software that lasts.

## Where to start

[Same as above]

## Lineage

[Same as above]

## Contributing

Aim Praxis is currently developed by one person (me). The methodology will benefit from outside practitioners applying it to their own work and reporting back — both successes and failures.

If you've applied any part of Aim Praxis to a real project, I'd love to hear about it. Open an issue with the tag `application-report` and tell me what worked, what didn't, and what you'd change.

Pull requests for typos, broken links, and obvious errors are welcome without prior discussion. Larger contributions — new concepts, changes to the practice documents, new ADRs — should start with an issue so we can talk about whether and how to integrate them. The methodology has a coherent center; changes need to preserve it.

## License

Apache License 2.0. See [`LICENSE`](LICENSE).

## Author

[Same as above]
