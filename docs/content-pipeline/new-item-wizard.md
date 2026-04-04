# New Item Wizard

**Overlooted → Content → New Item…**

Creates a fully wired item from a single form. What used to take four manual steps now takes 30 seconds.

## Preview

<div style="background:#282828;border:1px solid #111;border-radius:4px;font-family:'Segoe UI',sans-serif;font-size:12px;color:#c8c8c8;max-width:440px;overflow:hidden;margin:16px 0;">

  <div style="background:#323232;padding:6px 10px;font-weight:bold;border-bottom:1px solid #111;font-size:13px;">New Item Wizard</div>

  <div style="padding:10px;">
    <div style="background:#2a3a4a;border-left:3px solid #4a90d9;padding:6px 8px;margin-bottom:12px;font-size:11px;color:#9dc0e0;">
      ℹ Fills items.json, all localization files, and creates a placeholder prefab.
    </div>

    <div style="display:flex;margin-bottom:6px;align-items:center;gap:6px;">
      <div style="width:140px;color:#9e9e9e;flex-shrink:0;">Display Name (EN)</div>
      <div style="flex:1;background:#1e1e1e;border:1px solid #111;padding:2px 6px;color:#fff;">Rusty Dagger</div>
    </div>

    <div style="display:flex;margin-bottom:6px;align-items:center;gap:6px;">
      <div style="width:140px;color:#9e9e9e;flex-shrink:0;">Item Type</div>
      <div style="flex:1;background:#1e1e1e;border:1px solid #111;padding:2px 6px;color:#c8c8c8;">Weapon ▾</div>
    </div>

    <div style="display:flex;margin-bottom:6px;align-items:center;gap:6px;">
      <div style="width:140px;color:#9e9e9e;flex-shrink:0;">Rarity ID</div>
      <div style="flex:1;background:#1e1e1e;border:1px solid #111;padding:2px 6px;color:#c8c8c8;">rarity.common</div>
    </div>

    <div style="display:flex;margin-bottom:6px;align-items:center;gap:6px;">
      <div style="width:140px;color:#9e9e9e;flex-shrink:0;">Base Value (gold)</div>
      <div style="flex:1;background:#1e1e1e;border:1px solid #111;padding:2px 6px;color:#c8c8c8;">50</div>
    </div>

    <!-- Mesh ID with picker open -->
    <div style="display:flex;margin-bottom:2px;align-items:center;gap:6px;">
      <div style="width:140px;color:#9e9e9e;flex-shrink:0;">Mesh ID</div>
      <div style="flex:1;background:#1e1e1e;border:1px solid #3a7abf;padding:2px 6px;color:#c8c8c8;">dag</div>
      <div style="background:#3a3a3a;border:1px solid #111;padding:2px 6px;color:#aaa;font-size:11px;cursor:pointer;">↺</div>
    </div>
    <!-- Dropdown results -->
    <div style="margin-left:146px;margin-bottom:2px;background:#222;border:1px solid #111;box-shadow:2px 2px 6px rgba(0,0,0,0.5);font-size:11px;">
      <div style="padding:2px 8px;color:#9e9e9e;">bronze_<strong style="color:#fff;">dag</strong>ger</div>
      <div style="padding:2px 8px;background:#2c5070;color:#fff;">iron_<strong>dag</strong>ger</div>
      <div style="padding:2px 8px;color:#9e9e9e;">runed_<strong style="color:#fff;">dag</strong>ger</div>
    </div>
    <div style="margin-left:146px;margin-bottom:10px;font-size:10px;color:#4a9e4a;">✓ Found in Resources</div>

    <!-- SFX foldout collapsed -->
    <div style="margin-bottom:12px;color:#9e9e9e;font-size:11px;cursor:pointer;">▶ Audio / VFX Overrides (optional)</div>

    <div style="color:#666;font-size:11px;margin-bottom:8px;">Generated ID &nbsp; <span style="color:#7ab4e0;font-family:monospace;">item.rusty_dagger</span></div>

    <div style="background:#2c5f2c;border:1px solid #1a4a1a;padding:6px;text-align:center;color:#fff;font-size:13px;cursor:pointer;border-radius:2px;">Create</div>
  </div>
</div>

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
