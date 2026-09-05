# Installing rapore

[日本語](./INSTALL.md) | **English**

> **Please read this first.** rapore is **not code-signed** yet, so macOS and Windows will tell you the developer cannot be verified the first time you open it. This is not a sign that something is wrong with rapore — it's because a solo developer has not yet paid for a signing certificate (Apple: $99/year; Windows: a few hundred dollars a year). The steps below get you through it. We'll revisit signing based on how the app is used.

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

### 3. First launch (this is where the warning appears)

Double-clicking `rapore` will show:

> "rapore" can't be opened because Apple cannot check it for malicious software.

Use whichever applies to your macOS version.

**macOS 15 (Sequoia) and later**

1. Dismiss the dialog with "Done" or "OK"
2. Open **System Settings → Privacy & Security**
3. Scroll down to the message about "rapore" being blocked and click **"Open Anyway"**
4. Confirm with your administrator password or Touch ID

**macOS 14 (Sonoma) and earlier**

1. **Right-click (or control-click) `rapore`** in your `Applications` folder and choose **Open**
2. Click **Open** in the dialog that appears

After the first time, it opens normally with a double-click.

### If that doesn't work

Remove the quarantine attribute from Terminal, then launch it again.

```sh
xattr -dr com.apple.quarantine /Applications/rapore.app
```

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

There is no automatic update yet. Download the newer version from [Releases](../../releases/latest) and install it over the top the same way. **Your data is kept** — it lives separately from the app itself.
