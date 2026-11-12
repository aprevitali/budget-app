# 💸 Budget

**See where your money goes and whether your wealth is growing. One file, no account, no server.**

[![License: AGPL v3](https://img.shields.io/badge/license-AGPL--3.0-blue.svg)](LICENSE)

### 👉 [Try it now (sample data)](https://aprevitali.github.io/budget-app/)

Budget is a small personal-finance app that runs entirely in your browser. You bring a bank export or type a few numbers, and it answers the questions a spreadsheet makes you work for: *Am I spending too much this month? How many months could I live on my savings? Is my net worth going up?*

*(Italiano: [vai in fondo](#-italiano))*

---

## ✨ What you get

- **One glance, one answer.** A ring shows how much of your income you have spent, against a threshold you choose.
- **Trends that matter.** Income vs. spending for 6 months, 12 months or all time, plus a forecast and a "runway" (months of autonomy).
- **Net worth by account type.** Cash, deposit, investments, pension: month by month, so you can see if you are building value.
- **Goals as jars.** Emergency fund, holiday, a new laptop. Set a target, drag to reorder, watch them fill.
- **Recurring costs spotted for you.** Subscriptions and repeating payments are detected from your transactions.
- **Quick entry.** Press `/` or `Ctrl+K` for a command line: `spend 12.5 coffee`, `kpi`, `runway`, `forecast`, `trend`, `recurring`, `last`, `undo`, `help`. Number fields accept simple math.
- **Make it yours.** Seven themes (Nebula, Terminal, Aurora, Forest, Voxel, Synthwave, Paper), English and Italian, and small rewards for staying under your threshold.

## 🚀 Get started in a minute

1. Open the [demo](https://aprevitali.github.io/budget-app/) and choose **Data → Sample data** to explore with fictional numbers. Or download `index.html` and open it in your browser.
2. **Data → Import CSV / Excel:** drop one or several bank exports at once. **Intesa Sanpaolo** (.xlsx), **Fineco** (.xlsx) and **Revolut** (.csv) are recognized automatically, even if the header is not on the first row; any other bank goes through the generic CSV reader. You get a summary of new rows, duplicates skipped, transfers between your own accounts detected (same amount out of one bank and into another within 2 days, shown as *Giroconto* and excluded from totals), and invalid rows discarded. Fineco rows not yet booked (*Stato* other than *Contabilizzato*) are skipped and arrive with the next export. For a Revolut file in another currency you are asked for the exchange rate.
3. Want to go further back? Import a CSV with the columns `month;income;spending` (for example `2024-03;2100;1650`) to fill older months without transactions.
4. Fix what needs fixing: change a category from the dropdown or by dragging a row, delete a single transaction with **×**, add or remove a month with **+** and **−** next to the month selector.

> Every bank exports a different format. The importer looks for date, description and amount columns automatically, and tells you how many rows it could not read. If one of your banks does not work, please open an issue (with made-up sample rows, never real data).

## 🔒 Your data stays with you

- **No server, no account, no tracking.** Everything is read and stored in your browser. A strict Content-Security-Policy blocks the page from sending data anywhere.
- **Optional password.** *Data → Protect with password* encrypts what is stored in the browser (AES-GCM). The app locks after 5 minutes of inactivity, and **Hide amounts** turns every figure into dots.
- **Encrypted backups.** *Export data* can protect the backup with a passphrase. If you forget a password nothing can be recovered, so keep a backup.
- **One honest exception:** fonts are loaded from Google Fonts, which means Google sees your IP address when the page loads.
- **Good habits:** for real data, use a local copy of `index.html` in a browser profile without extensions, with disk encryption on. The online demo is meant for sample data. Data lives per browser and per address, so use *Export data / Import data* to move it. There is no sync between devices.

Never commit bank files or backups to your own fork. `.gitignore` already blocks the common ones.

## 🧭 Roadmap

- More ready-made import profiles (Intesa, Fineco and Revolut are done), and a guided "which column is which" step for the rest
- Balance history rebuilt automatically from your transactions
- Optional bank sync through a small backend you run yourself (credentials never in the browser or the repo); CSV import stays as the private alternative

## 🛠️ For developers

Plain HTML, CSS and JavaScript in a single file, no build step, no dependencies. See [CODE_GUIDE.md](CODE_GUIDE.md) to find your way around the code. Contributions and ideas are welcome.

## ⚖️ License

Copyright (C) 2026 Andrea Previtali. Licensed under the GNU Affero General Public License v3.0 or later ([AGPL-3.0-or-later](LICENSE)). If you run a modified version as a network service, you must offer its source code to your users.

*Budget is a personal tool, not financial advice.*

---

<details id="-italiano">
<summary><h2>🇮🇹 Italiano</h2></summary>

**Capisci dove vanno i tuoi soldi e se il tuo patrimonio cresce. Un solo file, nessun account, nessun server.**

Budget gira interamente nel tuo browser. Importi l'estratto della banca o scrivi poche cifre, e ti risponde alle domande che in un foglio di calcolo costano fatica: *sto spendendo troppo questo mese? Per quanti mesi potrei vivere con i miei risparmi? Il patrimonio sta salendo?*

**Cosa trovi:** anello spese/entrate con soglia a tua scelta, andamento a 6/12 mesi o totale, previsione e autonomia in mesi, patrimonio per tipo di conto, obiettivi come "barattoli", rilevamento delle spese ricorrenti, riga di comando (`/` o `Ctrl+K`), sette temi e interfaccia in italiano e inglese.

**Come iniziare:** apri la [demo](https://aprevitali.github.io/budget-app/) e scegli *Dati → Dati di esempio*, oppure scarica `index.html` e aprilo nel browser. Importa uno o più file con *Dati → Importa CSV / Excel*: Intesa Sanpaolo (.xlsx), Fineco (.xlsx) e Revolut (.csv) sono riconosciuti da soli, e i giroconti tra i tuoi conti vengono individuati. Per i mesi più vecchi usa un CSV con colonne `mese;entrate;spese`.

**Privacy:** nessun server, nessun account, nessun tracciamento. I dati restano nel tuo browser; puoi proteggerli con una password e cifrare i backup. Unica eccezione: i font arrivano da Google Fonts, che quindi vede il tuo indirizzo IP. Per dati veri usa una copia locale del file; non c'è sincronizzazione tra dispositivi, quindi sposta i dati con *Esporta dati / Importa dati*.

*Budget è uno strumento personale, non consulenza finanziaria.*

</details>
