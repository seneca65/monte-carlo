# Monte Carlo Retirement Simulator

A retirement withdrawal simulator that runs entirely in the browser as a
Progressive Web App. No server, no tracking, no data leaves your device.
Built with plain HTML, CSS, and JavaScript (Chart.js for the chart).

Each run performs 10,000 trials. Every trial simulates the full retirement
horizon year by year: the withdrawal is taken at the start of each year,
the remaining balance earns that year's market return, and the withdrawal
is adjusted for inflation annually. Results show survival rate, ruin rate,
median and mean ending balances, percentiles (10th–90th), and a
distribution chart.

## Two versions

| File | URL | Description |
|------|-----|-------------|
| `index.html` | [Original](https://seneca65.github.io/monte-carlo/) | Normal-distribution engine only (Box-Muller) |
| `monte-carlo-v2.html` | [Version 2](https://seneca65.github.io/monte-carlo/monte-carlo-v2.html) | Adds a bootstrap engine alongside the original |

## Simulation engines (v2)

**Normal distribution (Box-Muller)** — Each simulated year draws the market
return and inflation from bell-shaped distributions defined by the mean and
standard deviation inputs. Fully adjustable, so assumptions can include a
deliberate margin of safety.

**Bootstrap (historical)** — Each simulated year picks a random year from
1928–2025 and uses that year's *actual* 60/40 stock/bond blended return and
its *actual* inflation, together as a pair. This preserves real extremes
(1931: −27.3%) and real return/inflation pairings (1974: −14.7% return with
11% inflation). No distribution shape is assumed. The mean/std dev inputs
are ignored in this mode.

Running both engines at the same withdrawal rate and horizon is a useful
cross-check: with matched inputs they agree within about one percentage
point, with bootstrap typically slightly lower — the effect of real
history's fat tails.

## Historical data

The embedded series covers 98 years (1928–2025):

- 60/40 blend = 0.6 × S&P 500 total return + 0.4 × 10-year US Treasury
  total return, computed per year
- Inflation = annual US CPI
- Source: Aswath Damodaran, NYU Stern — *Historical Returns on Stocks,
  Bonds and Bills* (January 2026 update)
- Blend statistics: mean 9.04%, standard deviation 12.12%

## Verify the engine

With the engine set to Normal, enter: initial wealth $1,000,000,
withdrawal 0%, 10 years, return mean 7%, and all standard deviations and
inflation set to 0. Every trial should produce exactly **$1,967,151**
(1,000,000 × 1.07¹⁰) with a 0% ruin rate.

## Companion app

The [Endowment Withdrawal Planner](https://seneca65.github.io/endowment-planner/)
executes a chosen withdrawal strategy year by year using the Yale
smoothing formula with guard rails.
