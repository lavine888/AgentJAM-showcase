<div align="center">

# ⛏️ AgentJAM

### Multiplayer AI coding, reimagined as a place you can walk into.

**在 Minecraft 里，把“多人 + 多个 AI Agent 一起写代码”变成一个真正共享的空间。**

AgentJAM explores a simple idea: when AI can write code faster than ever, the next bottleneck is no longer typing — it is **shared context, coordination, and visibility**.

<br/>

[![Live Showcase](https://img.shields.io/badge/▶_Live_Showcase-07110F?style=for-the-badge&logo=github&logoColor=79ff8f)](https://lavine888.github.io/AgentJAM-showcase/)
[![Project Type](https://img.shields.io/badge/◆_Team_Co--Created-173329?style=for-the-badge)](#project-context--attribution)
[![Status](https://img.shields.io/badge/⛏_Interactive_Concept_Showcase-28483D?style=for-the-badge)](#what-this-repository-is)

`Minecraft-inspired spatial UI` · `Multi-agent collaboration` · `Voice + terminal` · `Shared project state`

<br/>

[![AgentJAM — multiplayer AI coding space](assets/agentjam-hero.svg)](https://lavine888.github.io/AgentJAM-showcase/)

*One shared room. Multiple builders. Multiple AI agents. One project state.*

</div>

---

## The problem: AI writes faster, teams desync faster

AI coding tools make an individual developer dramatically faster. But put several people — each with their own agent, terminal, branch and chat context — on the same fast-moving prototype, and a new problem appears:

> **Everyone can generate code quickly, but nobody has a clean shared view of what all the agents are doing.**

In a typical hackathon or product sprint, context is scattered across editors, chat windows, Git branches, screenshots, terminals and pull requests. The faster agents generate changes, the easier it becomes to lose track of:

- who is working on what;
- which version is currently the source of truth;
- what an agent just changed and why;
- whether the latest build still runs;
- where two agents are about to touch the same code;
- and how the team actually arrived at the final demo.

AgentJAM asks a different question:

**What if the project itself became a place the whole team could enter?**

---

## The big idea

AgentJAM turns AI coding collaboration into a **shared 3D workspace inspired by Minecraft**.

Each teammate gets an AI Agent workstation. You can walk up to a station, give instructions by voice or terminal, and see the agent's work reflected back into the shared room. A central project wall acts as the common source of truth — showing changes, previews, task state, tests and snapshots.

It is roughly:

> **Google Docs for code — but spatial, voice-driven and AI-powered.**

Instead of every developer privately operating an AI assistant, the team experiences **humans + agents working inside the same visible project state**.

---

## How a session works

| Step | In AgentJAM | What it solves |
| --- | --- | --- |
| **01 · Enter the room** | The project becomes a shared Minecraft-style collaboration space. | Everyone starts from the same visible context. |
| **02 · Take a workstation** | Each teammate owns an AI Agent station and a clear task boundary. | Makes ownership and parallel work legible. |
| **03 · Give an instruction** | Use voice for fast delegation or terminal input for precise control. | Keeps interaction lightweight without hiding the work. |
| **04 · Watch the project wall** | Diffs, previews, task progress, tests and conflict signals appear in the shared space. | Turns invisible agent activity into team-visible events. |
| **05 · Save a snapshot** | Important milestones become replayable project states. | Makes rollback, demo storytelling and retrospectives easier. |

---

## Minecraft is not just the skin

The Minecraft language maps directly onto the collaboration model:

| World element | Collaboration meaning |
| --- | --- |
| 🧱 **Blocks** | Modular tasks and pieces of the software system |
| 🔴 **Redstone** | Real-time synchronization and event flow |
| 🛠️ **Crafting table** | Combining ideas, prompts, code and agent capabilities into a feature |
| 💎 **Diamond ore** | High-value code changes or important discoveries |
| 🟣 **Portal** | Entering a shared project context from separate local tools |
| 💥 **Creeper warning** | Potential code conflicts before they explode at merge time |

The point is not to put a Minecraft texture on an IDE. The point is to make abstract coordination **physical, visible and intuitive**.

---

## Core product concepts

### 1. Personal AI Agent workstations

Each teammate has a spatially distinct workstation connected to their task, model context and coding session. Instead of asking “what are you doing?”, teammates can see the active area of work directly.

### 2. Voice + terminal as dual interfaces

Small instructions can be spoken naturally; complex work can still be controlled precisely through a terminal-style interface. AgentJAM does not try to replace developer tools — it gives them a shared spatial layer.

### 3. The central project wall

The wall is the room's source of truth: code Diff, running preview, task state, logs, tests and important decisions can all be surfaced in one place.

### 4. Conflict awareness

When multiple agents begin touching the same area of the project, the room can expose that collision before it becomes a painful late-stage merge problem.

### 5. Replayable snapshots

Hackathons, teaching and fast product sprints are not only about the final artifact. Snapshots preserve the path — what changed, when it changed, and how the team reached the result.

### 6. Presence

There is a surprisingly important difference between “three people are editing the same repo” and “three people feel like they are building in the same workshop.” AgentJAM is an experiment in making that collaboration feel present again.

---

## Who it is for

**Hackathon teams** — parallelize aggressively without completely losing the shared story of the build.

**AI-native product teams** — coordinate several humans and several coding agents around one fast-moving prototype.

**Programming education** — let instructors observe not only the final code, but how students divide tasks, prompt agents, debug and recover from mistakes.

**Remote creative coding teams** — create a stronger feeling of co-presence than a stack of tabs, calls and pull requests.

---

## Why this matters

AI coding is moving the bottleneck.

When code generation becomes cheap, the scarce resource becomes **coordination**: deciding what should be built, keeping agents aligned, understanding parallel changes, spotting collisions early, and preserving a coherent project state.

AgentJAM is a design exploration around that shift.

It does not ask how to make one AI programmer faster.

It asks:

> **What should the workspace look like when an entire team is collaborating with AI programmers at the same time?**

---

## Conceptual architecture

```text
[ Human teammates ]
        │
        │  voice / terminal / in-world interaction
        ▼
[ Shared Minecraft-style workspace ]
        │
        ├── Agent workstation A ──► coding agent / task context
        ├── Agent workstation B ──► coding agent / task context
        ├── Agent workstation C ──► coding agent / task context
        │
        ▼
[ Shared project state ]
        ├── code changes / Diff
        ├── running preview
        ├── tests + logs
        ├── task status
        ├── conflict signals
        └── historical snapshots
```

This repository focuses on communicating and demonstrating that interaction model rather than shipping the complete production runtime.

---

## What this repository is

`AgentJAM-showcase` is the **interactive showcase / portfolio presentation layer** for the AgentJAM concept.

```text
AgentJAM-showcase/
├── index.html              interactive GitHub Pages showcase
├── assets/
│   └── agentjam-hero.svg   README / project hero visual
├── _shared/fonts/          local presentation fonts
├── .nojekyll               GitHub Pages static-asset support
└── README.md               project story + documentation
```

The live page is intentionally designed like a Minecraft HUD / collaborative coding room so the product idea can be understood without requiring the full underlying system to be running.

**▶ [Open the live showcase](https://lavine888.github.io/AgentJAM-showcase/)**

---

## Project context & attribution

> **AgentJAM was a team co-created project.**

This repository presents the project from **Lavine's perspective as a project participant/contributor** and serves as a personal showcase of the work. It is **not intended to claim sole authorship or exclusive ownership of the original team project**.

Lavine has the right / permission to showcase the project and related outcomes in a portfolio context. Credit for the original project belongs to the team members who contributed to its creation.

This repository primarily contains a separately maintained presentation layer and documentation used to communicate the concept, interaction model and product thinking around AgentJAM.

If additional team credits or links to the original collaborative materials are published later, they can be listed here explicitly.

---

## Showcase note

AgentJAM is presented here as a **creative prototype / product concept**. Some interactions described in the product vision represent the intended system behavior and should not be interpreted as claims that every production capability is fully implemented in this showcase repository.

Minecraft is a trademark of Mojang Studios / Microsoft. AgentJAM is an independent creative project and is not affiliated with or endorsed by Mojang Studios or Microsoft.

---

<div align="center">

### GitHub solved distance between developers.
### AgentJAM explores what happens when the distance between **humans, agents and the project itself** disappears.

<br/>

[![Enter AgentJAM](https://img.shields.io/badge/⛏_ENTER_AGENTJAM-79ff8f?style=for-the-badge&labelColor=07110F)](https://lavine888.github.io/AgentJAM-showcase/)

</div>
