# Mirror Beam

Rotate mirrors to direct a laser beam from emitter to receiver.

## Components

| Component | Role |
|---|---|
| `BeamEmitterMono` | Fires a Physics.Raycast beam each frame |
| `MirrorMono` | Reflects the beam via `Reflect()` on normal |
| `BeamReceiverMono` | Opens the gate when the beam hits it |

## Setup

1. Place the **Mirror Beam** prefab
2. Position mirrors between emitter and receiver
3. No trigger items needed — player physically rotates mirrors via interaction
