# Puzzles

11 reusable puzzle types, each saved as a prefab and paired with a standalone demo scene.

## Build

```
Overlooted > Puzzles > Prefabs > Build All Prefabs   → Assets/Prefabs/Puzzles/
Overlooted > Puzzles > Demos > Build All Demos        → Assets/Scenes/Puzzles/
```

Drop any puzzle prefab into a zone scene. The demo scenes include trigger items and a player for isolated testing.

## Overview

| # | Puzzle | Key Components | Demo Trigger Items |
|---|---|---|---|
| 1 | [Gem Door](gem-door.md) | `GemSocketMono`, `GemDoorMono` | 3 gems (tag `Gem`) |
| 2 | [Drawbridge](drawbridge.md) | `DrawbridgeMono`, `WeightTriggerMono` | Boulder (tag `Heavy`) |
| 3 | [Cable Cut](cable-cut.md) | `CuttableCableMono` | Sword (tag `Sword`) |
| 4 | [Oil Gears](oil-gears.md) | `OilSprayInteractable`, `RustyGearMono`, `GearDoorMono` | — |
| 5 | [Pressure Plates](pressure-plates.md) | `PressurePlateMono`, `MultiPlateDoorMono` | Heavy boxes |
| 6 | [Domino Chain](domino-chain.md) | `DominoMono`, `ChainGoalMono` | Throwable ball |
| 7 | [Mirror Beam](mirror-beam.md) | `BeamEmitterMono`, `MirrorMono`, `BeamReceiverMono` | — |
| 8 | [Bell Sequence](bell-sequence.md) | `BellMono`, `BellSequenceDoorMono` | Throwable balls |
| 9 | [Balance Scale](balance-scale.md) | `ScalePanMono`, `BalanceDoorMono` | Weight spheres |
| 10 | [Ice & Torch](ice-torch.md) | `TorchMono`, `FireProximityEmitter`, `IceBlockMono` | — |
| 11 | [Pulley Elevator](pulley-elevator.md) | `PulleyElevatorMono`, `PulleyPlatformMono`, `RockDispenserMono` | Starter rocks |

## Architecture

All puzzles are **pure Unity adapters** — no Core changes needed. Puzzle state is ephemeral (resets on scene load). `PuzzleGateMono` is the shared sliding/rising gate used by every puzzle type.

## Tags Required

| Tag | Used by |
|---|---|
| `Gem` | `GemSocketMono` |
| `Sword` | `CuttableCableMono` |
| `Heavy` | `WeightTriggerMono` |
