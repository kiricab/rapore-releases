# Privacy Policy

[日本語](./PRIVACY.md) | **English**

Last updated: 2026-09-26

rapore is a 1-on-1 notes app designed around one idea: **your reports' information does not leave your machine.**

## 1. What we collect

**The developer collects no information about you whatsoever.**

- Personal information collected: none
- Usage analytics, telemetry, crash reports: none
- Account registration: not required
- Advertising or tracking: none

## 2. Where your data is stored

Everything you type — names, 1-on-1 notes, profiles, topics, tags, **today’s read (the seven-level entry)**, **member photos**, and images you paste into your notes — is stored in **a single SQLite file on your own machine**. Images live inside that same file, so nothing is written to an outside folder or server.

| OS | Location |
|---|---|
| macOS | `~/Library/Application Support/rapore/rapore.db` |
| Windows | `%APPDATA%\rapore\rapore.db` |

The exact path is shown in the app's Settings screen. This file is yours, and **the developer cannot reach it** — because the app sends nothing outbound, there is no route by which your data could arrive on the developer's side.

There is one exception, and only if **you** create it: when you turn on **AI access**, the AI client you connect can read this data. It is off by default, and while it is off the route does not exist at all. See [4. Letting your own AI work with rapore](#4-letting-your-own-ai-work-with-rapore-ai-access-off-by-default).

## 3. Network traffic

**By default, rapore makes no outbound connections.** It never validates licences online, syncs, uploads backups, or sends usage analytics, telemetry or crash reports — no setting turns any of that on. Every feature works with no internet connection at all.

There are exactly two exceptions.

### (1) Checking for a new version (off by default, only if you turn it on)

If you enable "Tell me about new versions" in Settings, the app asks GitHub — at most once a day — for **the latest version number** of the releases repository, and nothing else.

- The request carries only itself: the connection GitHub sees (your IP address and the app's name). **Nothing you have typed, no details about your reports, no usage data and no device identifier is included.**
- Even when a newer version exists, **the app never downloads an update or replaces itself.** It shows you a notice; going to fetch it is your decision.
- **It is off by default.** The app asks you once, on first launch, and **until you choose "Tell me", this request never happens even once.** You can change your mind at any time under **Settings → General**.

### (2) Opening a link from inside the app

Clicking a link (for example, a purchase page) **opens that URL in your default browser**. The browser makes that request, not rapore, and nothing you have typed is ever included in the URL.

> Separately: **this is not outbound traffic from rapore**, but if you turn it on, a route is created that hands your data to a generative AI running on your own machine (**off by default**). Because it is different in kind, it has its own section — 4. below.

## 4. Letting your own AI work with rapore (AI access, off by default)

rapore ships with a way for a generative AI you pay for yourself (Claude Desktop, Claude Code, Codex CLI, and so on) to read and write your 1-on-1 records — a built-in MCP server. **This is off by default. While it is off, nothing in this section happens.**

If you turn it on, here is exactly what does and does not happen.

- **Even with this feature, rapore itself sends nothing outbound.** All rapore provides is a single local channel on your machine (a socket file). **It opens no network port.**
- **The one doing the sending is the AI client you connected.** Whatever records you let the AI read **go to that AI's provider (Anthropic, OpenAI, and so on).** How they handle it **falls under that service's privacy policy** and is outside rapore's control.
- **At that point your data does leave your machine.** That decision is yours to make — the same principle as the sync folders in 6.

### Permission comes in two steps

| Setting | What the AI can read | What the AI can write |
|---|---|---|
| **Off (default)** | Nothing (**the route does not exist**) | Nothing |
| "Enable AI access" only | Member names, roles, teams | Create and edit records; update profiles |
| "Also allow reading" enabled | The above + **record bodies, profiles, today's read** | Same as above |

- **Even when you allow writing only, member names, roles and teams do go to the AI.** They are needed to decide whose record it is. Record bodies, profiles and today's read do not.
- **If you do not want the AI reading your record bodies, leave "Also allow reading" off.**
- The first time you enable it, a screen shows you all of the above. **Until you explicitly allow it, this route is never created.** You can change your mind at any time under **Settings → AI access**.

### How it works

- Connecting requires a shared secret (a token). It exists to stop other programs connecting on their own, and it is **stored in plain text in the settings file (`rapore-settings.json`)** — the same treatment as your licence key. The channel file itself is created so that only you can read it.
- rapore keeps a record of what the AI did (the most recent operation name and counts) **in memory only**, and shows it in Settings. **It is never written to a file** — a log of "which member's records the AI read" would itself be sensitive information.

## 5. About encryption

The current version does not encrypt the database file itself. **We strongly recommend turning on full-disk encryption — FileVault on macOS, BitLocker on Windows.** Encryption at rest is on the roadmap.

## 6. Backups and sync folders

To back up, use **Settings → Backup → "Create a backup (.db)"** in the app. It uses SQLite's online backup, so you get a single consistent file even while you're using the app.

**Copying the database file by hand is not recommended.** rapore runs SQLite in WAL mode, so your most recent sessions may still be in a separate `rapore.db-wal` file — copying only `rapore.db` loses them. If you must copy by hand, quit the app completely first and copy the whole folder.

For the same reason, putting the database file **directly** into a Dropbox / iCloud Drive / OneDrive folder can corrupt it. Put a copy written by the app there instead (the automatic backup feature writes a consistent snapshot to a folder you choose).

Note that a backup written into a sync folder then falls under that cloud service's privacy policy. **At that point your data does leave your machine.** That decision is yours to make.

Also, **when an update changes how records are stored, the app automatically saves a copy before migrating** (named `rapore-pre-v<version>-<timestamp>.db`, next to your database; the three most recent are kept and older ones are removed automatically). These copies stay on your machine and are never transmitted.

## 7. Getting your data out

Session notes and profile fields are stored as **plain Markdown strings**, not a proprietary format, and the database is standard SQLite. You can read it with other tools whenever you want. This app is not designed to trap your data.

## 8. Disclosure to third parties

**The developer** holds no such information, so there is nothing for the developer to disclose.

If **you** turn on the AI access described in 4., data does go to the AI service you chose. That is not disclosure by the developer — it is **you using that service**, and its handling follows that service's privacy policy.

## 9. Scope

This policy describes the behaviour of the rapore application itself. It says nothing about your operating system or other software you have installed (backup tools, security software, and so on).

## 10. Changes

If this policy changes, this file is updated and the change is noted in [CHANGELOG.en.md](./CHANGELOG.en.md).

## 11. Contact

Please open an [Issue](../../issues).
