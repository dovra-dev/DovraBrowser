# Dovra — 1.1.0

Windows x64 portable build with an English interface. Product version `1.1.0`. The underlying Chromium technical version is `153.0.8010.48`.

## What changed in 1.1.0

- **Native control bar (T-074 P1).** The browser now shows a built-in control bar for agent mode status and human takeover. The bar is drawn by the browser UI layer and does not inject into page DOM.
- **Input authorization (T-074 P2–P4).** In agent mode, physical keyboard and mouse input is gated at the browser input layer. CDP-authorized input (Input.insertText, Input.dispatchMouseEvent, etc.) passes through normally. After human takeover, a generation gate rejects stale agent CDP input.
- **Extended input paths gated (T-074 P5–P9).** IME composition, OS drag-and-drop, clipboard paste, context menu commands, and accessibility actions are gated in agent mode. Four of these paths require manual verification (see test documentation).

## Data directory change

The default browser data directory is `%LOCALAPPDATA%\Dovra\BrowserData`. Pre-1.0 builds used `%LOCALAPPDATA%\Dovra\Beta\BrowserData`. The old directory is not automatically migrated. Copy or move its contents to the new path yourself if you wish to keep them.

## What changed since pre-1.0 builds

- **Product version.** This is Dovra 1.1.0, a formal product version. Pre-1.0 builds used date-based identifiers without assigning a formal product version.
- **Branding.** Company name is DOVRA SOFTWARE LTD throughout the package, including the launcher PE fields. The default data path no longer includes a `Beta` segment.
- **Engine.** Chromium `153.0.8010.48`. The fingerprint parameter patches, network hardening and toolkit integration are carried over from the prior build of the same engine.

## Downloads

All files: `https://dl.dovra.dev/1.1.0/`

- `Dovra-1.1.0-win-x64-portable.zip`: complete browser, launcher and offline notices.
- `SHA256SUMS.txt`: SHA-256 checksums for the release files.
- Component source, relinking and LGPL modification archives: listed in [SOURCE-MATERIALS.md](SOURCE-MATERIALS.md).

GitHub's automatic repository source ZIP/tarball contains repository files, not the compiled browser or the full Chromium source tree.

## Verified scope

Tested environment: Windows Server 2022 x64, OS build 20348.5139; NVIDIA GeForce GTX 650 / ANGLE Direct3D 11.

### Native control bar and agent input authorization

Automated acceptance 5/5 pass: the control bar UI is present and does not pollute the page DOM. CDP `insertText` and `dispatchDragEvent` authorization input passes under agent mode. Clipboard paste is intercepted under agent mode. The generation gate does not false-trigger (CDP input is normal without takeover).

### Checks carried over from the prior build of the same engine

The following checks were performed on the prior build (same engine and configuration) and were not repeated for this release. Accepted tests: English built-in pages and the engine version were checked; the version, Settings, credits and GPU pages were visually reviewed. Targeted checks covered eight credits entries with complete licence text and expanded display, Canvas output, a WebGL 2 draw/readback, short local PCM and FLAC playback, and test localStorage retained after a graceful close and reopen. Proxy mode (HTTP and SOCKS5) was tested with DNS traffic capture: no local DNS query for pages, subresources, STUN or TURN servers. WebTransport sent 0 UDP packets with a proxy set. The toolkit's test suite passes all 61 checks including live proxy tests. Packaged runtime checks confirmed credits page renders, LICENSE/NOTICE/TERMS.md present in `bin/`, and 60-second idle run made no request to any external host. The post-release detection suite (55 signals) reported 33 passes with no newly failing item.

Code is in place but pending manual validation: IME composition input, TSF password learning gate, OS drag-and-drop, context-menu commands, and accessibility (AX) actions.

The tested CDP endpoint listened only on 127.0.0.1, rejected the tested foreign Host requests and foreign/null WebSocket Origin handshakes, and permitted the trusted local client. A foreign-Origin HTTP request returned 200 without an Access-Control-Allow-Origin response header; it was not rejected at the HTTP layer. Local programs can still control the browser through CDP. This is not authentication or protection from local malware.

The reviewed idle NetLog fields recorded WPAD activity and no external destination host. This finite observation is not a zero-network or zero-telemetry guarantee. WebGL success does not verify all WebGPU, GPU, codec or sandbox paths. Nonfatal SharedImageManager::ProduceSkia mailbox messages were observed; the sampled drawing and playback checks completed.

Signing status: `dovra_browser.exe`, `bin/chrome.exe` and `bin/chrome.dll` are unsigned (NotSigned), Azure Trusted Signing in progress. A checksum identifies bytes; it is not a trusted publisher signature.

The test scope is finite. Windows 10/11 client systems, a standard-user installation, every GPU, every media format and every website are not claimed to have been tested. Site compatibility, preserved login state and uninterrupted operation are not guaranteed.

## Use and limitations

Use this build for lawful workflows and authorized testing. Keep backups and a separate browser for important browsing. Configurable browser parameters do not grant access or guarantee anonymity.

The build does not provide a Dovra automatic updater. Google Safe Browsing is disabled in this build; do not rely on it for remote phishing or malware checks. The privacy notice explains the reviewed background-service settings and their limits. No universal zero-network or zero-telemetry guarantee is made.

Read the offline terms when starting the package. Project terms do not replace component licences or remove applicable open-source modification and relinking rights. The companion toolkit has a separate MIT licensing scope.

Project: https://dovra.dev/ · Support: legal@dovra.dev
