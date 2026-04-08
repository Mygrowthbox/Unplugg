# Contributing to Unplugg

Thank you for your interest in contributing. Unplugg is a small, focused open-source project and contributions of all kinds are welcome.

## Getting started

1. **Fork** this repository
2. **Clone** your fork locally
3. **Load the extension** in Chrome developer mode:
   - Go to `chrome://extensions`
   - Enable **Developer mode**
   - Click **Load unpacked** → select the `unplugg/` folder
4. Make your changes, reload the extension, and test on the relevant platform

## Types of contributions

### Translations

Add a new language by creating `_locales/<lang>/messages.json` following the structure of `_locales/en/messages.json`. Open a pull request with the new file.

### Bug reports

Open an issue and include:
- Which platform is affected (Facebook, Instagram, LinkedIn, YouTube)
- What you expected to happen
- What actually happened
- If relevant, a screenshot or the HTML snippet of the element not being blocked or incorrectly blocked

**Important for DOM-related bugs:** please include the relevant HTML of the element. Without the actual HTML, it is very difficult to reproduce issues since platforms change their DOM structure regularly.

### New detection signals

If you find a reliable DOM signal for a content type that isn't currently blocked, please open an issue before opening a PR to discuss whether it meets the stability criteria.

**A detection signal is acceptable if it:**
- Is based on a stable attribute (`data-pagelet`, `aria-label`, `role`, structural URL)
- Does not rely on CSS class names (they are obfuscated and change frequently)
- Does not produce false positives on organic content
- Works regardless of the user's interface language (or handles multiple languages explicitly)

**A detection signal is NOT acceptable if it:**
- Relies on CSS class names like `x1fey0fg`, `xlmi2g5`, etc.
- Reads the full text content of a post (risks false positives)
- Requires scanning `innerHTML` or parsing user-generated content
- Breaks organic posts when the platform updates

### UI improvements

The popup is built with vanilla HTML/CSS/JS — no build step required. Feel free to improve the stats display, settings layout, or accessibility.

## Code style

- Vanilla JavaScript only — no frameworks, no build tools
- Each content script is self-contained and uses an IIFE guard (`if (window.__unpluggXxInitialized) return`)
- Comments in English
- `'use strict'` at the top of every script

## Pull request checklist

- [ ] Tested on the relevant platform (live website)
- [ ] No new permissions added without justification
- [ ] No CSS class-based detection
- [ ] No data sent to external servers
- [ ] English comments and commit messages

## Questions

Open an issue and tag it with `question`.
