# New Rarity Wizard

**Overlooted → Content → New Rarity…**

Creates a new rarity tier in one click. Rarities control item value scaling, appraisal feedback intensity, and visual colour.

## Fields

| Field | Description |
|---|---|
| Display Name (EN) | English name — drives ID generation |
| Tier | Numeric rank (1 = lowest). Used for sorting and progression gating. |
| Color | Tint colour shown on item tooltips and appraisal UI |
| Value Multiplier | Multiplied against `baseValue` when an item is appraised |
| Particle Intensity | 0–1 scale for particle effect density during appraisal |
| Screen Shake | 0–1 scale for camera shake intensity during appraisal |
| Appraise SFX | Searchable picker — ID must be registered in `assets.json` |
| Appraise VFX | Searchable picker — ID must be registered in `assets.json` |

SFX and VFX fields are optional. Leave blank to use the item-level override or the global default (`sfx.item.appraise`).

## What Happens on Create

1. **ID generated** — `"Mythic"` → `rarity.mythic`
2. **rarities.json updated** — entry appended with all fields
3. **All localization files updated**

## After Creating

- Run **Overlooted → Build → 5 - Sync StreamingAssets**
- Set `"rarityId": "rarity.mythic"` on any item in `items.json` that should use this tier
- Register any new SFX/VFX assets via the **Asset Scanner** before assigning them here

## Override Priority

When `ItemMono` plays appraisal feedback, it resolves the sfx/vfx ID in this order:

1. Rarity override (`appraiseSfxId` on this rarity definition) ← highest priority
2. Item override (`appraiseSfxId` on the item definition)
3. Global default (`"sfx.item.appraise"` in `assets.json`) ← lowest priority
