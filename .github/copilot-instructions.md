# Copilot Instructions for EngLabs

## Build, test, and lint commands
- No build, test, or lint tooling is currently configured in this repository (no package/lockfile, test runner config, or lint config present).

## High-level architecture
- This repository currently centers on a single static page: `privacy.html`.
- `privacy.html` contains **all** UI layers inline:
  - Content markup for both languages
  - Design tokens and component styles in one `<style>` block
  - Behavior in one `<script>` block
- Localization is implemented by duplicating content into `.en` and `.vi` blocks, then toggling visibility with `body.lang-en` / `body.lang-vi`.
- Language switching is driven by `setLang(lang)` in the inline script and wired to `#btn-en` / `#btn-vi`.
- The only referenced asset is `images/icon.png` (header app icon).

## Key conventions for changes
- When editing policy content, keep English and Vietnamese sections in sync by updating both corresponding blocks.
- Preserve the language-toggle contract:
  - Body classes: `lang-en` and `lang-vi`
  - Toggle button IDs: `btn-en` and `btn-vi`
  - `setLang(lang)` updates body class, button active state, and `<html lang>`.
- Reuse existing CSS variables in `:root` (`--bg`, `--surface`, `--purple`, etc.) instead of hardcoding new colors.
- Keep visual structure based on existing reusable classes (`.section`, `.section-title`, `.perm-grid`, `.tp-item`, `.contact-box`) rather than one-off inline styles.
- Maintain current typography stack loaded from Google Fonts (`Syne` for headings, `Nunito Sans` for body text) unless a deliberate design change is requested.
