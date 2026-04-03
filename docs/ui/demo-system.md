# Demo System

## Flow

```
Main Menu → Demos button → DemoSelectUI panel
    → click a demo → LoadingScreen → demo scene
    → ESC → DemoReturnUI → LoadingScreen → Main Menu
```

## DemoSelectUI

UI Toolkit panel with a scrollable list of all 11 puzzle demos. Each entry shows the puzzle name and a short description. Clicking loads the scene via `LoadingScreen.Instance.LoadScene(sceneName)`.

## DemoReturnUI

UGUI overlay present in every demo scene. Shows "ESC : Back to Menu". On ESC press:
- Uses `LoadingScreen.Instance` if available (full Feel loading experience)
- Falls back to `SceneManager.LoadScene("MainMenu")` if not

## Build Settings

All 11 demo scenes plus the Feel loading screen must be registered in Build Settings. `BuildSettingsSetup` handles this automatically when you run the scene builders.
