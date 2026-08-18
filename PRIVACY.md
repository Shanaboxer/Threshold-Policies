# Privacy

Short version: **nothing about you leaves your computer.**

There is no account, no sign-in, and no server belonging to Threshold. We have
not built one, so there is nowhere for your information to be sent even if we
wanted it.

## What is stored, and where

Everything Threshold knows about you lives in your own browser's local storage,
on your own machine:

- what you wrote about why you installed it
- the question you asked to be asked
- the words and sites you added to your own list
- your wait and window settings
- whether the gate is currently open, and when it closes

You can inspect all of it yourself. Nothing is obfuscated.

## What is not stored at all

Threshold does **not** keep a record of:

- which sites you visited or tried to visit
- what you searched for
- when you asked for access, how often, or whether you went through with it
- anything at all about your browsing history

This isn't a promise to handle such a log carefully. There is no log. The
feature was never built, because a file listing one person's porn use is a
thing that ruins lives when it leaks, and the safest way to protect it is to
never create it.

## The one request that leaves your machine

Once a day, Threshold downloads a public blocklist file from GitHub — the
Blocklist Project's adult domain list. That request:

- is identical for every user of the extension
- contains nothing about you, your settings, or your browsing
- can be switched off in settings, in which case the list simply stops updating

That is the only outbound connection the extension makes. There is no
analytics, no crash reporting, no telemetry, and no third-party script of any
kind. The interface uses your system's own fonts rather than loading any, so
that even rendering a page contacts nobody.

## Third parties

None. Your information is not sold, shared, licensed, or disclosed to anyone,
because it is not collected in the first place.

## If Threshold is ever paid for

Any future payment would be handled by a payment processor, who would know that
you bought a piece of software. They would not know what it does for you, and
Threshold would still hold no account linked to your use of it.

## Removing it

Uninstalling Threshold deletes its local storage along with everything above.
Nothing survives elsewhere, because nothing was ever elsewhere.
