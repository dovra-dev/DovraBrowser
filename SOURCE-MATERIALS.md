# Source and relinking materials

Dovra 1.3.0 (engine 158) · Chromium 158.0.8127.18 · Windows x64. [manifest.md](manifest.md) identifies the application pair in this archive.

## Official base of this release

The upstream archive is `chromium-158.0.8127.18.tar.xz`, 4,619,686,576 bytes, SHA-256 `ea2e3b47bcc1a2d1344affd09d41454a0caaafb75b7525a2496874ec673b6db0`, revision `6449d9f9a6a906edff724b7b220199b3fde4615c`.

Official origin: <https://commondatastorage.googleapis.com/chromium-browser-official/chromium-158.0.8127.18.tar.xz>. The upstream source alone is not the complete matching Dovra source/relink delivery: the Dovra patch set for this engine is maintained by the project, and the build additionally needs three inputs that the official archive does not carry — Dawn's Windows Go toolchain, the `third_party/microsoft_multimedia_redirection/src` tree, and the TypeScript test data under `chrome/test/data`. The project's build runbook describes how each of them is obtained.

## Published material set

The material set below is published with this release. GitHub automatic repository archives are not substitutes for the upstream archive or for the finite supplements.

| Material | Bytes | SHA-256 |
| --- | ---: | --- |
| [chromium-158.0.8127.18.tar.xz.part01](https://github.com/dovra-dev/DovraBrowser/releases/download/v1.3.0/chromium-158.0.8127.18.tar.xz.part01) | 1500000000 | `9a415b9f2eda2a29457bee161d6a5174d533a70de8a73e9e86cb87abdcd03df8` |
| [chromium-158.0.8127.18.tar.xz.part02](https://github.com/dovra-dev/DovraBrowser/releases/download/v1.3.0/chromium-158.0.8127.18.tar.xz.part02) | 1500000000 | `9cf3738b8d7115215f77ccece2c2759f3d06ccd08ac0c1095d6e8aa41156b745` |
| [chromium-158.0.8127.18.tar.xz.part03](https://github.com/dovra-dev/DovraBrowser/releases/download/v1.3.0/chromium-158.0.8127.18.tar.xz.part03) | 1500000000 | `5f95aa6e550d7c6a964bdf72c3d4cf6f249c32777fde4028f704e95f9de54626` |
| [chromium-158.0.8127.18.tar.xz.part04](https://github.com/dovra-dev/DovraBrowser/releases/download/v1.3.0/chromium-158.0.8127.18.tar.xz.part04) | 119686576 | `d1cf77bdae76fec5107aba4c332defd8eab49694a27d46f68870b0f3b07357eb` |
| [Dovra-1.3.0-relink-part-01.zip](https://github.com/dovra-dev/DovraBrowser/releases/download/v1.3.0/Dovra-1.3.0-relink-part-01.zip) | 382466372 | `61753816bfb7c0a99de7df2fef01f473c310c22deb4f3f4afaa648fa55597d6f` |
| [Dovra-1.3.0-relink-part-02.zip](https://github.com/dovra-dev/DovraBrowser/releases/download/v1.3.0/Dovra-1.3.0-relink-part-02.zip) | 447398363 | `3962664ec0556c6d1a30e0c7c567c74d8a0623b63d358e05798f68cfbd248808` |
| [Dovra-1.3.0-relink-part-03.zip](https://github.com/dovra-dev/DovraBrowser/releases/download/v1.3.0/Dovra-1.3.0-relink-part-03.zip) | 29629671 | `743b567caf06d21fe2e6cc3aedd6aefafbd63daf96910ffc6d859826855a2a32` |
| [Dovra-1.3.0-relink-source-r3-update.zip](https://github.com/dovra-dev/DovraBrowser/releases/download/v1.3.0/Dovra-1.3.0-relink-source-r3-update.zip) | 3114734 | `9071754b403133ff49cf6a5a009b61b6c05c72ccbf4a38253aa123913ce62e3b` |
| [Dovra-1.3.0-component-source-build-licence.zip](https://github.com/dovra-dev/DovraBrowser/releases/download/v1.3.0/Dovra-1.3.0-component-source-build-licence.zip) | 457282 | `03884521e6a83e6fa760748329197185f42752195a529071c1ee01f11341782b` |
| [Dovra-1.3.0-generated-headers.zip](https://github.com/dovra-dev/DovraBrowser/releases/download/v1.3.0/Dovra-1.3.0-generated-headers.zip) | 4852319 | `abce2fc767c8d6e08780ef76defb16d02ea29d67249b48c5869e76b284d07795` |
| [Dovra-1.3.0-ffmpeg-build-provider-controls.zip](https://github.com/dovra-dev/DovraBrowser/releases/download/v1.3.0/Dovra-1.3.0-ffmpeg-build-provider-controls.zip) | 74166 | `42fdbd63d4548ff8420fcd1a59c0ffbb8a82519b017154a732565cdcf9e8d140` |
| [Dovra-1.3.0-ffmpeg-dependency-provider-index.zip](https://github.com/dovra-dev/DovraBrowser/releases/download/v1.3.0/Dovra-1.3.0-ffmpeg-dependency-provider-index.zip) | 105214 | `03771dcc6be47882dc8ae0d9bb30af94781b45342d4c10fd3cdd0b2d504a000d` |

## Reconstruction order

1. **Official source.** Concatenate the four numbered official-source parts in the order part01, part02, part03, part04. The result is `chromium-158.0.8127.18.tar.xz`, 4,619,686,576 bytes, SHA-256 `ea2e3b47bcc1a2d1344affd09d41454a0caaafb75b7525a2496874ec673b6db0`, which is the archive hash given above. The four parts were checked to re-concatenate to the archive byte for byte.
2. **Relink base.** Extract the three relink parts. They unpack to a root directory `Dovra-1.3.0-relink/` whose `src/` maps the Chromium source root together with the build output directory `out/Dovra13`: the compiled objects, the static libraries, the build response files, the recorded link commands, the LLVM runtime libraries, the CPython host, and the postimages of the modified LGPL files. The base holds 52,042 files.
3. **Merge the official source.** Copy the official archive into `src/`, keeping the tree's own version of every file it already carries and letting the archive fill only the gaps. On the verification run the archive contributed 16,495 files and the tree kept its own 178 versions.
4. **External toolchain.** Place the LLVM toolchain package at `src/third_party/llvm-build/Release+Asserts/`. It is `Win/clang-llvmorg-24-init-14453-ge063be79-1.tar.xz`, 52,783,904 bytes, SHA-256 `08abce6e1d01c2fff9b25a09e36d9976296f27842196f96411b8220364481818`. All six files it contributes were checked against the recorded input map.
5. **Source revision record.** `Dovra-1.3.0-relink-source-r3-update.zip` carries the source manifest of the revision this browser was built from, the source manifest of the preceding revision of this engine, the complete input map of the recorded link, the recorded link commands, the three control response files, and the recipe that runs the link. The relink base is already in the state of the shipped revision, so this package is a revision record rather than a patch to apply; the difference between the two revisions can be computed from the package alone.
6. **Component and header supplements.** `Dovra-1.3.0-component-source-build-licence.zip` carries, for every LGPL file the project modified, the upstream original, the modified file, the difference, the licence header and the licence text, plus the recorded compile command; it also carries the two files the project added itself that the LGPL translation units read. `Dovra-1.3.0-generated-headers.zip` carries the 2,738 headers that the LGPL translation units read, that the build generates, and that the official archive does not contain; every one of them was checked against the official archive member list.
7. **FFmpeg build controls.** `Dovra-1.3.0-ffmpeg-build-provider-controls.zip` carries the build commands of the two FFmpeg static libraries as argument vectors with the provider roots replaced by named placeholders, the provider identities and versions, and the build configuration — including the two archive response files that the build system deletes after the archive step, reconstructed from the member order of the archives the shipped build produced. `Dovra-1.3.0-ffmpeg-dependency-provider-index.zip` carries the dependency index of that build: every indexed file is hashed and the index has no unresolved entry.
8. **Relink.** Rebuild the two FFmpeg static libraries from the commands of step 7, then run the recorded link command for `chrome.dll`.

## External prerequisites

| Prerequisite | Version and where it comes from |
| --- | --- |
| Official source archive | `chromium-158.0.8127.18.tar.xz`, 4,619,686,576 bytes, SHA-256 `ea2e3b47bcc1a2d1344affd09d41454a0caaafb75b7525a2496874ec673b6db0`; public address given above |
| LLVM toolchain package | `Win/clang-llvmorg-24-init-14453-ge063be79-1.tar.xz`, 52,783,904 bytes, SHA-256 `08abce6e1d01c2fff9b25a09e36d9976296f27842196f96411b8220364481818`; <https://commondatastorage.googleapis.com/chromium-browser-clang/Win/clang-llvmorg-24-init-14453-ge063be79-1.tar.xz> |
| MSVC | 14.51.36231 |
| Windows SDK | 10.0.28000.0 |

MSVC and the Windows SDK are not redistributed with this material set; they remain subject to their own acquisition and licence terms. The recorded link command resolves all of its library references against these two providers and the LLVM package: four MSVC libraries, twenty Windows SDK libraries and six LLVM bin tools.

## What reconstruction was verified

On the build machine that produced this package, in a directory that did not exist before the exercise, the material set plus the external prerequisites above was enough to rebuild the two FFmpeg static libraries — 289 C translation units, 30 assembly units and two archive steps, 321 steps in total, every one of them executed, with every resulting object and library byte for byte identical to the shipped ones — and then to relink `chrome.dll`. The relinked `chrome.dll` was byte for byte identical to the `chrome.dll` in this archive. A copy of this package with that file substituted started, reported the same product identity and produced the same client-hint measurement as the shipped build.

That exercise ran on one machine. It was not repeated on a second machine, so it is a bounded observation rather than a general guarantee for other systems. `chrome.exe` and `chrome_elf.dll` were not relinked in that exercise; the material set carries their recorded commands and response files, but those were not executed.

Do not overlay reconstruction materials onto an installed browser, an active source tree or a user profile. The original/modified relink variants and test libraries are not substitutes for the main browser pair in [manifest.md](manifest.md).

## Availability and licences

The asset links above identify the material set published with this release. The Toolkit is a separate optional companion and is not part of this application archive. The material set of 1.2.0 (published on 22 October 2026 and withdrawn on 25 October 2026) was withdrawn together with that release and is no longer distributed; the asset names in it describe the 155 engine and do not apply here.

Retain all applicable component notices and licence texts. The [Terms](https://dovra.dev/terms/) and [Privacy notice](https://dovra.dev/privacy/) were adopted on 17 October 2026. Scoped grants for interface declarations, tools or documentation do not relicense the entire browser or certify the complete delivery. Physical-input acceptance is not certified by these material records.

Publisher: DOVRA SOFTWARE LTD, company number 17493263. Contact: <dovra.dev@gmail.com>. Built on Chromium; not affiliated with or endorsed by Google.
