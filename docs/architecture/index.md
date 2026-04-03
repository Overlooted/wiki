# Architecture Overview

Overlooted uses a strict two-repo split:

```
Overlooted-Core/          Pure C# — zero Unity dependency
  src/Overlooted.Core/    Referenced as a local Unity package
  Data/                   JSON registries (source of truth)
  docs/                   GDD, wiki

Overlooted-Unity/         Unity 6.3 project
  Assets/Scripts/Adapters/   MonoBehaviour adapters only
  Assets/StreamingAssets/Data/  Copy of Core/Data (runtime access)
  Assets/Editor/Overlooted/     Editor tooling & scene builders
```

---

## Two-Repo Pattern

```
Unity Event
    ↓
MonoBehaviour Adapter   (Overlooted-Unity)
    ↓
Core Method Call        (Overlooted-Core)
    ↓
Pure C# Logic / State
```

**When something goes wrong:**

| Symptom | Fix location |
|---|---|
| Wrong value, wrong state | Overlooted-Core |
| Missing inspector ref, wrong event, physics layer | Adapter script in Overlooted-Unity |
| Needs a new API | Overlooted-Core first, then adapter |

---

## Key Concepts

- **Data-driven** — 5 JSON registries loaded at runtime by `DataManager`. Nothing is hardcoded.
- **No manual inspector wiring for audio/VFX** — `AssetLibrary` maps IDs to Resources paths.
- **Scene builders** — all scenes are built programmatically via editor menu, not by hand.
- **Localization first** — all display text goes through `LocalizationManager.Instance.Get(key)`.
