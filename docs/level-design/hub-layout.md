# Hub Layout

The hub is split into two parts:

- **Hub scene** (`Assets/Scenes/Hub.unity`) — Bootstrap GO, player, lighting, HUD, and the HubLayout prefab instance
- **HubLayout prefab** (`Assets/Prefabs/Layout/HubLayout.prefab`) — all gameplay objects: floor, vendors, portals, cart recaller, tool shop

The prefab separation means you can edit the layout freely without losing your work on rebuilds.

## Editing the Layout

Open `HubLayout.prefab` in Prefab Mode and make changes. The Hub scene references this prefab as an instance — your changes persist through **Overlooted → Build → 3 - Zone Scenes** because the builder only replaces the Bootstrap GO, not the layout prefab.

## Resetting to Default

**Overlooted → Build → Layout → Hub (Reset Layout)**

This deletes the existing `HubLayout.prefab`, regenerates it from defaults, and updates the Hub scene. **All customisations are lost.**

## Default Layout Contents

| Object | Position | Notes |
|---|---|---|
| HubFloor | 0, -0.5, 0 | 24×24m box collider |
| Vendor (Blacksmith) | -6, 0, 10 | |
| Vendor (Jeweler) | 0, 0, 10 | |
| Vendor (General) | 6, 0, 10 | |
| Portal (Crypt) | -4, 0, 18 | zone.crypt |
| Portal (Forest) | 0, 0, 18 | zone.forest |
| Portal (Clockwork) | 4, 0, 18 | zone.clockwork_fortress |
| CartRecaller | -8, 0, 5 | |
| ToolShop | 8, 0, 5 | |
| VillageEntrance | 0, 0, 20 | VillagePortalAnchor for portal alignment |
