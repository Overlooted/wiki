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
| Mesh ID | Resource path key in `assets.json` (optional) |

## What Happens on Create

1. **ID generated** — `"Rusty Dagger"` → `item.rusty_dagger`
2. **items.json updated** — new entry appended with all fields
3. **All 8 localization files updated** — English gets the real name; other languages get `[lang] Display Name` as a placeholder to fill in later
4. **Prefab variant created** — `Assets/Prefabs/Items/{id}.prefab` (variant of `ItemBase.prefab`)

## After Creating

- Run **Overlooted → Build → 5 - Sync StreamingAssets** if you also need the data updated in the Core repo
- Drop a mesh into `Resources/ItemMeshes/` named `{meshId}` then run **Generate Item Prefabs** to pre-load it

## ID Convention

IDs are auto-generated as `item.{snake_case_name}`. If you need a custom ID, create the entry manually in `items.json` instead.

!!! note
    Existing items are never overwritten. If `item.rusty_dagger` already exists in `items.json`, the wizard will append a duplicate — check before creating.
