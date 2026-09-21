# Open-source release roadmap

The platform is released in stages: documentation first, then components in order of transferability and review readiness. Dates are targets, not promises; each component ships when its security review is complete.

<!-- TBD: 以下の時期・順序はドラフトです。実態に合わせて調整してください。 -->

| Stage | What | Target |
|---|---|---|
| ✅ **Stage 0 — Documentation** | Architecture, API Gateway design, educational model (this repository) | **Available now** (Sep 2026) |
| 🔄 **Stage 1 — Edge & sensing** | Sensor firmware samples and LoRa network node reference (privacy-preserving people counter) | 2026 Q4 <!-- TBD --> |
| ⏳ **Stage 2 — Device Abstraction Layer** | Vendor-agnostic device adapters and protocol unification core | 2027 H1 <!-- TBD --> |
| ⏳ **Stage 3 — API Gateway Layer** | Gateway implementation: RBAC, audit trail, resource scoping | 2027 <!-- TBD --> |
| ⏳ **Stage 4 — Data & Control reference** | Data layer schemas/ontology and Control Logic Layer application templates | 2027 <!-- TBD --> |
| ⏳ **Stage 5 — Agentic AI Layer reference** | Reference agents and the multi-agent building-control experiments (e-Nexus) | TBD |

## Why staged?

Two reasons, stated plainly:

1. **Security.** These components control real campus buildings. Each release is preceded by a review that strips deployment-specific configuration, credentials, and anything that would weaken the running campus deployment.
2. **Quality.** We would rather ship components that another institution can actually evaluate than dump a repository that only we can run.

## Following along

- **Watch** this repository for release announcements.
- Questions about a specific stage, or interested in evaluating a component early under collaboration? Open an issue or email ta.matsuhashi@uec.ac.jp.
