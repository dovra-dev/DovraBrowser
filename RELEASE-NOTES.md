# Dovra Beta — beta-20260925-4

Free experimental Windows x64 portable build with an English interface. This is a Beta, not a stable release or a formal Dovra product version. The underlying Chromium technical version is `153.0.8010.48`.

## What changed since beta-20260924

- **Browser — WebRTC name lookups.** In the default WebRTC IP handling of this build (which sends no UDP), WebRTC no longer resolves any host name itself: the names of TURN servers that use TCP (`transport=tcp`) or TLS (`turns:`) are handed to the connection layer, which sends them to the proxy when one is set, and remote candidates whose address is a host name (including mDNS `.local` names) are not resolved at all, with or without a proxy, so a peer is reachable only through its relay or IP-address candidates (a peer offering only host-name candidates and no relay cannot be reached). The earlier build looked these names up with the local DNS resolver or with multicast DNS even with a proxy set. The change is confined to the WebRTC integration of the renderer (`third_party/blink/renderer/platform/p2p/port_allocator.cc` with its header, and `third_party/blink/renderer/modules/peerconnection/peer_connection_dependency_factory.cc`; BSD-licensed Chromium code); the LGPL-licensed Blink files and their modifications are the same as in beta-20260924.
- **Toolkit.** `Dovra-Toolkit-beta-20260925-4.zip` contains the toolkit changes published as the toolkit-only batches `beta-20260925`, `beta-20260925-2` and `beta-20260925-3` (the `dovra` integration command line: launch contract, identity blueprints, checkpoints). New in this batch: `dovra` recognises this browser build and offers proxies on it (`network.mode = proxy` with `http` or `socks5`); with the `beta-20260924` browser, proxies remain refused.
- Release files are distributed from `https://dl.dovra.dev/beta-20260925-4/`; the GitHub release entry carries links only.
- The Chromium engine (`153.0.8010.48`), the rest of the patch set, the seed-derived variation module and the bundled component set are unchanged from beta-20260924.

## Downloads

All files: `https://dl.dovra.dev/beta-20260925-4/`

- `Dovra-Beta-20260925-4-win-x64.zip`: complete browser, launcher and offline notices.
- `Dovra-Toolkit-beta-20260925-4.zip`: optional companion toolkit; no browser included.
- `SHA256SUMS.txt`: SHA-256 checksums for the release files.
- Component source, relinking and LGPL modification archives: listed in [SOURCE-MATERIALS.md](SOURCE-MATERIALS.md).

GitHub's automatic repository source ZIP/tarball contains repository files, not the compiled browser or the full Chromium source tree.

## Verified scope

Tested environment: Windows Server 2022 x64, OS build 20348.5139; NVIDIA GeForce GTX 650 / ANGLE Direct3D 11.

### Checks run on this batch

- Without a seed, the page-observable build features (`tests/probe-dump.js`, 70 groups) and the open-source FingerprintJS components (`tests/probe-fpjs.js`, 41 components) of the packaged runtime were compared item by item against the beta-20260924 binary: the FingerprintJS components are identical; in the build features only the network downlink estimate and the timer-precision samples differ, and both also vary between two runs of the same binary.
- With `--fingerprint=123456789` and `--fingerprint=987654321` (`tests/probe-seeded-noise.js`) every recorded value equals the beta-20260924 run of the same seed.
- Proxy mode, HTTP and SOCKS5 proxy on this machine, DNS traffic captured at the network adapter while pages used freshly generated host names: no local DNS query for the page, its subresources, a STUN server, or TURN servers over UDP, TCP (`transport=tcp`) and TLS (`turns:`); the TURN server names appeared in the requests received by the proxy. Remote candidates added by the page with a host name (UDP and TCP) and with an mDNS `.local` name caused no DNS query and no multicast DNS packet (the capture covered port 5353 as well); on an intermediate build without this part of the change, the same page produced both. A lookup made outside the browser during the same capture was recorded, confirming the capture saw DNS traffic.
- WebTransport (HTTP/3 over UDP) to a UDP listener on the local network: 0 packets arrived with a proxy set, 6 without a proxy.
- With an unreachable proxy, navigation fails with `ERR_PROXY_CONNECTION_FAILED`; no direct TCP connection, no UDP and no DNS query for any of the names above were observed.
- Without a proxy, page and TURN server names are resolved by the browser's network service as before; remote candidate host names are not resolved in this build's default WebRTC IP handling with or without a proxy.
- The toolkit's test suite passes all 61 checks on this build, none skipped, including the live proxy tests (`proxy http`, `proxy socks5`: pages and downloads reach the proxy by host name, no other TCP connection from any browser process, no WebRTC UDP to an IP-literal STUN server).
- Packaged runtime (`tests/t11-acceptance.js`): the credits page renders, `LICENSE`, `NOTICE` and `TERMS.md` are present in `bin/`, and a 60-second idle run made no request to any external host.
- The post-release detection suite (`tests/post-release.js`, 55 signals, recommended profile) reported 33 passes on the packaged runtime, the same as beta-20260924, and no newly failing item; every remaining item was already attributed on earlier batches (`maxTouchPoints` reported by the host machine; the Intl default locale following the en-US interface language of this package; host and site-side items tracked separately).

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
