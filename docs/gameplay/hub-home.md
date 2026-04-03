# Hub & Home

The hub is the persistent safe area between dungeon runs. Items can be stored here across sessions.

## PlayerHomeMono

`[DefaultExecutionOrder(-10)]` singleton. Owns all `HomeItemSlotMono` instances in the scene. On `Start()`, reads `SaveManagerMono.HomeState` and restores item placements.

## HomeItemSlotMono

Named trigger slot. When an item enters the trigger:
- Item snaps to slot position (kinematic)
- Slot is marked occupied

When a grabbed item leaves:
- Slot is released
- Item physics resume

Each slot has a `_slotId` that matches a key in `HomeSaveState`. The ID is also used as the GameObject name for easy identification in the scene hierarchy.

## FireplaceMono

`Interactable` toggle. Activates/deactivates:
- Particle system (flame)
- Point light
- Audio source (crackling)

State is not persisted — resets each session.

## ChairMono

`Interactable` seat. On interact:
- Calls `PlayerSeatEvents.RaiseSeated(true)` — FirstPersonController responds by locking movement
- Camera remains free
- Press interact or jump to stand up

## Save Integration

```
SaveManagerMono.PreserveHome()
    ↑ called before portal return / quit
    Reads live slot state → builds HomeSaveState

SaveManagerMono.LoadGame()
    ↓ called at Bootstrap.Awake()
    Passes HomeSaveState to PlayerHomeMono.RestoreItems()
```
