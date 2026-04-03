# Progression

## ProgressionManager

Singleton. Wraps Core `ProgressionSystem`. Tracks which tools the player owns and which zones are unlocked.

```csharp
ProgressionManager.Instance.TryUnlockTool("tool.grease_gun");
ProgressionManager.Instance.OnToolUnlocked += handler;
```

## ZonePortalMono

Placed on zone portal GameObjects in the hub. Checks `ProgressionSystem` on player approach and either:
- Opens the portal (requirements met)
- Shows a lock reason string explaining what tool is needed

**Inspector fields:**
- `_zoneId` — matches a zone ID in `zones.json`
- `_lockReasonText` — `TextMeshPro` component for the "requires X" message

## Zone Requirements

Defined in `zones.json`:

```json
{
  "id": "zone.clockwork_fortress",
  "requiredTools": ["tool.fireproof_boots", "tool.grappling_hook"]
}
```

The player must own all listed tools before the portal opens.

## Tool Shop Setup

Tool display stands are placed in the hub scene (built by `ZoneSceneBuilder`). Each `ToolDisplayMono` links to a tool ID and handles the buy interaction. On purchase, `ProgressionManager.TryUnlockTool` is called and the event fires to update HUD and unlock portals.
