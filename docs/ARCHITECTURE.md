# AgentJAM Architecture

> Product architecture for a multiplayer, spatial AI coding room.
>
> **Current status:** this repository is an interactive product concept/showcase. The architecture below describes the intended production system rather than claiming every service is implemented in this repo today.

## 1. Design goal

AgentJAM is built around one idea: when several people are using coding agents on the same project, the important state should become **shared state** instead of remaining trapped in private IDE windows and chat sessions.

The system therefore separates four concerns:

1. **Presence** — who is in the room, where they are, and which task they own.
2. **Agent execution** — what each coding agent is doing and what files it may touch.
3. **Project truth** — the canonical branch/worktree, preview, tests, diffs, and snapshots.
4. **Spatial projection** — how all of that state becomes visible inside the 3D room.

## 2. High-level system

```text
┌──────────────────────────────────────────────────────────────┐
│                    Shared 3D Collaboration Room              │
│                                                              │
│  Human A        Human B        Human C        Project Wall   │
│     │              │              │                ▲          │
│  Agent A        Agent B        Agent C             │          │
└─────┼──────────────┼──────────────┼────────────────┼──────────┘
      │              │              │                │
      └──────────────┴──────┬───────┴────────────────┘
                            ▼
                  ┌──────────────────────┐
                  │ Collaboration Runtime │
                  │ events · permissions │
                  │ task ownership       │
                  │ conflict detection   │
                  └──────────┬───────────┘
                             ▼
        ┌─────────────────────────────────────────────┐
        │              Project Orchestrator           │
        │                                             │
        │ worktrees · diffs · tests · preview · git  │
        │ snapshots · rollback · merge checkpoints    │
        └──────────┬───────────────────────┬──────────┘
                   │                       │
                   ▼                       ▼
        ┌──────────────────┐     ┌────────────────────┐
        │ Agent Runtimes   │     │ Preview / Test Env │
        │ Codex / Claude / │     │ browser · logs · CI│
        │ other coding AIs │     └────────────────────┘
        └──────────────────┘
```

## 3. Core objects

### Room

A room represents one collaborative project session. It owns:

- repository identity;
- active participants;
- current snapshot/checkpoint;
- agent workstations;
- shared project wall state;
- event history.

### Workstation

A workstation binds one human to one coding agent context.

```text
Workstation
├── human_id
├── agent_id
├── task
├── allowed_paths
├── branch/worktree
├── status
└── current_diff
```

The important product principle is that an agent should not silently become a second invisible developer. Its task, scope, status, and output should be inspectable by everyone in the room.

### Project Wall

The project wall is the room's shared source of truth. It can project:

- current running preview;
- active tasks;
- code diffs;
- files being edited;
- test status;
- build/runtime logs;
- merge/conflict warnings;
- snapshots and rollback points.

### Snapshot

A snapshot captures a meaningful project state so a team can compare, demo, replay, or recover it later.

A production implementation could map snapshots to Git commits/tags plus metadata about active tasks, agents, prompts, tests, and preview state.

## 4. Event model

AgentJAM works best as an event-driven system. Instead of each UI polling several tools independently, the collaboration runtime emits a common event stream.

Example events:

```json
{
  "type": "agent.task.started",
  "agent": "agent-a",
  "task": "Add GitHub OAuth",
  "paths": ["src/auth/**"]
}
```

```json
{
  "type": "project.preview.updated",
  "url": "http://preview.local",
  "snapshot": "hackathon-demo-v4"
}
```

```json
{
  "type": "conflict.risk.detected",
  "agents": ["agent-a", "agent-c"],
  "paths": ["src/auth/session.ts"]
}
```

The 3D client only needs to subscribe to this shared event stream and turn events into spatial feedback: wall updates, workstation state, redstone-style signals, warnings, and timeline entries.

## 5. Agent isolation and merge strategy

The safest default is **one worktree or branch per active agent**.

```text
main / canonical project state
├── worktree-agent-a  → auth task
├── worktree-agent-b  → landing page task
└── worktree-agent-c  → tests task
```

This provides three benefits:

1. agent changes remain attributable;
2. conflicts can be detected before they hit the canonical state;
3. the room can show each agent's diff independently.

A merge checkpoint can then validate:

- path overlap;
- tests;
- formatting/linting;
- build success;
- human approval when required.

## 6. Conflict awareness

Traditional Git often reveals conflicts late, during merge. AgentJAM should surface **conflict risk before merge**.

A simple first implementation can combine:

- declared task/file ownership;
- live changed-file sets;
- overlapping diff hunks;
- dependency graph hints;
- test failures after integration.

The 3D metaphor can make this legible without inventing a new Git model: a workstation or shared wall can flash a warning when two agents enter the same code area.

## 7. Voice and terminal input

Voice and terminal are two interfaces to the same task model.

- **Voice** is best for lightweight intent: “make the login page support GitHub OAuth.”
- **Terminal** is best for precise instructions, debugging, commands, and reviewing generated output.

Both should resolve into a structured task containing owner, scope, acceptance criteria, and execution state.

## 8. Suggested implementation layers

```text
client/
  Minecraft/Fabric or another 3D client

collaboration-runtime/
  WebSocket event bus
  room + presence state
  task ownership
  conflict awareness

agent-runtime/
  adapters for coding agents
  permission / sandbox layer
  task execution lifecycle

project-runtime/
  Git worktrees
  preview process
  tests / lint / build
  snapshots + rollback

web/
  browser dashboard / fallback interface
  optional project-wall renderer
```

Possible technologies include a Minecraft/Fabric client or browser-based 3D client, a Node/TypeScript realtime runtime, Git worktrees for agent isolation, and adapters for whichever coding agents a team chooses to run.

## 9. What this repository contains today

`AgentJAM-showcase` currently contains the interactive concept page used to communicate the product idea:

```text
AgentJAM-showcase/
├── index.html
├── _shared/fonts/
├── assets/
│   └── agentjam-hero.svg
├── docs/
│   └── ARCHITECTURE.md
└── README.md
```

It is intentionally lightweight. The next engineering milestone would be to turn one thin vertical slice into reality:

> two users → two isolated agent worktrees → one shared preview wall → visible diffs → one merge checkpoint.

That slice would test the core thesis before building a full Minecraft runtime.
