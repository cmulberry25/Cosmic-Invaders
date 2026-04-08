# Cosmic Commanders for ThinkReality A3

> **Project Discovery README**  
> Reference application architecture for an **AR Space Invaders-style multiplayer experience** built in **Unity** for **Lenovo ThinkReality A3**, integrating **Unity Services/SDKs** with **partner XR SDKs**.

---

## Table of Contents

- [Overview](#overview)
- [Vision](#vision)
- [Strategic Messaging](#strategic-messaging)
- [Solution Scope](#solution-scope)
- [Capability Model](#capability-model)
- [Bill of Materials](#bill-of-materials)
- [Reference Architecture](#reference-architecture)
- [Runtime Service Sequence](#runtime-service-sequence)
- [Content Supply Chain Sequence](#content-supply-chain-sequence)
- [Service-to-Capability Mapping](#service-to-capability-mapping)
- [Key Architecture Decisions](#key-architecture-decisions)
- [Commercial and Technical Value](#commercial-and-technical-value)
- [Functional View](#functional-view)
- [Non-Functional Considerations](#non-functional-considerations)
- [Assumptions and Dependencies](#assumptions-and-dependencies)
- [Risks and Open Questions](#risks-and-open-questions)
- [Suggested Repository Structure](#suggested-repository-structure)
- [Next Steps](#next-steps)
- [Glossary](#glossary)

---

## Overview

**Cosmic Invaders** is a shared, spatial AR combat experience for **ThinkReality A3** where players see and battle alien invaders in the real world using gesture, gaze, controller, or hand-driven interactions.

This project discovery defines a **reference application architecture** that brings together:

- **ThinkReality / partner XR SDKs**
- **OpenXR**
- **Unity XR Interaction Toolkit**
- **Unity client gameplay runtime**
- **Unity Cloud Services**
- **Unity content supply chain tooling**

The architecture is intentionally separated into three planes:

1. **ThinkReality A3 Client Runtime**
2. **Unity Cloud Services**
3. **Content Supply Chain**

---

## Vision

Create a **premium, category-defining AR multiplayer game** on ThinkReality A3 that demonstrates:
<img width="1024" height="1536" alt="download (1)" src="https://github.com/user-attachments/assets/8aec111a-bc4f-44f8-aaa5-24756df09ae3" />


- immersive spatial gameplay
- synchronized shared-world encounters
- low-latency multiplayer sessions
- configurable LiveOps
- competitive progression and rewards
- continuous content delivery without requiring a full app rebuild

---

## Strategic Messaging

- **A showcase of how Unity accelerates creation and reduces creative friction by enabling continuous release of real-time 3D content generation without full application rebuilds.**

- **The experience is powered by Unity Asset Manager, Version Control, Pipeline Automation, Asset Transformer with 3D Data Streaming, and Cloud Content Delivery to govern, optimize, package, and distribute real-time 3D ready content on-demand.**

---

## Solution Scope

### In Scope

- ThinkReality A3 AR gameplay runtime
- Shared spatial multiplayer session architecture
- Unity service integration pattern
- Content pipeline and content delivery architecture
- Capability naming and taxonomy
- Runtime and supply-chain sequence views
- LiveOps and progression services
- Analytics and adaptive intelligence integration

### Out of Scope

- Final art direction and detailed game design
- Complete UX/UI wireframes
- Production infrastructure sizing
- Detailed anti-cheat implementation
- Store publication and marketplace packaging
- Dedicated authoritative server implementation

---

## Capability Model

### Recommended Top-Level Capabilities

1. **Platform & Device Integration**
2. **Spatial Experience Management**
3. **Encounter Orchestration**
4. **Combat Resolution**
5. **Entity Lifecycle Management**
6. **Multiplayer Session Orchestration**
7. **Competition, Rewards & Progression**
8. **LiveOps & Personalization**
9. **Content Supply Chain**
10. **Insights & Adaptive Intelligence**

### Recommended Sub-Capabilities

| Gameplay Term | Recommended Capability Name |
|---|---|
| Attack | **Offensive Actions** |
| Defend | **Defensive Actions** |
| Entity Generation | **Encounter Orchestration** or **Entity Lifecycle Management** |
| Wave Spawning | **Threat Generation** |
| Shielding | **Damage Mitigation** |
| Powerups | **Buff & Ability Management** |

### Capability Definitions

| Capability | Description |
|---|---|
| **Platform & Device Integration** | Provides tracking, input, spatial understanding, and shared-world alignment on ThinkReality A3. |
| **Spatial Experience Management** | Creates and maintains the battlefield, safe zones, coordinate system, and environmental alignment. |
| **Encounter Orchestration** | Controls invader wave generation, boss timing, enemy placement, pacing, and difficulty tuning. |
| **Combat Resolution** | Processes aim, fire, shield, damage, hit detection, special abilities, and combat effects. |
| **Entity Lifecycle Management** | Manages spawn, activation, pooling, synchronization, despawn, and cleanup of gameplay entities. |
| **Multiplayer Session Orchestration** | Handles identity, lobby formation, matchmaking, connectivity, and session lifecycle. |
| **Competition, Rewards & Progression** | Supports scores, leaderboards, rewards, unlocks, currencies, and progression loops. |
| **LiveOps & Personalization** | Controls live tuning, event activation, seasonal content, A/B testing, and segmented experiences. |
| **Content Supply Chain** | Manages content creation, transformation, versioning, automation, packaging, and runtime distribution. |
| **Insights & Adaptive Intelligence** | Captures telemetry, supports balancing and retention analysis, and enables inference-based adaptation. |

---

## Bill of Materials

### ThinkReality A3 Client Runtime

- **Partner SDKs / ThinkReality SDK**
- **OpenXR**
- **XR Interaction Toolkit**
- **Inference Engine**
- **Gameplay Runtime**
- **Session Runtime**

### Unity Cloud Services

- **Authentication**
- **Remote Config**
- **Lobby**
- **Matchmaker**
- **Relay**
- **Multiplayer Services SDK**
- **Economy**
- **Leaderboards**
- **Unity Analytics**
- **Cloud Content Delivery**

### Content Supply Chain

- **Unity Asset Manager**
- **Unity Version Control**
- **Unity Pipeline Automation**
- **Unity Asset Transformer**
- **3D Data Streaming**
- **Cloud Content Delivery**

---

## Reference Architecture

### One-Page Reference Architecture Diagram

```mermaid
flowchart TB

  subgraph ContentOps["Content Supply Chain"]
    Creators["Artists, Designers, Developers"]
    AM["Unity Asset Manager"]
    UVC["Unity Version Control"]
    PA["Unity Pipeline Automation"]
    AT["Unity Asset Transformer<br/>+ 3D Data Streaming"]
    CCD["Cloud Content Delivery"]

    Creators --> AM
    Creators --> UVC
    AM --> PA
    UVC --> PA
    PA --> AT
    AT --> CCD
  end

  subgraph Cloud["Unity Cloud Services"]
    Auth["Authentication"]
    RC["Remote Config"]
    Lobby["Lobby"]
    MM["Matchmaker"]
    Relay["Relay"]
    MPS["Multiplayer Services SDK"]
    Econ["Economy"]
    LB["Leaderboards"]
    Analytics["Unity Analytics"]
  end

  subgraph Client["ThinkReality A3 Client Runtime"]
    Device["Partner SDKs / OpenXR<br/>Tracking, Spatial Mapping, Shared Anchor"]
    XRIT["XR Interaction Toolkit"]
    Infer["Inference Engine"]
    Game["Gameplay Runtime<br/>Spatial Experience Management<br/>Encounter Orchestration<br/>Combat Resolution<br/>Entity Lifecycle Management"]
    Session["Session Runtime<br/>Host-Authoritative State Sync"]

    Device --> XRIT
    XRIT --> Game
    Infer --> Game
    Game --> Session
  end

  Session <-->|sign-in| Auth
  Game <-->|rules, tuning, content IDs| RC
  Session <-->|party and pre-match| Lobby
  Session <-->|match assignment| MM
  Session <-->|connectivity| Relay
  Session <-->|real-time session| MPS
  Game <-->|bundles and streamed 3D| CCD

  Session -->|submit scores| LB
  Session -->|grant rewards| Econ
  Game -->|telemetry| Analytics
  Session -->|session telemetry| Analytics

  Analytics -->|balance insights| RC
  Analytics -->|content/perf insights| PA
