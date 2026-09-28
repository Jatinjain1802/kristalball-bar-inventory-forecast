# Bar inventory forecasting prototype

A notebook and short report for the Kristalball take-home. For each of six bars and 16 brands, it audits historical inventory movements, makes a one-step forecast, calculates an illustrative par stock level, and simulates a replenishment scenario. The companion `report.pdf` answers the five assessment questions.

## Run

Python 3.11 or newer recommended:

```bash
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook bar_inventory_forecast.ipynb
# Run All cells from the repository root
```

The notebook has been executed and includes output and figures. It writes `illustrative_recommendations.csv` on rerun. No API key is needed. Source snapshot: [Google Sheet](https://docs.google.com/spreadsheets/d/14i7oWnBOoIf3pai37bsGYkby3VXJL1AlX_KxC8ZMKtg/edit?gid=1742513311#gid=1742513311), downloaded 28 September 2026. The attached CSV has 6,575 rows of historical movements; don't treat it as current hotel stock. Check the source's reuse terms before repurposing outside this assessment.

## Method in one minute

- 96 bar-brand series, with irregular intervals between logs. A row's consumption is taken as demand for the interval since the previous entry, not as a whole day; the first row in each series has no known interval and is excluded from evaluation. Unlogged days are **not** zero-filled.
- Train before 1 Oct 2023, choose among three simple historical-rate methods on 1 Oct to 14 Nov, and report an untouched test from 15 Nov 2023 to 1 Jan 2024. One-step predictions use only earlier observations.
- The validation winner is a lifetime, duration-weighted rate. Test MAE is **247.80 ml per observed interval** and WAPE **82.97%** across 852 test intervals. These errors are large: the prototype has **not** established a reliable service level or real stockout reduction.
- Par uses predicted ml/day times an assumed 2-day lead plus 1-day review cycle, plus 20% provisional buffer, rounded up to 100 ml. Suggested order uses the last logged closing balance and assumes no open orders, solely to show how it would work. A manager must use a *current* count and true supplier terms before placing an order.
- The seven-day simulation is synthetic; it is not a backtest of stockout reduction. Extend with point-of-sale, occupancy, observed stockouts, waste, open purchase orders, supplier lead time and costs before deployment.

## Contents

- `bar_inventory_forecast.ipynb`: documented, executed end-to-end analysis and demonstration
- `bar_inventory_movements.csv`: unchanged CSV export of supplied source
- `illustrative_recommendations.csv`: generated examples for all 96 series
- `report.pdf`: two-page assessment write-up
- `demo_walkthrough.md`: outline to help Jatin record his own 3-5 minute video
