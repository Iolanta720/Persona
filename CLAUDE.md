# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A single static HTML page (`index.html`) — a whimsical Russian-language "персона" (persona) bio card for a fictional character named Иоланта. There is no build system, no package manager, no server-side code, and no test suite. This is not a software project in the conventional sense; it's a self-contained web page plus its source content.

## Structure

- `index.html` — the entire site: inline `<style>` in the `<head>` (CSS custom properties defined on `:root` around line 9: `--accent`, `--ink`, `--paper`, `--dark`, `--muted`, etc.) followed by the page markup in `<body>`. Background/section images are embedded directly as base64 data URIs inside the HTML (not referenced via `<img src="images/...">`), which is why the file is ~1.8MB despite being conceptually simple. Sections in document order: `.hero` (header/tagline) → `#about` → `#work` → `#facts` → `.finale` → `<footer>` (image credits).
- `images/` — the *source* JPEGs that were base64-encoded into `index.html`, plus `CREDITS.md` documenting license/attribution for each (all sourced from Wikimedia Commons, mix of CC0/public-domain and CC BY-SA — attribution must be preserved per the license terms noted in `CREDITS.md`).
- `про-меня.md`, `проекты.md`, `факты.md` — the Russian-language source content (bio, projects, fun facts) that `index.html`'s `#about`, `#work`, and `#facts` sections are derived from. These read as the "content draft"; `index.html` is the "published" rendering of the same material, reworded/condensed for the page.

## Working in this repo

- There is no git repository initialized here (`git init` would be needed before any version control operations).
- There is no build/lint/test command — changes are made directly to `index.html` (and mirrored in the corresponding `.md` source file if the underlying content changes) and verified by opening the file in a browser.
- When editing content, keep `index.html` and the matching `.md` file (про-меня.md / проекты.md / факты.md) in sync — the markdown files appear to be the editable source of truth for prose, while `index.html` holds the styled/HTML-escaped version.
- When adding or replacing an image, update `images/CREDITS.md` with the source, author, and license, and re-embed it as a base64 data URI in `index.html` (do not link to `images/*.jpg` by path — the existing pattern embeds images inline).
- All content is in Russian; keep tone consistent with the existing self-ironic, whimsical voice when editing.
