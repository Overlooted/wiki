# Deploying to itch.io

Deploys are handled by [butler](https://itch.io/docs/butler/) via `josephbmanley/butler-publish-itchio-action`.

## Channels

| Channel | Branch | Audience |
|---|---|---|
| `windows` | `master` | Public stable release |
| `windows-beta` | `development` (with `[deploy]`) | Beta testers |

## itch.io Page

`serinoxxx/overlooted`

## Discord Notification

A Discord embed is posted to the configured webhook after every successful deploy. It includes:

- Branch name
- itch.io channel
- Commit message

Webhooks for both stable and beta deploys go to the same channel — configure in the `DISCORD_WEBHOOK` secret.

## Manual Deploy

To trigger a build + deploy from any branch without pushing code:

GitHub → Actions → CI → Run workflow → select branch.
