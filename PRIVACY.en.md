# Privacy Policy

[日本語](./PRIVACY.md) | **English**

Last updated: 2026-09-05

rapore is a 1-on-1 notes app designed around one idea: **your reports' information does not leave your machine.**

## 1. What we collect

**The developer collects no information about you whatsoever.**

- Personal information collected: none
- Usage analytics, telemetry, crash reports: none
- Account registration: not required
- Advertising or tracking: none

## 2. Where your data is stored

Everything you type — names, 1-on-1 notes, profiles, topics, tags — is stored in **a single SQLite file on your own machine**.

| OS | Location |
|---|---|
| macOS | `~/Library/Application Support/rapore/rapore.db` |
| Windows | `%APPDATA%\rapore\rapore.db` |

The exact path is shown in the app's Settings screen. This file is yours; no third party, the developer included, can reach it.

## 3. Network traffic

**rapore makes no outbound connections.** It does not check for updates, validate licences online, sync, or upload backups. Every feature works with no internet connection at all.

The only exception is that clicking a link inside the app (for example, a purchase page) **opens that URL in your default browser**. The browser makes that request, not rapore, and nothing you have typed is ever included in the URL.

## 4. About encryption

The current version does not encrypt the database file itself. **We strongly recommend turning on full-disk encryption — FileVault on macOS, BitLocker on Windows.** Encryption at rest is on the roadmap.

## 5. Backups and sync folders

To back up, use **Settings → Backup → "Create a backup (.db)"** in the app. It uses SQLite's online backup, so you get a single consistent file even while you're using the app.

**Copying the database file by hand is not recommended.** rapore runs SQLite in WAL mode, so your most recent sessions may still be in a separate `rapore.db-wal` file — copying only `rapore.db` loses them. If you must copy by hand, quit the app completely first and copy the whole folder.

For the same reason, putting the database file **directly** into a Dropbox / iCloud Drive / OneDrive folder can corrupt it. Put a copy written by the app there instead (the automatic backup feature writes a consistent snapshot to a folder you choose).

Note that a backup written into a sync folder then falls under that cloud service's privacy policy. **At that point your data does leave your machine.** That decision is yours to make.

## 6. Getting your data out

Session notes and profile fields are stored as **plain Markdown strings**, not a proprietary format, and the database is standard SQLite. You can read it with other tools whenever you want. This app is not designed to trap your data.

## 7. Disclosure to third parties

We hold no such information, so there is nothing to disclose.

## 8. Scope

This policy describes the behaviour of the rapore application itself. It says nothing about your operating system or other software you have installed (backup tools, security software, and so on).

## 9. Changes

If this policy changes, this file is updated and the change is noted in [CHANGELOG.en.md](./CHANGELOG.en.md).

## 10. Contact

Please open an [Issue](../../issues).
