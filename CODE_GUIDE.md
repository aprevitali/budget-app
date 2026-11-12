# Code guide

`index.html` is the whole app: no framework, no build step, no dependencies (only Google Fonts links).
It has three parts: `<style>`, the HTML skeleton, and one `<script>`.

## 1. Styles
- Colors, fonts and radius are CSS variables on `:root`. Each theme is a block `:root[data-theme="..."]`
  (nebula is the default, plus terminal, aurora, foresta, voxel, synthwave, carta). `setTheme()` sets the attribute.
- The page is a stack of full-screen "scenes" (`#s1` ... `#s7`): ring, income/spending chart, where the money is,
  buckets, month close, transactions, level.

## 2. HTML skeleton
Header with month selector and "Data" menu, side dots navigation, seven `<section class="scene">`
with empty containers (`#hero`, `#chart`, `#comp`, `#goals`, `#nw`, `#cats`, `#tx`, `#lvl`) and the command palette (`#cp`).
JavaScript fills the containers.

## 3. Script
- **State**: one object `S` (`tx`, `goals`, `acc`, `bal`, `sum`, `thr`, `rules`, `lang`, `theme`, ...), saved in
  `localStorage` under the key `budget_v1` by `save()`. `S.bal[month][accountIndex]` holds balances,
  `S.sum[month]` holds income/spending typed by hand when there are no transactions.
- **Languages**: the source text is Italian. `L(en,it)` picks a string in new code; `EN` and `RX` translate the old text to
  English; `applyLang()` walks the page after every render and translates text nodes and attributes in place.
- **Categories**: `CATS` is a list of `[name, regex]`; `cat(x)` returns the category from a manual override,
  the learned rule `S.rules[description]`, or the first matching regex (`guess`). `OUT` (transfers) is excluded
  from totals; `INV` (investments) is excluded from spending unless the switch is on.
- **Numbers**: `months()` lists the months; `stats(month)` returns income, spending, per-category totals and the
  spending/income percentage; `nwOf(month)` sums the balances. These feed every chart and every KPI.
- **Rendering**: `render()` rebuilds all panels with template strings (`innerHTML`) and re-attaches the handlers;
  `nwRender()`, `lvlRender()` and `dnd()` are called at its end. Simple and predictable; if the app grows a lot,
  this is the part to replace with a small framework.
- **Bank import**: `BK` lists the banks (Intesa, Fineco, Revolut): the header names that identify each one and how to read a row. `bankTable()` finds the header in the first 30 rows; `xlsxSheets()` reads .xlsx with the browser's own unzip (`DecompressionStream`) and `DOMParser`, so there is no library and the strict CSP stays as is; `pairTransfers()` marks matching out/in amounts between different banks as transfers. To add a bank, add one object to `BK`. Anything not recognized falls back to the generic `parseCSV()`.
- **Input**: `parseCSV()` reads bank CSVs, `addTx()` adds transactions and skips duplicates (same date, description,
  amount). `ev()` is a safe calculator (recursive descent, no `eval`) used by every numeric field and by the commands.
- **Drag and drop**: `moveAcc()` also remaps the saved balances when accounts change order; `moveGoal()` reorders buckets;
  dropping a transaction on a category writes a rule in `S.rules`.
- **Level and badges**: `lvlRender()` computes XP from your data; nothing extra to enter.
- **Command line**: the `CMD` object maps names to functions (`kpi`, `runway`, `forecast`, `trend`, `vs`, `recurring`...);
  Italian aliases are added with `Object.assign`. `runCmd()` parses a line; Tab completes and arrows browse history.
  To add a command: write `name: args => "text to print"` inside `CMD` and one line in `HELP`.

## Where to change things
- Source link: `SOURCE_URL` near the top of the script.
- Default categories: `CATS`. Default accounts and buckets: the initial value of `S`.
- New theme: copy a `:root[data-theme="..."]` block, add an `<option>` in the menu and the name in `THEMES`.
- Bank API later: add a function that fetches `/api/sync` and calls `addTx()` and writes `S.bal`, then a button that calls it.

## License
AGPL-3.0-or-later, see `LICENSE`.
