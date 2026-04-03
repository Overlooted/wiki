# New Vendor Wizard

**Overlooted → Content → New Vendor…**

Creates a new vendor definition in one click. Vendors are the sell points players bring their cart to — each one specialises in certain item types and pays different rates.

## Fields

| Field | Description |
|---|---|
| Display Name (EN) | English name — drives ID generation |
| Base Multiplier | Gold multiplier applied to all items this vendor accepts |
| Type Match Multiplier | Additional multiplier when the item type exactly matches the vendor's specialty |
| Accepted Item Types | Toggle which `ItemType` values this vendor will buy |

## What Happens on Create

1. **ID generated** — `"Antique Dealer"` → `vendor.antique_dealer`
2. **vendors.json updated** — entry appended with accepted types and multipliers
3. **All localization files updated** — English gets the real name; other languages get `[lang] Display Name`

## After Creating

- Run **Overlooted → Build → 5 - Sync StreamingAssets**
- Place a `VendorMono` in a scene and set its **Vendor ID** field to `vendor.antique_dealer`
- Optionally add a `VendorAnimator` to the same GameObject for the celebration animation on sale

## Multiplier Maths

Final gold = `item.baseValue × rarity.valueMultiplier × vendor.baseMultiplier`

If the item type matches the vendor's specialty, an additional `typeMatchMultiplier` is applied on top.

| Scenario | Multiplier chain |
|---|---|
| Wrong type | `baseValue × rarityMult × baseMult` |
| Right type | `baseValue × rarityMult × baseMult × typeMatchMult` |
