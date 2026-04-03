# Build Pipeline

GitHub Actions workflow at `.github/workflows/ci.yml` using [GameCI](https://game.ci).

## Branch Strategy

| Branch | Builds | Deploys |
|---|---|---|
| `master` | Always | itch.io `windows` (stable) |
| `development` | Only if commit contains `[deploy]` | itch.io `windows-beta` |
| Pull Requests | Windows build only | No deploy |

## Triggering a Beta Deploy

Include `[deploy]` in the commit message on the `development` branch:

```bash
git commit -m "Add grease gun particle effect [deploy]"
```

Without `[deploy]`, pushes to `development` are not built — preserving GitHub Actions minutes.

## Build Config

- Platform: `StandaloneWindows64`
- Unity version: `6000.3.10f1`
- Versioning: `Semantic`
- Runner: `windows-latest`

## Required GitHub Secrets

| Secret | Value |
|---|---|
| `UNITY_LICENSE` | Contents of your `.ulf` license file |
| `UNITY_EMAIL` | Unity account email |
| `UNITY_PASSWORD` | Unity account password |
| `BUTLER_CREDENTIALS` | itch.io butler API key |
| `DISCORD_WEBHOOK` | Discord channel webhook URL |

Set these at `github.com/Overlooted/{repo}/settings/secrets/actions`.
