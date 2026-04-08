# Security Policy

## Supported versions

Only the latest release of Unplugg receives security updates.

| Version | Supported |
|---|---|
| 1.0.x | ✅ Yes |

## Reporting a vulnerability

If you discover a security issue, please **do not open a public GitHub issue**.

Instead, open a [GitHub Security Advisory](https://github.com/YOUR_USERNAME/unplugg/security/advisories/new) (private disclosure).

We will acknowledge your report within 72 hours and aim to release a fix within 14 days for confirmed vulnerabilities.

## Scope

Relevant security concerns for this project include:

- Any mechanism that could cause Unplugg to read or leak private user data (messages, credentials, personal information)
- Any mechanism that could allow a third-party website to execute arbitrary code through the extension
- Any permission escalation beyond what is declared in `manifest.json`

Out of scope:

- Issues requiring physical access to the user's device
- Social engineering attacks
- Issues in browser internals or third-party platforms
