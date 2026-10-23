# Dovra 1.2.0 release notes

Windows x64; Chromium 155.0.8059.85. This batch uses the source34 application pair identified in [manifest.md](manifest.md).

## Changes

- Native Agent/Human control bar with Take Control and Resume Agent; takeover revokes previous automation authorization.
- Native control-state interfaces and authenticated automation integration.
- Native save-dialog and JavaScript-dialog support for authorized automation.
- Google Search defaults for fresh profiles, while preserving existing choices.
- Versioned source patches and branding overlay for repeatable Chromium upgrades.

## Validation scope

The current browser pair completed its incremental build and 53 selected configuration, profile, storage, controller and proxy regression cases. The native-control matrix has 34 of 38 cases adopted from direct, reviewed carry-forward and composed evidence; it is not 38 fresh runs on this pair. Core takeover, Human input, fresh authorization, stale-authorization rejection, disconnect handling and normal close have reviewed evidence. Three virtual displays were checked at actual 100%, 150% and 200% Windows DPI settings. Earlier bounded Save As and SDK checks are not a guarantee for every Windows dialog or website.

Validation remains incomplete for native context-menu paste, OS drag-and-drop, renderer-crash recovery, and manual input recovery after a safety-bar layout failure. This release does not claim complete coverage of all native-control scenarios.

These incomplete validations are not classified as confirmed Chromium defects. No claim is made of comprehensive hardware, accessibility, input-method or failure-recovery coverage. Do not treat Agent mode as an operating-system security boundary.

## Maintenance and compatibility

Google Safe Browsing and automatic component updates, including security-data updates, are disabled by default. Do not assume bundled security data stays current. Manual component-update and final network acceptance remain incomplete. Automatic GAIA browser-account reconciliation and GCM background services are disabled by default. OAuth, Web Push and compatibility with every website are not guaranteed. Websites, certificate retrieval, user-initiated updates and connected tools can still make network requests. These defaults are not a zero-network or anonymity guarantee.

Use separate profiles and retain backups before migration. New profiles default to Google; manual choices persist. Searches are processed by the selected provider under its terms and privacy policy.

Read [SOURCE-MATERIALS.md](SOURCE-MATERIALS.md) for matching materials and reconstruction limits. The [Terms](https://dovra.dev/terms/) and [Privacy notice](https://dovra.dev/privacy/) were adopted on 17 October 2026. Optional companion-tool licences do not relicense the browser.

DOVRA SOFTWARE LTD, company number 17493263. Contact: <dovra.dev@gmail.com>. Built on Chromium; not affiliated with or endorsed by Google.
