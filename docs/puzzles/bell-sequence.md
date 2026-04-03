# Bell Sequence

Strike bells in the correct order to open the gate.

## Components

| Component | Role |
|---|---|
| `BellMono` | Rings when struck by a thrown object; reports to sequence door |
| `BellSequenceDoorMono` | Tracks sequence; opens gate when correct order completed |

## Setup

1. Place the **Bell Sequence** prefab
2. Set the correct sequence on `BellSequenceDoorMono`
3. Provide throwable balls in the scene for the player to throw
