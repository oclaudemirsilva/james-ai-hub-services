# Privacy Policy — James AI Assistant

**Last updated:** 2026-05-20

## TL;DR

James AI Assistant ("JAMES") is a **personal, single-user desktop
application that runs entirely on the user's local machine**. The
software has **no backend, no central server, no shared database, and
no analytics or telemetry**. All data the software handles stays on
the user's local disk. The Developer does not see, collect, or
transmit any data from any user's machine.

## 1. What Data the Software Processes Locally

When you run JAMES on your own machine, the software may locally:

### 1.1 Read inputs from your hardware
- **Microphone audio** — for voice commands (when you activate it)
- **Camera frames** — only for capabilities you explicitly enable
- **Screen content** — only for capabilities you explicitly enable
  (e.g., "describe what's on my screen")
- **Keyboard input** — only when push-to-talk hotkey is active

### 1.2 Read content from your filesystem
- Local files you explicitly point the software to (videos to upload,
  notes to read, etc.)
- The software's own config files in `config/` (your API credentials)
- The software's own memory/cache files in `memory/`

### 1.3 Make API calls **on your behalf**
When you authorize integrations (Google, YouTube, TikTok, Meta,
ElevenLabs, OpenAI, Anthropic, etc.), the software makes API calls
**from your local machine to those third parties** using credentials
**you generated and provided**. Each third party has its own privacy
policy — review them at the relevant developer portals.

## 2. What the Software Does NOT Do

JAMES does **NOT**:

- ❌ Send any of your data to a backend operated by the Developer (there
  is no such backend)
- ❌ Phone home with telemetry, analytics, or crash reports to the
  Developer
- ❌ Share, sell, or transmit your data to any third party except the
  third-party APIs you have explicitly authorized
- ❌ Read content from any social media account you have not authorized
  via OAuth
- ❌ Read content from other users' accounts on any platform — only
  your own
- ❌ Run as a service for any party other than the local user who
  installed it

## 3. Where Credentials Are Stored

OAuth tokens, API keys, and other credentials you configure are stored
**locally on your machine** in these files:

- `config/api_keys.json` — third-party API credentials you added
- `config/google_oauth_client.json` — Google OAuth Desktop client
- `config/google_token.json` — Google OAuth tokens (after consent flow)
- Other per-integration cache files (e.g., `memory/spotify_token.json`)

All of these files are:
- **Stored exclusively on your local filesystem**
- **Gitignored** — they are never committed to the repository
- **OS-protected** by your local user account's file permissions

You are responsible for keeping these files private (e.g., not posting
them publicly, not sharing them).

## 4. Third-Party APIs

JAMES, when you authorize it, calls APIs of:

- **Google** (Calendar, Gmail, Drive, YouTube)
- **TikTok** (Content Posting API)
- **Meta** (Instagram Graph API)
- **ElevenLabs** (Text-to-Speech)
- **OpenAI / Anthropic / Gemini** (Large Language Models)
- **Spotify** (Web API)
- Others you opt in to via configuration

Each third party processes the data you send through their API
according to **their own privacy policy and terms of service**. The
Developer is not party to that relationship. You should review the
privacy policies of any service you integrate before granting access.

## 5. Data Retention

Local data (logs, memory, cached responses) is retained on your
machine until **you delete it**. You may delete any of the software's
local data at any time by:

- Deleting files under `config/`, `memory/`, `logs/`
- Or following the procedure in [DATA_DELETION.md](./DATA_DELETION.md)

The software does not have a remote storage tier, so deletion is
final and complete the moment you remove the local files.

## 6. Children

JAMES is not directed at children under 13. The Developer does not
knowingly collect data from children. If you are a parent and your
child has installed JAMES on a device you own, you may delete it the
same way as any other software (uninstall + remove `config/` and
`memory/` directories).

## 7. Changes to This Policy

The Developer may revise this policy at any time. Updated policies are
published in the same location as the source code. Users who clone the
repository should `git pull` to see updates.

## 8. Contact

For privacy-related questions, open an issue at
[github.com/oclaudemirsilva/james-ai-assistant/issues](https://github.com/oclaudemirsilva/james-ai-assistant/issues)
or email the address listed in the repository.
