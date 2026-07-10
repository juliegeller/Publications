# The Geller Index

An editorial archive site. Everything you see is driven by two CSV files — you never touch the HTML.

- `index.html` — the page (design + logic). Leave it alone.
- `settings.csv` — the site's wording, title, and highlight colour.
- `data.csv` — the list of articles/research.

## Changing the title, colour, and copy — `settings.csv`

Open `settings.csv` in Excel, Numbers, or Google Sheets. It's a simple `key,value` list. Change the value in the right-hand column:

| key | What it controls |
|---|---|
| `site_title` | The big headline + top-left brand (e.g. change "Julie Geller" to anything) |
| `hero_accent` | The word inside the title shown in the highlight colour (must appear in `site_title`) |
| `tagline` | The sentence under the headline |
| `highlight_color` | The accent colour, as a hex value, e.g. `#e4231b` |
| `established` | Small top-right mark |
| `kicker_left` | The label on the thin line above the title |
| `statement` | The large statement sentence |
| `statement_accent` | The phrase within the statement shown in the highlight colour |
| `featured_heading` | Heading of the "Selected" section |
| `featured_count` | How many pieces appear in the featured block (e.g. `6`) |
| `footer_line` | The big footer line |
| `footer_accent` | The word within it shown in the highlight colour |
| `focus` | Footer "Focus" column — separate items with ` · ` and each becomes its own line |
| `subject_label` | Footer "Who" credit — separate with ` · ` for line breaks |
| `contact_email` | Where the Contact form sends (currently `julie@gellerstrategic.com`) |
| `linkedin_url` | Link for the LinkedIn icon in the header. **Update this to Julie's real profile URL.** Leave blank to hide the icon. |
| `contact_form_action` | Optional — see "The Contact form" below. Leave blank to use the email-app method. |

The footer's "Featured in" column and the "By the Numbers" stats are generated automatically from `data.csv` — no setting needed.

If a value contains a comma, wrap it in double quotes: `"A statement, with a comma."` (The `·` separators are fine as-is — just save as **CSV UTF-8** so they don't get garbled.)

## The Contact form

The header's **Contact** button opens a form (first name, last name, email, message).

By default — and with no setup — pressing Send opens the visitor's own email app with a message pre-addressed to `contact_email`, ready to send. This works everywhere with zero configuration.

If you'd rather the message send silently from the page (no email app opening), create a free form endpoint at [formspree.io](https://formspree.io) (2-minute signup, confirm `julie@gellerstrategic.com`), then paste the endpoint URL into `contact_form_action` in `settings.csv`. The form will POST to it and show a "message sent" confirmation. Leave `contact_form_action` blank to keep the email-app method.

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

## Seeing your CSV edits (no terminal, no scripts)

1. Double-click `index.html` to open it.
2. Either **drag `settings.csv` and `data.csv` onto the page**, or click the **"↑ Update from CSV"** button (bottom-left) and pick them.
3. The page redraws instantly with your latest content.

You can drop both files at once, or just the one you changed. The page figures out which is which from its header row.

Why this step exists: for security, browsers won't let a double-clicked page read other files on your computer on its own — so you hand it the files once. Nothing is installed, uploaded, or sent anywhere; it all happens in your browser.

## Publishing

Drop all three files (`index.html`, `settings.csv`, `data.csv`) onto any static host — [Netlify drop](https://app.netlify.com/drop) or GitHub Pages. Keep them in the same folder. **When hosted, the page loads the CSVs automatically** — no drag step needed. Re-upload a CSV to update the live site.
