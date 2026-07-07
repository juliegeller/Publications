# The Geller Index

A small archive site listing Julie Geller's press citations and Info-Tech research publications. Two files, no build step:

- `index.html` — the page itself (design, search, filters)
- `data.csv` — the actual list of publications

## Updating the list

Open `data.csv` in Excel, Numbers, or Google Sheets. Keep the header row exactly as-is:

```
title,outlet,type,date,topic,url,note
```

Add one row per publication:

| Column | What goes here |
|---|---|
| `title` | The headline of the article or research piece |
| `outlet` | Publication name, e.g. `CX Dive`, `Computerworld`, `Info-Tech Research Group` |
| `type` | Either `Media` (press coverage) or `Research` (an Info-Tech-authored piece) |
| `date` | `YYYY-MM-DD` format, e.g. `2026-03-11` |
| `topic` | A short tag, e.g. `Contact Center AI`, `RevOps`, `Agentic Commerce` |
| `url` | Full link to the piece |
| `note` | One sentence on what she said or the piece covers |

Save as CSV (if your spreadsheet app asks, choose "CSV UTF-8"), and make sure the saved filename is still `data.csv`, replacing the old one. Reload the page — no code editing needed.

If a title or note contains a comma, wrap that whole field in double quotes, e.g. `"AWS, Salesforce upgrade contact center tech"`. Most spreadsheet apps do this automatically when you export to CSV.

## Viewing it locally

Browsers block a webpage from loading a local CSV file directly (a security restriction on the `file://` protocol), so double-clicking `index.html` won't show any entries — you'll see an error message on the page itself explaining this.

To preview on your own machine, open a terminal in this folder and run:

```
python3 -m http.server 8000
```

Then visit `http://localhost:8000` in a browser.

## Publishing it for others to view

Any static file host works, since it's just these two files:

- **Netlify** — drag the folder onto [app.netlify.com/drop](https://app.netlify.com/drop) for an instant link. To update later, edit `data.csv` and drag the folder again.
- **GitHub Pages** — push both files to a repo and enable Pages in the repo settings.

Either way, keep `index.html` and `data.csv` in the same folder — the page looks for `data.csv` right next to it.
