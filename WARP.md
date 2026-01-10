# WARP.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

## Development commands

### Local preview
- The site is a static HTML app; there is no build step.
- To preview locally, open `index.html` in a browser (for example on macOS: `open index.html`).
- Alternatively, run a simple static server from the repo root and visit `http://localhost:8000`:
  - `python3 -m http.server 8000`

### Timeline tests
- Browser-based tests live in `timeline-tests.html` and exercise the real app loaded via a hidden iframe.
- To run the full test suite, open `timeline-tests.html` in a browser (for example: `open timeline-tests.html`). The page will display a pass/fail summary and per-test results.
- There is no CLI test runner and no built-in way to run a single test; to focus on one test, temporarily edit the `tests` array in `timeline-tests.html` so it contains only the desired test.

### Deployment expectations
- The project plan in `grantheimer.com Claude Plan.md` assumes static hosting on a platform like Vercel, with the repo deployed as-is (no bundling or build tooling).
- Any new tooling or build steps should preserve the ability to host the site as a static export.

## Code architecture and structure

### Overall layout
- This repo is intentionally minimal and consists primarily of two HTML files:
  - `index.html` – the main site, containing all CSS and JavaScript inline.
  - `timeline-tests.html` – a self-contained browser test harness for the timeline logic in `index.html`.
- There are no external JavaScript or CSS dependencies; the stack is “single HTML file with embedded CSS and JavaScript” as described in `grantheimer.com Claude Plan.md`.

### `index.html`: pages, layout, and navigation
- The page defines a CSS custom-properties palette (`:root`) and a substantial inline stylesheet implementing:
  - A light "Home" view (`.home-page`) with simple text sections and social icons.
  - A dark, animated "Timeline" view (`.timeline-page`) with a parallax background (`.bg-gradient`), a sticky nav (`.timeline-nav`), and a vertical timeline section.
- Two views are toggled purely on the client using `showHome()` and `showTimeline()`:
  - `showHome()` shows the `.home-page`, hides the `.timeline-page`, restores a white `body` background, and scrolls to the top.
  - `showTimeline()` hides the `.home-page`, shows the `.timeline-page`, sets a dark `body` background, and scrolls to the top.
- The nav links in both views call these functions via `onclick` handlers; there is no routing or URL change.

### Timeline data model and layout
- Timeline content is encoded as a single `timelineData` object with three arrays:
  - `cities` – location history (📍), each entry has `title`, `shortTitle`, `icon`, `start`, `end`, `description`.
  - `education` – education milestones (🎓), same shape.
  - `work` – work history (💼), same shape.
- Dates are strings in `"Month Year"` or `"Present"` form; the rendering logic treats them as a continuous numeric axis:
  - `parseDate(dateStr)` converts `"Month Year"` to a decimal year (`YYYY + monthIndex/12`) and maps `"Present"` to `END_YEAR`.
  - `yearToPixels(decimalYear)` converts a decimal year to a vertical pixel offset using `START_YEAR`, `END_YEAR`, and `YEAR_HEIGHT` constants.
- `processColumn(entries, type)` normalizes each column (cities/education/work) by:
  - Attaching a `type` tag (`'city' | 'education' | 'work'`).
  - Computing `startDecimal`/`endDecimal` via `parseDate`.
  - Adding a preformatted `dates` string used in the modal.
- `getEntries()` simply returns the processed `cities`, `education`, and `work` arrays.

### Timeline rendering and sticky behavior
- `buildTimeline()` is the main entry point for constructing the timeline and is invoked once on page load:
  - Computes overall `totalHeight` based on `START_YEAR`, `END_YEAR`, and `YEAR_HEIGHT` and applies it to `#timelineContainer` so the page scroll height matches the full time range.
  - Adds a central vertical gradient bar (`.timeline-strand`) and a `year-marker` element for each year between `START_YEAR` and `END_YEAR`.
- Each of the three logical columns (cities, education, work) is laid out via:
  - `calculatePositions(entries)` which walks the ordered entries and assigns a `topPos` and `laneHeight` to each “lane”:
    - `idealTop` is derived from `startDecimal` via `yearToPixels`.
    - `laneHeight` is the max of a minimum slot height (`SLOT_HEIGHT`) and the pixel distance from `startDecimal` to `endDecimal`.
    - `lastBottom` ensures lanes for a given column never overlap vertically; later entries are pushed down as needed.
  - `renderColumn(entries, laneClass, nodeClass, baseZIndex)` which emits:
    - An `.entry-lane` container per entry with a lane class (`city-lane`, `education-lane`, `work-lane`) and inline `top`/`height`/`z-index`.
    - A `.timeline-node` with `data-*` attributes (`data-type`, `data-title`, `data-dates`, `data-description`).
    - A styled `.node-circle` containing the emoji icon, title, and a `+` click indicator.
- CSS assigns each column a fixed horizontal lane:
  - `.city-lane` on the left, `.education-lane` as a narrow center column, `.work-lane` on the right.
  - `.timeline-node` elements use `position: sticky` with `top: 50%` so they “pin” as you scroll through their lane height, creating the continuous-scroll effect.
- After building the lanes, `buildTimeline()` appends a "To be continued..." marker (`.tbc`) after `#timelineContainer`.

### Modal behavior and interactions
- `addTimelineClickHandlers()` attaches click listeners to every `.timeline-node` to open a details modal using the `data-*` fields set by `buildTimeline()`.
- `openModal(type, title, dates, description)`:
  - Switches the modal card’s class to `${type}-modal` (`city-modal`, `education-modal`, or `work-modal`) to pick up type-specific borders and glows.
  - Sets the modal title and description and (currently) hides the date string (`modalDates.style.display = 'none'`).
  - Adds the `active` class to `.modal-overlay` and sets `document.body.style.overflow = 'hidden'` to lock background scrolling.
- `closeModal()` clears the `active` class and re-enables body scrolling.
- Clicking on the semi-transparent backdrop (the overlay itself) also closes the modal.
- A scroll listener updates the parallax gradient background (`#bgGradient`) by adjusting `background-position` based on the scroll offset.

### `timeline-tests.html`: browser-based unit tests
- `timeline-tests.html` is a tiny, dependency-free test runner intended to validate timeline behavior in a real browser environment:
  - It loads `index.html` into a hidden `<iframe>` and, on iframe load, obtains `frame.contentWindow` and `frame.contentWindow.document` for testing.
  - All functions under test (`parseDate`, `yearToPixels`, `processColumn`, `buildTimeline`, `openModal`, `closeModal`) are referenced from that iframe’s global scope.
- A lightweight assertion library (`assert`, `assertEqual`, `assertApproxEqual`) is defined inline. Test results are accumulated and rendered into the DOM.
- Tests currently cover:
  - `parseDate` mapping for month/year and `Present`.
  - `yearToPixels` behavior and relationship to `START_YEAR`/`YEAR_HEIGHT`.
  - `processColumn` output shape and use of `parseDate`.
  - `buildTimeline` side effects: year marker count, lane counts vs. data lengths, data attributes on nodes, and container height.
  - `openModal`/`closeModal` toggling of overlay state, classes, and `body` overflow.
- The test harness is intentionally simple and not integrated with any JS testing framework; maintainers should keep this style if adding new tests (append to the `tests` array and rely on the browser to run them).

### Design and specification document
- `grantheimer.com Claude Plan.md` is a detailed design and requirements document for this site and should be treated as the source of truth for visual and interaction goals (color palette, dual-strand timeline concept, modal content expectations, hosting assumptions).
- Before making significant structural or visual changes to the timeline or navigation, consult that plan to stay aligned with the original design intent.