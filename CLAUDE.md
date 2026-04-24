# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is Grant Heimer's personal website (grantheimer.com). The entire site is a **single `index.html` file** with all CSS and JavaScript embedded — no build system, no package manager, no external dependencies (except Google Fonts). Deployed on Vercel; `vercel.json` rewrites `/timeline` to `index.html`.

## Development

Open `index.html` directly in a browser to preview. No build step required.

Run tests by opening `timeline-tests.html` in a browser — it loads `index.html` in a hidden iframe and tests the timeline's core JS functions.

Deploy: push to `main` on GitHub; Vercel auto-deploys in ~30 seconds.

## Architecture

The site has two views rendered inside a single HTML page, toggled via JS (no routing library):

- **Home page** (`#homePage`) — clean white minimal bio. Shown by default at `/`.
- **Timeline page** (`#timelinePage`) — dark navy animated timeline. Shown at `/timeline`.

`showHome()` / `showTimeline()` swap CSS classes and use `history.pushState` for URL updates.

### Timeline layout

The timeline is built entirely in JavaScript via `buildTimeline()`, which injects HTML into `#timelineContainer`. Layout uses **CSS `position: sticky`** nodes inside **absolutely positioned `.entry-lane` divs**:

- Cities column (left) — green nodes
- Education column (center, on the strand) — burnt orange nodes  
- Work column (right) — cyan nodes

Key layout constants in the `<script>` block:

| Constant | Value | Effect |
|---|---|---|
| `YEAR_HEIGHT` | 800px | Pixels per year; controls total timeline length |
| `SLOT_HEIGHT` | 220px | Minimum lane height; controls spacing between bumped nodes |
| `START_YEAR` / `END_YEAR` | 2009 / 2026 | Year range rendered |

Column offsets (desktop: 90px, mobile: 65px, small mobile: 63px) are the half-node-width + gap. These appear in both CSS and must stay in sync if node sizes change.

### Adding or editing timeline entries

All content lives in the `timelineData` object near the top of the `<script>` block. Each entry has: `title`, `shortTitle`, `icon`, `start` (e.g. `"August 2022"`), `end` (`"Present"` or `"Month Year"`), and `description`.

### CSS custom properties

Colors are defined in `:root` at the top of the `<style>` block: `--navy-bg`, `--cyan`, `--orange`, `--burnt-orange`, `--teal`, `--green`, `--white`, `--gray`. Use these variables rather than hardcoding hex values.

### Responsive breakpoints

- `≤768px` — mobile: node circles shrink to 110px, column offsets adjust to 65px
- `≤400px` — small phone: circles set to 115px (larger than mid-mobile to prevent text cutoff), offsets 63px
