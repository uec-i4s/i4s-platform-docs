# Architecture: the five-layer UEC i4s Platform

<p align="center">
  <img src="../assets/architecture.svg" alt="Five-layer architecture diagram" width="760">
</p>

## Design principles

1. **Transparent and modifiable at every layer.** Conventional building operating systems hide everything. Here, every layer can be observed, analyzed, and extended by authorized campus members. The black box dissolves.
2. **No rip-and-replace.** The platform wraps existing vendor systems rather than replacing them. Institutions keep their current building management investments.
3. **Safe, authenticated access.** Developers get real access to real infrastructure — through authenticated, role-based, fully traceable APIs, never raw device credentials.
4. **Human-on-the-loop oversight.** Operators and faculty can monitor every layer and intervene when needed. Crucially, the equipment's native physical controls always take precedence over API operations: even if an application misbehaves, control can be safely reclaimed on the spot.

## The layers

### 1. Device Abstraction Layer
Unifies heterogeneous vendor devices and protocols behind a common interface. Integration is done per building: for each facility, control paths for HVAC, ventilation, and other equipment are worked out with the building's facility managers, and adapter APIs are designed against the central monitoring systems accordingly. Legacy building equipment, modern IoT sensors, and custom-built devices all appear as uniform resources.

Note that adapters are inherently site-specific: ours are built against UEC's own central monitoring systems and vendor-specific interfaces. What transfers to other institutions is the abstraction interface and the adapter pattern — adopting institutions must survey their own buildings' control paths and implement adapters for them. See the [roadmap](../ROADMAP.md) for what is released at this layer.

### 2. Data Layer
Continuous ingestion and logging of sensor data across campus buildings. Time-series storage plus an ontology that gives the data meaning: which sensor, in which room, in which building, measuring what.

### 3. API Gateway Layer
The single, authenticated entry point for every read and write. Authentication is federated with the university's existing accounts; authorization is role-based for all campus members, with full traceability of who did what, when. See [api-gateway.md](api-gateway.md).

### 4. Control Logic Layer
Where custom applications are deployed: Safe RL, MPC, and rule-based control, plus arbitrary applications built against the Gateway APIs. Safety constraints bound what any application can do to the physical plant. This layer is application territory: what runs here is built by each institution and developer, not shipped as a platform component (see [ROADMAP.md](../ROADMAP.md), "Scope").

### 5. Agentic AI Layer
Agentic AI acting on live data — real-time control logic changes, energy optimization, and occupancy-aware environment control. Because the layers below are open, developers can observe which sensors an agent reads and why it acts — behavior that stays hidden in conventional building OSs. Like the Control Logic Layer, this is application territory — each adopter builds and owns what runs here.

## Physical deployment

The platform currently runs across the UEC campus (Tokyo), spanning lecture, library, and research facilities, connected to a secure campus sensor network (including a LoRa network independent of the campus LAN for low-power sensors).

As of September 2026, the platform integrates **over 1,000 devices in 24 buildings**: 594 sensors and 416 actuators.

| | Count | Buildings | Types |
|---|---|---|---|
| **Sensors** | 594 | 24 | 16 (CO₂, energy, temperature, humidity, occupancy, power, light, sound, pressure, eTVOC, discomfort index, heatstroke risk, radiant temperature, gate, people counting, pollen) |
| **Actuators** | 416 | 4 | 7 (lighting, air conditioners, ventilators, HDS control stops, signal lights, an elevator, a display wall) |

Actuation is concentrated where write access has been worked out with facility managers — most densely in Building E11 (330 controllable lights, 21 air conditioners, 19 ventilators) and the Library, Building E3 — while sensing covers the campus broadly. The full device inventory:

<details>
<summary><b>Device inventory by building (September 2026)</b></summary>

**Actuators**

| Building | Type | Count |
|---|---|---|
| E3 (Library) | Air Conditioner | 10 |
| E3 (Library) | Light | 12 |
| E3 (Library) | Ventilator | 12 |
| E11 | Air Conditioner | 21 |
| E11 | HDS control stop | 8 |
| E11 | Light | 330 |
| E11 | Ventilator | 19 |
| E36 | Signal light (Patlite) | 1 |
| W9 | Display wall | 1 |
| W9 | Elevator | 1 |
| W9 | Signal light (Patlite) | 1 |

**Sensors**

| Building | Types (count) |
|---|---|
| A | CO₂ (10) |
| B | CO₂ (4) |
| C | CO₂ (8) |
| E_daigaku | energy monitor (2) |
| E1 | energy monitor (12) |
| E2 | energy monitor (1) |
| E3 (Library) | CO₂ (9), energy monitor (19), gate (1), occupancy (30), humidity (30), light (30), temperature (30) |
| E4 | CO₂ (4) |
| E5 | CO₂ (2), energy monitor (34) |
| E6 | CO₂ (4), energy monitor (13) |
| E8 | energy monitor (1) |
| E11 | CO₂ (26), occupancy (48), humidity (26), power consumption (64), radiant temperature (3), temperature (26) |
| E34 | discomfort index, eTVOC, heatstroke risk, humidity, light, pressure, sound, temperature (1 each) |
| E36 | discomfort index, eTVOC, heatstroke risk, humidity, light, pressure, sound, temperature (3 each) |
| E37 | discomfort index, eTVOC, heatstroke risk, humidity, light, pressure, sound, temperature (1 each) |
| W1 | energy monitor (3) |
| W2 | CO₂ (6), energy monitor (1) |
| W4 | energy monitor (3) |
| W5 | CO₂ (3) |
| W6 | CO₂ (1), energy monitor (1) |
| W7 | energy monitor (1) |
| W8 | CO₂ (2), energy monitor (2) |
| W9 | people counter (1), pollen (1), discomfort index, eTVOC, heatstroke risk, humidity, light, pressure, sound, temperature (9 each) |
| W10 | CO₂ (6), energy monitor (14) |

</details>

## Transferability

The layer structure itself is domain-agnostic — smart buildings are its first deployment — and intentionally minimal in its assumptions: any institution with existing building systems and a campus network can, in principle, reproduce the stack. The practical work of adoption is less about code than about integration and governance — designing the per-building adapters with facility managers, binding the Gateway to the institution's identity system, and agreeing on access policies and audit responsibilities. The staged open-source release ([ROADMAP.md](../ROADMAP.md)) covers the platform layers and starts with the most reusable ones; the Control Logic and Agentic AI layers are, by design, each adopter's own application space.
