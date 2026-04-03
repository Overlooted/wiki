# Oil Gears

The player sprays oil on rusted gears to make them turn, which opens a gear-locked door.

## Components

| Component | Role |
|---|---|
| `OilSprayInteractable` | Player-interactable oil can |
| `RustyGearMono` | Receives oil, starts rotating |
| `GearDoorMono` | Opens when all gears are spinning |

## Setup

1. Place the **Oil Gears** prefab
2. Assign gear references on `GearDoorMono`
3. No trigger items needed — the oil can is built into the prefab
