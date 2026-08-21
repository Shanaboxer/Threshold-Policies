# Installing CoolHeaded

Two parts, and the first one is enough to start:

1. **The extension** — blocks sites, runs the gate. Installed per browser.
2. **The protection layer** *(optional, later)* — stops the extension being
   removed in two clicks, forces SafeSearch, disables private browsing.
   Installed once per computer. See `linux/` or `windows/`.

Do part 1 first and use it for a while. Part 2 makes it hard to undo, which is
the last thing you want while you're still finding out whether you like it.

---

## Chrome, Edge, Brave, Opera, Vivaldi

All Chromium browsers, all the same steps.

1. Unzip CoolHeaded somewhere permanent — **Documents, not Downloads.** The
   browser reads this folder every time it starts. Move or delete it and the
   extension breaks.
2. Open a new tab and go to `chrome://extensions`
   *(Edge: `edge://extensions` · Brave: `brave://extensions`)*
3. Turn on **Developer mode** — the toggle in the top right
4. Click **Load unpacked** — top left
5. Select the **`coolheaded` folder itself** — the one containing
   `manifest.json`. Don't go into it and don't pick the file.
6. Setup opens in a new tab automatically. Work through it and click
   **Finish setup**.

### Did it work?

Click the CoolHeaded icon in the toolbar, then **Check it's working**. You want:

```
Sites blocked: 35 (or several hundred thousand once the list downloads)
Setup finished: yes
Test match (pornhub.com): blocked
```

Then try visiting a porn site. You should land on the block page with your own
words on it.

### Common problems

**Nothing happens when you visit a blocked site.** Check the popup says *Setup
finished: yes*. If it says NO, the setup tab was closed before finishing —
reopen it from the extensions page under **Details → Extension options**.

**"Manifest file is missing or unreadable".** You selected the wrong folder.
It must be the one directly containing `manifest.json`.

**A warning bar about developer mode extensions.** Normal for anything not
installed from a store. Nothing is wrong.

---

## Firefox

Firefox needs a different build, because it uses an event-page background
script instead of a service worker.

### 1. Build it

```bash
cd coolheaded/firefox
bash build.sh
```

Use `bash build.sh`, **not** `./build.sh` — archives don't preserve the Unix
executable bit, so `./` fails with *Permission denied*, and `sudo ./build.sh`
then reports the misleading *command not found*.

This creates `coolheaded/firefox/build/`.

### 2. Load it

1. Go to `about:debugging#/runtime/this-firefox`
2. Click **Load Temporary Add-on…**
3. Select **`coolheaded/firefox/build/manifest.json`**

> **It must be the one inside `build/`.** The `firefox/` folder itself has no
> extension code in it — only the build script and a manifest template. Picking
> that one loads a manifest with nothing behind it, and the console shows:
>
> ```
> Loading failed for the <script> with source ".../background.js"
> ```
>
> If you see that, you selected the wrong manifest. `bash build.sh` prints the
> full correct path at the end — copy it from there.

Setup opens automatically, same as Chrome.

### The Firefox catch

**Temporary add-ons are deleted every time Firefox restarts.** Fine for
checking it runs; useless as an actual blocker, since a restart removes it.

To make it permanent, one of:

**Publish to addons.mozilla.org** — free, no developer fee, and Mozilla signs
it. Then it installs like any normal add-on and stays. This is the real answer,
and it's less hassle than Chrome's process.

**Firefox Developer Edition or Nightly** — set
`xpinstall.signatures.required` to `false` in `about:config`, then install the
built extension permanently. Regular Firefox ignores this setting, so it must
be one of those builds. Do this **before** running the protection scripts,
which block `about:config`.

---

## Which browsers do I need it in?

Every browser you actually use. Extensions live inside a browser, not on the
computer, so Chrome and Firefox each need their own copy and their own setup.

**Any browser you skip is an open door.** If CoolHeaded is in Chrome but you
also have Firefox installed, Firefox bypasses it completely in one click. The
protection scripts in `linux/` and `windows/` help — they apply SafeSearch and
disable private browsing across every browser they find, extension or not — but
site blocking still needs the extension in each one.

The simplest fix is usually to uninstall the browsers you don't use.

---

## Updating

Chromium browsers: `chrome://extensions` → the reload icon on the CoolHeaded
card. If files were added or removed, remove it and Load unpacked again.

Firefox: rebuild with `bash build.sh` and load the temporary add-on again.

Your settings and your written answers survive a reload. They're wiped if you
remove the extension entirely.

**If you've installed the protection layer**, the extensions page may be
blocked, so you can't reload anything. Run the removal script first, or pick
option 3 (development mode) when installing it in the first place.
