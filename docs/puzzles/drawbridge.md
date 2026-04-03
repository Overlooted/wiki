# Drawbridge

A heavy object must be placed on a weight trigger to lower the bridge.

## Components

| Component | Role |
|---|---|
| `WeightTriggerMono` | Fires when a `Heavy`-tagged object enters |
| `DrawbridgeMono` | Rotates the bridge transform down on trigger |

## Setup

1. Place the **Drawbridge** prefab
2. Assign `WeightTriggerMono` reference on `DrawbridgeMono`
3. Place a boulder or heavy box in the scene tagged `"Heavy"`
