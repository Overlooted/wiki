# Goblin System

## GoblinMono

NavMesh-driven agent controlled by `GoblinStateMachine` (Core). Spawned by `GoblinSpawner`.

**Behaviour:**

1. Wanders toward the cart
2. Enters cart trigger → `Cart.GoblinSteal()` → steals a random loose item
3. Flees to escape point
4. Despawns on reaching escape

Requires a GameObject tagged `"Cart"` in the scene for the trigger detection.

## GoblinSpawner

Timer-based spawner. Set `_spawnInterval`, `_goblinPrefab`, `_spawnPoint`, and `_escapePoint` in the inspector.

## Tags Required

| Tag | Used by |
|---|---|
| `Cart` | `GoblinMono.OnTriggerEnter` — detects the cart |
| `Player` | `ZonePortalMono` — detects player proximity |

These tags must be registered in `ProjectSettings/TagManager.asset`.
