# Retirement Planning Calculator

Public, self-contained educational retirement calculator. The default figures are **fictional examples**, not a specific person’s financial data.

## Features
- Editable traditional IRA, Roth IRA, spending, Social Security, retirement dates, inflation and return assumptions
- Illustrative balanced 50/40/10 and moderate growth 60/35/5 allocations using broad Fidelity index-fund categories
- Annual cash-flow, estimated taxes, RMD approximations, withdrawal shortfalls, year-end balances, early downturn stress test, and CSV export
- Runs client-side without external scripts or account connections

## Privacy
This is intended for a **new public repository with a fresh Git history**. Never make the original private financial-planning repository public: prior commits may expose personal planning assumptions. Input settings are stored in the browser’s local storage, not uploaded to GitHub; avoid using shared devices for sensitive inputs.

## Modeling limitations
Deterministic educational projections, not validated financial or tax advice. Tax, RMD, Social Security and market assumptions are approximate. The model does not fully account for tax-law changes, ACA/Medicare premiums, county taxes, wages, sequence-of-returns probabilities or real-world fees.

## Publish
Create a **new public repository** named `retirement-planner-public`, upload these files, then select **Settings → Pages → Source: GitHub Actions**. The included workflow deploys `index.html`.