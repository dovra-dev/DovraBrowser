# Dovra 1.3.1 quick start

Windows x64; Chromium 158.0.8127.37.

1. Download [Dovra-1.3.1-win-x64-portable.zip](https://dl.dovra.dev/1.3.1/Dovra-1.3.1-win-x64-portable.zip) from the [official release](https://github.com/dovra-dev/DovraBrowser/releases/tag/v1.3.1) and compare its full SHA-256 with [SHA256SUMS.txt](https://dl.dovra.dev/1.3.1/SHA256SUMS.txt). The browser ZIP SHA-256 is `aab65b58c3ef12464dff1b7ab30452a8aedff8a8323b1572bc6f51fc72c7fa7b`.
2. Extract into a new directory and keep the files together. Read the [README](README.md), [release notes](RELEASE-NOTES.md) and extracted ZIP's `legal/` notices. The [Terms](https://dovra.dev/terms/) and [Privacy notice](https://dovra.dev/privacy/) are also on the project website.
3. Run `dovra_browser.exe`. For an explicit separate evaluation profile, run the following in PowerShell from the extracted directory:

```powershell
$evaluationProfile = Join-Path $env:TEMP ('Dovra-evaluation-' + [guid]::NewGuid().ToString('N'))
& .\bin\chrome.exe "--user-data-dir=$evaluationProfile" --no-first-run --no-default-browser-check about:blank
```

A checksum establishes file identity, not trusted-publisher status. Do not disable Windows security controls. Close all processes using a profile before changing builds; never open a newer profile in an older engine for rollback.

## Human and agent control

Use Take Control to return input to the person and revoke the current agent authorization. Resume Agent makes agent control available again; the agent needs a fresh grant. Agents must observe control state instead of repeatedly retrying rejected actions. Dismissing the notification is separate from takeover. A matching runtime-aware adapter is required for optional native interfaces; this browser archive does not include the optional Toolkit.

Validation remains incomplete for native context-menu paste, OS drag-and-drop, renderer-crash recovery, and manual input recovery after a safety-bar layout failure. This release does not claim complete coverage of all native-control scenarios.

## Search and maintenance

New profiles use Google Search. Change the provider in Settings; a manual choice persists after restart. Existing user, extension and policy choices take precedence. Searches contact the chosen provider; see [Google's Privacy Policy](https://policies.google.com/privacy).

Google Safe Browsing and automatic component updates, including security-data updates, are disabled by default. Do not assume bundled security data stays current. Manual component-update and final network acceptance remain incomplete. Automatic GAIA browser-account reconciliation and GCM background services are disabled by default. OAuth, Web Push and compatibility with every website are not guaranteed. Websites, certificate retrieval, user-initiated updates and connected tools can still make network requests. These defaults are not a zero-network or anonymity guarantee.

Close windows normally and wait for their processes to exit before removing evaluation files. Removing program files does not remove profiles or downloads. Contact <dovra.dev@gmail.com> with a small redacted reproduction.
