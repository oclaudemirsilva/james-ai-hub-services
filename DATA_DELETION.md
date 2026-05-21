# Data Deletion Instructions — James AI Assistant

**Last updated:** 2026-05-20

## Summary

James AI Assistant ("JAMES") is a **single-user desktop application
that stores all data locally on the user's own machine**. There is **no
backend, no central database, no user accounts** beyond the local
operating system user.

Because all data lives on your machine, **you have full control to
delete it at any time** — no request to a service operator is needed.

This document is published per Meta's requirement that every app
provide a "Data Deletion Instructions URL", and the same procedure
satisfies any platform's data-deletion requirements (TikTok, Google,
etc.).

## 1. To delete all JAMES data on your machine

### 1.1 Stop the application

If JAMES is running, close it via Task Manager, the kill script
(`scripts/kill_james.ps1`), or:

```powershell
Get-Process python -ErrorAction SilentlyContinue | Where-Object {
  (Get-CimInstance Win32_Process -Filter "ProcessId = $($_.Id)").CommandLine -match 'main.py'
} | Stop-Process -Force
```

### 1.2 Delete local data directories

Open the JAMES installation folder (typically the `Mark-XXXIX/` directory
where you cloned the repository) and **delete the following**:

```
config/          # Your API credentials + OAuth tokens
memory/          # Local caches, conversation history, brain data
logs/            # Runtime logs
_runtime_*.log   # Any runtime log files at the root
```

On Windows PowerShell:

```powershell
Remove-Item -Recurse -Force config, memory, logs
Remove-Item _runtime_*.log -ErrorAction SilentlyContinue
```

This permanently removes every byte of your data the software stored
on your machine.

### 1.3 (Optional) Uninstall the software entirely

```powershell
# From the parent directory of where you cloned the repo:
Remove-Item -Recurse -Force james-ai-assistant
```

## 2. To revoke access to third-party APIs

Deleting local files removes your tokens locally, but the third-party
service still has an OAuth grant record. To **fully revoke** the
software's access to your accounts:

### 2.1 Google (Calendar, Gmail, Drive, YouTube)

1. Go to [myaccount.google.com/permissions](https://myaccount.google.com/permissions)
2. Find **"James AI Assistant"** (or the app name you used during
   OAuth setup)
3. Click **Remove Access**

### 2.2 TikTok

1. TikTok app or [tiktok.com](https://tiktok.com) → Profile → Settings
   → **Apps and websites**
2. Find **"James AI Assistant"** → **Disconnect**

### 2.3 Meta (Instagram + Facebook)

1. Go to [facebook.com/settings/?tab=business_tools](https://facebook.com/settings/?tab=business_tools)
2. Find **"James AI Assistant"** under **Business Integrations**
3. Click **Remove**

This invalidates the Page Access Token JAMES had, so even if your
local config file still has the token, Meta will reject it.

### 2.4 Spotify

1. [spotify.com/account/apps](https://www.spotify.com/account/apps)
2. Find **"James AI Assistant"** → **Remove Access**

### 2.5 ElevenLabs

ElevenLabs uses raw API keys, not OAuth. To revoke:

1. [elevenlabs.io/app/settings/api-keys](https://elevenlabs.io/app/settings/api-keys)
2. Delete the API key you used in `config/api_keys.json`
3. (Optional) Generate a new one for any other purpose

## 3. To request the Developer delete data

**The Developer does not hold any data about you.** JAMES has no
backend infrastructure — there is no server, database, or cloud
storage operated by the Developer that could hold your data.

If you have nonetheless interacted with the Developer (e.g., by
opening a GitHub issue), the data in that issue is hosted by
**GitHub** under their own privacy policy. To delete it:

1. Edit or delete your own comments at
   [github.com/oclaudemirsilva/james-ai-assistant/issues](https://github.com/oclaudemirsilva/james-ai-assistant/issues)
2. Or contact GitHub support to remove your account

## 4. Confirmation

After following steps 1.1-1.2 above, you can verify deletion by
checking that the directories listed no longer exist:

```powershell
Test-Path config, memory, logs
# Should output: False, False, False
```

If you also performed step 2 (revoking third-party access), you can
verify by attempting to run JAMES again — it will report all
integrations as "not configured" because the tokens are gone both
locally and at the third party.

## 5. Contact

If you need help with the deletion process, open an issue at
[github.com/oclaudemirsilva/james-ai-assistant/issues](https://github.com/oclaudemirsilva/james-ai-assistant/issues).
