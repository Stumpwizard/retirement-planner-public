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

## Additional account types
- **HSA:** Editable balance and annual qualified medical spending (medical spending is included in the overall annual spending budget). HSA withdrawals are limited to this qualified-medical budget in the projection.
- **Taxable brokerage:** Editable account balance and cost basis, with withdrawals used before IRA withdrawals. The calculator estimates long-term capital gains on brokerage sales using proportional cost basis and simplified federal/Indiana rates. It does **not** model dividend/interest taxes, short-term capital gains, capital-loss carryforwards, or HSA nonqualified distributions. Results involving brokerage balances are preliminary and may understate tax and withdrawal needs.
- The annual projection includes separate year-end HSA and brokerage balances for both strategies; all defaults are fictional and set to $0 for the new accounts.


## Tax model update
Brokerage sales realize gains proportional to the entered cost basis. Federal ordinary income and long-term capital gains brackets, Social Security provisional-income taxation, an estimated age-65 deduction, state/county income taxes and a simplified net investment income tax are included. The model assumes all gains are long-term and uses illustrative inflation-indexed 2026 thresholds; it does not replicate a tax return. Required minimum distributions are approximated and any excess is reinvested in taxable brokerage. The first retirement year's wages and detailed federal senior deductions, Indiana exemptions, dividend taxes, Medicare and ACA effects are not modeled. Results remain preliminary.


## Regression tests and deployment gate
Run `node tests/smoke.cjs` from the repository root. The Pages deployment workflow runs this check before uploading the site. It tests JavaScript syntax, account handling, selected tax calculations, shortfall constraints, baseline and downturn outputs. A successful workflow is required before considering a release verified. These automated checks do not validate tax-law completeness, actual browser rendering, or retirement forecasting accuracy.

## Known modeling limitations
- The engine now models monthly withdrawals and monthly-compounded investment returns. Annual tax budgets and year-end reconciliation remain approximations; the downturn scenario is illustrative rather than a probability distribution.
- Brokerage sales assume proportional basis and long-term gains, and do not model dividends, short-term gains or capital-loss carryovers.
- State/county income tax and RMD calculations are approximations; tax-law changes and other income are excluded.
- HSA balances are earmarked for qualified medical expenses only; a remaining HSA does not eliminate general spending shortfalls.


## Monthly projection update
Cash withdrawals are now applied each month before monthly investment growth. Social Security begins in the selected month; qualified medical spending may be funded from the HSA; taxable brokerage proceeds are tracked with proportional basis; IRA and Roth funds are used afterward. Annual tax estimates are budgeted monthly and reconciled at year end. The resulting forecasts remain approximations because tax timing, intra-year asset-class paths, dividends, health insurance, and future law are not fully modeled.


## Portfolio Builder (November 2026)
Choose Conservative (40/48/12), Balanced Retirement (50/40/10), Moderate Growth (60/35/5), or Growth (75/20/5). The selector displays target asset sleeve percentages and Fidelity mutual-fund options. Verified fund historical average annual total returns for 1, 3, 5 and 10 years are displayed as of August 31, 2026 for FSKAX, FTIHX, FXNAX, and FUMBX, with links to Fidelity's source pages. Unverified alternatives show a dash rather than invented returns. Money market yield history is not displayed as comparable total return. The fund picker is informational and does not change the existing Balanced-vs-Moderate retirement projections or execute trades; model return assumptions remain independent of historical returns.
