# Release notes

[日本語](./CHANGELOG.md) | **English**

Only changes that are visible to you are listed here.

## v0.2.0

**Fixed: sessions could not be deleted.** Opening a session and choosing "Delete" then confirming did nothing (this affected v0.1.0 and v0.1.1).

**Fixed: the Enter key that confirms Japanese IME conversion was treated as "save" or "add".** Typing a name in Japanese no longer adds the member the moment you confirm the conversion. This affected adding members, editing name and team, and entering tags.

**Topics and tags now use a chip input.** Type and press Enter to turn the text into a chip, and remove it with ×. **Pasting a comma- or newline-separated list adds every item at once**, which helps when copying from another note. Topics can be reordered by dragging.

**Search now has tag and period filters.** You can narrow sessions down by tag or date range without typing a keyword.

**The session list is easier to scan.** The topics you covered now stand out as the heading of each entry.

Known limitations (unchanged since v0.1.1)

- The app is not code-signed, so your OS shows a warning the first time you open it. See [INSTALL.en.md](./INSTALL.en.md).
- macOS builds are for Apple Silicon (M1 or later) only.

## v0.1.1

**Fixes the macOS build refusing to launch with "rapore is damaged and can't be opened."**

The macOS build of v0.1.0 shipped with a code signature that did not match the contents of the app bundle. macOS therefore treated the downloaded app as damaged and offered no option other than moving it to the Trash. **The app itself was never damaged.**

**If you have v0.1.0, please replace it with this build.** Your data lives separately from the app, so nothing is lost when you replace it.

The app is still not code-signed, so you will still see an OS warning on first launch. See [INSTALL.en.md](./INSTALL.en.md) for how to open it — **a reliable Terminal command has been added to those instructions.**

The Windows build is unchanged from v0.1.0.

## v0.1.0

First release.

- Add, edit, archive, and permanently delete the people you have 1-on-1s with
- Record 1-on-1 sessions (date, notes, topics, tags). Notes are edited in a Markdown WYSIWYG editor and saved automatically as you type
- Per-person timeline for browsing past sessions in order
- Keyword search across notes, topics, and tags for everyone at once
- Member dashboard showing four profile fields next to the session history
- Automatic backup to a folder you choose
- English and Japanese (follows your OS locale by default)
- Everything stored in SQLite on your machine. Nothing is transmitted

**Known limitations**

- **macOS support is Apple Silicon only.** There is no build for Intel Macs ([INSTALL.en.md](./INSTALL.en.md))
- The app is not code-signed, so your OS will warn you the first time you open it ([INSTALL.en.md](./INSTALL.en.md))
- There is no automatic update. New versions must be downloaded manually
- The database file itself is not encrypted. Turning on FileVault (macOS) or BitLocker (Windows) is recommended
