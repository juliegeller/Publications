# The Geller Index

An editorial archive site. Everything you see is driven by two CSV files — you never touch the HTML.

- `homepage.html` — the page (design + logic). Leave it alone.
- `settings.csv` — the site's wording, title, and highlight colour.
- `data.csv` — the list of articles/research.

## Changing the title, colour, and copy — `settings.csv`

Open `settings.csv` in Excel, Numbers, or Google Sheets. It's a simple `key,value` list. Change the value in the right-hand column:

| key | What it controls |
|---|---|
| `site_title` | The big headline + top-left brand (e.g. change "The Geller Index" to anything) |
| `hero_accent` | The word inside the title shown in the highlight colour (must appear in `site_title`) |
| `tagline` | The sentence under the headline |
| `highlight_color` | The accent colour, as a hex value, e.g. `#e4231b` |
| `established` | Small top-right mark |
| `kicker_left` / `kicker_right` | The two labels on the thin line above the title |
| `statement` | The large statement sentence |
| `statement_accent` | The phrase within the statement shown in the highlight colour |
| `featured_heading` | Heading of the "Selected" section |
| `featured_count` | How many pieces appear in the featured block (e.g. `6`) |
| `footer_line` | The big footer line |
| `footer_accent` | The word within it shown in the highlight colour |
| `subject_label` | Colophon "Subject" credit |

If a value contains a comma, wrap it in double quotes: `"A test statement, with a comma."`

## Adding articles — `data.csv`

Keep the header row exactly as-is. Add one row per piece:

```
title,outlet,type,date,topic,url,note,download
```

| Column | What goes here |
|---|---|
| `title` | Headline of the article or research piece |
| `outlet` | Publication name, e.g. `CX Dive`, `Computerworld` |
| `type` | `Media` or `Research` — these become the filter buttons + stats automatically |
| `date` | `YYYY-MM-DD` — the list sorts newest-first on its own |
| `topic` | Short tag, e.g. `RevOps`, `Agentic Commerce` |
| `url` | Full link |
| `note` | One sentence on the piece (optional) |
| `download` | Leave blank |

Counts, year range, filters, and stats all recalculate from `data.csv` — add rows and everything updates.

## The one step after editing a CSV

After you change `settings.csv` or `data.csv`, **double-click `Refresh site.command`.** A small window opens, says "Snapshot refreshed," and closes. That's it.

Why: browsers block a double-clicked page from reading separate files on your computer. The refresh script copies your latest CSV content into `homepage.html` so it works on a plain double-click. Then just double-click `homepage.html` to view.

(First time only: macOS may say the script is from an "unidentified developer." Right-click `Refresh site.command` → Open → Open. After that, double-click works normally.)

## Viewing

Double-click `homepage.html`. No web server, no terminal.

## Publishing

Drop all four files (`homepage.html`, `settings.csv`, `data.csv`, `Refresh site.command`) onto any static host — [Netlify drop](https://app.netlify.com/drop) or GitHub Pages. Keep them in the same folder. When hosted, the page reads the live CSVs directly, so hosted edits show up without the refresh step.
