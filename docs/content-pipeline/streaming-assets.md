# StreamingAssets Setup

JSON data files are read at runtime from `Assets/StreamingAssets/Data/`. The source of truth is always `Overlooted-Core/Data/` — never edit the StreamingAssets copy directly.

## Required Structure

```
Assets/StreamingAssets/Data/
├── Assets/
│   └── assets.json           AssetLibrary registry
├── Items/
│   └── items.json
├── Zones/
│   └── zones.json
├── Vendors/
│   └── vendors.json
├── Tools/
│   └── tools.json
├── Rarities/
│   └── rarities.json
└── Localization/
    ├── en.json
    ├── ja.json
    ├── ko.json
    ├── es.json
    ├── fr.json
    ├── de.json
    ├── zh-CN.json
    └── zh-TW.json
```

## Syncing

**Overlooted → Build → 5 - Sync StreamingAssets**

Copies all files from `../Overlooted-Core/Data/` to `Assets/StreamingAssets/Data/`. Run this whenever you edit data files in Core.

## Live Reload

While in Play Mode, **Overlooted → Reload Data** re-reads all registries from StreamingAssets without restarting. Useful for tweaking values — edit the JSON, save, reload, test immediately.

See [Live Data Reload](../editor-tools/live-reload.md) for details.
