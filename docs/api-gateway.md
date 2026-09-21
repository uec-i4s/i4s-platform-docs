# API Gateway: safe, authenticated access to a real campus

> This document describes the *design* of the Gateway layer. Endpoint URLs, schemas, and deployment details will be published together with the corresponding code release ([ROADMAP.md](../ROADMAP.md)).

## Why a single gateway

Opening campus infrastructure to thousands of campus members only works if access is **safe by construction**. The Gateway is the one and only path between applications (including AI agents) and the building systems below. Nothing talks to devices directly.

This single choke point is what lets us hand real control to developers who are not building professionals — including students: every capability that reaches the physical plant is authenticated, scoped, and logged.

## Access model

| Aspect | Design |
|---|---|
| **Authentication** | Federated with the university's existing accounts — every request is tied to a real campus member |
| **Authorization** | Role-based access control: read scopes and write scopes are granted per role (student / faculty / operator / service), per resource group |
| **Traceability** | Full audit trail: who called what, when, with what effect. Operation history is reviewable by faculty and building operators |
| **Safety** | Write operations pass through safety constraints in the Control Logic Layer; physical actuation is bounded regardless of what an application requests |
| **Physical precedence** | The equipment's native physical controls always override API operations — control can be reclaimed on the spot at the device |
| **Blast radius** | Resource scoping limits any credential to the rooms/buildings it was granted — an application cannot touch systems outside its scope |

## What developers experience

From a developer's point of view, the campus looks like a well-documented web API: discover sensors, read live and historical data, and — with the appropriate role — actuate devices within granted scopes. The barrier to a first build is deliberately low; the audit trail, safety bounds, and physical precedence are what make that low barrier responsible.
