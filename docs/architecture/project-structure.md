# Project Structure

```
Assets/
├── Scripts/
│   ├── OverlootedMono.cs               Base class for all MonoBehaviours
│   └── Adapters/
│       ├── Bootstrap.cs                Singleton init order [ExecutionOrder(-100)]
│       ├── DataManager.cs              Loads JSON registries [ExecutionOrder(-200)]
│       ├── AssetLibrary.cs             Maps IDs → Resources paths [ExecutionOrder(-150)]
│       ├── LocalizationManager.cs      Language service
│       ├── Items/
│       │   ├── ItemMono.cs             Per-item adapter (grab, appraise, tooltip)
│       │   └── AppraisalSystemMono.cs  Singleton appraisal system
│       ├── Cart/
│       │   ├── CartMono.cs             SpringJoint cart
│       │   ├── CrateMono.cs            Seals items, destroys Rigidbodies
│       │   ├── WheelControl.cs         Renders wheels from WheelCollider physics
│       │   ├── BrakeLever.cs           Interactive brake
│       │   ├── HandleMover.cs          Trigger-based handle repositioning
│       │   ├── WheelSqueak.cs          RPM-based audio pitch
│       │   └── CartRecaller.cs         Teleports cart to home position
│       ├── Economy/
│       │   ├── WalletMono.cs           Singleton, broadcasts OnGoldChanged
│       │   ├── VendorMono.cs           OnTriggerEnter → TrySell
│       │   ├── VendorAnimator.cs       Triggers "Cheer" anim on sale
│       │   └── VendorShopUpgradeMono.cs Activates upgrades at gold thresholds
│       ├── Interaction/
│       │   ├── Interactor.cs           Raycast from camera, fires Interact()
│       │   ├── Interactable.cs         Base class, registers on enable
│       │   ├── InteractableToggle.cs   Stateful on/off interactable
│       │   └── InteractUI.cs           HUD prompt (key + action label)
│       ├── Hub/
│       │   ├── PlayerHomeMono.cs       Hub singleton [ExecutionOrder(-10)]
│       │   ├── HomeItemSlotMono.cs     Named trigger slot, snaps items
│       │   ├── FireplaceMono.cs        Toggle: particles + light + audio
│       │   └── ChairMono.cs            Seat: locks movement, not camera
│       ├── Zone/
│       │   ├── ZoneLoader.cs           Rolls loot table, spawns ItemMono prefabs
│       │   ├── PortalMono.cs           Cart door save point
│       │   └── ScenePortalManager.cs   Additive scene load + alignment
│       ├── Progression/
│       │   ├── ProgressionManager.cs   TryUnlockTool + OnToolUnlocked
│       │   └── ZonePortalMono.cs       Blocks entry, shows lock reason
│       ├── Save/
│       │   └── SaveManagerMono.cs      File I/O, saves on quit + portal
│       └── UI/
│           ├── GoldHUD.cs              Subscribes to WalletMono.OnGoldChanged
│           ├── PauseMenuUI.cs          ESC menu
│           ├── SettingsUI.cs           Audio, graphics, language, controls
│           └── LoadingScreen.cs        UGUI progress bar (DontDestroyOnLoad)
│
├── Editor/Overlooted/
│   ├── Core/
│   │   ├── BuilderSettings.cs          ScriptableObject — prefab/UI/audio refs
│   │   ├── SceneBuilderBase.cs         Shared helpers for scene builders
│   │   ├── PrefabBuilder.cs            Prefab creation helpers
│   │   └── OverlootedMenus.cs          All Overlooted/ menu entries
│   ├── Scenes/
│   │   ├── BootstrapSceneBuilder.cs    Builds Bootstrap scene
│   │   ├── MainMenuSceneBuilder.cs     Builds Main Menu scene
│   │   ├── ZoneSceneBuilder.cs         Builds Hub + zone scenes
│   │   ├── PuzzleDemoBuilder.cs        Builds 11 puzzle prefabs + demo scenes
│   │   ├── PrefabBuildStep.cs          Cart, item, player prefab setup
│   │   └── ShopTestSceneBuilder.cs     Standalone shop test scene
│   ├── AssetScannerWindow.cs           Overlooted > Assets > Asset Scanner
│   ├── NewItemWizard.cs                Overlooted > Content > New Item…
│   └── ItemPrefabGenerator.cs          Overlooted > Content > Generate Item Prefabs
│
├── Prefabs/
│   ├── Items/                          ItemBase.prefab + per-item variants
│   ├── Puzzles/                        11 puzzle prefabs (generated)
│   └── Layout/HubLayout.prefab         Editable hub layout prefab
│
└── StreamingAssets/Data/               Runtime copy of Overlooted-Core/Data/
    ├── Items/items.json
    ├── Zones/zones.json
    ├── Vendors/vendors.json
    ├── Tools/tools.json
    ├── Rarities/rarities.json
    ├── Assets/assets.json              AssetLibrary registry
    └── Localization/en.json  ja.json  …
```
