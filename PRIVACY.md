# Dovra Privacy Notice

Document adopted: 17 October 2026. Applies to Dovra 1.2.0 for Windows x64, based on Chromium 155.0.8059.85. This notice accompanies that release; earlier packages retain their own notices.

## Responsible company and contact

DOVRA SOFTWARE LTD is the operator of Dovra and dovra.dev, and the controller of personal information it receives for website delivery and correspondence. It is a private company limited by shares registered in England and Wales, company number 17493263, registered office 128 City Road, London, EC1V 2NX, United Kingdom. Contact [legal@dovra.dev](mailto:legal@dovra.dev). If that address fails, use [dovra.dev@gmail.com](mailto:dovra.dev@gmail.com). Our legal and company-administration function handles privacy requests; this description does not claim a statutory DPO appointment.

## Your browser and local records

Profiles can retain history, cookies, site storage, cache, settings, download records and saved credentials. Downloads can be outside the profile. The supplied launcher uses `%LOCALAPPDATA%/Dovra/BrowserData` by default; a user-data-dir override or another launch method can use another location. Local records are not, merely by existing on your device, records provided to the Company.

Use browser controls to manage browsing data. Close the browser and identify the correct profile before deleting a complete profile. Deleting application files does not necessarily delete profiles, downloads, backups or automation output. We do not promise that every local record is encrypted or safe to share.

## Agent control and connected software

The browser portable archive does not include a companion automation toolkit. A separately supplied toolkit has its own documentation and licence. Automation software you connect can access pages, create screenshots, downloads, logs or archives, and send information to its own model or other services. Review the software and provider you choose. A local connection is not a guarantee of local-only processing.

The native control interface can expose control state, page identifiers, dialog text and responses, download paths and results to an authorized connected agent. Choosing human control revokes that agent's write authority; permitted state observation can remain available. Returning control requires a new authorization. This control change does not erase information an agent already received or stop independent services processing it. Downloading or saving a file creates a local file and does not by itself send its contents to the Company. Do not expose control or debugging interfaces to untrusted users or networks.

## Network requests and security limitations

Websites receive request information such as your IP address, URL, headers, submitted information and existing site identifiers. DNS, network, proxy and extension providers have their own roles. Browser configuration does not guarantee anonymity or compatibility with every service.

This build disables browser-level GAIA account coordination and GCM/FCM background messaging by default. That can make browser-account integration and related Web Push unavailable. This does not remove existing website sessions or prohibit normal website sign-in traffic. Automatic component checking and program-triggered updates are disabled. An explicit user request from `chrome://components` is an exception; support and successful updates vary by component. Installed security data can become out of date. Do not assume that visiting that page updates it or that a supported update succeeds.

Google Safe Browsing is disabled; do not rely on remote Safe Browsing phishing or malware checks. TLS/certificate validation and component signature/hash checks remain part of the browser. Certificate processing can request missing issuer certificates, and user-requested component updates can contact download servers. The built-in desktop new-tab page is local by default; policies, extensions, startup pages, navigation and searches can contact remote services. These are configuration descriptions, not a claim that every network path has been tested or that security data is current.

No zero-network, zero-telemetry or zero-storage guarantee is made. No automatic Dovra browser-update service is promised. Use supported replacement releases and review their notices. Avoid sending private profiles, passwords or tokens as diagnostics.

## Website, downloads and public reports

The project site is [dovra.dev](https://dovra.dev/). Cloudflare delivers and protects it and the `dl.dovra.dev` download service. Requests involve connection/request data, including IP addresses, URLs, browser information and times. Delivery, security and operational monitoring can produce service records. This notice does not assert that all provider logs or optional measurement are absent, or promise a provider-wide retention period. See [Cloudflare's privacy policy](https://www.cloudflare.com/privacypolicy/).

When you follow a source/relinking-material or issue link to GitHub, GitHub receives your request information under its [privacy statement](https://docs.github.com/en/site-policy/privacy-policies/github-general-privacy-statement). Public issues and comments can be visible to others. Use private correspondence for information that should not be public. Third-party websites you browse using Dovra have their own notices; the Company does not control them.

## Correspondence, purposes and legal bases

If you email us, we receive your address, message and information you choose to include. Email uses Cloudflare routing and Gmail; [Google's privacy policy](https://policies.google.com/privacy) describes Google's processing. Send a redacted description or small reproduction instead of a full profile, identity document, credential or another person's private information.

Where UK data-protection law applies, we rely on legitimate interests for proportionate website/download delivery and security, answering inquiries, investigating defects and managing records of a matter. Those interests are maintaining a usable, secure distribution service and responding to people who contact us. We limit information to what those purposes need and consider effects on individuals. We use the legal-obligation basis when processing is necessary for a specific applicable obligation, such as responding to a statutory privacy request. This notice does not authorize unrelated marketing or make legitimate interests a substitute for consent where consent is required.

Providing correspondence is voluntary. Without enough information to identify a problem or verify a request, we may be unable to resolve it. Access is limited to people and service providers needed for the matter. We may disclose necessary records to authorities when lawfully required or for the establishment, exercise or defence of legal claims. We do not ask you to supply sensitive personal information for routine support.

We retain correspondence while needed to resolve and document the matter, for necessary follow-up, or for a specific legal obligation or claim. We review records when a matter closes and delete or de-identify unnecessary information. Provider backups and security records can have different handling; deletion is not a promise of immediate removal from all backups.

## International processing

Cloudflare, Google, GitHub and their service providers operate internationally, including in the United States. Company administration from Singapore can involve authorized access there. Applicable protections depend on the provider, the processing role and the transfer. Cloudflare publishes a [data-processing addendum](https://www.cloudflare.com/cloudflare-customer-dpa/) containing contractual transfer mechanisms, including EU standard contractual clauses with the UK Addendum where applicable. The provider links describe their own arrangements; they are not a claim that every service or transfer has the same protection. Ask the privacy contact for information about safeguards applicable to information under the Company's control and how to obtain a copy.

## Your rights

Depending on applicable law and the processing involved, you can request access, correction, deletion, restriction or portability of information under our control. **You can object to processing based on legitimate interests, on grounds relating to your particular situation.** Contact the privacy address above; we will consider the request under applicable law and explain any lawful reason for retaining information or refusing a request. We may need proportionate information to locate a record and verify identity. Where processing relies on consent, you can withdraw it without affecting earlier lawful processing.

You can complain to the [UK Information Commissioner's Office](https://ico.org.uk/make-a-complaint/) or another competent regulator. You do not have to contact us first. Rights over information controlled by a website or tool provider may need to be exercised with that provider. We update this notice if our relevant practices change; a new notice does not retroactively change an open-source licence.
