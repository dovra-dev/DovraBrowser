# Dovra Beta — Source and relinking materials

Batch `beta-20260923` · Windows x64 · Chromium engine `153.0.8010.48`.

The browser statically links FFmpeg-derived software under LGPL 2.1 or later, together with separately licensed portions. The component licence, copyright and source-file notices remain applicable. Dovra-specific terms do not prohibit modification for your own use or reverse engineering to debug those modifications. The separate Microsoft runtime terms do not restrict these FFmpeg rights or access to the materials below.

## Get the matching materials

All files below accompany the browser on the project download server (`https://dl.dovra.dev/beta-20260923/`), and the [Beta release page](https://github.com/dovra-dev/dovra/releases/tag/beta-20260923) links to them. They are available without accepting the Microsoft runtime terms or requesting individual access. Check the archive names and SHA-256 values; a different build's link inputs may not be compatible.

| Asset | Bytes | SHA-256 |
| --- | ---: | --- |
| [dovra-beta-ffmpeg-source.tar.gz](https://dl.dovra.dev/beta-20260923/dovra-beta-ffmpeg-source.tar.gz) | 19982329 | `82b3bd4374c62b311b53fb6d98059225588319c9019df4646a3f1a26c1420679` |
| [dovra-beta-opus-source.tar.gz](https://dl.dovra.dev/beta-20260923/dovra-beta-opus-source.tar.gz) | 4365781 | `e779d2069a4bc2f4962ea834c910c6b33ba5db08a66ef1b60dc0a6dd797301c1` |
| [Dovra-Beta-rebuild-companion-beta-20260923.zip](https://dl.dovra.dev/beta-20260923/Dovra-Beta-rebuild-companion-beta-20260923.zip) | 966567 | `6f4ceb849259feb7344d1c8e7e240709fdd695c9bd83badabfb5297e75f91a6a` |
| [Dovra-Beta-relink-part-01.zip](https://dl.dovra.dev/beta-20260923/Dovra-Beta-relink-part-01.zip) | 478995161 | `6c4b58eec3bce725be53dda4210687f86c02736fdf51527d1ad847f34442f5da` |
| [Dovra-Beta-relink-part-02.zip](https://dl.dovra.dev/beta-20260923/Dovra-Beta-relink-part-02.zip) | 522449671 | `7e891d2c92a78a3944e2eae2e25eb6cfaad2310c14a8a4673122b6deac192329` |
| [Dovra-Beta-relink-part-03.zip](https://dl.dovra.dev/beta-20260923/Dovra-Beta-relink-part-03.zip) | 477738246 | `1f73cc9f29e37e821430f9f165e618ba869f86903aac8c8c90e04b48e48db6a9` |
| [Dovra-Beta-lgpl-blink-modifications-beta-20260923.zip](https://dl.dovra.dev/beta-20260923/Dovra-Beta-lgpl-blink-modifications-beta-20260923.zip) | 15763 | `ba4fe7bdcad2f9e449754c8bda9c489a1f777c477afe33f982422b067b23f900` |

Download **every** `Dovra-Beta-relink-part-*.zip` file and extract all parts into the same parent directory. Each is an independently extractable ZIP, not a byte segment to concatenate. They share the `Dovra-Beta-relink/` root and their members do not overlap. Keep the directory layout: thin archives reference objects outside the archive file itself. Extract the rebuild companion into a separate directory and follow its README. `Dovra-Beta-lgpl-blink-modifications-beta-20260923.zip` contains, as unified diffs against the unmodified upstream files, every modification made to the four LGPL-2.1 Blink source files of this build (`element.cc`, `range.cc`, `local_frame.cc`, `navigator.cc`); FFmpeg is covered by the archives above.

The FFmpeg archive contains the complete prepared 11,041-file source subtree, configuration, notices, transformations and reconstruction instructions. Its Chromium fork pin is `53fa34a23be9054d25ac2500dbdae9a0e570bb5c`. The Opus archive contains its complete 714-file prepared subtree and reproduction records at pin `55513e81d8f606bd75d0ff773d2144e5f2a732f5`.

These source archives retain the provenance of the earlier prepared source snapshot. Their source and configuration were checked against this engine update and retained unchanged; the application inputs and their manifest are specific to this `.48` build. The archives' original provenance files have not been relabelled as a different original download. A general upstream URL or patch alone is not a substitute for the supplied exact materials.

## Build and replace FFmpeg

The companion provides the recorded 286 C and 29 NASM compile actions and two FFmpeg thin-archive commands. The application kit supplies the corresponding original objects, dependencies, response files, a file manifest and `relink.py`. It is a component replacement and application relinking kit, not a claim to contain the entire Chromium development tree.

Use a separate working copy. Modify the applicable FFmpeg sources, rebuild affected translation units and archives, record the changed file hashes as described by the helper, and link to a new output directory. Copy the resulting `chrome.dll` into a separate copy of the matching original browser package and test it. The optional Dovra launcher does not enforce a publisher-only hash on `chrome.dll` or undo your replacement.

The required external tool versions and original tool identities are in the companion. Obtain the applicable Clang/LLD, NASM, Microsoft Visual C++ and Windows SDK tools lawfully from their distributors. Microsoft SDK/MSVC link libraries are referenced as installed prerequisites, not included in these archives. The recorded library candidate list is conservative and is not a trace proving every listed library was loaded. Follow the companion's path and environment instructions; do not flatten directories or substitute a similarly named but incompatible tool without reviewing the consequences.

Application ThinLTO remains enabled; the recorded `.48` configuration disables its disk cache. Linking a Chromium-sized application requires substantial memory and temporary disk space. Review the helper's plan before executing it, and preserve your original package and input kit.

## Exact browser pairing and verification

Application `input-manifest.json` SHA-256: `82b8fc8912458b4ddc52473f18ac71b55f6e4e6b1f4c868ae287d17dfd42997f`.

Original application response SHA-256: `ab35c6c0ef3f921125a179c70ca315a78d1364af67258694547f03ec9d27b7cb`.

| Original browser file | Bytes | SHA-256 |
| --- | ---: | --- |
| `bin/chrome.exe` | 3898368 | `e409e52a044d24c386980bcc392d2dd3e77142469f9455aa82ac98405e4093fd` |
| `bin/chrome.dll` | 333782528 | `e3b9a6e282c348f12cdde87ff58f5388fcdf608495691237ef29444bfb7a99df` |
| `bin/resources.pak` | 22788272 | `53ca0368ccd572c6fac52940e3d298c99a2280aaad3a754fc129819b63c5d0e2` |

The FFmpeg sources, objects, archives and compile commands of this batch are byte-identical to those of beta-20260916 (checked against the recorded identities before the kit was mapped); only the other application objects changed. The modified-library link below was performed on the beta-20260916 build of this engine and was not repeated for this batch: the modified FFmpeg library was linked into the `.48` application and the short FLAC sample played to completion in normal multiprocess mode with `SymphoniaAudioDecoding` disabled. In a separate `--single-process` diagnostic using the same decoder-selection flag, the original library produced 0 probe markers and the modified library produced 2. Only `chrome.dll` differed in the tested runtime copies. The diagnostic demonstrates this deliberate library change; it does not certify single-process sandboxing, default decoder selection, all codecs, arbitrary modifications or general legal compliance. Normal multiprocess stderr marker output was not required for success.

These identities bind the original browser files to the supplied inputs. The outer browser ZIP checksum is listed separately in `SHA256SUMS.txt`. A successful link or an embedded marker alone does not establish playback or compatibility with every possible FFmpeg modification.

## Licences

Read `bin/NOTICE`, `bin/NOTICE.RUNTIME.txt`, `bin/licenses/` and the notices in each source archive. The LGPL text is in `bin/licenses/LGPL-2.1.txt`. These files do not place every application object under a single licence or provide patent rights beyond any express applicable upstream grant. Only the auxiliary files expressly identified by their own licence use the included Dovra tools licence.

GitHub's automatic repository source ZIP/tarball is not the compiled browser, complete FFmpeg source archive or application relinking kit. Use the explicitly named release assets above.

For a missing or damaged material, contact dovra.dev@gmail.com with the batch, filename and a redacted description. Do not send credentials or a browser profile.
