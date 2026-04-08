# Changelog

All notable changes to Unplugg are documented here.
Format follows [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

---

## [1.0.0] — 2026-04

### Added
- **Facebook**: Block Reels, Stories, suggested Videos, suggested Groups (sidebar)
- **Instagram**: Block Reels, Stories, sponsored content, suggested accounts
- **LinkedIn**: Block promoted content (ads), suggested posts
- **YouTube**: Block Shorts in feed and sidebar
- Per-platform master on/off toggle
- Daily time tracking per platform with yesterday comparison
- Midnight auto-reset of daily counters
- JSON data export
- French and English UI
- Consent screen on first install

### Decided not to implement

**Facebook — Block sponsored posts**
Facebook obfuscates the "Sponsored" label by rendering each letter in a separate `<span>` with a randomly generated CSS class, rotated on every platform deployment. Detection based on these classes breaks within days and produces false positives (hiding organic posts). This feature was removed to avoid degrading the feed experience.

**Facebook — Block Follow suggestions in feed**
Same root cause: the CSS class used on the Follow button inline in post headers is unstable. It also appears on organic posts from pages the user hasn't yet followed, making accurate targeting impossible without false positives.

---

*Older entries will appear here as the project evolves.*
