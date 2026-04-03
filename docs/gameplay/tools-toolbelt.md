# Tools & Toolbelt

## Tool Definitions

Tools are defined in `tools.json` and loaded into `DataManager.ToolRegistry`. Each tool has an ID, display name key, cost, and capability flags.

## ToolbeltMono

Singleton wrapping Core `Toolbelt`. Manages equipped tool slots (1–5). Lives on the Bootstrap GameObject.

## ToolDisplayMono

Placed in the hub shop — one per tool. Shows tool name, cost, and description via `SimpleTooltip`. Handles the buy interaction.

**On purchase:**

1. `ProgressionManager.TryUnlockTool(toolId)` is called
2. If successful: tooltip updates to show "Owned", visual changes to indicate purchased
3. `FlashCostRed()` coroutine fires if the player can't afford it

**Inspector fields:**
- `_toolId` — matches a tool ID in `tools.json`
- `_displayVisual` — the mesh/GameObject to tint on purchase
- `_tooltip` — `SimpleTooltip` component on the same GameObject

## ToolSlotHUD

Displays the current toolbelt state (slots 1–5). Subscribes to `ProgressionManager.OnToolUnlocked`.

## tools.json

```json
{
  "id": "tool.grease_gun",
  "displayNameKey": "tool.grease_gun",
  "cost": 200,
  "description": "Lubricates rusty mechanisms"
}
```
