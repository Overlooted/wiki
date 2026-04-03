# New Tool Wizard

**Overlooted → Content → New Tool…**

Creates a new tool definition in one click. Tools gate zone access — a player must own the tool before they can enter zones that require it.

## Fields

| Field | Description |
|---|---|
| Display Name (EN) | English name — drives ID generation |
| Cost (gold) | Price to purchase from the shop |
| Slot Number | Toolbelt slot (1-based) |
| Description | Short flavour text shown in the shop UI |
| Unlocks Zones | List of zone IDs this tool grants access to — add one per line |

## What Happens on Create

1. **ID generated** — `"Lantern"` → `tool.lantern`
2. **tools.json updated** — entry appended with all fields
3. **All localization files updated** — English gets the real name; other languages get `[lang] Display Name`

## After Creating

- Run **Overlooted → Build → 5 - Sync StreamingAssets** to push data to Core
- Add `"tool.lantern"` to the `requiredTools` array of any zone it should gate (use the **New Zone Wizard** or edit `zones.json` directly)
- Create a physical tool prefab and wire it to `ProgressionManager.TryUnlockTool()` so purchasing it in-game registers the unlock

## Zones List

The Unlocks Zones list is free-text — type zone IDs directly. The data validator will flag any IDs that don't exist in `zones.json` and surface the error in the Console immediately.

!!! tip
    Leave Unlocks Zones empty if the tool is purely cosmetic or functional (e.g. a lantern that lights the area) without gating zone entry.
