# CoolHeaded

A browser extension that puts a pause between the impulse and the page.

You write the terms while you're calm — why you're installing it, and one
question you want your calm self to ask you later. When you hit something
blocked, you meet your own words, a short wait, and then a choice. The choice
is always yours. The point is only that you make it having actually thought.

**Everything stays on your computer.** No account, no server, no monitoring, no
history kept.

---

## This repository

Public documents for CoolHeaded. The extension's own code is not here.

- **[PRIVACY.md](PRIVACY.md)** — the privacy policy
- **[INSTALL.md](INSTALL.md)** — how to install and set it up
- **[LICENSE.txt](LICENSE.txt)**

The optional browser lock scripts live in a separate repository, linked from
the store listings.

---

## Get it

- **Chrome, Edge, Brave, Opera, Vivaldi** — Chrome Web Store
- **Firefox** — Firefox Add-ons

Install it in **every browser you use**. An extension only works inside the
browser it's installed in — so if you have Chrome and Firefox on the same
computer, installing it in one does nothing for the other.

---

## What it does

**Enforced SafeSearch.** Google, Bing, DuckDuckGo, Brave Search, Ecosia,
Startpage and Yandex are forced into their safe modes at the address level.
This holds regardless of what your account settings say and needs no access to
any account. In practice it does more work than anything else here, because
most of what people run into arrives through a search box.

**Domain blocking.** Seeded on install, then refreshed daily from the Blocklist
Project's public adult list. Matches subdomains.

**Your own words and sites.** Words you add are blocked in addresses and search
queries everywhere. CoolHeaded has no opinion about where your line goes — it
ships empty and you fill it in.

**Settings-page protection.** Reddit, X and Tumblr keep adult content behind a
switch in your own account. Setup asks you to turn those off by hand, then
blocks the specific settings pages so they can't be switched back on. Narrow
paths only — you can still change your password without an interrogation.

**The gate.** Your written reason → four dull yes/no questions → the question
you wrote for yourself → a countdown (5 minutes minimum, longer if you choose)
→ access for a fixed window (5 minutes by default, 15 maximum), then it
re-locks by itself.

Cancelling costs nothing, at any point, and nothing is recorded.

---

## What it deliberately doesn't do

**No accountability partner.** Nobody is watching, nobody gets a report, no
screenshots are taken.

**No streaks or relapse counters.** Nothing resets to zero and tells you that
you failed. This is a tool for limiting something, not a programme for quitting
it.

**No logging.** No history of blocks or unlocks is kept — not on a server, and
not on your own computer. That feature was never built, because a record of one
person's browsing is the worst possible thing to be holding.

**No shaming.** The four questions at the gate are deliberately mundane. Shame
stops working the moment it's familiar, and makes things worse in the meantime.

---

## Design decisions worth keeping

**Adding a restriction is instant. Removing one goes through the gate.** That
asymmetry is the whole product. If editing were symmetrical, nobody would need
to bypass anything.

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

---

## Honest limitations

- **It must be installed in each browser separately.** A browser you skip is a
  way straight round it.
- **On its own, it can be removed from the extensions page in two clicks.** No
  extension can prevent that — browsers deliberately give the user the final
  say. The optional lock scripts close it properly.
- **Private browsing bypasses it** unless you run those scripts.
- **Anyone with administrator access can undo the lock scripts.** No software
  running on a computer you control can prevent that.
- **The lock scripts are Windows and Linux only.** The extension itself works
  anywhere the browser does. macOS is not supported.
- **Mixed-content platforms are out of scope.** Reddit, X, Telegram and Discord
  serve everything from one domain. Blocking the settings page is the
  achievable part; filtering inside them is not.
- **No blocklist is complete.** New domains appear daily.

---

## A note on YouTube

YouTube filtering is available in the optional lock scripts and is **off by
default**. YouTube's Restricted Mode disables comments entirely — that's
YouTube's behaviour, and there's no way to keep the filtering without losing
them.

YouTube isn't a porn site, so the trade-off usually isn't worth it.

---

## Removing it

There is always a way out, and it's documented.

**If you only installed the extension:** browser menu → Extensions →
CoolHeaded → Remove.

**If you also ran the lock scripts**, take the lock off first — while it's
active, the extensions page is blocked.

1. Open CoolHeaded's settings and click **Start removal**
2. Wait out the 30-minute cooling-off. Cancel at any point, free.
3. Click **Show removal code**
4. Run the removal script and enter it:
   - **Linux:** `cd linux && sudo bash remove-coolheaded.sh`
   - **Windows:** right-click `windows\remove-coolheaded.bat` → Run as administrator
5. Quit the browser completely and reopen

**If you're locked out or something has gone wrong**, this needs no code and no
waiting:

**Linux**
```bash
sudo rm -f /etc/opt/chrome/policies/managed/coolheaded.json
sudo rm -f /etc/chromium/policies/managed/coolheaded.json
sudo rm -f /etc/firefox/policies/policies.json
```

**Windows** — open `regedit` as Administrator and delete:
```
HKLM\SOFTWARE\Policies\Google\Chrome
HKLM\SOFTWARE\Policies\Microsoft\Edge
HKLM\SOFTWARE\Policies\Mozilla\Firefox
```

Then restart the browser.

**Removing the extension does not remove the lock scripts.** They're separate
things. Delete the extension without running the removal script and private
browsing stays disabled.

---

## Before you undo it

If you're here to turn it off, read what you wrote first. It's on the settings
page under **Your words**, along with the question you asked to be asked.

Then, honestly: has this been doing what you wanted? Is this a decision you'd
also make tomorrow morning, or only right now?

If the answer is still yes, that's your call to make, and the instructions are
above. Nothing here is trying to trap you.

---

## Contact

gudwindavids@gmail.com
