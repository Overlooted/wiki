# New Zone Wizard

**Overlooted → Content → New Zone…**

Creates a new zone data definition in one click. A zone is a dungeon area the player can enter and loot.

## Fields

| Field | Description |
|---|---|
| Display Name (EN) | English name — drives ID generation |
| Loot Table ID | ID of the loot table this zone uses (leave blank if not yet defined) |
| Required Tools | List of tool IDs the player must own to enter — add one per line |

## What Happens on Create

1. **ID generated** — `"Sunken Crypt"` → `zone.sunken_crypt`
2. **zones.json updated** — entry appended with empty `itemSpawnPoints` array
3. **All localization files updated** — English gets the real name; other languages get `[lang] Display Name`

## After Creating

The zone definition exists in data but has no spawn points yet. To finish setting it up:

1. Run **Overlooted → Build → 5 - Sync StreamingAssets**
2. Edit `zones.json` to add `itemSpawnPoints` entries (item ID + spawn chance + spawn point name)
3. Run **Overlooted → Build → 3 - Zone Scenes** to generate the Unity scene — spawn point GameObjects are auto-created from the JSON
4. Open the scene and reposition the spawn point GameObjects to sensible world positions
5. Add `"zone.sunken_crypt"` to the `unlocksZones` array of the tool that should gate it

## Spawn Points

Spawn points are not set in the wizard because they require scene-level decisions (world positions, density). The zone builder creates them in a grid as a starting point — you just reposition them.

```json
{
  "itemSpawnPoints": [
    { "itemDefinitionId": "item.gold_ring", "spawnChance": 0.6, "spawnPointId": "crypt_spawn_01" },
    { "itemDefinitionId": "item.old_sword",  "spawnChance": 0.4, "spawnPointId": "crypt_spawn_02" }
  ]
}
```
