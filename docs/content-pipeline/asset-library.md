# Asset Library

`Assets/Scripts/Adapters/AssetLibrary.cs` — DontDestroyOnLoad singleton initialized by Bootstrap after DataManager.

Maps string IDs → `Resources/` paths. No inspector wiring required anywhere.

## assets.json

Located at `Assets/StreamingAssets/Data/Assets/assets.json`.

```json
{
  "entries": [
    { "id": "sfx.item.pickup",   "path": "Audio/SFX/item/pickup_whoosh" },
    { "id": "sfx.item.drop",     "path": "Audio/SFX/item/drop_thud" },
    { "id": "sfx.item.appraise", "path": "Audio/SFX/item/appraise_shimmer" },
    { "id": "sfx.vendor.sell",   "path": "Audio/SFX/vendor/cash_register" },
    { "id": "vfx.item.appraise", "path": "Effects/VFX_Appraise" },
    { "id": "vfx.vendor.coins",  "path": "Effects/VFX_Coins" }
  ]
}
```

!!! important
    The `path` value is relative to a `Resources/` folder — no file extension. The asset must live inside a `Resources/` folder for `Resources.Load` to find it.

## API

```csharp
// Load any asset type
AudioClip clip = AssetLibrary.Instance.Get<AudioClip>("sfx.item.pickup");

// Play audio at world position
AssetLibrary.Instance.PlaySfx("sfx.item.pickup", transform.position);

// Spawn VFX prefab (auto-destroys after particle lifetime)
AssetLibrary.Instance.SpawnVfx("vfx.item.appraise", transform.position);
```

## Override Priority

For item appraisal, the system checks in this order:

```
RarityDefinition.AppraiseSfxId     (highest priority)
    ↓ if empty
ItemDefinition.AppraiseSfxId
    ↓ if empty
"sfx.item.appraise"                 (default fallback)
```

## Per-Item Overrides

Add to an item in `items.json`:

```json
{
  "id": "item.hero_gauntlet",
  "pickupSfxId":   "sfx.weapon.pickup_heavy",
  "dropSfxId":     "sfx.weapon.drop_heavy",
  "appraiseSfxId": "sfx.relic.appraise",
  "appraiseFxId":  "vfx.relic.appraise"
}
```

## ID Naming Convention

```
sfx.{category}.{name}     e.g.  sfx.item.pickup_whoosh
vfx.{category}.{name}     e.g.  vfx.item.appraise
mesh.{category}.{name}    e.g.  mesh.item.sword
```
