# Threshold

A Chrome extension that puts a pause between the impulse and the page.

You write the terms while you're calm — why you're installing it, and one
question you want your calm self to ask you later. When you hit something
blocked, you meet your own words, a short wait, and then a choice. The choice
is always yours. The point is only that you make it having actually thought.

**Everything stays on your computer.** No account, no server, no history kept.
See [PRIVACY.md](PRIVACY.md).

> **Running any script in this project?** Use `bash script.sh`, never
> `./script.sh`. Archives don't preserve the Unix executable bit, so `./` will
> fail with *Permission denied* — and `sudo ./script.sh` then reports the
> misleading *command not found*.

## Install

**Full step-by-step for both browsers: [INSTALL.md](INSTALL.md)**

Quick version for Chromium browsers (Chrome, Edge, Brave, Opera, Vivaldi):

1. Open `chrome://extensions`
2. Turn on **Developer mode** (top right)
3. Click **Load unpacked** and choose this folder
4. Setup opens automatically

Firefox needs a separate build first — see [INSTALL.md](INSTALL.md#firefox).

Then check it's working: click the Threshold icon → **Check it's working**.

## What it does

**Enforced SafeSearch.** Google, Bing, DuckDuckGo, Brave, Ecosia, Startpage
and Yandex are forced into their safe modes at the URL level. This
holds regardless of what your account setting says, and needs no access to any
account. It's the single highest-value thing in here.

**Domain blocking.** Seeded immediately on install, then updated daily from the
Blocklist Project's public adult list (~500k domains). Matches subdomains.

**Your own words and sites.** Terms you add are blocked in addresses and search
queries everywhere, not just on blocked sites. Threshold has no opinion about
where your line goes — it ships empty and you fill it in.

**Settings-page protection.** Reddit, X and Tumblr keep adult content behind an
account switch. Onboarding asks you to turn those off by hand, then blocks the
specific settings paths so switching them back on goes through the gate.
Narrow paths only — you can still change your password without an interrogation.

**The gate.** Your reason → four dull yes/no questions → your own question →
a countdown (5 min minimum, configurable up) → access for a fixed window
(5 min default, 15 max), then it re-locks on its own.

## Design decisions worth keeping

**Adding a restriction is instant. Removing one goes through the gate.** This
asymmetry is the whole product. If editing were symmetrical, nobody would need
to bypass anything — they'd just delete three entries.

**Backing out is free.** Cancel the countdown at any point, no penalty, nothing
recorded. Punishing the request teaches people not to use the gate honestly.

**The timer never escalates.** A wait that grows because you asked twice reads
as the software disciplining you, and once it feels like punishment the frame
is broken.

**Timers are absolute timestamps, never countdowns.** Disabling and re-enabling
the extension can't reset a running clock.

**The blocklist is never displayed.** A searchable directory of every blocked
site would be exactly the wrong thing to hand someone avoiding them. Settings
show a count.

**Nothing shames anyone.** The four questions are deliberately mundane. Shame
stops working the moment it's familiar, and makes the spiral worse meanwhile.

**Serif for your words, sans for ours.** When you're standing at the gate, the
difference between your own voice and the software's should be visible before
it's read.

## If a script won't run

```
bash: ./install-threshold.sh: Permission denied
sudo: ./install-threshold.sh: command not found
```

Unzipping strips the executable bit from shell scripts. Run them through
`bash` instead — no `chmod` needed:

```bash
sudo bash install-threshold.sh
bash build.sh
```

### A note on YouTube

YouTube filtering is **off by default**, and the installer asks before turning
it on. YouTube's Restricted Mode disables comments entirely — that's YouTube's
behaviour and there's no way to keep filtering while allowing them.

YouTube isn't a porn site, so for the adult version the trade-off usually isn't
worth it: you'd break a normal part of the web to cover suggestive content
rather than explicit. For a parental build the calculation flips, and it should
default on.

## Honest limitations

- **On its own, the extension can be removed in two clicks.** No extension can
  prevent that; browsers deliberately give the user final say. The policy
  scripts in `linux/` and `windows/` close it properly using `force_installed`,
  which removes every route to removal — the extensions page and the toolbar
  icon's menu — while leaving your other extensions alone. That needs a Chrome
  Web Store extension ID, so it only works with the published version.
- **Anyone with administrator access can undo the policy.** No software on a
  machine you control can prevent that.
- **Currently Chrome only, desktop only.** Firefox Coming Soon.
- **Other browsers are unaffected.** Installing it in one browser leaves the
  others open.
- **Mixed-content platforms are out of scope.** Reddit, X, Telegram and Discord
  serve everything from one domain. Blocking the settings path is the
  achievable part; filtering inside them is not.
- **Discord's settings are an in-app overlay** with no distinct URL, so there's
  nothing for a URL-based blocker to match.
- **No blocklist is complete.** New domains appear daily.


## Turning incognito back on / removing the protection

**Before you read the instructions, read what you wrote.**

When you set Threshold up, you were asked two things while you were calm.
Your answers are in the tool, on the settings page, under **Your words**. Go
and read them now, before you go any further down this page.

You were also asked to write one question — your own, in your own words — to
be asked at exactly this moment. Read that too.

Then, honestly:

- Has this tool been doing what you wanted it to do?
- Is this a decision you would also make tomorrow morning, or only right now?
- Is there something else you could do for the next ten minutes?

If the answer is still that you want it undone, that's your call to make and
the instructions are below. Nothing here is trying to trap you — there is
always a way out, and it's documented.

> **Tip:** at the end of setup, Threshold offers to save a file called
> `threshold-how-to-undo.txt`. That file has *your own* answers written into
> it, followed by these instructions. If you saved it, read that instead of
> this — it's the same steps, in your own words.

### The proper way — through the cooling-off period

1. Open Threshold's settings in your browser
2. Click **Start removal**
3. Wait 30 minutes. Cancel any time, free, no penalty.
4. Click **Show removal code**
5. Run the removal script and enter the code:
   - **Linux:** `cd linux && sudo bash remove-threshold.sh`
   - **Windows:** right-click `windows\remove-threshold.bat` → Run as administrator
6. Quit the browser completely and reopen it

> **Locked out of your extensions page?** You picked option 2 at install. Run
> the removal script, or delete the policy file directly (below), then re-run
> the installer and pick option 1 or 3.

### The direct way — if you're locked out or something's broken

**Linux:**
```bash
sudo rm -f /etc/opt/chrome/policies/managed/threshold.json
sudo rm -f /etc/chromium/policies/managed/threshold.json
```

**Windows:** open `regedit` as Administrator and delete
`HKLM\SOFTWARE\Policies\Google\Chrome` and
`HKLM\SOFTWARE\Policies\Microsoft\Edge`.

Then restart the browser. No code, no waiting. This exists so that nobody can
ever be genuinely trapped by this tool.

### Removing the extension itself

Do the above **first**. While the policy is active the extensions page is
blocked, so you can't remove anything from it.

Then: browser menu → Extensions → Threshold → Remove.

**Removing the extension does not remove the policy.** They're separate things.
Delete the extension without running the removal script and incognito stays
disabled and the extensions page stays blocked.

## Next, if it survives contact with real use

1. Firefox port (mostly a manifest change)
2. Optional local DNS-level enforcement for coverage outside the browser
3. Import/export of settings, so a reinstall doesn't start from nothing

## Licence

Your call. The Blocklist Project list has its own licence — check it before
distributing commercially.
