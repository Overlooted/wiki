# StreamingAssets

`Assets/StreamingAssets/Data/` is the single source of truth for all game data. Edit here. The game reads from here at runtime. There is no second copy.

## Structure

```
Assets/StreamingAssets/Data/
├── Assets/assets.json           AssetLibrary registry
├── Items/items.json
├── Zones/zones.json
├── Vendors/vendors.json
├── Tools/tools.json
├── Rarities/rarities.json
├── VendorUpgrades/vendor_upgrades.json
└── Localization/
    ├── en.json  ja.json  ko.json  es.json
    ├── fr.json  de.json  zh-CN.json  zh-TW.json
```

## Editing Data

Use the [content wizards](index.md) — they write directly to these files and handle localization automatically. If you prefer to edit JSON by hand, edit the files here directly.

The [data validator](../editor-tools/build-phases.md) runs automatically whenever a `.json` file is saved and logs any broken cross-references to the Console immediately.

## Data Validation

[EditMode tests](../cicd/build-pipeline.md) load from `StreamingAssets/Data/` and pass the data through `DataValidator` in the Core library. This runs on every CI push and blocks the build if validation fails — the same logic that catches errors locally also gates shipping.

## Live Reload

While in Play Mode, **Overlooted → Reload Data** re-reads all registries from StreamingAssets without restarting. Edit a JSON file, save, reload, test — no Play Mode restart needed.

See [Live Data Reload](../editor-tools/live-reload.md) for details.
