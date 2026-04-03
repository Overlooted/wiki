# New Item Wizard

**Overlooted → Content → New Item…**

Creates a fully wired item from a single form. What used to take four manual steps now takes 30 seconds.

## Fields

| Field | Description |
|---|---|
| Display Name (EN) | English display name — drives ID generation |
| Item Type | Weapon, Armor, Jewelry, Relic, Trophy, Ash, Potion, Misc |
| Rarity ID | e.g. `rarity.common`, `rarity.legendary` |
| Base Value | Gold value after appraisal |
| Mesh ID | Searchable picker — scans `Resources/ItemMeshes/` for `.prefab` names |

### Searchable ID Pickers

**Mesh ID**, **Pickup SFX**, **Drop SFX**, **Appraise SFX**, and **Appraise VFX** all use a searchable combo-box:

- Start typing to filter the list — matching substring is **bolded** in the results
- Click a result to fill the field, or type freely if the asset isn't imported yet
- The ↺ button rescans the source folder / registry

**Validation indicators** appear below each field:

| Colour | Meaning |
|---|---|
| Green ✓ Found | ID matches an existing asset exactly |
| Amber ⚠ Not found | Free-typed value — will be saved as-is and resolved at runtime |
| Grey | No value entered yet — shows count of available options |

### Source modes

| Field | Source | Valid when… |
|---|---|---|
| Mesh ID | `Resources/ItemMeshes/` folder — prefab filenames | Prefab exists under that path |
| SFX / VFX overrides | `assets.json` — IDs filtered by prefix (`sfx.` or `vfx.`) | ID is registered in `assets.json` |

### Audio / VFX Overrides (optional)

Expand **Audio / VFX Overrides (optional)** to set per-item sfx/vfx IDs.
Leave blank to fall back to the rarity profile defaults from `rarities.json`, then the global defaults in `assets.json`.

Override priority (highest to lowest):

1. `ItemDefinition` field (set here in the wizard)
2. `RarityDefinition` feedback profile
3. Global default ID string (`"sfx.item.pickup"` etc.)

## What Happens on Create

1. **ID generated** — `"Rusty Dagger"` → `item.rusty_dagger`
2. **items.json updated** — new entry appended with all fields; override fields only written if non-empty
3. **All 8 localization files updated** — English gets the real name; other languages get `[lang] Display Name` as a placeholder to fill in later
4. **Prefab variant created** — `Assets/Prefabs/Items/{id}.prefab` (variant of `ItemBase.prefab`)

## After Creating

- Drop a mesh into `Resources/ItemMeshes/` named `{meshId}` then run **Generate Item Prefabs** to pre-load it
- Register audio/VFX assets via **Overlooted → Assets → Asset Scanner** so they appear in the SFX/VFX pickers

## ID Convention

IDs are auto-generated as `item.{snake_case_name}`. If you need a custom ID, create the entry manually in `items.json` instead.

!!! note
    Existing items are never overwritten. If `item.rusty_dagger` already exists in `items.json`, the wizard will append a duplicate — check before creating.
