# Main Menu

Built by `MainMenuSceneBuilder` using UI Toolkit.

## Scripts

- `MainMenuUI` — Start, Demos, Options, Exit buttons
- `SettingsUI` — audio, graphics, language, controls panels

## Settings Panel

`SettingsUI` reads/writes `SaveManagerMono` settings. Changes are applied immediately and persisted on close.

| Setting | Backed by |
|---|---|
| Language | `LocalizationManager` |
| Audio volumes | Audio Mixer parameters |
| Quality | `QualitySettings.SetQualityLevel` |
| Controls | `InputActionReference` rebinding |
