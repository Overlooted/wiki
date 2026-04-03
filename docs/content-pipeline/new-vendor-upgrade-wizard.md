# New Vendor Upgrade Wizard

**Overlooted → Content → New Vendor Upgrade…**

Creates a new vendor upgrade tier in one click. Vendor upgrades are milestone rewards — when the player trades enough gold with a vendor, the vendor's stall visually upgrades.

## Fields

| Field | Description |
|---|---|
| Display Name (EN) | English name — drives ID generation |
| Gold Traded Required | Cumulative gold traded threshold that triggers this upgrade |
| Description | Flavour text describing what changes at this tier |

## What Happens on Create

1. **ID generated** — `"Gilded Stall"` → `upgrade.gilded_stall`
2. **vendor_upgrades.json updated** — entry appended
3. **All localization files updated**

## After Creating

- Open the vendor's GameObject in the scene and find `VendorShopUpgradeMono`
- Add an entry to its upgrade list, set the **Upgrade ID** to `upgrade.gilded_stall`, and assign the GameObjects to activate at that tier

## How Upgrades Work at Runtime

`VendorShopUpgradeMono` listens to gold-traded events. When the cumulative total crosses a threshold, it activates the corresponding set of GameObjects (e.g. a fancier stall mesh, extra decorations). The threshold values come from `vendor_upgrades.json` — no hardcoding in the component.
