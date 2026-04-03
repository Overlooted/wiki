# Builder Settings

`BuilderSettings` is a ScriptableObject at `Assets/Editor/BuilderSettings.asset`.

Create or open via **Overlooted → Open Builder Settings**.

## Fields

### Player Prefabs (StarterAssets)

The three-prefab FPS setup from StarterAssets:

| Field | Prefab |
|---|---|
| `mainCameraPrefab` | `StarterAssets/.../MainCamera.prefab` |
| `playerCapsulePrefab` | `StarterAssets/.../PlayerCapsule.prefab` |
| `playerFollowCameraPrefab` | `StarterAssets/.../PlayerFollowCamera.prefab` |

These are used by `SceneBuilderBase.AddPlayer()`. The `PlayerFollowCamera` has its `Follow` target wired to `PlayerCameraRoot` (child of `PlayerCapsule`) automatically so vertical look works.

### Gameplay Prefabs

| Field | Purpose |
|---|---|
| `goblinPrefab` | GoblinMono prefab |
| `itemBasePrefab` | Base item prefab |
| `sellParticlePrefab` | VFX on successful sale |

### UI References

| Field | Purpose |
|---|---|
| `panelSettings` | UI Toolkit PanelSettings asset |
| `mainMenuUxml` | Main menu document |
| `settingsUxml` | Settings panel document |
| `demoSelectUxml` | Demo select panel document |

### Audio

| Field | Purpose |
|---|---|
| `sfxMixer` | SFX audio mixer group |
| `musicMixer` | Music audio mixer group |
