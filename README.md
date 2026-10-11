# Personal Expense Tracker & Budget Dashboard

**Developer:** Sheik Imtiaz Hossain  
**Stack:** React 18, Vite 6, JavaScript, Recharts, Lucide React, CSS, browser localStorage.

A responsive, local-first personal finance dashboard for managing income, expenses, category budgets, and monthly spending trends. Suitable for a software engineering internship portfolio.

## Features

- Add, edit, delete income and expense transactions with confirmation before deletion
- Search and filter by type and category; view transactions by month
- Monthly income, expenses, balance and remaining budget cards
- Six-month income/expense area chart and expense-category doughnut chart
- Monthly category budget editor with progress indicators and overspending warnings
- CSV export for the currently selected month and active transaction filters
- JSON backup and restore (restore replaces existing transactions and budgets after confirmation)
- Dark/light mode, mobile navigation, responsive layout
- Currency display preference (NZD, AUD, USD, GBP, EUR, BDT)
- Demo data button, empty states, keyboard-accessible forms, basic validation
- Local storage persistence; no login or server required

**Important:** Changing the display currency changes the *currency symbol and formatting only*. It does not convert monetary values or fetch exchange rates. Use a single currency for all transactions in a given dataset. No banking data is connected.

## Requirements

- Node.js 20.19+ or 22.12+ (recommended: current Node.js LTS)
- npm

## Start locally

```bash
npm install
npm run dev
```

Open the local URL printed by Vite (typically `http://localhost:5173`).

## Test and build

```bash
npm test
npm run build
npm run preview
```

The `dist/` directory contains the static production site.

## Live Demo Url:


## Structure

```text
spendwise/
├── public/
│   └── favicon.svg
├── src/
│   ├── components/
│   │   ├── StatCard.jsx
│   │   └── TransactionModal.jsx
│   ├── lib/
│   │   ├── finance.js
│   │   └── storage.js
│   ├── App.jsx
│   ├── main.jsx
│   └── styles.css
├── tests/
│   └── finance.test.js
├── .gitignore
├── index.html
├── netlify.toml
├── package.json
├── vercel.json
└── vite.config.js
```

## Architecture decisions

**Why no backend?** This is a single-user portfolio application with no authentication, multi-device synchronization, or shared data. A Node.js API and database would add hosting cost and complexity without being necessary. Node.js is used for Vite development and building. The code can be extended later with Express and PostgreSQL/Supabase for account-based syncing.

**Storage:** Transactions, monthly budgets, theme and display currency are stored under the `spendwise-v1` key in `localStorage`. Storage is per-browser and can be erased by clearing site data. Export a JSON backup before clearing data or changing devices.

**Demo data:** Click **Load sample data** to insert example transactions for the selected month. Repeated clicks won't duplicate the same sample IDs.

**Budget behavior:** Budgets are month-specific; expenses are compared with the total of category limits. No budget limit is treated as zero in the remaining-budget card until at least one budget is set.

**Known limitations:** No user accounts, multi-device sync, automatic recurring transactions, real FX conversion, or cloud backups. This is not financial advice.

## Suggested portfolio improvements

- Add user authentication and cloud synchronization
- Add recurring transactions and savings goals
- Add end-to-end tests with Playwright and CI on GitHub Actions
- Add automatic exchange-rate conversion with an explicit base currency

## License

MIT License — copyright (c) 2026 Sheik Imtiaz Hossain.
