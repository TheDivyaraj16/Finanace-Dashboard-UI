# Finanace-Dashboard-UI
A finance dashboard UI built with React and JavaScript offers a clean interface to track income, expenses, and balances. It includes charts, summary cards, and transaction lists with real-time updates. Reusable components and responsive design ensure smooth performance and easy navigation.
# FinManage — By Divyaraj
A clean, interactive finance dashboard built with HTML/CSS/JavaScript.
OUTPUTS ARE IN THE REPOSITORY
---
## Quick Start

```bash
# Option 1: Open directly
open index.html

## Features

### Dashboard Overview
- **Summary cards** — Net Balance, Total Income, Total Expenses, Savings Rate
- **Monthly Cash Flow bar chart** — Income vs Expenses for the last 3 months, with hover tooltips
- **Spending Breakdown donut chart** — SVG donut showing top expense categories for the current month

### Transactions Section
- Full transaction table with date, description, category, type, and amount
- **Search** — live filter by description or category
- **Filters** — by type (income/expense), category, and month
- **Sortable columns** — click any column header to sort ascending/descending
- **Add/Edit/Delete** — Admin-only CRUD via modal dialog

### Role-Based UI
Switch roles from the sidebar dropdown:
| Role    | Behaviour |
|---------|-----------|
| Admin   | Full access — can add, edit, delete transactions |
| Viewer  | Read-only — action buttons hidden, Add button hidden |

### Insights Section
- **Top Spending Category** — with percentage bar
- **Month Comparison** — Feb vs Mar for income and expenses with % change indicator
- **Savings Rate** — progress bar vs 30% target
- **Observations** — 4 auto-generated text insights from the data

### Data Persistence
All transactions and theme preference are saved to `localStorage` automatically. Refresh the page — your data stays.

### Export
- **CSV export** — downloads all transactions as a spreadsheet-compatible CSV
- **JSON export** — downloads raw JSON for API/developer use

### Light / Dark Mode
Toggle from the sidebar. Preference is persisted to localStorage.

---

## Project Structure

```
finance-dashboard/
├── index.html       
└── README.md
```

## Design Decisions

**Aesthetic direction:** Dark-first, editorial finance — inspired by Bloomberg Terminal meets modern fintech apps. Uses DM Serif Display for numerics/headings (personality and weight) paired with DM Sans for UI chrome (legibility). Accent color (`#C8F04D`) — a warm chartreuse — adds energy without feeling garish on dark backgrounds.

**State management:** A single `state` object holds all mutable data (transactions, role, sort, edit target). Every render function reads from `state` and re-renders its section. Changes call `saveState()` which writes to localStorage.

**Charts:** Hand-rolled SVG and DOM — the bar chart renders `div` elements scaled to percentage heights; the donut is a proper SVG arc-path donut computed with trigonometry. No canvas, no charting library.

**RBAC simulation:** Role is stored in `state.role`. All write actions (`openModal`, `editTransaction`, `deleteTransaction`) guard on `state.role === "admin"` before proceeding. The UI also hides the Add button and Actions column for Viewer role.

---

## Evaluation Checklist

| Criterion | Implementation |
|-----------|---------------|
| Dashboard Overview | ✅ Summary cards + bar chart + donut |
| Transactions Section | ✅ Table with search, filter, sort |
| Role-Based UI | ✅ Admin/Viewer toggle with guarded mutations |
| Insights Section | ✅ 4 insight cards with real computed data |
| State Management | ✅ Single state object + localStorage persistence |
| UI/UX | ✅ Dark/light mode, responsive, empty states |
| Export | ✅ CSV + JSON |
| Animations | ✅ Fade-up card reveals, hover effects, bar transitions |

---

## Browser Support

Works in all modern browsers (Chrome, Firefox, Safari, Edge). No polyfills needed.
