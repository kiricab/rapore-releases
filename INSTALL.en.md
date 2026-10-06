# Installing rapore

[日本語](./INSTALL.md) | **English**

> **Please read this first.** **The macOS version is notarized by Apple**, so you can download it and open it as is. **The Windows version is not code-signed yet**, so Windows will show a "Windows protected your PC" warning the first time you open it. This is not a sign that something is wrong with rapore — it's because a solo developer has not yet paid for a Windows signing certificate. The steps below get you through it.

---

## macOS

### 0. Check your Mac

**rapore requires a Mac with Apple Silicon (M1 / M2 / M3 / M4 …). Intel Macs are not supported.**

Open  menu → About This Mac and look at the "Chip" line.

- It says **Apple M1 / M2 / M3 / M4 …** → you're good, continue below
- It says **Intel Core …** → sorry, rapore won't run on this machine

There is no Intel build. Rosetta doesn't help either: Rosetta runs Intel apps on Apple Silicon, not the other way around.

### 1. Download

Download `rapore-<version>-arm64.dmg`.

### 2. Install

Double-click the DMG and drag `rapore` into your `Applications` folder.

### 3. First launch

The first time you double-click `rapore`, macOS asks for confirmation:

> "rapore" is an app downloaded from the Internet. Are you sure you want to open it?

Click **Open** and rapore starts. After that, it opens normally with a double-click.

rapore is notarized by Apple, so you don't need Terminal or any changes in System Settings.

> **If you used v0.4.0 or earlier**: earlier versions were not code-signed, and you had to open them with a Terminal command (`xattr`) or similar. Versions after v0.4.0 don't need that.

---

## Windows

### 1. Download

Download `rapore-Setup-<version>-x64.exe`.

### 2. First launch (this is where the warning appears)

Double-clicking it shows:

> Windows protected your PC

1. Click **"More info"**
2. Click the **"Run anyway"** button that appears

(Your browser may also warn you during the download. If so, choose "Save" → "Show more" → "Keep".)

### 3. Install

Follow the installer. When it finishes, `rapore` is added to your Start menu.

---

## Using it from your AI (optional, off by default)

You can have a generative AI you pay for yourself (Claude Desktop, Claude Code, Cursor, Codex CLI, and so on) create and read your 1-on-1 records. **This is off by default, and the route does not exist until you turn it on.**

> ⚠️ **Know this first.** rapore itself sends nothing, but **whatever records you let the AI read go to that AI's provider (Anthropic, OpenAI, and so on).** How they handle it falls under their privacy policy and is outside rapore's control. See ["4. Letting your own AI work with rapore"](./PRIVACY.en.md) for the details.

### Which AI works

You need a client that **runs on your own machine**.

| Works | Does not work |
|---|---|
| Claude Desktop / Claude Code / Cursor / Codex CLI, and similar | ChatGPT connectors, Codex cloud tasks, and anything else **running in the cloud** |

Cloud-run AI cannot reach a route that exists only inside your machine — which is the flip side of not putting your data anywhere else.

### Steps

1. Open **Settings → AI access** in rapore.
2. Turn on "Enable AI access". A confirmation screen appears; read it and choose "Enable".
3. If you also want the AI to read the **body** of your records, turn on "Also allow reading" as well (**a separate consent**. Left off, the AI can only create and edit records and read member names, roles and teams).
4. Pick your client under "Client" and rapore shows you **which file to paste into** and **what to paste**. Paste it into that configuration file as-is.
5. Restart your AI client.

> The paths and the shared secret are shown already filled in for your machine. **Do not retype them by hand** — the quoting rules differ per format, so a transcription slip means it will not connect.

### If it does not work

- Your AI says rapore is not running or AI access is off → start rapore and check the setting. Once rapore is running you do not need to restart your AI client.
- Settings says "Not listening" → restart rapore.
- You moved rapore somewhere else → what you paste changes. Copy it again from Settings.

---

## Uninstalling, and where your data lives

Removing the app leaves your data in place. To delete the data as well, remove the folder below.

| OS | Location |
|---|---|
| macOS | `~/Library/Application Support/rapore/` |
| Windows | `%APPDATA%\rapore\` |

`rapore.db` inside it is the database. The exact path is also shown in the app's Settings screen.

> ⚠️ **Do not back up by copying that file by hand.**
> rapore runs SQLite in WAL mode, so **your most recent sessions may still be sitting in a separate `rapore.db-wal` file**. Copying only `rapore.db` will silently lose them, and copying while the app is running can produce a corrupt file.
>
> **Do this instead**: use **Settings → Backup → "Create a backup (.db)"** in the app. It writes a single, consistent file, and it's safe to do while you're using the app.
>
> If you really must copy by hand, **quit the app completely first and copy the whole `rapore` folder** (`rapore.db-wal` and `rapore.db-shm` may still be there).

- macOS: delete `rapore` from your `Applications` folder
- Windows: Settings → Apps → Installed apps → uninstall `rapore`

---

## Updating

There are three ways to find out that a new version is out. Pick whichever suits you.

### 1. Let the app tell you (off by default)

**Only if you turn it on**, rapore asks GitHub for the latest version number at startup and tells you inside the app when a newer one is out. It asks you once, on first launch, whether you want this. You can change your mind any time under **Settings → General → "Tell me about new versions"**.

**It is off by default — the app makes no connection at all.** Even when it is on, the only thing requested is the latest version number: **none of your notes, your reports' details, or your usage is ever sent** (see the [Privacy Policy](./PRIVACY.en.md)).

### 2. Get notified by GitHub (needs a GitHub account)

On the [releases repository](../../), use **Watch → Custom → Releases** at the top right. GitHub then emails you when a new version ships.

### 3. Subscribe to the feed (no account needed)

Add this URL to any RSS / Atom reader:

```
https://github.com/kiricab/rapore-releases/releases.atom
```

### How to update

Download the newer version from [Releases](../../releases/latest) and install it over the top, the same way you installed it the first time. **Your data is kept** — it lives separately from the app itself. The app never downloads an update or replaces itself.
