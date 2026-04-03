# Cable Cut

The player must use a sword (or any item tagged `Sword`) to cut a cable, releasing a counterweight that opens the gate.

## Components

| Component | Role |
|---|---|
| `CuttableCableMono` | `OnTriggerEnter` — checks `CompareTag("Sword")` |
| `PuzzleGateMono` | Gate opens when cable is cut |

## Setup

1. Place the **Cable Cut** prefab
2. Assign the `PuzzleGateMono` reference on `CuttableCableMono`
3. Place a sword item in the scene tagged `"Sword"`
