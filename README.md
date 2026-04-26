# Monte Carlo Retirement Simulator

A mobile-friendly Progressive Web App (PWA) that runs 10,000 retirement simulations to calculate the probability that your portfolio will last through retirement.

## What it does

Each simulation runs 10,000 independent trials. In each trial:

1. Start with your portfolio value
2. Withdraw the annual amount at the **beginning** of each year (adjusted for cumulative inflation)
3. Apply a **random** market return for the year (drawn from a normal distribution)
4. Apply a **random** inflation rate for the year (drawn from a normal distribution)
5. Repeat for the number of simulation years
6. If the portfolio reaches zero, the trial fails

After 10,000 trials, the app reports:
- **Survival rate** — percentage of trials where the portfolio lasted the full period
- **Percentile table** — 10th, 25th, 50th, 75th, 90th percentile final balances
- **Histogram** — distribution of all 10,000 final balances
- **Color-coded survival rate** — green ≥90%, yellow ≥75%, red below 75%

## Adjustable inputs

| Input | Default | Description |
|-------|---------|-------------|
| Starting portfolio | $1,000,000 | Total invested balance at retirement |
| Withdrawal rate | 4% | Annual withdrawal as % of starting portfolio |
| Simulation years | 30 | Length of retirement to simulate |
| Mean return | 7.5% | Expected average annual portfolio return |
| Std dev of return | 12% | Year-to-year variability of returns |
| Mean inflation | 2.5% | Expected average annual inflation |
| Std dev of inflation | 1.5% | Year-to-year variability of inflation |

## Installing on iPhone

1. Open the app URL in **Safari**
2. Tap the **Share** button (box with arrow at the bottom)
3. Tap **Add to Home Screen**
4. The app installs and opens full-screen like a native app

## Using on desktop

Open the URL in any browser — no installation required.

## Using with the Endowment Withdrawal Planner

Use this simulator to find a withdrawal rate that gives you a survival rate you are comfortable with (typically 90% or higher). Then enter that rate into the [Endowment Withdrawal Planner](https://seneca65.github.io/endowment-planner) to manage your annual withdrawals using the Yale smoothing formula with guard rail zones.

## Running locally

No server required. Open `index.html` in any browser.

## Files

| File | Purpose |
|------|---------|
| `index.html` | The complete app — simulation engine + UI |
| `manifest.json` | PWA install metadata |
| `sw.js` | Service worker for offline use |
