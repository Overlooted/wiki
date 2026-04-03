# Pause Menu

`PauseMenuUI` — in-game ESC menu built with UI Toolkit.

## Features

- Save game
- Load game
- Settings (delegates to `SettingsUI`)
- Return to Main Menu
- Quit

## Cursor Handling

On open: `UnityEngine.Cursor.lockState = CursorLockMode.None` — cursor freed for UI interaction.  
On close: cursor re-locked for FPS control.

The `Interactor` component respects `Interactor.Blocked = true` while the pause menu is open, preventing accidental interactions through the UI.

## Present in All Gameplay Scenes

`PauseMenuPrefabPath` is placed in every scene by `ZoneSceneBuilder`, `ShopTestSceneBuilder`, and `OnboardingSceneBuilder`. It is not present in the Bootstrap or Main Menu scenes.
