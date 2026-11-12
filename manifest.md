# Dovra 1.3.0 file identity

Windows x64; Chromium 158.0.8127.18, upstream revision `6449d9f9a6a906edff724b7b220199b3fde4615c`.

| Archive member | Bytes | SHA-256 |
| --- | ---: | --- |
| `bin/chrome.exe` | 2819072 | `319501c13095a34eec8efb0f1a429e523fd5430d49c32630704174aaf3f8b89d` |
| `bin/chrome.dll` | 320041472 | `b83916751960aeb0d0cb12330d86d8bb3099aeb658393c08e679e08782384e37` |

The archive contains 41 runtime files, five root documents, two browser-directory documents, two legal documents with their browser-directory copies, and the launcher: 53 members. The final ZIP checksum is distributed with the release and is not printed here, to avoid a self-referential archive hash. These hashes identify files and are not a signing certificate.

This is the 1.3.0 production pair on the 158 engine. It is not interchangeable with any other Dovra package. The 1.2.0 package (published on 22 October 2026 and withdrawn on 25 October 2026) carried a different binary, and two of its runtime files are absent here: the Privacy Sandbox attestations preload, which the 158 engine no longer produces for Windows.

See [SOURCE-MATERIALS.md](SOURCE-MATERIALS.md) for matching materials and [RELEASE-NOTES.md](RELEASE-NOTES.md) for bounded validation. The [Terms](https://dovra.dev/terms/) and [Privacy notice](https://dovra.dev/privacy/) were adopted on 17 October 2026.
