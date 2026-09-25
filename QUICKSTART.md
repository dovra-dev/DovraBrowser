# Dovra Beta — Quick start

Batch `beta-20260925-4` · Windows x64 · English interface.

## Verify and open

1. Download the browser ZIP and `SHA256SUMS.txt` from the project download server: `https://dl.dovra.dev/beta-20260925-4/Dovra-Beta-20260925-4-win-x64.zip` and `https://dl.dovra.dev/beta-20260925-4/SHA256SUMS.txt`. The [Beta release page](https://github.com/dovra-dev/dovra/releases/tag/beta-20260925-4) lists the same links; this batch has no attachments on GitHub.
2. Compare the ZIP with the checksum, for example `Get-FileHash .\Dovra-Beta-20260925-4-win-x64.zip -Algorithm SHA256` in PowerShell. A checksum checks file identity; it is not a trusted publisher signature.
3. Extract the entire archive into a normal local folder. Do not run the launcher from the ZIP viewer or separate it from `bin/` and `legal/`.
4. Open `dovra_browser.exe`. It starts the browser in English with the default local profile and shows no dialog; `bin\chrome.exe` can also be started directly. The project terms and privacy notice are in `legal/` and `bin/` for review.

The launcher is a small .NET Framework 4.x program that only starts `bin\chrome.exe` with default arguments. This Beta has been tested on Windows Server 2022 x64, OS build 20348.5139; NVIDIA GeForce GTX 650 / ANGLE Direct3D 11; other configurations are not claimed to be verified. No paid certificate or trusted-publisher reputation is claimed. Review the release's signing status; do not disable Windows security settings to install this Beta.

## Profiles and updates

The normal launcher uses `%LOCALAPPDATA%\Dovra\Beta\BrowserData`. It writes no other record and uploads nothing. Browser data, downloaded files and other programs' output have their own locations.

For a separate test profile, pass an explicit path:

```powershell
.\dovra_browser.exe "--user-data-dir=C:\Dovra-Test\Profile"
```

Keep important browsing in a separate browser while evaluating the Beta. Before changing builds, close every process using the selected profile and make a backup you control. Extract a new build into a new program folder. Removing the program folder leaves the default profile above and other files stored outside that folder in place. If you chose a profile or download directory inside the program folder, copy it to a safe location first. There is no Dovra automatic-update service; check the release page for replacement builds and security information.

## Optional agent toolkit

Get the separately identified toolkit `Dovra-Toolkit-beta-20260925-4.zip` from the download server (`https://dl.dovra.dev/beta-20260925-4/Dovra-Toolkit-beta-20260925-4.zip`). Follow its README and toolkit guide for Node.js and `playwright-core` requirements. Point `DOVRA_EXE` to this package's `bin\chrome.exe`; point `DOVRA_HOME` to the extracted toolkit directory. The toolkit starts the selected browser directly; no acceptance step is involved.

Named toolkit profiles live under the toolkit workspace's `_logs\dovra-profiles\`. They are separate from the normal launcher profile above and would be removed if you deleted that toolkit directory. Back them up before replacing or removing the toolkit. Reusing a profile does not guarantee that a website will retain a login. Use the toolkit's normal close command and check its result before changing profile files.

CDP gives connected software control over the browser. Keep the debugging listener on your own machine and do not forward it to untrusted networks. Complete website login and verification through their normal processes. Follow website terms and use only permissions you actually hold.

## Help and component rights

Send the batch identifier and a short, redacted reproduction to dovra.dev@gmail.com. Do not send a full profile or credentials. Read the package notices and [SOURCE-MATERIALS.md](SOURCE-MATERIALS.md) for component licences and modifying/relinking the applicable components.
