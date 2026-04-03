# StreamingAssets Setup

`Assets/StreamingAssets/Data/` is where Unity reads all game data at runtime. It is the **only** copy that matters for the running game.

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

## Editing data

**Use the content wizards** — they write directly to `StreamingAssets/Data/` and update all localization files in one step. The data validator runs automatically after each save and surfaces any errors in the Console.

If you edit JSON files by hand, edit the files in `StreamingAssets/Data/` directly. The data validator will catch broken references immediately.

## Sync StreamingAssets

**Overlooted → Build → 5 - Sync StreamingAssets**

Copies files from `../Overlooted-Core/Data/` → `Assets/StreamingAssets/Data/`.

Only run this when you have edited data files **in the Core repo** (e.g. after changing a data schema or running Core-side tooling). Do **not** run it after using a content wizard — the sync goes the wrong direction and will overwrite the wizard's changes with Core's older data.

## Live Reload

While in Play Mode, **Overlooted → Reload Data** re-reads all registries from StreamingAssets without restarting. Useful for tweaking values — edit the JSON, save, reload, test immediately.

See [Live Data Reload](../editor-tools/live-reload.md) for details.
