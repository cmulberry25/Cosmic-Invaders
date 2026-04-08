# Cosmic Commanders for ThinkReality A3

> **Project Discovery README**  
> Reference application architecture for an **AR Space Invaders-style multiplayer experience** built in **Unity** for **Lenovo ThinkReality A3**, integrating **Unity Services/SDKs** with **partner XR SDKs**.

---

## Overview

**Cosmic Invaders** is a shared, spatial AR battle-royal inspired experience for **ThinkReality A3 AR glasses** where players see and battle alien invaders outside in the real world using gesture, gaze, and hand-driven interactions.

This project discovery defines a **reference application architecture** that brings together:

- **ThinkReality / Partner SDKs**
- **OpenXR**
- **Unity XR Interaction Toolkit**
- **Unity Engine runtime**
- **Unity Cloud Services**
- **Digital content supply chain tooling**

The architecture is intentionally built upon three essential building blocks:

1. **ThinkReality A3 Client Runtime**
2. **Unity Cloud Integrated Services**
3. **Intelligent Content Generation**

---

## Vision
<img width="1024" height="1536" alt="download (1)" src="https://github.com/user-attachments/assets/8aec111a-bc4f-44f8-aaa5-24756df09ae3" />

Create a **premium, category-defining AR multiplayer game** on ThinkReality A3 that demonstrates:
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

## User Experience
- Players join the same AR session, see a shared battlefield, fight synchronized enemy waves using basic offensive and defensive actions, and receive a final match result.

## Project Scope

### In Scope

- ThinkReality A3 integration
- shared-world alignment
- session creation/join
- synchronized gameplay state
- wave-based enemy spawning
- attack/defense gameplay
- enemy damage/death/despawn
- scoring
- match completion
- replay flow

### Out of Scope

- persistent progression
- monetization
- LiveOps
- content pipeline tooling
- advanced analytics
- personalization
- production-grade matchmaking
- multi-mode support

---

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

## Build Structure

### Extension Layer

- **Partner SDKs / ThinkReality SDK**
- **OpenXR**
- **XR Interaction Toolkit**
- **Inference Engine**
- **Gameplay Runtime**
- **Session Runtime**

### Service Layer

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

### Content Layer

- **Unity Asset Manager**
- **Unity Version Control**
- **Unity Pipeline Automation**
- **Unity Asset Transformer**
- **3D Data Streaming**
- **Cloud Content Delivery**

---

## Reference Architecture
![3  Reference Architectures - Cosmic Commanders Simplified Reference Architecture](https://github.com/user-attachments/assets/460b0b71-4611-4803-9814-07f58631a807)
