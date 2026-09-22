# Dovra Beta — beta-20260923

Free experimental Windows x64 portable build with an English interface. This is a Beta, not a stable release or a formal Dovra product version. The underlying Chromium technical version is `153.0.8010.48`.

## What changed since beta-20260916

- The seed-derived variation of canvas pixel readback, canvas text metrics and layout rectangles (`--fingerprint=<seed>`) was reimplemented in a single module written for this project. It replaces the previously included Bromite-derived implementation, which is no longer part of the build. Without a seed these APIs return the unmodified Chromium values.
- The launcher is now `dovra_browser.exe` (previously `dovra_browser.exe`). The runtime-terms manifest revision changed accordingly, so the offline Microsoft runtime terms are shown again on first start.
- Release files are distributed from `https://dl.dovra.dev/beta-20260923/`; the GitHub release entry carries links only.
- The Chromium engine (`153.0.8010.48`), the remaining patch set, the build configuration and the bundled component notices are unchanged.

## Downloads

All files: `https://dl.dovra.dev/beta-20260923/`

- `Dovra-Beta-20260923-win-x64.zip`: complete browser, launcher and offline notices.
- `Dovra-Toolkit-beta-20260923.zip`: optional companion toolkit; no browser included.
- `SHA256SUMS.txt`: SHA-256 checksums for the release files.
- Component source, relinking and LGPL modification archives: listed in [SOURCE-MATERIALS.md](SOURCE-MATERIALS.md).

GitHub's automatic repository source ZIP/tarball contains repository files, not the compiled browser or the full Chromium source tree.

## Verified scope

Tested environment: Windows Server 2022 x64, OS build 20348.5139; NVIDIA GeForce GTX 650 / ANGLE Direct3D 11.

### Checks run on this batch

- Without a seed, the page-observable build features (`tests/probe-dump.js`, 70 groups) and the open-source FingerprintJS components (`tests/probe-fpjs.js`, 41 components) of the packaged runtime were compared item by item against the beta-20260916 binary; only the network downlink estimate differed.
- With `--fingerprint=123456789` and `--fingerprint=987654321` (`tests/probe-seeded-noise.js`, two page loads per start): `getBoundingClientRect()` equals the union of `getClientRects()`; Element and Range rectangles carry the same factor; a same-origin iframe reports the same coordinates; values repeat exactly across reloads; the factor is within 1 ± 1e-4 and differs between the two seeds. `measureText()` width and actual bounding box carry one factor, `fontBoundingBox*` is unchanged, a Worker `OffscreenCanvas` returns the same width as the main thread, and the empty string measures 0. `getImageData()` of a region equals the same region of a full read, two `toDataURL()` calls are identical, decoding the PNG and reading it back differs only by single-unit steps in the perturbed channels, WebGL `readPixels()` is stable across two reads, and all readback values differ between the two seeds and from the no-seed run.
- `--disable-spoofing=canvas` removed only the canvas readback variation; `--disable-spoofing=all` reproduced the no-seed values exactly.
- The post-release detection suite (`tests/post-release.js`, 55 signals, recommended profile) reported 32 passes on the packaged runtime. Every remaining item was already attributed in earlier batches or reproduces identically on the beta-20260916 binary with the same profile (`maxTouchPoints` reported by the host machine; the Intl default locale following the en-US interface language of this package); none is introduced by this batch.

### Carried over from the beta-20260916 build of the same engine

The following checks were performed on the beta-20260916 build (same engine, configuration and component set) and were not repeated for this batch. Accepted tests: English built-in pages and the engine version were checked; the version, Settings, credits and GPU pages were visually reviewed. Targeted checks covered eight credits entries with complete licence text and expanded display, Canvas output, a WebGL 2 draw/readback, short local PCM and FLAC playback, and test localStorage retained after a graceful close and reopen. These were browser checks, not a test of the packaged launcher's first-use terms dialog or a clean-machine installation.

The tested CDP endpoint listened only on 127.0.0.1, rejected the tested foreign Host requests and foreign/null WebSocket Origin handshakes, and permitted the trusted local client. A foreign-Origin HTTP request returned 200 without an Access-Control-Allow-Origin response header; it was not rejected at the HTTP layer. Local programs can still control the browser through CDP. This is not authentication or protection from local malware.

The reviewed idle NetLog fields recorded WPAD activity and no external destination host. This finite observation is not a zero-network or zero-telemetry guarantee. WebGL success does not verify all WebGPU, DXIL, GPU, codec or sandbox paths. Nonfatal SharedImageManager::ProduceSkia mailbox messages were observed; the sampled drawing and playback checks completed..

Signing status: `dovra_browser.exe`, `bin/chrome.exe` and `bin/chrome.dll` are unsigned (NotSigned). A checksum identifies bytes; it is not a trusted publisher signature..

The test scope is finite. Windows 10/11 client systems, a standard-user installation, every GPU, every media format and every website are not claimed to have been tested. Site compatibility, preserved login state and uninterrupted operation are not guaranteed.

## Use and limitations

Use this build for lawful workflows and authorized testing. Keep backups and a separate browser for important browsing. Configurable browser parameters do not grant access or guarantee anonymity.

The build does not provide a Dovra automatic updater. Google Safe Browsing is disabled in this candidate; do not rely on it for remote phishing or malware checks. The privacy notice explains the reviewed background-service settings and their limits. No universal zero-network or zero-telemetry guarantee is made.

Read the offline terms when starting the package. Project terms do not replace component licences or remove applicable open-source modification and relinking rights. The companion toolkit has a separate MIT licensing scope.

Project: https://dovra.dev/ · Support: dovra.dev@gmail.com
