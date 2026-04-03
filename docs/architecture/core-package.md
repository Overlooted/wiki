# Core Package

`Overlooted-Core` is a sibling repo at `../Overlooted-Core` relative to the Unity project.

It is referenced as a **local Unity package** (`com.overlooted.core`) — Unity compiles the C# source directly. No DLL rebuild needed; save a `.cs` file in Core and Unity recompiles automatically.

## What Core Contains

- Domain logic — `ItemSystem`, `AppraisalSystem`, `VendorSystem`, `GoblinStateMachine`, etc.
- Data contracts — `ItemDefinition`, `RarityDefinition`, `ZoneDefinition`, etc.
- `DataLoader` — deserialises JSON into typed records
- `DataValidator` — validates cross-references between registries (no file I/O)

Core has no dependency on Unity. It does not own or read any data files.

## Running Core Tests

```bash
cd ../Overlooted-Core
dotnet test
```

Core tests use mock/inline data. They test logic, not data files.

## Data Validation

Real game data lives in `Assets/StreamingAssets/Data/` in the Unity project. Unity's EditMode tests load from there and pass the data into `DataValidator`:

```csharp
// DataValidationTests.cs (EditMode)
var items    = DataLoader.Load<ItemDefinition>(File.ReadAllText(...));
var rarities = DataLoader.Load<RarityDefinition>(File.ReadAllText(...));
var errors   = DataValidator.Validate(items, rarities, tools, zones, vendors, en, assetIds);
Assert.IsEmpty(errors);
```

This runs automatically on every CI push. Broken rarity references, missing localization keys, invalid spawn chances — all caught before a build ships.

## JSON Registries

| File | Registry | Type |
|---|---|---|
| `Items/items.json` | `DataManager.ItemRegistry` | `ItemDefinition` |
| `Zones/zones.json` | `DataManager.ZoneRegistry` | `ZoneDefinition` |
| `Vendors/vendors.json` | `DataManager.VendorRegistry` | `VendorDefinition` |
| `Tools/tools.json` | `DataManager.ToolRegistry` | `ToolDefinition` |
| `Rarities/rarities.json` | `DataManager.RarityRegistry` | `RarityDefinition` |
| `Assets/assets.json` | `AssetLibrary` | ID → Resources path |
