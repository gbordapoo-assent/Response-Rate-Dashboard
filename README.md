![The Automated Compliance Trend Reporting Framework](assets/automated-compliance-trend-reporting-framework.png)

# Response Rate Dashboard

A lightweight, single-page dashboard for exploring response-rate trends by client over time.

The app is fully client-side (`index.html`) and uses:

- [Chart.js](https://www.chartjs.org/) for chart rendering
- [PapaParse](https://www.papaparse.com/) for CSV parsing

A sample dataset is included in `many_modules_part_level.csv` and auto-loads on startup.

## Features

- Multi-client trend lines for **Response Rate (%)**
- Optional **Submission Delta** bars on a secondary Y-axis
- Filters for:
  - Module
  - SubModule (dependent on selected Module)
- Client spotlighting via:
  - Dropdown selection
  - Clicking a line directly in the chart
- Dynamic status text showing current filters/highlight state

## Project Structure

- `index.html` – complete dashboard UI, styles, and JavaScript logic
- `many_modules_part_level.csv` – sample CSV data used for default loading

## Getting Started

### 1) Open the hosted dashboard (recommended)

You can access the dashboard directly via GitHub Pages:

```text
https://gbordapoo-assent.github.io/Response-Rate-Dashboard/
```

No installation is required for normal use.

### 2) Run locally (optional, for development)

If you want to run the project locally, serve it through a local web server (not `file://`) because the page fetches the CSV file.

From the project root:

```bash
python3 -m http.server 8000
```

Then open:

```text
http://localhost:8000
```

### 3) Load your own CSV (optional)

Use the file picker in the UI to load another CSV.

## Expected CSV Columns

The dashboard supports multiple header aliases, but these are the primary fields:

- `ClientDBName` (client identifier)
- `SnapshotDate` (date)
- `SubmissionRate` (response rate, accepts values like `45` or `45%`)
- `SubmissionsDelta` (delta value)
- `ModuleName` (module)
- `SubModuleName` (submodule)

## Interaction Guide

- **Highlight a client:** choose from the client dropdown or click a line.
- **Toggle delta bars:** enable "Show Submission Delta".
- **Filter by module/submodule:**
  - Choose a module first.
  - Then optionally choose a submodule.
- **Reset highlight:** click the highlighted line again or clear the dropdown selection.

## Notes

- Legend is intentionally hidden to reduce clutter with many clients.
- Dates are parsed and sorted chronologically before rendering.
- If no rows match the selected module/submodule filters, the chart is cleared and a status message is shown.
