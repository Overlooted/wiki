# Portal System

The portal is a **seamless additive scene load** — the hub (village) and dungeon coexist in world space simultaneously. `ScenePortalManager` aligns the two scenes at runtime so the doorways line up perfectly.

## Zone Scene Setup

1. Place `PortalMono` on the dungeon wall GameObject
2. Set `_zoneId` to the zone ID (e.g. `zone.crypt`)
3. Assign `_portalVisual` (the archway mesh — starts disabled, enabled when portal unlocks)
4. Add `LandingPadMono` with a trigger collider sized to the pad area near the portal
5. Add `PortalThresholdMono` at the doorway centre — assign dungeon + village PP volumes

## Hub Scene Setup

1. Place `VillagePortalAnchor` on an empty GameObject at the centre of the village entrance doorway
    - Floor level, facing **into** the village
2. Add a local PP Volume covering the village area
3. Add a local PP Volume just inside the dungeon side with dungeon lighting profile

## ScenePortalManager

Singleton on the Bootstrap GameObject. Set `_villageSceneName` to the hub scene name (e.g. `"Hub"`).

At runtime it:
1. Additively loads the hub scene when the player approaches the portal
2. Finds `VillagePortalAnchor` in the hub scene
3. Offsets the hub scene's root transform so both doorways align
4. Blends PP volumes via `PortalThresholdMono` as the player crosses the threshold

## Level Design Contract

- Both doorways must be the **same size** and face **opposing directions**
- Keep hub geometry at a large world-space offset in the editor (e.g. Z+500) to prevent clipping during design — `ScenePortalManager` corrects this at runtime
- Use PP volume blend distance ~2–3m for a smooth atmospheric transition
