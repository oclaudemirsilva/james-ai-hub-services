# james-ai-hub-services

Public-facing **policy and service-contract hub** for the JAMES AI Assistant project.

## What this repo is

A single source of truth for the policies and contracts that govern how
JAMES interacts with external services (TikTok, Meta, Google, Spotify,
and any future integration). It exists because third-party API providers
require publicly accessible URLs for Terms of Service, Privacy Policy,
and Data Deletion instructions before approving an app for production.

## What's here

| File | Purpose |
|---|---|
| [TERMS.md](./TERMS.md) | Terms of Service for the JAMES project |
| [PRIVACY.md](./PRIVACY.md) | Privacy Policy — no backend, no telemetry, all data stays local |
| [DATA_DELETION.md](./DATA_DELETION.md) | How to delete JAMES data + revoke third-party access |
| [SECURITY.md](./SECURITY.md) | Vulnerability disclosure policy |

## What this repo is NOT

- ❌ The JAMES source code (lives in a separate repository)
- ❌ A runtime component — JAMES does not fetch from this repo at execution
- ❌ User data — JAMES has no backend; this repo stores policy text only

## Who can use this

| Audience | Action |
|---|---|
| Anyone | Read any document at the URLs above |
| Reviewer (TikTok, Meta, Spotify, etc.) | Verify compliance against required policy URLs |
| Contributor | Open a pull request to propose changes |
| Self-hoster running the official JAMES code unchanged | These policies apply to your installation as written |
| Anyone modifying the JAMES code | These policies apply only to the official, unmodified project; modified forks need their own policies |

## Contact

- **Policy questions:** open an issue, or email the address listed in [TERMS.md](./TERMS.md)
- **Vulnerability disclosure:** see [SECURITY.md](./SECURITY.md)
