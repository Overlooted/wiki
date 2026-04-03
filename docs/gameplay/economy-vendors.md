# Economy & Vendors

## WalletMono

Singleton. Wraps Core `Wallet`. Broadcasts `OnGoldChanged` when gold changes.

```csharp
WalletMono.Instance.Wallet.Add(amount);
WalletMono.Instance.OnGoldChanged += handler;
```

`GoldHUD` subscribes to `OnGoldChanged` and updates the display.

---

## VendorMono

`OnTriggerEnter` → `Vendor.TrySell(item)` → returns `SellResult`.

Each vendor has a `_vendorId` that maps to a `VendorDefinition` in `vendors.json`. The definition specifies accepted `vendorTags` and sell multipliers. Items must be appraised before a vendor will buy them.

**Sell flow:**
1. Player walks item into vendor trigger zone
2. `VendorMono.OnTriggerEnter` fires
3. `TrySell` checks: item appraised? vendor accepts this item type? 
4. On success: gold added to wallet, `VendorAnimator` plays "Cheer", `AssetLibrary` plays `sfx.vendor.sell`

---

## VendorAnimator

Triggers the `"Cheer"` animation parameter on the vendor's `Animator` when a successful sale occurs. Attach to the same GameObject as `VendorMono`.

---

## VendorShopUpgradeMono

Activates upgrade GameObjects at cumulative gold-traded thresholds (200g / 400g / 600g). Attach to the vendor root and assign the upgrade GameObjects in the inspector.

---

## vendors.json

```json
{
  "id": "vendor.blacksmith",
  "displayNameKey": "vendor.blacksmith",
  "acceptedTags": ["blacksmith", "general"],
  "sellMultiplier": 1.0
}
```

Items tag themselves with `vendorTags` in `items.json`. A vendor accepts an item if any tag matches.
