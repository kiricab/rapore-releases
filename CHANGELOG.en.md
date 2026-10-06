# Release notes

[日本語](./CHANGELOG.md) | **English**

Only changes that are visible to you are listed here.

## v0.4.1

**The macOS version is now notarized by Apple.** The first time you open a downloaded copy of rapore, you no longer need the Terminal command (`xattr`) or a trip to System Settings. macOS just asks “"rapore" is an app downloaded from the Internet. Are you sure you want to open it?” — click **Open** and it starts.

There are no changes to the app's features. Everything you have recorded carries over untouched.

Known limitations

- **The Windows version is not code-signed yet**, so Windows shows a warning the first time you open it. See [INSTALL.en.md](./INSTALL.en.md).
- macOS support is Apple Silicon (M1 and later) only.
- **AI access has not yet been verified on a real Windows machine.** If it does not work for you, please let us know in [Issues](../../issues).

## v0.4.0

**The AI you already use can now work with your rapore records (AI access, off by default).** From an AI client that runs on your machine — Claude Desktop, Claude Code, Cursor, Codex CLI, and so on — you can save what was said in a 1-on-1 as a record, or have it read past sessions and suggest topics for the next one. No more copy-and-paste back and forth. Turn it on under **Settings → AI access**, then use the “Copy” button to paste the snippet shown into your AI client. Steps are in [INSTALL.en.md](./INSTALL.en.md).

- **It is off by default.** Until you turn it on, the route does not exist at all.
- Permission comes in two steps. Turning it on only lets the AI create and edit records and read member names, roles and teams. To let it read record **bodies**, turn on “Also allow reading” separately.
- **rapore itself sends nothing**, but **whatever records your AI reads go to that AI’s provider (Anthropic, OpenAI, and so on).** See section 4 of [PRIVACY.en.md](./PRIVACY.en.md).
- AI that runs in the cloud, such as ChatGPT connectors, cannot use it.

**The app can now tell you when a new version is out (off by default).** It asks you once, on first launch. When turned on, it checks only the latest version number, at most once a day — none of your records or your reports’ details are sent. You can switch it under **Settings → General** at any time.

**Search can now be narrowed to one person.** The filters (person, tag, date range) now sit in a column to the left of the results, so the results start near the top of the screen. Archived members can be picked too.

**rapore no longer runs twice at once.** Opening it again while it is already running brings the existing window to the front.

Everything you have recorded carries over untouched.

Known limitations

- The app is not code-signed, so your OS shows a warning the first time you open it. See [INSTALL.en.md](./INSTALL.en.md).
- macOS support is Apple Silicon (M1 and later) only.
- **AI access has not yet been verified on a real Windows machine.** If it does not work for you, please let us know in [Issues](../../issues).

## v0.3.2

**Editing a past session now changes only the part you clicked.** Clicking the date or a topic used to swap the whole card into an editor, turning the notes you were reading into an input box. Now the date, topics, tags and notes are each edited in place, with the cursor already in the field you pressed.

**Clicking a topic or tag no longer collapses the card.** Previously, pressing a topic on an open card folded it away and the notes you were reading disappeared. To collapse a card, use the chevron on the right or click the empty part of its heading.

**You can see and change “today’s read” from the heading of an open session.** The level now appears as a word — “Energized”, “A bit spent” — instead of only a colored band, and pressing it lets you pick a different one. Sessions without a read show “+ Read”.

**Deleting a session has moved to the “⋯” menu.** Open the session and use “⋯” at the top right (the confirmation step is unchanged).

Everything you have recorded carries over untouched.

Known limitations (unchanged from v0.2.0)

- The app is not code-signed, so your OS shows a warning the first time you open it. See [INSTALL.en.md](./INSTALL.en.md).
- macOS support is Apple Silicon (M1 and later) only.

## v0.3.1

**Fixed the “today’s read” picker wrapping onto a second line in English.** The last of the seven levels dropped to its own row, so the levels no longer read as one scale — and widening the window did not help. The level names are now shorter words (`Very spent` to `Very lively`). **Japanese is unchanged.**

Everything you have recorded carries over untouched.

Known limitations (unchanged from v0.2.0)

- The app is not code-signed, so your OS shows a warning the first time you open it. See [INSTALL.en.md](./INSTALL.en.md).
- macOS support is Apple Silicon (M1 and later) only.

## v0.3.0

**You can now record “today’s read” with each 1-on-1.** Pick one of seven levels (very drained → very energized) in the session editor. Press the same one again to clear it. **This is your own impression, not a performance rating.**

**Each person now has a mood trend chart.** It sits on their card, so you can see how the last session compares with earlier ones, or notice someone who has been low for a while. The chart is readable by shape and height as well as color, so it still works if colors are hard to tell apart.

**You can give each person a photo.** Faces in the list make people easier to find. Drop an image onto the avatar, or click it to pick a file. You can undo a change right after making it. **Images are stored in the database on your machine and never transmitted.**

**The app now keeps a copy of your data before an upgrade changes it.** When an update changes how records are stored, rapore saves a full copy of the database first (the three most recent copies are kept; older ones are removed automatically). If the copy cannot be written, the app stops instead of touching your data. This does not replace your own backups, but it does protect you from losing notes during an update.

**Fixes**

- A session you were still writing could appear twice in the timeline. Fixed.

Known limitations (unchanged from v0.2.0)

- The app is not code-signed, so your OS will warn you the first time you open it. See [INSTALL.en.md](./INSTALL.en.md).
- macOS is supported on Apple Silicon (M1 and later) only.

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
