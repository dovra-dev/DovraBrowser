# Dovra — Source and relinking materials

Version `1.1.0` · Windows x64 · Chromium engine `153.0.8010.48`.

The browser statically links FFmpeg-derived software under LGPL 2.1 or later, together with separately licensed portions. The component licence, copyright and source-file notices remain applicable. Dovra-specific terms do not prohibit modification for your own use or reverse engineering to debug those modifications.

## Get the matching materials

All files below accompany the browser on the project download server (`https://dl.dovra.dev/1.1.0/`), and the [release page](https://github.com/dovra-dev/DovraBrowser/releases/tag/v1.1.0) links to them. They are available without any acceptance step or individual access request. Check the archive names and SHA-256 values; a different build's link inputs may not be compatible.

| Asset | Bytes | SHA-256 |
| --- | ---: | --- |
| dovra-ffmpeg-source.tar.gz | 19982329 | `82b3bd4374c62b311b53fb6d98059225588319c9019df4646a3f1a26c1420679` |
| dovra-opus-source.tar.gz | 4365781 | `e779d2069a4bc2f4962ea834c910c6b33ba5db08a66ef1b60dc0a6dd797301c1` |
| Dovra-lgpl-blink-modifications-1.1.0.zip | 15764 | `ada6c88b014398efb082992c18ef0eb5a2eca883f8dcc44dda052faa790bbf5c` |
| Dovra-rebuild-companion-1.1.0.zip | 966570 | `4e2c6daf500f7f5588abb11a22f1cca9af07569ec7992fccde60ff9fe5a533bb` |

The FFmpeg archive contains the complete prepared source subtree, configuration, notices, transformations and reconstruction instructions. The Opus archive contains its complete prepared subtree and reproduction records. The LGPL Blink modifications archive contains, as unified diffs against the unmodified upstream files, every modification made to the LGPL-2.1 Blink source files of this build (`element.cc`, `range.cc`, `local_frame.cc`, `navigator.cc`); FFmpeg is covered by the archives above. The rebuild companion provides the recorded compile actions and FFmpeg thin-archive commands for rebuilding the modified FFmpeg library.

These source archives are byte-identical to those of the prior build of the same engine (the FFmpeg and Opus sources and configuration do not change with the application patches). A general upstream URL or patch alone is not a substitute for the supplied exact materials.

## Exact browser pairing and verification

| Original browser file | Bytes | SHA-256 |
| --- | ---: | --- |
| `bin/chrome.exe` | 3893248 | `fc5a245985c99c83960bbcf733c9ee2c91d97cb67bac84730730eafa215ca434` |
| `bin/chrome.dll` | 333719552 | `5996b639a4c364eeba7a967dedce53a9f405c628692122df8bb5895901f1092f` |
| `bin/resources.pak` | 22787876 | `081c25358279c047fe6b4104657a27d9ce811bb51946836e75c0d9555cd138ea` |

These identities bind the original browser files to the supplied inputs. The outer browser ZIP checksum is listed separately in `SHA256SUMS.txt`. A successful link or an embedded marker alone does not establish playback or compatibility with every possible FFmpeg modification.

## Licences

Read `bin/NOTICE`, `bin/licenses/` and the notices in each source archive. The LGPL text is in `bin/licenses/LGPL-2.1.txt`. These files do not place every application object under a single licence or provide patent rights beyond any express applicable upstream grant. Only the auxiliary files expressly identified by their own licence use the included Dovra tools licence.

GitHub's automatic repository source ZIP/tarball is not the compiled browser, complete FFmpeg source archive or application relinking kit. Use the explicitly named release assets above.

For a missing or damaged material, contact legal@dovra.dev with the version, filename and a redacted description. Do not send credentials or a browser profile.
