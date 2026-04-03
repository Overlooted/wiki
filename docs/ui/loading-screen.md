# Loading Screen

`LoadingScreen` is a `DontDestroyOnLoad` singleton that wraps Feel's `MMAdditiveSceneLoadingManager`.

## How It Works

1. `LoadingScreen.Instance.LoadScene("SceneName")` is called
2. Feel's `MMAdditiveSceneLoadingManager.LoadScene()` additively loads `MMAdditiveLoadingScreen.unity`
3. Feel handles: entry fade, progress bar (`MMProgressBar`), scene lifecycle
4. `SetHold(BeforeExitFade, true)` pauses after 100% — shows "Press any key to continue"
5. On any key press: hold released → Feel plays exit fade → destination scene revealed

## Requirements

- `MMAdditiveLoadingScreen.unity` must be in Build Settings (added by `BuildSettingsSetup`)
- `LoadingScreen` prefab must be in the first scene or instantiated before use

## Usage

```csharp
LoadingScreen.Instance.LoadScene("zone.crypt");
```
