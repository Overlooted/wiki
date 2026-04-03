# Build Phases

Run phases in order. Each phase depends on the previous.

## Phase 1 — Bootstrap Scene

**Overlooted → Build → 1 - Bootstrap Scene**

Creates `Assets/Scenes/Bootstrap.unity` with a single Bootstrap GameObject containing all singleton components: `DataManager`, `AssetLibrary`, `LocalizationManager`, `WalletMono`, `ProgressionManager`, `AppraisalSystemMono`, `SaveManagerMono`, `Bootstrap`.

## Phase 1b — Main Menu Scene

**Overlooted → Build → 1b - Main Menu Scene**

Creates the main menu scene with UI Toolkit canvas and all menu scripts wired.

## Phase 2 — Prefabs

**Overlooted → Build → 2 - Prefabs**

Builds all runtime prefabs:

- `Bootstrap.prefab` — all singletons on one GO
- `ItemBase.prefab` — base item prefab (used by ZoneLoader and Item Prefab Generator)
- Cart prefab with WheelCollider, CartMono, WheelControl, etc.
- Vendor variant prefabs (Blacksmith, Jeweler, General, Antiquarian, Trophy Collector)
- GameHUD, PauseMenu, GoblinSpawner, CartRecaller, ZonePortal prefabs

Must run before Phase 3.

## Phase 3 — Zone Scenes

**Overlooted → Build → 3 - Zone Scenes**

Builds `Hub.unity` and one scene per zone from `zones.json`.

**Smart rebuild:** if a scene file already exists, only the Bootstrap GO is replaced. Delete the scene file to force a full rebuild.

## Phase 4 — UI / HUD

**Overlooked → Build → 4 - UI / HUD**

Builds HUD prefabs for tool slots, gold display, interaction prompts, etc.

## Build All

**Overlooted → Build → All**

Runs phases 1–4 in sequence. Does not build puzzle prefabs/demos — run those separately if needed.
