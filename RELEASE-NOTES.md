# Dovra Beta — beta-20260924

Free experimental Windows x64 portable build with an English interface. This is a Beta, not a stable release or a formal Dovra product version. The underlying Chromium technical version is `153.0.8010.48`.

## What changed since beta-20260923

- The package no longer contains the Microsoft SDK runtime files `d3dcompiler_47.dll` and `dxil.dll`, nor the DirectX Shader Compiler `dxcompiler.dll` that was built for them. WebGL uses the `d3dcompiler_47.dll` that ships with Windows 10 and later; WebGPU on Direct3D 12 is now built to compile shaders with FXC, so the adapter no longer reports the `subgroups` feature. There are therefore no Microsoft runtime terms to accept: `dovra_browser.exe` is a small entry point that only starts `bin\chrome.exe` with default arguments and shows no dialog, the toolkit performs no acceptance check, and `MICROSOFT-RUNTIME-TERMS.md`, the SDK licence copies and the runtime-terms manifest are no longer part of the package.
- The ungoogled-chromium first-run page (`chrome://ungoogled-first-run`) is no longer built in; a first start opens the new-tab page.
- Release files are distributed from `https://dl.dovra.dev/beta-20260924/`; the GitHub release entry carries links only.
- The Chromium engine (`153.0.8010.48`), the fingerprint patch set and the seed-derived variation module are unchanged from beta-20260923.

## Downloads

All files: `https://dl.dovra.dev/beta-20260924/`

- `Dovra-Beta-20260924-win-x64.zip`: complete browser, launcher and offline notices.
- `Dovra-Toolkit-beta-20260924.zip`: optional companion toolkit; no browser included.
- `SHA256SUMS.txt`: SHA-256 checksums for the release files.
- Component source, relinking and LGPL modification archives: listed in [SOURCE-MATERIALS.md](SOURCE-MATERIALS.md).

GitHub's automatic repository source ZIP/tarball contains repository files, not the compiled browser or the full Chromium source tree.

## Verified scope

Tested environment: Windows Server 2022 x64, OS build 20348.5139; NVIDIA GeForce GTX 650 / ANGLE Direct3D 11.

### Checks run on this batch

- Without a seed, the page-observable build features (`tests/probe-dump.js`, 70 groups) and the open-source FingerprintJS components (`tests/probe-fpjs.js`, 41 components) of the packaged runtime were compared item by item against the beta-20260923 binary; apart from the network downlink and RTT estimates, the only difference is the WebGPU adapter feature list, which no longer contains `subgroups` (FXC shader path).
- Graphics runtime without the Microsoft SDK files (`tests/probe-gpu-runtime.js`): the WebGL renderer string and the pixel hash of a 64×64 shader-drawn triangle are identical to beta-20260923 (the `d3dcompiler_47.dll` shipped with Windows is used); WebGPU adapter and device creation and a compute dispatch succeed without any command-line flag, with 16 adapter features (17 before).
- With `--fingerprint=123456789` and `--fingerprint=987654321` (`tests/probe-seeded-noise.js`) every recorded value equals the beta-20260923 run of the same seed, so the seed-derived variation of layout rectangles, text metrics and canvas readback is unchanged.
- First start (`tests/probe-first-run.js` and a direct start of `bin\chrome.exe` without arguments on a fresh profile): only the new-tab page opens; `chrome://ungoogled-first-run` is no longer a valid URL.
- `dovra_browser.exe` (thin entry point, 6,144 bytes): started from a three-file layout, it launched `bin\chrome.exe` with `--fingerprint-brand=chrome`, `--lang=en-US` and the default `%LOCALAPPDATA%\Dovra\Beta\BrowserData` profile, passed an explicit `--user-data-dir` and other arguments through unchanged, and exited immediately without showing a dialog.
- The post-release detection suite (`tests/post-release.js`, 55 signals, recommended profile) reported 33 passes on the packaged runtime and no newly failing item; every remaining item was already attributed on beta-20260923 (`maxTouchPoints` reported by the host machine; the Intl default locale following the en-US interface language of this package; host and site-side items tracked separately).

### Carried over from the beta-20260916 build of the same engine

The following checks were performed on the beta-20260916 build (same engine and configuration; the Microsoft SDK runtime components present in that build are no longer shipped) and were not repeated for this batch. Accepted tests: English built-in pages and the engine version were checked; the version, Settings, credits and GPU pages were visually reviewed. Targeted checks covered eight credits entries with complete licence text and expanded display, Canvas output, a WebGL 2 draw/readback, short local PCM and FLAC playback, and test localStorage retained after a graceful close and reopen. These were browser checks, not a test of the packaged launcher or a clean-machine installation.

The tested CDP endpoint listened only on 127.0.0.1, rejected the tested foreign Host requests and foreign/null WebSocket Origin handshakes, and permitted the trusted local client. A foreign-Origin HTTP request returned 200 without an Access-Control-Allow-Origin response header; it was not rejected at the HTTP layer. Local programs can still control the browser through CDP. This is not authentication or protection from local malware.

The reviewed idle NetLog fields recorded WPAD activity and no external destination host. This finite observation is not a zero-network or zero-telemetry guarantee. WebGL success does not verify all WebGPU, GPU, codec or sandbox paths. Nonfatal SharedImageManager::ProduceSkia mailbox messages were observed; the sampled drawing and playback checks completed..

Signing status: `dovra_browser.exe`, `bin/chrome.exe` and `bin/chrome.dll` are unsigned (NotSigned). A checksum identifies bytes; it is not a trusted publisher signature..

The test scope is finite. Windows 10/11 client systems, a standard-user installation, every GPU, every media format and every website are not claimed to have been tested. Site compatibility, preserved login state and uninterrupted operation are not guaranteed.

## Use and limitations

Use this build for lawful workflows and authorized testing. Keep backups and a separate browser for important browsing. Configurable browser parameters do not grant access or guarantee anonymity.

The build does not provide a Dovra automatic updater. Google Safe Browsing is disabled in this candidate; do not rely on it for remote phishing or malware checks. The privacy notice explains the reviewed background-service settings and their limits. No universal zero-network or zero-telemetry guarantee is made.

Read the offline terms when starting the package. Project terms do not replace component licences or remove applicable open-source modification and relinking rights. The companion toolkit has a separate MIT licensing scope.

Project: https://dovra.dev/ · Support: dovra.dev@gmail.com
