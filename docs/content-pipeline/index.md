# Content Pipeline

The content pipeline eliminates manual inspector wiring and prevents authoring mistakes. All game data is driven by JSON registries — wizards write the JSON for you, the validator catches errors instantly, and CI blocks builds if anything is broken.

## Content Wizards

Every JSON-driven content type has a one-click wizard under **Overlooted → Content**. Fill in a form, press Create — the wizard writes the JSON, updates all 8 localization files, and (for items) creates a prefab variant.

| Wizard | Menu | Target file |
|---|---|---|
| [New Item](new-item-wizard.md) | Overlooted > Content > New Item… | `items.json` + prefab |
| [New Tool](new-tool-wizard.md) | Overlooted > Content > New Tool… | `tools.json` |
| [New Zone](new-zone-wizard.md) | Overlooted > Content > New Zone… | `zones.json` |
| [New Vendor](new-vendor-wizard.md) | Overlooted > Content > New Vendor… | `vendors.json` |
| [New Rarity](new-rarity-wizard.md) | Overlooted > Content > New Rarity… | `rarities.json` |
| [New Vendor Upgrade](new-vendor-upgrade-wizard.md) | Overlooted > Content > New Vendor Upgrade… | `vendor_upgrades.json` |

## Other Pipeline Tools

| Tool | Menu | What it does |
|---|---|---|
| [Data Tables](data-tables.md) | Overlooted > Content > Data Tables | Sortable, filterable table view of all JSON — inline edit and delete |
| [Asset Library](asset-library.md) | *(runtime)* | Maps IDs → Resources paths, plays sfx/vfx |
| [Asset Scanner](asset-scanner.md) | Overlooted > Assets > Asset Scanner | Finds unregistered files, one-click register |
| [Item Prefab Generator](item-prefab-generator.md) | Overlooted > Content > Generate Item Prefabs | Batch-creates prefab variants from items.json |
| [Rarity Feedback Profiles](rarity-feedback.md) | *(data)* | Per-rarity sfx/vfx/screen-shake |
| [Live Reload](../editor-tools/live-reload.md) | Overlooted > Reload Data | Re-reads all JSON without exiting Play Mode |

## Error Prevention Layers

The system is designed so you can't ship broken data:

1. **Wizards** — searchable pickers show valid options; invalid cross-references turn amber, not silent
2. **Console validator** — every time a `.json` file is saved, `DataValidatorEditor` runs and logs errors to the Unity Console immediately
3. **CI gate** — EditMode tests run `DataValidator` on every push; the build job won't start if validation fails

## Typical Workflows

### Adding a new item
1. **Overlooted → Content → New Item…** → fill in name / type / rarity / value → Create
2. Drop mesh into `Resources/ItemMeshes/` → **Generate Item Prefabs** (optional)
3. Register audio via **Asset Scanner** if needed

### Adding a new tool + zone it unlocks
1. **New Zone…** → set display name → Create
2. Edit `zones.json` to add spawn points for the zone
3. **New Tool…** → set cost / slot → add the zone ID to Unlocks Zones → Create
4. **Build → 3 - Zone Scenes** to generate the Unity scene

### Adding new audio
1. Drop `.wav` into `Assets/Resources/Audio/SFX/item/`
2. **Asset Scanner** → Scan Now → Register Selected
3. Done — `AssetLibrary` picks it up; assign the ID in any wizard's SFX field
