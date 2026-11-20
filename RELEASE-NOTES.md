# Dovra 1.3.1 release notes

Windows x64; Chromium 158.0.8127.37. This is the 1.3.1 release. The browser reports product version 1.3.1 on the 158 engine.

## Release history in this document

1.2.0 was published on 22 October 2026 and withdrawn on 25 October 2026. It is no longer distributed, and its download addresses no longer resolve. The notes below therefore describe the whole sequence — 1.1.0, the release that was publicly downloadable before 1.2.0, then 1.2.0, then 1.3.0, then 1.3.1 — so that the history is complete without pointing at withdrawn files.

## Changes from 1.1.0 to 1.2.0

- Native Agent/Human control bar with Take Control and Resume Agent; takeover revokes previous automation authorization.
- Native control-state interfaces and authenticated automation integration.
- Native save-dialog and JavaScript-dialog support for authorized automation.
- Google Search defaults for fresh profiles, while preserving existing choices.
- Versioned source patches and branding overlay for repeatable Chromium upgrades.

## Changes from 1.2.0 to 1.3.0

- The product display version moved from 1.2.0 to 1.3.0 for this engine upgrade. The dovra CLI protocol stays `dovra.cli` 1.0; there are no breaking changes.
- The Chromium engine moved from 155.0.8059.85 to 158.0.8127.18. The Dovra patch set was ported to the new engine and the build configuration is unchanged apart from the engine version.
- The launcher defaults now take effect when the caller passes a `--` argument: Chromium ends switch parsing at that sentinel, so the launcher inserts its defaults before it. The launcher's other behaviour and its defaults are unchanged; the default user-data directory and interface language are the same as in 1.2.0.
- The default settings and the legal documents are unchanged from 1.2.0.
- The 1.2.0 package carries two Privacy Sandbox attestations preload files that the 158 engine no longer produces for Windows: upstream 158 stopped adding them to the product directory and ships no desktop reader for them. This package therefore carries two runtime files fewer than the 1.2.0 package.

## Changes from 1.3.0 to 1.3.1

- The product display version moved from 1.3.0 to 1.3.1. The dovra CLI protocol stays `dovra.cli` 1.0; there are no breaking changes.
- The Chromium engine moved from 158.0.8127.18 to 158.0.8127.37, a security update of the same 158 engine. The Dovra patch set was re-parented to the new engine source and the build configuration is unchanged apart from the engine and product versions.
- The default settings and the legal documents are unchanged from 1.3.0.

## Validation scope

**Run on the 1.3.1 binaries.** The 1.3.1 build was compared with the published 1.3.0 package with identical parameters on both sides; the comparison found no behavioural difference beyond the version fields and the known upstream changes of the engine patch update. On the 1.3.1 binaries the following were exercised: launch and identity in headless mode (headed launch carries from the 158 engine of the published 1.3.0 by review), the UA-CH version fields, the release gate for credits, legal files and telemetry, a 60-second network log, a direct network probe, the default search provider, the five basic Playwright operations, three File System Access frames, and the optional Toolkit command set.

**Carried from the previous engine.** The native-control matrix was not re-run on the 158 engine. It stands at 34 of 38 cases, adopted from direct, reviewed carry-forward and composed evidence on the 155 build of 1.2.0 — it is not 38 fresh runs on this pair. Core takeover, Human input, fresh authorization, stale-authorization rejection, disconnect handling and normal close have reviewed evidence from that build. Three virtual displays were checked at actual 100%, 150% and 200% Windows DPI settings on that build. The 53 selected configuration, profile, storage, controller and proxy regression cases were completed on that build as well. The four deferred scenarios are the same ones deferred at 1.2.0, with the same reasons: native context-menu paste, OS drag-and-drop, renderer-crash recovery, and manual input recovery after a safety-bar layout failure.

Validation remains incomplete for native context-menu paste, OS drag-and-drop, renderer-crash recovery, and manual input recovery after a safety-bar layout failure. This release does not claim complete coverage of all native-control scenarios.

These incomplete validations are not classified as confirmed Chromium defects. No claim is made of comprehensive hardware, accessibility, input-method or failure-recovery coverage. Do not treat Agent mode as an operating-system security boundary.

## Maintenance and compatibility

Google Safe Browsing and automatic component updates, including security-data updates, are disabled by default. Do not assume bundled security data stays current. Manual component-update and final network acceptance remain incomplete. Automatic GAIA browser-account reconciliation and GCM background services are disabled by default. OAuth, Web Push and compatibility with every website are not guaranteed. Websites, certificate retrieval, user-initiated updates and connected tools can still make network requests. These defaults are not a zero-network or anonymity guarantee.

Use separate profiles and retain backups before migration. New profiles default to Google; manual choices persist. Searches are processed by the selected provider under its terms and privacy policy.

Read [SOURCE-MATERIALS.md](SOURCE-MATERIALS.md) for matching materials and reconstruction limits. The [Terms](https://dovra.dev/terms/) and [Privacy notice](https://dovra.dev/privacy/) were adopted on 17 October 2026. Optional companion-tool licences do not relicense the browser.

DOVRA SOFTWARE LTD, company number 17493263. Contact: <dovra.dev@gmail.com>. Built on Chromium; not affiliated with or endorsed by Google.
