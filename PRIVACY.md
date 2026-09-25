# Dovra Beta — Privacy Notice

Document date: 25 September 2026. Beta build: `beta-20260925-4`. This notice covers the Windows x64 Beta, a separately provided toolkit where identified, the project website and correspondence. It does not certify every third-party website or automation service.

## Who is responsible

The responsible operator is the individual maintainer using the GitHub identity [dovra-dev](https://github.com/dovra-dev), who operates the project website and support mailbox. Dovra is a project name, not an incorporated company. Contact the maintainer about privacy at dovra.dev@gmail.com.

## Browser data on your device

A browser profile can retain cookies, site storage, browsing history, cache, settings, download records and credentials you choose to save. Downloads may be stored separately. These local records are not, by their existence alone, information supplied to the Dovra operator. Websites can write data into your profile and read data they are permitted to access.

The default `dovra_browser.exe` launcher uses `%LOCALAPPDATA%/Dovra/Beta/BrowserData` for browser data unless you provide an explicit `--user-data-dir=...` argument. It stores no other record and sends nothing to the Publisher.

When separately using the Dovra toolkit launch script, each profile ID selects a directory under `<toolkit workspace>/_logs/dovra-profiles/`; reusing the same profile ID is intended to reuse its data. The script also records a local session pointer under `<toolkit workspace>/_logs/dovra-session.json`. Launching the executable another way can select a different profile directory. Check the active profile path before managing its files.

Use the browser's data controls for browsing data. Before deleting a complete profile, close the browser and identify the exact profile you intend to remove; deleting the application is not the same operation. Backups and downloaded files may remain elsewhere. Do not share a profile as a routine diagnostic attachment: it can contain private information and signed-in sessions. We do not promise that every record is encrypted, portable or safe to share.

The toolkit normally requests a graceful close. If closure cannot be confirmed, it preserves the session record and profile. Explicit forced termination can lose unsaved data. Closing a session does not itself delete the profile.

## Local toolkit output and connected tools

The portable browser archive does not itself include the optional toolkit. The following practices apply when you separately obtain and use the toolkit supplied for this Beta.

The toolkit can read page content and create screenshots or other task output. `read --md` archives the page URL, a page snapshot, before/after text and processing metadata under `<toolkit workspace>/_logs/dovra-runs/` by default. `--no-archive` disables that read archive; it does not disable separate screenshots, output files or records created by your own automation software. Screenshot and failed-task output may be saved under `_logs/dovra-tasks/` or a path you choose. Keep or delete these records according to the needs and permissions of your task.

The public toolkit supplied for this Beta excludes the optional model-based page-cleaning adapter. Its `read --llm` option is rejected before a browser connection is made. This does not control integrations in other tools you install or connect.

You may connect other automation software to the local browser. Such software can read page content and may send it to its own services. A local browser connection does not mean that the connected tool processes everything locally. Review its permissions and provider terms before exposing sensitive pages. Do not expose the browser's debugging connection to untrusted users or networks.

## Browsing and background connections

Websites receive information needed for requests, which can include your IP address, requested URL, browser headers, submitted information and existing site identifiers. Your network, DNS or proxy provider may also process traffic. Extensions and optional services have their own practices.

This Beta disables the Windows Chromium Crashpad initialisation path, remote experiment-seed fetching, Chromium network-time fetching, domain-reliability reporting, and the component and extension automatic-update request paths covered by these changes. Local experiment settings, component records and browser metrics code can still exist. These changes do not disable Windows' own reporting or every possible connection, and the browser does not provide a Dovra automatic-update service. Check the download page for replacement builds and their security status.

Secure DNS starts off in this Beta; normal system DNS and proxy discovery remain possible. Certificate validation remains present and can fetch missing issuer certificates from certificate-provided addresses when needed. Websites, a proxy auto-configuration service, extensions you install and other software on your computer can make their own requests. The bundled component data is not a promise of automatic future updates. Google Safe Browsing is disabled in this Beta; do not rely on it for remote phishing or malware checks.

Configurable browser parameters do not make you anonymous or prevent every request. This notice does not promise zero network activity.

## The project website and downloads

The project website is https://dovra.dev/. Its static application code contains no advertising, analytics script, account-registration form or contact form, and no project-operated application backend. The region example changes the current page and does not store its selections in cookies or local storage. Reloading resets that example. It does not connect to a browser profile or read your physical location.

Cloudflare hosts and protects the website. Serving and protecting requests involves processing connection and request information, such as an IP address, URL, browser information and request time. Provider security features can operate separately from the static page code. At the configuration check for this Beta, Workers Logs and Workers Traces were disabled, Logpush was off and no tail consumer was configured. The site's Web Analytics ruleset was disabled; its automatic-install setting existed, so this is not a claim that a beacon was never configured. These settings do not eliminate Cloudflare's service, delivery or security processing. No provider-wide retention period is promised here. We will review the notice if the site's data collection settings change. See [Cloudflare's privacy policy](https://www.cloudflare.com/privacypolicy/) for its own processing.

If you follow a link to a download hosted by GitHub, GitHub processes the download request under its own practices. Any issue or comment you choose to post publicly can be visible to others. Use private correspondence for information that should not appear in a public issue. See [GitHub's privacy statement](https://docs.github.com/en/site-policy/privacy-policies/github-general-privacy-statement).

## Email and privacy requests

Email to dovra.dev@gmail.com is received through Gmail. Support accepts information you actively send, such as your email address and a redacted description or small reproduction of a problem. We use the information needed to respond, resolve and document the issue, and meet applicable legal obligations. We do not request full browser profiles or credentials for routine support. An email link opens your mail application; it does not send a message automatically.

Send only the information needed. Do not send passwords, access tokens, full profiles, identity documents or other people's private information in ordinary support messages. Prefer a small, redacted reproduction of an issue.

We retain only correspondence needed to resolve and document the issue or meet a specific legal obligation. We review it when a matter is resolved and delete or de-identify material no longer needed, subject to necessary follow-up, legal preservation and provider backup handling. This notice does not promise immediate removal from a provider's backups. No fixed number of retention days is promised.

Cloudflare, Google and a chosen distribution provider may process data in countries other than your own. Their policies describe their processing; a policy link does not itself establish the operator's legal basis or transfer arrangements. The operator remains responsible for arrangements applicable to data under its control. See [Google's privacy policy](https://policies.google.com/privacy).

Contact dovra.dev@gmail.com to request access, correction or deletion of correspondence, or to raise another applicable privacy right. We may request proportionate information needed to locate a record and establish that a request is yours. We will explain a lawful reason for refusing or retaining information where one applies. Depending on applicable law, you may have additional rights or a right to complain to the relevant regulator. The rights available to you depend on applicable law.

## Changes

Changes to this notice will be identified with their effective date. We will update it when the operator, relevant features or handling practices change.
