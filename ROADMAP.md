# Open-source release roadmap — UEC i4s Platform

The i4s Platform is released in stages: documentation first, then platform components in order of transferability and review readiness. Dates are targets, not promises; each component ships when its security review is complete.

<!-- TBD: 以下の時期はドラフトです。実態に合わせて調整してください。 -->

| Stage | What | Target |
|---|---|---|
| ✅ **Stage 0 — Documentation** | Architecture, API Gateway design, reference applications (this repository) | **Available now** (Sep 2026) |
| 🔄 **Stage 1 — Edge & sensing** | Sensor firmware samples and LoRa network node reference (privacy-preserving people counter) | 2026 Q4 <!-- TBD --> |
| ⏳ **Stage 2 — Device Abstraction Layer** | Abstraction interfaces, adapter patterns, and our reference adapters for UEC's building systems (see note below) | 2027 H1 <!-- TBD --> |
| ⏳ **Stage 3 — API Gateway Layer** | Gateway implementation: RBAC, audit trail, resource scoping | 2027 <!-- TBD --> |

## Scope: what we release, and what you build

This roadmap covers **platform components** — the layers that provide access to building systems.

The **Control Logic Layer** and the **Agentic AI Layer** are intentionally *not* on this roadmap: they are where each institution, and each developer, builds their own applications on top of the platform APIs. We do not ship them as platform components. Instead, we document what has been built on the platform in [docs/applications.md](docs/applications.md), as examples of what those layers can hold.

## A note on the Device Abstraction Layer

Adapters must match each building's own control systems. Our implementation targets UEC's buildings — their central monitoring systems and vendor-specific interfaces — so what we release is a **reference, not a drop-in**. Adopting institutions will need to survey the control paths of their own buildings (typically together with their facility managers) and implement adapters accordingly. The abstraction interfaces and adapter patterns are what transfer; the concrete adapters are inherently site-specific.

## Why staged?

Two reasons, stated plainly:

1. **Security.** These components control real campus buildings. Each release is preceded by a review that strips deployment-specific configuration, credentials, and anything that would weaken the running campus deployment.
2. **Quality.** We would rather ship components that another institution can genuinely evaluate — with the interfaces, patterns, and documentation needed to adapt them — than dump code that only makes sense inside our own deployment.

## Following along

- **Watch** this repository for release announcements.
- Questions about a specific stage, or interested in evaluating a component early under collaboration? Open an issue or email ta.matsuhashi@uec.ac.jp.
