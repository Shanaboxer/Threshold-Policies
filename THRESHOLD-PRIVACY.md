# Privacy Policy — Threshold

**Effective date:** 18 August 2026
**Contact:** leeangus77@gmail.com

## Summary

Threshold does not collect, transmit, store on our servers, sell, or share any
user data. There is no account, no server operated by us, and no analytics.
Everything the extension knows stays in your own browser on your own computer.

## What data Threshold handles, and where it goes

Threshold stores the following **locally**, using the browser's own extension
storage API (`chrome.storage.local`). None of it is transmitted anywhere.

| What | Why | Where it goes |
|---|---|---|
| Text you write during setup (your reason for installing it, and a question you write for yourself) | Shown back to you at the block screen | Your browser only |
| Your wait and access-window settings | To apply the delay you chose | Your browser only |
| Words and site addresses you add to your own block list | To block them | Your browser only |
| Whether access is currently open, and when it expires | To apply the time limit | Your browser only |
| A downloaded public blocklist of adult website domains | To decide what to block | Your browser only |

## What Threshold does not collect

Threshold does **not** record, store, or transmit:

- Your browsing history
- Which sites you visited or attempted to visit
- What you searched for
- When or how often you requested access, or whether you proceeded
- Any personally identifiable information
- Authentication or payment information
- Your location
- Any analytics, telemetry, crash reports, or usage statistics

No log of blocked or unblocked activity is created at any point. This is not a
promise to handle such a log carefully — the feature does not exist in the
code, which is publicly readable.

## Network requests

Threshold makes exactly one kind of outbound request: once every 24 hours it
downloads a public blocklist file from GitHub
(`raw.githubusercontent.com/blocklistproject/Lists`).

This request:

- Is identical for every user of the extension
- Contains no information about you, your settings, or your browsing
- Downloads a file; it uploads nothing

GitHub will see that a request was made from your IP address, in the same way
it would if you opened that file in your browser. Their handling of that is
governed by GitHub's own privacy policy.

There are no other network requests. No analytics service, no error reporting,
no third-party scripts, and no web fonts — the interface uses your system's own
fonts specifically so that displaying a page contacts nobody.

## Third parties

None. Your data is not sold, licensed, shared, or disclosed to anyone, because
it is not collected in the first place.

## Data retention and deletion

All data is held in your browser's local extension storage for as long as the
extension is installed.

To delete everything: remove Threshold from your browser
(`chrome://extensions` in Chrome, `about:addons` in Firefox). This deletes all
stored data immediately and permanently. There is nothing held anywhere else,
so there is nothing further to request, and no deletion request to send us.

You can also inspect or clear individual items from the extension's settings
page at any time.

## Permissions, and why each is needed

| Permission | Why |
|---|---|
| `storage`, `unlimitedStorage` | To save your settings and the downloaded blocklist locally. The blocklist can exceed the default storage quota. |
| `webNavigation` | To see the address of a page before it loads, so a blocked address can be intercepted. This is how the extension performs its only function. |
| `tabs` | To redirect a tab to the block screen when a blocked address is detected. |
| `alarms` | To schedule the daily blocklist update. |
| `host_permissions: <all_urls>` | A blocker must be able to check **every** address the user navigates to, because any address could be one that should be blocked. It is not possible to filter a list of sites without being able to see the address of the site being visited. Threshold reads only the address. It does not read page content, and it does not transmit addresses anywhere. |

## Children

Threshold is a self-binding tool intended for adults choosing to limit their
own access. It is not directed at children and collects no data from anyone.

## Changes to this policy

If this policy changes, the effective date above will be updated and the change
will be noted in the extension's public repository.

## Contact

leeangus77@gmail.com
