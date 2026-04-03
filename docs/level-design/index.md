# Level Design

| Topic | Summary |
|---|---|
| [Zone Setup](zone-setup.md) | Scene checklist, physics layers, tags |
| [Spawn Points](spawn-points.md) | Auto-generation from zones.json |
| [Portal System](portal-system.md) | Seamless additive scene load between hub and dungeon |
| [Hub Layout](hub-layout.md) | Editable hub prefab, resetting the layout |

## Build Order

Scenes are built programmatically — never set up by hand. The correct order:

```
Overlooted > Build > 1 - Bootstrap Scene
Overlooted > Build > 1b - Main Menu Scene
Overlooted > Build > 2 - Prefabs
Overlooted > Build > 3 - Zone Scenes      ← creates Hub + all zone scenes
Overlooted > Build > 4 - UI / HUD
```

Or run all at once: **Overlooted → Build → All**

Zone scenes are **smart rebuild** — if the scene file already exists, only the Bootstrap GameObject is replaced. Delete the scene file to force a full rebuild.
