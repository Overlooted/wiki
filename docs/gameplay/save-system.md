# Save System

## SaveManagerMono

Handles all file I/O. Singleton on the Bootstrap GameObject. Uses JSON serialization to `Application.persistentDataPath`.

## When Saves Happen

| Trigger | What's saved |
|---|---|
| Portal return | Gold, tools, home state |
| Application quit | Gold, tools, home state |
| `LoadSettings()` on boot | Language, audio, quality (read-only here) |

## Save Data

**Game state:**
- `WalletMono` — current gold
- `ProgressionManager` — owned tool IDs
- `PlayerHomeMono` — item placements in home slots (`HomeSaveState`)

**Settings:**
- Current language
- Audio mixer volumes
- Quality level

## Home State

```csharp
// Before returning from a zone:
SaveManagerMono.Instance.PreserveHome();

// On boot (called by Bootstrap):
SaveManagerMono.Instance.LoadGame();
// → PlayerHomeMono.RestoreItems(homeState)
```

`PreserveHome()` skips updating home state if `PlayerHomeMono.Instance` is null (i.e., you're in a zone scene, not the hub) — it preserves whatever was last saved from the hub.
