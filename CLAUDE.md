# gibsonlopez.com — Site Conventions

Personal academic website for Matthew Gibson-Lopez, Associate Professor,
Department of Computer Science, UT San Antonio. Hosted on GitHub Pages
(gibsonlopez-utsa.github.io), plain HTML/CSS — no static site generator,
no build step. Keep it that way; edits are made directly to the HTML files.

## Site structure

- `index.html` — About / home page (bio, research interests, contact, featured video)
- `research.html` — Research page (currently a "coming soon" placeholder)
- `workforce.html` — Workforce Development page (currently a "coming soon" placeholder)
- `seminar_<season><year>.html` — Algorithms Seminar page for a given semester,
  e.g. `seminar_2025fall.html`

Every page shares the same header/nav/footer boilerplate and the same
embedded `<style>` block (no external stylesheet). When editing shared
elements (nav links, header text, footer), update all pages together.

## Design system

- Primary (header/footer background): `#032044` (UTSA midnight blue)
- Accent (rules, active nav link, links, left-border accents): `#F15A22` (UTSA orange)
- Body text: `#333` on white background
- Font stack: `-apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
  Ubuntu, Cantarell, sans-serif`
- Layout: single `.container` / `main` column, `max-width: 1000px`, centered
- Nav: sticky, `#f8f9fa` background, active page marked with `class="active"`
  (orange text + orange bottom border)
- "Coming soon" placeholder pattern: `.coming-soon` box, light gray background,
  orange left border, centered italic-gray text
- Responsive breakpoint at `768px`: smaller header font, tighter nav padding,
  profile photo goes from floated to centered/stacked

## Seminar page conventions

Each talk is a `.talk-item` card:
- `.talk-header` — date, speaker, italic talk title, status badge, expand chevron
- `.talk-details` — collapsed by default, expands via `toggleTalk()` JS
  (max-height transition) to show `.talk-abstract` and an optional
  `.talk-slides` link (`slides/<file>.pdf`)
- Status badges: `status-completed` (green), `status-upcoming` (yellow),
  `status-no-talk` (gray) — reused for "No Talk", "TBD", and holiday breaks
- Weeks with no speaker get a header-only `.talk-item` (no chevron, no
  onclick, no details block)
- Talks are listed in chronological order down the page as an HTML comment
  per week (`<!-- Month Day -->`) — keep that comment convention, it makes
  the file easy to scan/diff

## Archive workflow (Option A — in use)

`seminar.html` is the stable nav target and always holds the *current*
semester. Past semesters live in `seminar_<season><year>.html` with an
`.archive-notice` banner pointing back to `seminar.html`, and are listed
in the `.archive-links` box on `seminar.html`. Nav links on all pages
point to `seminar.html` and never change at rotation time.

## Semester rotation checklist

1. Copy `seminar.html` to `seminar_<oldseason><oldyear>.html`; retitle
   (`(Archive)` in `<title>` and `<h2>`), swap the `.archive-links` box for
   the `.archive-notice` banner (CSS from an existing archive file), and
   mark any leftover "Upcoming" talks as Completed
2. In `seminar.html`: update the `<h2>` semester, add the archived file to
   `.archive-links`, update time/location, and replace the schedule with one
   header-only `.talk-item` per date (`status-no-talk` labelled "TBD")
3. Fill in talks as they're confirmed (chevron, onclick, details block)
4. Nav links need no changes

Current: Fall 2026 — Fridays 10am, SP2 340K; Sept 25, Oct 9, Oct 23,
Nov 6, Nov 20, Dec 4 (all TBD).

## Working preferences

- Lightweight solutions only: plain HTML/CSS/vanilla JS, Unicode/HTML
  entities for math instead of MathJax, no frameworks or generators
- When asked for changes, give complete, ready-to-use file contents or
  clearly-scoped blocks — not partial snippets requiring manual assembly
- Slide decks (LaTeX/Beamer) for talks follow the same UTSA color scheme:
  orange rule under frame titles, footline with name + page number — kept
  in a separate slides workflow, not part of this repo's scope
