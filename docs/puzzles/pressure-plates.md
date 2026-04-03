# Pressure Plates

Multiple plates must all be activated simultaneously to open the gate.

## Components

| Component | Role |
|---|---|
| `PressurePlateMono` | Activates when a `Heavy`-tagged object is on it |
| `MultiPlateDoorMono` | Opens when all assigned plates are active |

## Setup

1. Place the **Pressure Plates** prefab
2. Assign all `PressurePlateMono` references on `MultiPlateDoorMono`
3. Place heavy boxes (tagged `Heavy`) in the scene — one per plate required
