# Editor Tools

All Overlooted editor tools are under the **Overlooted/** menu.

## Menu Structure

```
Overlooted/
├── Build/
│   ├── 1 - Bootstrap Scene
│   ├── 1b - Main Menu Scene
│   ├── 2 - Prefabs
│   ├── 3 - Zone Scenes
│   ├── 4 - UI / HUD
│   ├── 5 - Sync StreamingAssets
│   ├── All                         ← runs all phases in order
│   ├── Build Onboarding Level
│   ├── Shop Test Scene
│   └── Layout/
│       └── Hub (Reset Layout)
├── Puzzles/
│   ├── Prefabs/ Build All Prefabs
│   └── Demos/ Build All Demos
├── Content/
│   ├── New Item…                   ← New Item Wizard
│   └── Generate Item Prefabs       ← Item Prefab Generator
├── Assets/
│   └── Asset Scanner
├── Wiki/
│   └── Build Wiki
└── Reload Data                     ← Live reload (Play Mode only)
```

| Page | Details |
|---|---|
| [Build Phases](build-phases.md) | What each phase does, correct order |
| [Builder Settings](builder-settings.md) | ScriptableObject with prefab + UI refs |
| [Live Data Reload](live-reload.md) | Reload JSON without restarting Play Mode |
