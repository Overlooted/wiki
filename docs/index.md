# Overlooted Developer Wiki

**Overlooted** is a cozy first-person extraction / scavenger game. You venture into dungeons, grab loot, appraise it, haul it back in your cart, and sell it to vendors in the hub village.

---

## Repositories

| Repo | Purpose |
|---|---|
| `Overlooted-Unity` | Unity 6.3 project — MonoBehaviour adapters, scenes, prefabs, assets |
| `Overlooted-Core` | Pure C# game logic — no Unity dependency |

All game logic lives in **Overlooted-Core**. The Unity project contains only thin adapter scripts that translate Unity events into Core method calls.

---

## Quick Links

<div class="grid cards" markdown>

- :material-folder-cog: **[Architecture](architecture/index.md)**  
  Project structure, initialization order, Core package

- :material-pipe: **[Content Pipeline](content-pipeline/index.md)**  
  AssetLibrary, wizards, prefab generator, hot-reload

- :material-gamepad-variant: **[Gameplay Systems](gameplay/index.md)**  
  Items, cart, vendors, goblins, tools, save system

- :material-map: **[Level Design](level-design/index.md)**  
  Zone setup, portals, spawn points, hub layout

- :material-puzzle: **[Puzzles](puzzles/index.md)**  
  All 11 puzzle types with components and trigger items

- :material-monitor: **[UI & Demo System](ui/index.md)**  
  Main menu, demos, loading screen, pause menu

- :material-wrench: **[Editor Tools](editor-tools/index.md)**  
  Build phases, Builder Settings, live reload

- :material-rocket-launch: **[CI/CD](cicd/index.md)**  
  GitHub Actions, GameCI, itch.io deploy

</div>

---

## Core Rule

> **No game logic in MonoBehaviours.** Adapters only — translate Unity events into Core method calls. If you're writing business logic in a `.cs` file in the Unity project, it belongs in Overlooted-Core instead.
