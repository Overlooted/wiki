# Core Package

`Overlooted-Core` is a sibling repo that lives at `../Overlooted-Core` relative to the Unity project.

It is referenced as a **local Unity package** (`com.overlooted.core`) — Unity compiles the C# source directly. No DLL rebuild is needed; save a `.cs` file in Core and Unity recompiles automatically.

## Running Core Tests

```bash
cd ../Overlooted-Core
dotnet test
```

## StreamingAssets Sync

JSON data files are authored in `Overlooted-Core/Data/` and copied to `Assets/StreamingAssets/Data/` for runtime access.

```
Overlooted-Core/Data/   ← source of truth (edit here)
        ↓
Assets/StreamingAssets/Data/   ← runtime copy (never edit directly)
```

To sync: **Overlooted → Build → 5 - Sync StreamingAssets**

## JSON Registries

| File | Registry | Type |
|---|---|---|
| `Items/items.json` | `DataManager.ItemRegistry` | `ItemDefinition` |
| `Zones/zones.json` | `DataManager.ZoneRegistry` | `ZoneDefinition` |
| `Vendors/vendors.json` | `DataManager.VendorRegistry` | `VendorDefinition` |
| `Tools/tools.json` | `DataManager.ToolRegistry` | `ToolDefinition` |
| `Rarities/rarities.json` | `DataManager.RarityRegistry` | `RarityDefinition` |
| `Assets/assets.json` | `AssetLibrary` | ID → Resources path |
