# Content Pipeline

The content pipeline eliminates manual inspector wiring. Audio, VFX, meshes, and item data are all driven by JSON registries — drag a file into a folder, register it, and it works automatically at runtime.

## Tools at a Glance

| Tool | Menu | What it does |
|---|---|---|
| [Asset Library](asset-library.md) | *(runtime)* | Maps IDs → Resources paths, plays sfx/vfx |
| [Asset Scanner](asset-scanner.md) | Overlooted > Assets > Asset Scanner | Finds unregistered files, one-click register |
| [New Item Wizard](new-item-wizard.md) | Overlooted > Content > New Item… | Creates item in JSON + localization + prefab |
| [Item Prefab Generator](item-prefab-generator.md) | Overlooted > Content > Generate Item Prefabs | Batch-creates prefab variants from items.json |
| [Rarity Feedback Profiles](rarity-feedback.md) | *(data)* | Per-rarity sfx/vfx/screen-shake |
| [Live Reload](../editor-tools/live-reload.md) | Overlooted > Reload Data | Re-reads all JSON without exiting Play Mode |

## Typical Workflow: Adding New Audio

1. Drop `.wav` file into `Assets/Resources/Audio/SFX/item/`
2. Open **Asset Scanner** → Scan Now → confirm ID → Register Selected
3. Done — `ItemMono` picks it up on next grab/appraise via `AssetLibrary`

## Typical Workflow: Adding a New Item

1. Open **New Item Wizard** → fill in name/type/rarity/value → Create
2. (Optional) drop a mesh into `Resources/ItemMeshes/` and run **Generate Item Prefabs**
3. Run **Sync StreamingAssets** if Core data also changed
