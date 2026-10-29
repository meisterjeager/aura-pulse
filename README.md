# Aura Pulse

A lightweight, zero-install time-tracking app for Aura Tekton consultants. Log entries, run a live timer, export to CSV or XLSX, and push directly to Google Sheets — all from a single HTML file.

## Features

- **Live timer** — start a stopwatch while you work; stopping it auto-fills the hours field and opens the entry form
- **Time entries** — log date, client, project, Jira ticket, description, hours, and billable status; inline editing and delete
- **Week navigation** — browse any week; entries are scoped to Monday–Sunday
- **CSV export** — week or all-time, formatted to match the Aura Tekton Time Entry Template (columns A–G)
- **XLSX export** — two-sheet workbook: *Time Entries* (with autofilter) and *Summary* (hours by client/project, billable breakdown)
- **Google Sheets push** — writes entries directly to your timesheet sheet via the Sheets API, filling the header cells (name, week start, time zone)
- **Submission message generator** — pre-written message with open questions flagged, ready to copy and paste
- **Settings** — your name (stamps filenames), time zone, and Google Sheets Client ID
- **Dark / light theme** — follows system preference with a manual override
- **No install, no server** — one HTML file, runs entirely in the browser; data lives in `localStorage`

## Usage

1. Download `index.html`
2. Open it in any modern browser
3. Click ⚙ to set your name and time zone
4. Log time entries or use the timer
5. Export when ready

## Google Sheets Setup (optional)

To push entries directly to a Google Sheet:

1. Go to [Google Cloud Console](https://console.cloud.google.com)
2. Create a project and enable the **Google Sheets API**
3. Go to **APIs & Services → Credentials → Create Credentials → OAuth 2.0 Client ID**
4. Choose **Web application**
5. Add the URL where you're hosting `index.html` as an **Authorized JavaScript origin** (e.g. `http://localhost:8080` or your GitHub Pages URL)
6. Copy the **Client ID** and paste it into ⚙ Settings in the app

Then click **↑ Google Sheets**, paste your Sheet ID (from the sheet URL), and authorize. The app writes entries to the *Time Entries* tab starting at row 10.

> The Sheet ID is the long string in your sheet's URL:  
> `https://docs.google.com/spreadsheets/d/`**`SHEET_ID_HERE`**`/edit`

## CSV / XLSX Column Format

Exports match the Aura Tekton Time Entry Template (Time Entries tab, row 6):

| Column | Field |
|--------|-------|
| A | Work date |
| B | Client |
| C | Project / engagement |
| D | Jira ticket / link |
| E | Work description |
| F | Hours |
| G | Billable? |

## File Naming

With your name set in Settings, exports are named:

```
2026-10-27 - Dallin Cummings - Timesheet.csv
2026-10-27 - Dallin Cummings - Timesheet.xlsx
```

## Tech

Single-file vanilla HTML/CSS/JS. No framework, no build step.

- [SheetJS](https://sheetjs.com/) (cdnjs) — XLSX generation
- [Google Identity Services](https://developers.google.com/identity) — OAuth 2.0 for Sheets push (loaded on demand)
- [Outfit + DM Sans](https://fonts.google.com/) — typography
- `localStorage` — all data stored locally in the browser

## License

MIT
