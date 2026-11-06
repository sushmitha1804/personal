# Finora — Node.js Personal Finance Dashboard

A complete full-stack personal-finance dashboard built with Node.js, Express, SQLite, and vanilla HTML/CSS/JavaScript.

## Features
- Register and sign in with email/password; passwords are hashed with bcrypt.
- Session-based authentication backed by SQLite.
- Separate user data for each account.
- Customizable display name, monthly salary, currency, light/dark theme, overall monthly budget, savings target, and saved amount.
- Add, edit, delete, search, and filter income/expense transactions.
- Category budgets with progress bars and overspending indicators.
- Savings-goal progress, cash-flow chart, spending breakdown, report insights, and CSV export.
- Responsive layout for desktop, tablet, and mobile.
- SQLite persistence in `data/finora.sqlite`; data survives app restarts.
- Sample data and default budgets are created when an account is registered.

## Requirements
- Node.js 18 or newer
- npm
- Internet connection for Google Fonts and Chart.js CDN (the core app otherwise runs locally).

## Run locally
1. Extract the ZIP.
2. Open a terminal in the extracted `finora_nodejs` folder.
3. Install packages:
   ```bash
   npm install
   ```
4. Copy `.env.example` to `.env` and set a long random `SESSION_SECRET`.
   - Windows PowerShell: `Copy-Item .env.example .env`
   - macOS/Linux: `cp .env.example .env`
5. Start the server:
   ```bash
   npm start
   ```
6. Open **http://localhost:3000** and create an account.

For development with Node's watch mode:
```bash
npm run dev
```

## How to customize
- **Salary, currency, theme, budget, savings:** Sign in → Settings → change values → Save all preferences.
- **Transactions:** Transactions → Add transaction. Edit or delete entries from the transaction table.
- **Budgets:** Budgets → Add budget. Existing category budgets can be updated by adding the same category name again.
- **Savings:** Settings → update “Amount saved so far” and “Savings target”.
- **Reports:** Reports → Export CSV.

Salary note: the settings endpoint maintains one designated `Salary` transaction so updating the configured salary does not double-count salary income. You can still add separate income transactions such as freelance work.

## Project structure
```
finora_nodejs/
├── server.js
├── package.json
├── .env.example
├── README.md
├── public/
│   ├── index.html
│   ├── styles.css
│   └── app.js
└── data/              # created automatically at runtime
```

## Important deployment notes
This is a complete learning/demo project, not a security-audited financial product. Before exposing it to the public internet:
- Set a long, random `SESSION_SECRET` in `.env`; never commit `.env`.
- Use HTTPS and `NODE_ENV=production`.
- Configure rate limiting, CSRF protection appropriate to your deployment, strict content-security policy, secure cookie/proxy settings, and account recovery.
- Back up and protect the SQLite database and session database.
- Review all dependencies and run security tests.
- Avoid storing actual bank credentials or sensitive financial account details.
