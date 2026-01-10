---
title: Home
layout: home
nav_order: 1
---

# Online Web Clock Docs

Welcome to the Online Web Clock docs!

[Get Started](/docs/installation){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }
[Docs GitHub](https://github.com/ikartehfox/web-clock-docs){: .btn .fs-5 .mb-4 .mb-md-0 }

## Quick Access

- 📷 [Gallery](/docs-gallery)
- 📖 [Features](/docs)
- 💡 [Troubleshooting](/troubleshooting)

## Latest Updates
See what's new for Online Web Clock:

### v1.8.2 - **Bountiful Update QF2 (24 December, 2025)**
#### 🔧 Changes
- Use `setSecondsVis()` function to simplify code in `time.ts`
  - I also hope this fixes an edge-case bug where the second colon isn't reenabled

Check out this update! ([GitHub](https://github.com/iKarTehFox/web-clock/releases/tag/v1.8.2))

### v1.8.1 - **Bountiful Update QF1 (18 December, 2025)**
#### 🔧 Changes
- Add missing `bsmodal.button.reset` and `toasts.importexport.backupreset` keys
- Clear `onlinewebclock-autoload-preference` localStorage key in multiple parts of `importExport.ts`
  - Also add boolean parameter to `importFromLS()` function to avoid displaying import toast in certain cases

Check out this update! ([GitHub](https://github.com/iKarTehFox/web-clock/releases/tag/v1.8.1))

### v1.8.0 - **Bountiful Update (18 December, 2025)**
#### 🆕 Additions
- Add new AMOLED menu theme
- Menu accordion now has new icons provided by Bootstrap Icons
- Add position label for weather container
  - This eases URL parameter creation for weather card positioning
- Add custom positioning for toasts
- Add new "Welcome" modal popup for new users
- Respect system reduced motion setting
  - Background color transition and timebar width animations are disabled when this setting is preferred
- Localize the new date format options
- Add new timezone floating windows
  - All settings are exportable to JSON settings exports
- Add ability to save settings to localStorage
- Add button to reset timezone to system default
- Preset filenames now have aliases
- Add automatic idle mouse cursor hiding

#### 🔧 Changes
- Consolidate clock interval to new main function
  - Time to next second is now constantly calculated rather than using a fixed interval
- Replace Iconify with Bootstrap Icons
- Finally fix weather card dragging logic
  - The weather container now uses the same logic as the Dev Console, fixing it inside the viewport
- Menu Theme now uses select element rather than radio buttons
- Exports now popup a new modal for custom filenames
- Weather card now properly displays night icons
- Replace Toastify with Bootstrap Toasts
- Background Color Mode now uses select element rather than radio buttons
- Fix offcanvas rounded corners and broken syntax
- Remove legacy time refresh functionality
- Add tooltip to modal timeout label
- Fullscreen toggle toast now only displays for 1 second
- Fix broken toast titles for weather section
- "Read the Docs" button renamed to "Documentation", now opens in new tab

Check out this update! ([GitHub](https://github.com/iKarTehFox/web-clock/releases/tag/v1.8.0))

<hr>

Found a mistake? [Open an issue](https://github.com/iKarTehFox/web-clock-docs/issues) or [make a pull request](https://github.com/iKarTehFox/web-clock-docs/pulls) instead!
