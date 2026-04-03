# Domino Chain

Knock over the first domino to start a chain reaction that triggers the goal.

## Components

| Component | Role |
|---|---|
| `DominoMono` | Physics-based domino; knocks the next on fall |
| `ChainGoalMono` | Fires when the final domino reaches it |
| `PuzzleGateMono` | Opens on `ChainGoalMono` trigger |

## Setup

1. Place the **Domino Chain** prefab
2. A throwable ball is included in the demo scene to start the chain
3. Adjust domino spacing so the chain reliably continues
