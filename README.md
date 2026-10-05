# Budget

Personal budget and net-worth tracker. Single static file, no server, no account.

## Run
Open `index.html` in a browser. Data is stored in that browser's localStorage.
Use **Data → Export data** regularly to back up; **Import data** to restore or move to another browser or URL.

## Features
- Spending ratio ring with a configurable threshold, income/spending history (6M / 12M / all)
- Net worth by account type, month close, buckets (goals) with drag and drop ordering
- Transactions: sort by date/category/amount, drag a row onto a category
- Command line (`/` or Ctrl+K): `kpi`, `runway`, `forecast`, `trend`, `vs`, `recurring`, `help`
- English / Italian, 7 themes

## Code
See [CODE_GUIDE.md](CODE_GUIDE.md) for how the code is organized.

## Privacy
Never commit exports or bank files (`budget-backup*.json`, `*.csv`) — they are in `.gitignore`.
Never put API keys in `index.html`.

## Roadmap
1. Small backend that holds bank-aggregator credentials (`.env`, never in the repo)
2. `GET /api/sync` returns accounts, balances and transactions in the app's format
3. "Sync" button in the app merges them (dedupe by transaction id); CSV import stays as fallback

## License
Copyright (C) 2026 Andrea Previtali. Licensed under the GNU Affero General Public License v3.0 or later (AGPL-3.0-or-later). See [LICENSE](LICENSE).
If you run a modified version as a network service, you must offer its source code to your users.
