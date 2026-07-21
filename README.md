# The Archive

A single-file, vanilla JS/HTML/CSS browsing interface for a fictional library — 79 subjects across three "wings," each with 4 catalogued books. No build step, no dependencies, no backend. Open `the-archive.html` in any browser.

## Structure

Three-level drill-down, all rendered client-side from one data array:

```
Home  →  Wing  →  Shelf  →  Book
(3 wings)  (subjects)  (books)  (detail panel)
```

- **Home** — hero + three wing cards (Dark, Sciences, General), each showing its Dewey range, subject count, and volume count.
- **Wing** — grid of subject "shelf" cards (Dewey code, name, volume count, preview title).
- **Shelf** — grid of book cards for the selected subject (title, author, blurb preview, tags).
- **Book** — slide-up detail panel: full blurb, tags, a reader reaction card, and Previous/Next volume navigation.

A breadcrumb trail (`Home / Wing / Subject`) sits in the top bar at every level and is clickable to jump back. A search box in the top bar does typeahead over subject names and jumps straight into a subject's shelf view on selection.

## Data

Everything is generated at load time from a single `CATS` array (name, short label, Dewey code, wing) in the `<script>` block — no external data file. Books, authors, blurbs, tags, and reader reactions are deterministically derived from small template arrays (`TITLE_TPL`, `BLURBS`, `TAGS_BY_GROUP`, `REACTIONS`, etc.) so re-opening the file always shows the same content.

To add or edit subjects, edit the `CATS` array — each row is `[name, short label, Dewey code, wing key]`, where `wing key` is one of `dark`, `nature`, `default`.

## Design

Vintage library / card-catalog aesthetic:

- **Fonts** — Fraunces (display serif), Inter (body), JetBrains Mono (codes, meta, labels).
- **Palette** — near-black background, warm brass gold, muted teal, and brick red accents (one color per wing).
- **Motion** — panels ease in with a short "drawer pulling open" animation; the book detail panel slides up from the bottom like an index card.

## Files

- `the-archive.html` — the whole app (HTML + CSS + JS, no external assets besides the Google Fonts import).
