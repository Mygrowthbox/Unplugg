# Privacy Policy — Unplugg

**Last updated:** April 2026

## Summary

Unplugg does not collect, transmit, or share any personal data. Everything stays on your device.

## What Unplugg reads

To detect and hide algorithmic content, Unplugg reads **interface labels only** — specifically structural DOM attributes (`data-pagelet`, `aria-label`, `role`) and link URLs (e.g. `/reels/`) on the following websites:

- `facebook.com`
- `instagram.com`
- `linkedin.com`
- `youtube.com`

**Unplugg does NOT read:**
- Your private or direct messages
- Posts, comments, or content you write
- Your profile, connections, or social graph
- Any personal or behavioral data
- Cookies or authentication tokens

## Data storage

The only data stored by Unplugg is:

| Data | Purpose | Location |
|---|---|---|
| Time spent per platform (in seconds) | Display daily usage stats | `chrome.storage.local` on your device |
| Your toggle preferences | Remember which content types to block | `chrome.storage.local` on your device |
| Consent flag | Know that you've seen the onboarding | `chrome.storage.local` on your device |

This data:
- **Never leaves your device**
- **Is not shared with any third party**
- **Is automatically deleted when you uninstall the extension**
- Can be exported at any time as JSON from the extension popup

## Third parties

Unplugg sends **zero data** to any external server. There are no analytics, no tracking pixels, no remote logging, no telemetry of any kind.

The extension makes **no network requests** other than the Chrome APIs it uses locally.

## Permissions justification

| Permission | Justification |
|---|---|
| `storage` | Required to save your preferences and time data locally |
| `tabs` | Required to send settings update messages to open social media tabs when you change a preference |
| `alarms` | Required to reset daily time counters at midnight |

Host permissions are strictly limited to the four domains listed above.

## Data retention

Daily time data is retained for **30 days** on your device. Data older than 30 days is automatically purged. You can also export or clear your data manually from the extension popup.

## Changes to this policy

If this policy changes in a future version, the "Last updated" date at the top will be updated. Significant changes will be noted in the GitHub release notes.

## Contact

For any questions or concerns, open an issue at:
[https://github.com/YOUR_USERNAME/unplugg/issues](https://github.com/YOUR_USERNAME/unplugg/issues)
