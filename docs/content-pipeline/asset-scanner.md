# Asset Scanner

**Overlooted → Assets → Asset Scanner**

Scans designated `Resources/` sub-folders and shows any files not yet registered in `assets.json`. Register them in one click — no manual JSON editing required.

## Scanned Folders

| Resources folder | ID prefix | File types |
|---|---|---|
| `Audio/SFX/` | `sfx.` | `.wav`, `.mp3`, `.ogg` |
| `ItemMeshes/` | `mesh.` | `.prefab` |
| `Effects/` | `vfx.` | `.prefab` |

## Workflow

1. Drop new audio / prefab files into the appropriate `Resources/` sub-folder
2. Open **Asset Scanner** → click **Scan Now**
3. Review the list — suggested IDs are derived from the file path
4. Edit any IDs that look wrong (they're editable inline)
5. Click **Register Selected** — entries are written to `assets.json` immediately

## ID Auto-Generation

The scanner derives IDs from file paths using this pattern:

```
Resources/Audio/SFX/item/pickup_whoosh.wav   →  sfx.item.pickup_whoosh
Resources/Audio/SFX/vendor/cash_register.wav →  sfx.vendor.cash_register
Resources/Effects/VFX_Appraise.prefab        →  vfx.vfx_appraise
Resources/ItemMeshes/item_sword.prefab        →  mesh.item_sword
```

Spaces become underscores, everything is lowercased.

!!! tip
    Name files using snake_case before importing to get clean IDs without editing.
