# Items & Appraisal

## ItemMono

`Assets/Scripts/Adapters/Items/ItemMono.cs`

Wraps the Core `Item` model. Requires `Rigidbody` and `GrabbableObject` (GrabMaster).

### Initialization

Called by `ZoneLoader` when spawning items from the loot table:

```csharp
itemMono.Initialize(itemDefinition);
```

This sets up the Core `Item`, refreshes the tooltip, and applies the rarity glow colour to `HighlightEffect`.

### Grab Detection

`ItemMono` polls `GrabbableObject.IsHeld` every `Update()` to detect grab/release edges, then plays the appropriate sfx via `AssetLibrary`.

### Shake-to-Appraise

While an item is held, mouse delta magnitude is accumulated and fed into `AppraisalSystem.ApplyShake()`. When the system reports appraisal complete:

1. `Item.SetAppraised(true)` is called
2. Tooltip is refreshed with name + gold value
3. HighlightEffect glow is updated to the true rarity colour
4. `AssetLibrary` plays sfx + spawns VFX
5. `MMCameraShakeEvent` fires if rarity `screenShakeIntensity > 0`

### Audio / VFX IDs

Default IDs (used when item/rarity overrides are empty):

| Event | Default ID |
|---|---|
| Grab | `sfx.item.pickup` |
| Drop | `sfx.item.drop` |
| Appraise (sfx) | `sfx.item.appraise` |
| Appraise (vfx) | `vfx.item.appraise` |

Override per-item in `items.json` or per-rarity in `rarities.json`. See [Asset Library](../content-pipeline/asset-library.md).

### Layer Helpers

```csharp
itemMono.SwitchToInCartLayer();    // moves to InCartLoot layer
itemMono.SwitchToDefaultLayer();   // moves back to Default layer
itemMono.DestroyPhysics();         // removes Rigidbody (used by CrateMono on seal)
```

### SimpleTooltip

`ItemMono` has a `[SerializeField] SimpleTooltip _tooltip`. The tooltip shows `???` until appraised, then shows `{name}\n{type}` on the left and `{value}g` on the right. Unity's `OnMouseOver` drives display — works with cursor-locked FPS (maps to screen centre).

---

## AppraisalSystemMono

`Assets/Scripts/Adapters/Items/AppraisalSystemMono.cs`

Singleton wrapping Core `AppraisalSystem`. Lives on the Bootstrap GameObject.

```csharp
bool done = AppraisalSystemMono.Instance.AppraisalSystem
    .ApplyShake(itemId, shakeMagnitude * Time.deltaTime);
```
