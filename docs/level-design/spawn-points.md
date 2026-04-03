# Spawn Points

`ZoneSceneBuilder` auto-generates spawn point GameObjects from `zones.json` when a zone scene is first built. No manual naming or placement required.

## How It Works

1. `zones.json` is read for all `spawnPointId` values in `itemSpawnPoints`
2. Duplicate IDs are de-duplicated
3. An empty GameObject is created for each unique ID, named exactly as the `spawnPointId`
4. GameObjects are positioned in a grid as a starting point
5. `ZoneLoader` is added to the container with `_zoneId` set

## Runtime

`ZoneLoader.Start()` rolls the loot table. For each winning spawn point:

1. Finds the child GameObject by name (matches `spawnPointId`)
2. Instantiates the item prefab at that position
3. Calls `ItemMono.Initialize(itemDefinition)`

## Adding a New Spawn Point

1. Add the `itemSpawnPoints` entry to `zones.json`:
   ```json
   { "itemDefinitionId": "item.sword", "spawnChance": 0.7, "spawnPointId": "crypt_spawn_04" }
   ```
2. Run **Overlooted → Build → 5 - Sync StreamingAssets**
3. Delete the zone scene file to force a full rebuild, then run **Overlooted → Build → 3 - Zone Scenes**
4. The new `crypt_spawn_04` GameObject appears in the scene — reposition it as desired

!!! tip
    To add a spawn point without rebuilding the whole scene, just create an empty GameObject named `crypt_spawn_04` as a child of `ItemSpawnPoints` manually. `ZoneLoader` finds it by name.
