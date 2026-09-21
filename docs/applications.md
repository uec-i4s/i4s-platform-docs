# Reference applications

Applications currently running on the UEC i4s Platform (smart building deployment), and the layers they exercise. All of them operate on live campus infrastructure through the API Gateway — none bypass it.

## Elevator-integrated autonomous mobile robot (Building W9)

An autonomous mobile robot travels between floors on its own by calling the building's elevator API. A live proof of concept for cross-system integration: robot navigation (external system) × elevator control (Device Abstraction + Gateway).

*Layers exercised: Device Abstraction → API Gateway → Control Logic*

## Library crowding prediction (Library, Building E3)

An application forecasts congestion from infrared people counts and CO₂ levels, using continuously logged time-series data.

*Layers exercised: Data Layer → API Gateway*

## Privacy-preserving people counting on a campus-wide sensor network

An edge-AI camera device senses occupancy without capturing identities — counting people, not faces. Paired with a secure LoRa sensor network that runs independently of the campus LAN, the sensor package is deployable anywhere on campus.

*Layers exercised: Device Abstraction → Data Layer; network: LoRa (campus-LAN independent)*

## Agentic building control (e-Nexus — in progress, AY2026)

Experimental agentic AI control of a campus building. Role-divided agents converse with each other, exposing which sensors they read and why they act — making the control loop observable end to end. Human-on-the-loop oversight applies throughout, and the building's physical controls always take precedence.

*Layers exercised: full stack — Data → Gateway → Control Logic → Agentic AI*

---

## Context

Several of these applications were built by students in UEC's year-long project-based courses, which use the platform as their development environment; student work has been presented at academic conferences and submitted to external competitions. The educational practice built on this platform was presented at the **EDUCAUSE Annual Conference 2026** poster session (Denver, CO).

If you build on the platform and would like your application listed here, open an issue.
