# Initialization Order

`Bootstrap.cs` (`[DefaultExecutionOrder(-100)]`) drives startup from a single `Awake()` call. All singletons must exist on the Bootstrap GameObject in the first scene.

```
Bootstrap.Awake()
  │
  ├─ DataManager.Initialize()           [ExecutionOrder -200]
  │    Loads 5 JSON registries from StreamingAssets
  │
  ├─ AssetLibrary.Initialize()          [ExecutionOrder -150]
  │    Loads assets.json (ID → Resources path map)
  │
  ├─ LocalizationManager.Initialize()
  │    Loads language file for current locale
  │
  ├─ WalletMono.Initialize()
  │    Creates Wallet (depends on DataManager)
  │
  ├─ ProgressionManager.Initialize()
  │    Creates ProgressionSystem with zone unlock requirements
  │
  ├─ AppraisalSystemMono.Initialize()
  │    Creates AppraisalSystem (standalone)
  │
  ├─ SaveManagerMono.LoadSettings()
  │    Restores language / audio / quality settings
  │
  └─ SaveManagerMono.LoadGame()
       Restores gold + owned tools + home item placements
```

## Rules

- All singletons **must be on the Bootstrap GameObject** in the first scene — they call `DontDestroyOnLoad` and persist everywhere.
- The execution order attributes (`[DefaultExecutionOrder]`) ensure Awake runs before Bootstrap, so `Instance` properties are set before `Initialize()` is called on them.
- Never call `Initialize()` from outside `Bootstrap` — ordering matters.
