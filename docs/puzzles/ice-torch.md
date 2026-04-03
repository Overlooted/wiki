# Ice & Torch

Melt an ice block using a torch's heat proximity to unblock the gate.

## Components

| Component | Role |
|---|---|
| `TorchMono` | Interactable; toggles flame on/off |
| `FireProximityEmitter` | Emits heat radius while torch is lit |
| `IceBlockMono` | Melts (destroys self) when heat accumulates |

## Setup

1. Place the **Ice Torch** prefab
2. Position the torch so its heat radius can reach the ice block
3. `IceBlockMono` blocks the path until melted — attach `PuzzleGateMono` or use it to unblock a physics obstacle
