# i4s-platform-docs

**Documentation for the UEC open smart building platform — "Campus as an AI Sandbox"**

The University of Electro-Communications (UEC), Tokyo, Japan
Institute for Self-Evolving Smart Societies

---

## What this is

This repository documents an open, five-layer smart building platform deployed across multiple buildings on the UEC campus. The platform wraps closed, vendor-locked building systems — HVAC, ventilation, elevators, sensors, energy — behind a vendor-agnostic abstraction layer and a unified, authenticated API Gateway, so that campus infrastructure becomes a transparent, safely accessible development environment.

This is a **documentation-first release**. The platform's core components are being open-sourced in stages (see [ROADMAP.md](ROADMAP.md)); this repository is the entry point for institutions and engineers who want to evaluate the architecture.

## Contents

| Document | Description |
|---|---|
| [docs/architecture.md](docs/architecture.md) | The five-layer architecture: design principles, layer responsibilities, and how they compose |
| [docs/api-gateway.md](docs/api-gateway.md) | API Gateway design: authentication, role-based access, and traceability model |
| [docs/applications.md](docs/applications.md) | Reference applications running on the platform today |
| [ROADMAP.md](ROADMAP.md) | Staged open-source release plan |

## Design in one paragraph

Don't replace the vendor systems. Wrap them. Building equipment is integrated through per-building adapters at the Device Abstraction Layer, sensor data flows continuously into the Data Layer, and every read and write from above passes through the API Gateway — authenticated against campus identity, scoped by role, rate-limited, and fully logged. Control applications and agentic AI sit on top, bounded by safety constraints, and the equipment's native physical controls always override API operations, so control can be safely reclaimed on the spot. Human-on-the-loop oversight is a property of the architecture, not a policy bolted on afterwards.

## Who uses it

The platform serves research and development across campus. It is also the foundation of hands-on, project-based courses at UEC, where students build and deploy applications — including agentic AI — on live building systems; that educational practice was presented at the **EDUCAUSE Annual Conference 2026** poster session (Denver, CO).

## Status

- ✅ Deployed across multiple campus buildings at UEC
- ✅ In production use for research, development, and project-based courses
- 🔄 Core components: staged open-source release in progress ([ROADMAP.md](ROADMAP.md))

## Contact

- Takuto Matsuhashi — ta.matsuhashi@uec.ac.jp
- Issues and discussions on this repository are welcome.

## License

Documentation in this repository is licensed under [CC BY 4.0](LICENSE.md). Licenses for platform code components will be announced per component at release (Apache-2.0 planned <!-- TBD: 最終決定後に更新 -->).
