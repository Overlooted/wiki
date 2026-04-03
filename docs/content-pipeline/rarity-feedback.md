# Rarity Feedback Profiles

Configure per-rarity audio, VFX, and screen shake by adding fields to `rarities.json`. Legendary items can feel dramatically different from common ones with zero code changes.

## rarities.json Fields

```json
{
  "id": "rarity.legendary",
  "displayNameKey": "rarity.legendary",
  "tier": 4,
  "color": "#FFD700",
  "valueMultiplier": 5.0,
  "particleIntensity": 1.0,
  "appraiseSfxId": "sfx.appraise.legendary",
  "appraiseFxId": "vfx.appraise.legendary",
  "screenShakeIntensity": 0.8
}
```

## Field Reference

| Field | Type | Default | Description |
|---|---|---|---|
| `appraiseSfxId` | string | `""` | AssetLibrary ID for appraisal sound |
| `appraiseFxId` | string | `""` | AssetLibrary ID for appraisal VFX prefab |
| `screenShakeIntensity` | float | `0.0` | Camera shake magnitude (0 = none, 1 = max) |
| `particleIntensity` | float | `0.0` | Passed through to particle systems |

## Override Priority

Rarity fields take priority over item-level fields:

```
rarities.json appraiseSfxId   ← checked first
items.json    appraiseSfxId   ← fallback
"sfx.item.appraise"           ← default if both empty
```

## Screen Shake

Screen shake uses `MMCameraShakeEvent` from Feel. The event fires automatically in `ItemMono` when an item is appraised if `screenShakeIntensity > 0`. The shake amplitude and duration are scaled by the intensity value.

## Example Setup

```json
[
  { "id": "rarity.common",    "screenShakeIntensity": 0.0 },
  { "id": "rarity.uncommon",  "screenShakeIntensity": 0.1 },
  { "id": "rarity.rare",      "screenShakeIntensity": 0.3,
    "appraiseSfxId": "sfx.appraise.rare" },
  { "id": "rarity.epic",      "screenShakeIntensity": 0.55,
    "appraiseSfxId": "sfx.appraise.epic",
    "appraiseFxId":  "vfx.appraise.epic" },
  { "id": "rarity.legendary", "screenShakeIntensity": 0.8,
    "appraiseSfxId": "sfx.appraise.legendary",
    "appraiseFxId":  "vfx.appraise.legendary" }
]
```
