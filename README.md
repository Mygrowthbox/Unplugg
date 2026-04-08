# Unplugg

> Reclaim your attention. Block algorithmic content on social media and track your screen time.

Unplugg is a free, open-source Chrome extension that hides algorithmic distractions on Facebook, Instagram, LinkedIn, and YouTube — without touching your personal data.

---

## Features

Unplugg lets you selectively block content types per platform. Each platform has a master on/off toggle.

### Facebook
| Feature | Status |
|---|---|
| Block Reels | ✅ Active |
| Block Stories (top bar) | ✅ Active |
| Block suggested Videos | ✅ Active |
| Block suggested Groups (sidebar) | ✅ Active |
| Block sponsored posts | ❌ Removed — Facebook obfuscates the "Sponsored" label with randomized CSS classes that change on every deploy. Reliable detection without false positives is not possible. |
| Block Follow suggestions (feed) | ❌ Removed — Same reason: CSS class instability causes false positives on organic posts. |

### Instagram
| Feature | Status |
|---|---|
| Block Reels | ✅ Active |
| Block Stories (top bar) | ✅ Active |
| Block sponsored content | ✅ Active |
| Block suggested accounts | ✅ Active |

### LinkedIn
| Feature | Status |
|---|---|
| Block promoted content (ads) | ✅ Active |
| Block suggested posts | ✅ Active |

### YouTube
| Feature | Status |
|---|---|
| Block Shorts (feed) | ✅ Active |
| Block Shorts (sidebar) | ✅ Active |

### Time tracking
- Tracks time spent on each platform daily
- Shows today's usage vs. yesterday
- Auto-resets at midnight
- Export data as JSON
- All data stays on your device — never transmitted

---

## How it works

Unplugg injects content scripts on the four supported domains. Each script uses **stable, semantic DOM signals** to identify and hide content:

- `data-pagelet` attributes (Facebook's internal rendering system — stable across deploys)
- `[role]` ARIA attributes
- Structural URL patterns (e.g. `/reels/`)

**What Unplugg does NOT do:**
- Read your messages, posts, or personal data
- Use CSS class heuristics that break with every platform deploy
- Send any data to external servers
- Inject ads or affiliate links

---

## Installation

### From the Chrome Web Store
*(Coming soon)*

### Manual installation (developer mode)

1. Clone or download this repository
2. Open Chrome → `chrome://extensions`
3. Enable **Developer mode** (top right)
4. Click **Load unpacked**
5. Select the `unplugg/` folder

---

## Project structure

```
unplugg/
├── manifest.json                  # Extension manifest (MV3)
├── privacy-policy.md              # Privacy policy
├── icons/                         # Icons (16, 32, 48, 128px)
├── _locales/
│   ├── en/messages.json           # English strings
│   └── fr/messages.json           # French strings
├── popup/
│   ├── popup.html                 # Settings & stats UI
│   ├── popup.css                  # Styles
│   └── popup.js                   # UI logic, settings persistence
├── background/
│   └── service-worker.js          # Time tracking, badge, midnight reset
└── content/
    ├── shared/
    │   └── activity-tracker.js    # Sends activity pings to service worker
    ├── fb-blocker.js              # Facebook content script
    ├── ig-blocker.js              # Instagram content script
    ├── li-blocker.js              # LinkedIn content script
    └── yt-blocker.js              # YouTube content script
```

---

## Privacy

Unplugg collects **zero personal data**. See [PRIVACY.md](PRIVACY.md) for the full policy.

**Permissions used:**
| Permission | Why |
|---|---|
| `storage` | Save preferences and time data locally on your device |
| `tabs` | Broadcast settings changes to open platform tabs |
| `alarms` | Reset daily counters at midnight |

**Host permissions:** strictly limited to `facebook.com`, `instagram.com`, `linkedin.com`, `youtube.com`.

---

## Contributing

Contributions are welcome. Please read [CONTRIBUTING.md](CONTRIBUTING.md) before submitting a pull request.

**Good first issues:**
- Adding new language translations in `_locales/`
- Improving LinkedIn/Instagram detection with new real HTML examples
- Improving the time tracking UI
- Writing automated tests

**Important:** all detection logic must be based on stable, semantic signals (ARIA attributes, `data-pagelet`, `data-*` attributes, structural URLs). CSS class-based detection is explicitly discouraged — classes are obfuscated and rotated by platforms.

---

## Why some features were removed

Facebook aggressively obfuscates its DOM to prevent third-party tools from reading it. The "Sponsored" label is rendered with **one `<span>` per letter**, each assigned a randomly generated CSS class that changes on every platform deployment. Any detection relying on these classes breaks within days and produces false positives — hiding organic posts from accounts you actually follow.

Rather than ship unreliable features, Unplugg only includes detection methods that remain consistent without degrading the user experience.

---

## License

MIT — see [LICENSE](LICENSE).

---

## Roadmap

- [ ] Chrome Web Store listing
- [ ] Weekly and monthly time stats
- [ ] Pause mode (disable Unplugg for N minutes)
- [ ] Per-platform time limit alerts
- [ ] Firefox support
