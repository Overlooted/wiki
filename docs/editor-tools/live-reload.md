# Live Data Reload

**Overlooted → Reload Data** *(only active in Play Mode)*

Re-reads all JSON registries and `assets.json` from StreamingAssets without exiting Play Mode. The menu item is grayed out outside Play Mode.

## What Updates

| System | Updates on reload |
|---|---|
| `DataManager` | All 5 registries (items, zones, vendors, tools, rarities) |
| `AssetLibrary` | `assets.json` ID → Resources path map |

## What Doesn't Update

- Items already spawned in the scene (they hold a cached `ItemDefinition` reference)
- Wallet balance, owned tools, save state
- Any MonoBehaviour that read data at `Awake`/`Start` and doesn't re-read it

## Workflow

1. Enter Play Mode
2. Edit a JSON file in `Assets/StreamingAssets/Data/`
3. Save the file
4. **Overlooted → Reload Data**
5. New spawns (e.g. zone reload) will use updated values

## Tip

Assign a keyboard shortcut via **Edit → Shortcuts → Overlooted/Reload Data** for fastest iteration.
