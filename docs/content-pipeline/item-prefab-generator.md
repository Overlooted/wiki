# Item Prefab Generator

**Overlooted → Content → Generate Item Prefabs**

Reads every entry in `items.json` and creates a prefab variant of `ItemBase.prefab` for each item that doesn't already have one. Run this after adding new items to get playable prefabs immediately.

## What It Does Per Item

1. Checks if `Assets/Prefabs/Items/{id}.prefab` already exists — if yes, **skips it**
2. Instantiates `ItemBase.prefab` as a variant
3. Sets `SimpleTooltip.infoLeft` to the item ID as a placeholder
4. If `meshId` is set and a prefab exists at `Resources/ItemMeshes/{meshId}`:
    - Swaps the `MeshFilter.sharedMesh`
    - Copies `MeshRenderer.sharedMaterials`
    - Resizes `BoxCollider` to match mesh bounds
5. Saves to `Assets/Prefabs/Items/{id}.prefab`

## Requirements

- Run **Phase 2 — Prefabs** first so `ItemBase.prefab` exists
- Mesh prefabs must be in `Resources/ItemMeshes/` (not just `Assets/`)

## Forcing a Rebuild

Existing prefabs are **never overwritten**. To regenerate:

1. Delete the specific prefab file from `Assets/Prefabs/Items/`
2. Run Generate Item Prefabs again

To regenerate all: delete the entire `Assets/Prefabs/Items/` folder contents (except `ItemBase.prefab`) then regenerate.
