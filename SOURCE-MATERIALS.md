# Source and relinking materials

Dovra 1.2.0 · Chromium 155.0.8059.85 · Windows x64. [manifest.md](manifest.md) identifies the source34 application pair.

## Official base and finite supplements

The upstream archive is `chromium-155.0.8059.85.tar.xz`, 4,391,079,296 bytes, SHA-256 `673670a10e8194efcdd1609600cc55f3dd2b7f248543dc3559b3d17176927bd4`, revision `0e66b94549a8bd85f03fbdf189b752d6e7b63c32`.

Official origin: <https://commondatastorage.googleapis.com/chromium-browser-official/chromium-155.0.8059.85.tar.xz>. This upstream source alone is not the complete matching Dovra source/relink delivery. GitHub automatic repository archives are not substitutes for it or for the finite supplements.

The matching reconstruction follows the original two relink archives, the source27 update, source28 update, source29 update and one combined source34 update in that order. The source34 update combines two source29-to-source31 and five source31-to-source34 postimages, seven files totalling 30,783,186 bytes. No separate public source31 archive is required. The current public input-map SHA-256 is `1077a720db1c81761a3ea819a6754d75fea6bf523f952b7b1297b82f50b5be32`; it describes 47,830 internal inputs and 94 external prerequisites. A map checksum is not the ZIP checksum.

| Material | Bytes | SHA-256 |
| --- | ---: | --- |
| [chromium-155.0.8059.85.tar.xz.part01](https://github.com/dovra-dev/DovraBrowser/releases/download/v1.2.0/chromium-155.0.8059.85.tar.xz.part01) | 1500000000 | `c3f3c2174d5d2dd84a5d235e20a2392de2392386c3a782ae658a31ba04ea06a0` |
| [chromium-155.0.8059.85.tar.xz.part02](https://github.com/dovra-dev/DovraBrowser/releases/download/v1.2.0/chromium-155.0.8059.85.tar.xz.part02) | 1500000000 | `abcd93a0f91bc851caec53d68f91cf15d05f97c9fda2e311a900622dd9299a50` |
| [chromium-155.0.8059.85.tar.xz.part03](https://github.com/dovra-dev/DovraBrowser/releases/download/v1.2.0/chromium-155.0.8059.85.tar.xz.part03) | 1391079296 | `b281efc80950972a5c5701845897479052d1c290b30d852230d74d9717793b8a` |
| [relink-part-01.zip](https://github.com/dovra-dev/DovraBrowser/releases/download/v1.2.0/relink-part-01.zip) | 380438517 | `c0e33f400b56d9a012fc2993ebd2ba6a7cdcbeb7f572034fe6fef4c266d0245c` |
| [relink-part-02.zip](https://github.com/dovra-dev/DovraBrowser/releases/download/v1.2.0/relink-part-02.zip) | 263826753 | `4d66fab9c89d9dbef129c4cfb874c4401c99029192fcd969433d69b5d409b100` |
| [Dovra-1.2.0-relink-source27-update.zip](https://github.com/dovra-dev/DovraBrowser/releases/download/v1.2.0/Dovra-1.2.0-relink-source27-update.zip) | 3449634 | `b70e02edd6a3c9bac440d15741cdd8e4af6139037b60847d90b0976c75ce61d6` |
| [Dovra-1.2.0-relink-source28-update.zip](https://github.com/dovra-dev/DovraBrowser/releases/download/v1.2.0/Dovra-1.2.0-relink-source28-update.zip) | 3133324 | `3a46b95175af4655dcf55e573ff1934bfd3f986f6747d1ae1bdac7dc5b184ca0` |
| [Dovra-1.2.0-relink-source29-update.zip](https://github.com/dovra-dev/DovraBrowser/releases/download/v1.2.0/Dovra-1.2.0-relink-source29-update.zip) | 3029240 | `94e81f1f53b46deffc01cbe1fd6e3be0b5e488436efa6e4d2f94f23e80c30655` |
| [Dovra-1.2.0-relink-source34-update.zip](https://github.com/dovra-dev/DovraBrowser/releases/download/v1.2.0/Dovra-1.2.0-relink-source34-update.zip) | 5748594 | `77067eaeeb8747bc2696bb1ef849b8a864b7febe059b0a662afc5249e4e454f1` |
| [Dovra-1.2.0-component-source-build-licence-candidate.zip](https://github.com/dovra-dev/DovraBrowser/releases/download/v1.2.0/Dovra-1.2.0-component-source-build-licence-candidate.zip) | 628091 | `73cf40896ae81887d9e43a3935f412eec5d8acfa4f15316364ef56d9bb99f170` |
| [Dovra-1.2.0-generated-headers.zip](https://github.com/dovra-dev/DovraBrowser/releases/download/v1.2.0/Dovra-1.2.0-generated-headers.zip) | 4915492 | `99390a70ed13e952d1d9823bb1ca1d30b1091fb80b05e2cd82c2040cbcc40199` |
| [Dovra-1.2.0-ffmpeg-build-provider-controls.zip](https://github.com/dovra-dev/DovraBrowser/releases/download/v1.2.0/Dovra-1.2.0-ffmpeg-build-provider-controls.zip) | 47534 | `5e6d292f6186f77f69690da09475aa819ac1c57235e77a26ded81c25236512e2` |
| [Dovra-1.2.0-ffmpeg-dependency-provider-index.zip](https://github.com/dovra-dev/DovraBrowser/releases/download/v1.2.0/Dovra-1.2.0-ffmpeg-dependency-provider-index.zip) | 40410 | `a91dfe345d7a5a81438e09649c3cc3cd90f6f76798b96e09cdb8100862f0d3e5` |

Concatenate the three numbered official-source parts in order to recover the upstream archive identified above. Extract relink parts 01 and 02, then apply updates source27, source28, source29 and source34 in that order. Use the accompanying component source/build/licence, generated-header and FFmpeg provider supplements. The combined source34 update supplies the current Blink plan overlay: place it adjacent to the original helper as blink-plan.json. Current public-helper validation completed 16 steps, including four compilation and two thin-archive commands; this is bounded reconstruction evidence, not a byte-for-byte browser reproduction claim.

The preservation record contains 240 source/resource entries: 173 native browser files, 57 official additions and 10 branding resources, with 33 code patches plus one resource overlay. That private preservation count does not identify a public source archive. Separately scoped Blink source, three interfaces and their licence texts, FFmpeg source/configuration and build controls, generated-header indices and relinking supplements retain their individual allowlists and licences. Private implementations are not included merely because a declaration is supplied. No silence-test patch or modified-library experiment is production browser source.

## Reconstruction and external prerequisites

The current source34 delivery layout passed full input validation and five native reconstruction commands. Both official final EXE operations and two targeted PCM cases passed in that material layout. Conservative input/search coverage does not prove selection of every archive member or byte-for-byte reproduction of the main browser. Official final executable processing and targeted decoding tests have separate receipts; their results do not replace final application-archive acceptance.

Use the matching portable recipes and explicit tool/provider identities. MSVC, Windows SDK and other external prerequisites remain subject to their own acquisition and licence terms and are not all redistributed. Do not overlay reconstruction materials onto an installed browser, an active source tree or a user profile. The original/modified relink variants and test libraries are not substitutes for the main browser pair in [manifest.md](manifest.md).

## Availability and licences

The asset links above identify the matching material set for this release. The Toolkit is a separate optional companion and is not part of this application ZIP. The earlier 1.1.0 materials issue remains separate.

Retain all applicable component notices and licence texts. The [Terms](https://dovra.dev/terms/) and [Privacy notice](https://dovra.dev/privacy/) were adopted on 17 October 2026. Scoped grants for interface declarations, tools or documentation do not relicense the entire browser or certify the complete delivery. Physical-input acceptance is not certified by these material records.

Publisher: DOVRA SOFTWARE LTD, company number 17493263. Contact: <dovra.dev@gmail.com>. Built on Chromium; not affiliated with or endorsed by Google.
