# Gem Door

The player must find and place three gems into sockets to open the gate.

## Components

| Component | Role |
|---|---|
| `GemSocketMono` | Trigger zone that accepts items tagged `Gem` |
| `GemDoorMono` | Gate that opens when all sockets are filled |
| `PuzzleGateMono` | Shared sliding/rising gate (on the same GO as `GemDoorMono`) |

## Setup

1. Place the **Gem Door** prefab from `Assets/Prefabs/Puzzles/`
2. Assign the three `GemSocketMono` references on `GemDoorMono`
3. Place 3 gem items in the scene tagged `"Gem"`

## Gem Items

Gems use `ItemMono` with the `Gem` tag. In the demo scene they are pre-placed near the puzzle.
