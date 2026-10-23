# Dovra 1.2.0

A Chromium-based browser for authorized agent workflows and web testing. Windows x64; Chromium 155.0.8059.85.

Read [QUICKSTART.md](QUICKSTART.md) before first use, [RELEASE-NOTES.md](RELEASE-NOTES.md) for tested scope and limitations, and the [Terms](https://dovra.dev/terms/) and [Privacy notice](https://dovra.dev/privacy/). The extracted browser ZIP also includes these notices in `legal/`. Use only systems you are authorized to access.

## Control

The native Agent/Human bar lets you take control and resume agent work. Taking control revokes the previous automation authorization. An agent must observe the control state and obtain fresh authorization before continuing. Closing the notification and taking control are distinct actions.

Validation remains incomplete for native context-menu paste, OS drag-and-drop, renderer-crash recovery, and manual input recovery after a safety-bar layout failure. This release does not claim complete coverage of all native-control scenarios.

## Maintenance and privacy

Google Safe Browsing and automatic component updates, including security-data updates, are disabled by default. Do not assume bundled security data stays current. Manual component-update and final network acceptance remain incomplete. Automatic GAIA browser-account reconciliation and GCM background services are disabled by default. OAuth, Web Push and compatibility with every website are not guaranteed. Websites, certificate retrieval, user-initiated updates and connected tools can still make network requests. These defaults are not a zero-network or anonymity guarantee.

Use a separate profile when evaluating this version. Do not open an important existing profile with a newer engine without a backup. Separate profiles are not operating-system security boundaries. New profiles default to Google Search; user, extension and managed-policy choices take precedence. Google Search requests are governed by [Google's Privacy Policy](https://policies.google.com/privacy).

## Distribution

Download the [Windows x64 portable ZIP](https://dl.dovra.dev/1.2.0/Dovra-1.2.0-win-x64-portable.zip) and compare its SHA-256 with [SHA256SUMS.txt](https://dl.dovra.dev/1.2.0/SHA256SUMS.txt). Browser ZIP SHA-256: `c4bbf57d8bc88d66f783f762824cfe7de1363a20655d5109646143bd691d877b`. In the extracted browser ZIP, the browser is in `bin/` and `dovra_browser.exe` is the launcher. See [manifest.md](manifest.md) for core file identities and [SOURCE-MATERIALS.md](SOURCE-MATERIALS.md) for matching source and relinking materials. Optional Toolkit software is distributed separately. GitHub automatic repository archives are not browser packages or complete matching Chromium materials.

The [Terms](https://dovra.dev/terms/) and [Privacy notice](https://dovra.dev/privacy/) were adopted on 17 October 2026. Component licences retain their own scope. Report small, redacted reproductions with the exact version; never send credentials or complete profiles.

DOVRA SOFTWARE LTD, company number 17493263. Contact: <dovra.dev@gmail.com>. Built on Chromium; not affiliated with or endorsed by Google.
