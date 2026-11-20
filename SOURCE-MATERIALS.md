# Source and relinking materials

Dovra 1.3.1 (engine 158) · Chromium 158.0.8127.37 · Windows x64. [manifest.md](manifest.md) identifies the application pair in this archive.

## Official base of this release

The upstream archive is `chromium-158.0.8127.37.tar.xz`, 4,244,858,244 bytes, SHA-256 `de2a72ec4e0cbcde04b876f9763b17f18575dae9cf374383a3932f59efe7ce6d`, revision `b8c2be851f62f6a394ec57955d7f31335d7cb6d4`.

Official origin: <https://commondatastorage.googleapis.com/chromium-browser-official/chromium-158.0.8127.37.tar.xz>. The upstream source alone is not the complete matching Dovra source/relink delivery: the Dovra patch set for this engine is maintained by the project, and the build additionally needs three inputs that the official archive does not carry — Dawn's Windows Go toolchain, the `third_party/microsoft_multimedia_redirection/src` tree, and the TypeScript test data under `chrome/test/data`. The project's build runbook describes how each of them is obtained.

## Published material set

The material set below is published with this release. GitHub automatic repository archives are not substitutes for the upstream archive or for the finite supplements.

| Material | Bytes | SHA-256 |
| --- | ---: | --- |
| [chromium-158.0.8127.37.tar.xz.part01](https://github.com/dovra-dev/DovraBrowser/releases/download/v1.3.1/chromium-158.0.8127.37.tar.xz.part01) | 1500000000 | `e3af1bf36164984f86043d17f7e649f34b653801f7bcedf338e03e4b13019903` |
| [chromium-158.0.8127.37.tar.xz.part02](https://github.com/dovra-dev/DovraBrowser/releases/download/v1.3.1/chromium-158.0.8127.37.tar.xz.part02) | 1500000000 | `c073658bd0210f969de21ebd1f2fe632e95bd17b048202ded997c3156a51ef31` |
| [chromium-158.0.8127.37.tar.xz.part03](https://github.com/dovra-dev/DovraBrowser/releases/download/v1.3.1/chromium-158.0.8127.37.tar.xz.part03) | 1244858244 | `de49f7bc1153e7c80ed9c5728f145dc8dd135e871c4dd05215653d31ff19ac7b` |
| [Dovra-1.3.1-relink-part-01.zip](https://github.com/dovra-dev/DovraBrowser/releases/download/v1.3.1/Dovra-1.3.1-relink-part-01.zip) | 382614911 | `b228e5d67b5fb07e388213c1a84b9f6ebdfb7864a7109160d67a876753315d99` |
| [Dovra-1.3.1-relink-part-02.zip](https://github.com/dovra-dev/DovraBrowser/releases/download/v1.3.1/Dovra-1.3.1-relink-part-02.zip) | 539782256 | `377974a6810863ac177abfbc325a7bdbda6d28a5d098c68e4d180b31f46c594c` |
| [Dovra-1.3.1-relink-part-03.zip](https://github.com/dovra-dev/DovraBrowser/releases/download/v1.3.1/Dovra-1.3.1-relink-part-03.zip) | 58596733 | `839bbf72e32447b4a0257a95ad44fc2dbd57af62f6183be34d234b5f61b516c2` |
| [Dovra-1.3.1-relink-source-r5-update.zip](https://github.com/dovra-dev/DovraBrowser/releases/download/v1.3.1/Dovra-1.3.1-relink-source-r5-update.zip) | 3228845 | `69808316d24c037f7ae93d6f7d7641d2605cb7c673083053fb70638092b96ca3` |
| [Dovra-1.3.1-component-source-build-licence.zip](https://github.com/dovra-dev/DovraBrowser/releases/download/v1.3.1/Dovra-1.3.1-component-source-build-licence.zip) | 457574 | `0081895c006d3feb72cb8f9e98ad3e7d5e87b51df74f2631549601505079ff37` |
| [Dovra-1.3.1-generated-headers.zip](https://github.com/dovra-dev/DovraBrowser/releases/download/v1.3.1/Dovra-1.3.1-generated-headers.zip) | 4852133 | `b92cbde94a96cbae8fafd9488da60a379a7e0824c4eb0170d169160e4f4ad065` |
| [Dovra-1.3.1-ffmpeg-build-provider-controls.zip](https://github.com/dovra-dev/DovraBrowser/releases/download/v1.3.1/Dovra-1.3.1-ffmpeg-build-provider-controls.zip) | 73983 | `93eb15c8ee46f0009c96fe626ebaa7ecd3e5f6a6d196f1fbd95ff8381e34b871` |
| [Dovra-1.3.1-ffmpeg-dependency-provider-index.zip](https://github.com/dovra-dev/DovraBrowser/releases/download/v1.3.1/Dovra-1.3.1-ffmpeg-dependency-provider-index.zip) | 71972 | `168e09b80c3fa1eaa623572d6b79ab90e47312a5c693b3493870250e163b9cbc` |

## Reconstruction order

1. **Official source.** Concatenate the three numbered official-source parts in the order part01, part02, part03. The result is `chromium-158.0.8127.37.tar.xz`, 4,244,858,244 bytes, SHA-256 `de2a72ec4e0cbcde04b876f9763b17f18575dae9cf374383a3932f59efe7ce6d`, which is the archive hash given above. The three parts were checked to re-concatenate to the archive byte for byte.
2. **Relink base.** Extract the three relink parts. They unpack to a root directory `Dovra-1.3.1-relink/` whose `src/` maps the Chromium source root together with the build output directory `out/Dovra13`: the compiled objects, the static libraries, the build response files, the recorded link commands, the LLVM runtime libraries, the CPython host, and the postimages of the modified LGPL files. The base holds 54,318 files.
3. **Merge the official source.** Copy the official archive into `src/`, keeping the tree's own version of every file it already carries and letting the archive fill only the gaps. On the verification run the archive contributed 16,651 files and the tree kept its own 22 versions.
4. **External toolchain.** Place the LLVM toolchain package at `src/third_party/llvm-build/Release+Asserts/`. It is `Win/clang-llvmorg-24-init-14453-ge063be79-1.tar.xz`, 52,783,904 bytes, SHA-256 `08abce6e1d01c2fff9b25a09e36d9976296f27842196f96411b8220364481818`. All six files it contributes were checked against the recorded input map.
5. **Source revision record.** `Dovra-1.3.1-relink-source-r5-update.zip` carries the source manifest of the revision this browser was built from, the source manifest of the preceding revision of this engine, the complete input map of the recorded link, the recorded link commands, the three control response files, and the recipe that runs the link. The relink base is already in the state of the shipped revision, so this package is a revision record rather than a patch to apply; the difference between the two revisions can be computed from the package alone.
6. **Component and header supplements.** `Dovra-1.3.1-component-source-build-licence.zip` carries, for every LGPL file the project modified, the upstream original, the modified file, the difference, the licence header and the licence text, plus the recorded compile command; it also carries the two files the project added itself that the LGPL translation units read. `Dovra-1.3.1-generated-headers.zip` carries the 2,737 headers that the LGPL translation units read, that the build generates, and that the official archive does not contain; every one of them was checked against the official archive member list.
7. **FFmpeg build controls.** `Dovra-1.3.1-ffmpeg-build-provider-controls.zip` carries the build commands of the two FFmpeg static libraries as argument vectors with the provider roots replaced by named placeholders, the provider identities and versions, and the build configuration — including the two archive response files that the build system deletes after the archive step, reconstructed from the member order of the archives the shipped build produced. `Dovra-1.3.1-ffmpeg-dependency-provider-index.zip` carries the dependency index of that build: every indexed file is hashed and the index has no unresolved entry.
8. **Relink.** Rebuild the two FFmpeg static libraries from the commands of step 7, then run the recorded link command for `chrome.dll`.

## External prerequisites

| Prerequisite | Version and where it comes from |
| --- | --- |
| Official source archive | `chromium-158.0.8127.37.tar.xz`, 4,244,858,244 bytes, SHA-256 `de2a72ec4e0cbcde04b876f9763b17f18575dae9cf374383a3932f59efe7ce6d`; public address given above |
| LLVM toolchain package | `Win/clang-llvmorg-24-init-14453-ge063be79-1.tar.xz`, 52,783,904 bytes, SHA-256 `08abce6e1d01c2fff9b25a09e36d9976296f27842196f96411b8220364481818`; <https://commondatastorage.googleapis.com/chromium-browser-clang/Win/clang-llvmorg-24-init-14453-ge063be79-1.tar.xz> |
| MSVC | 14.51.36231 |
| Windows SDK | 10.0.28000.0 |

MSVC and the Windows SDK are not redistributed with this material set; they remain subject to their own acquisition and licence terms. The recorded link command resolves all of its library references against these two providers and the LLVM package: four MSVC libraries, twenty Windows SDK libraries and six LLVM bin tools.

## What reconstruction was verified

On the build machine that produced this package, in a directory that did not exist before the exercise, the material set plus the external prerequisites above was enough to rebuild the two FFmpeg static libraries — 289 C translation units, 30 assembly units and two archive steps, 321 steps in total, every one of them executed, with every resulting object and library byte for byte identical to the shipped ones — and then to relink `chrome.dll`. The relinked `chrome.dll` was byte for byte identical to the `chrome.dll` in this archive. A copy of this package with that file substituted started, reported the same product identity and produced the same client-hint measurement as the shipped build.

That exercise ran on one machine. It was not repeated on a second machine, so it is a bounded observation rather than a general guarantee for other systems. `chrome.exe` and `chrome_elf.dll` were not relinked in that exercise; the material set carries their recorded commands and response files, but those were not executed.

Do not overlay reconstruction materials onto an installed browser, an active source tree or a user profile. The original/modified relink variants and test libraries are not substitutes for the main browser pair in [manifest.md](manifest.md).

## Availability and licences

The asset links above identify the material set published with this release. The Toolkit is a separate optional companion and is not part of this application archive. The material set published with 1.3.0 matches the 158.0.8127.18 binaries of that release; its asset names and checksums do not apply to this one.

Retain all applicable component notices and licence texts. The [Terms](https://dovra.dev/terms/) and [Privacy notice](https://dovra.dev/privacy/) were adopted on 17 October 2026. Scoped grants for interface declarations, tools or documentation do not relicense the entire browser or certify the complete delivery. Physical-input acceptance is not certified by these material records.

Publisher: DOVRA SOFTWARE LTD, company number 17493263. Contact: <dovra.dev@gmail.com>. Built on Chromium; not affiliated with or endorsed by Google.
