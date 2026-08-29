# Leveraged home-equity return explorer

Interactive chart for task 13 of the Data Visualization portfolio, Data Analytics for Finance I & II, Università della Svizzera italiana (USI), Lugano, September 2026. Author: Eray AKYOL.

**Live page:** https://erayakyol.github.io/FinancialDataAnalytics-DataVisualizationPortfolio/

The page opens in any browser; no download, installation or account is needed.

## What the chart shows

Hypothesis C of the portfolio: mortgage leverage gives an individual home buyer outsized equity returns. The chart tests it on real house-price data for eight countries (Switzerland, Germany, France, Italy, Spain, United Kingdom, United States, Japan).

The user chooses a country, a purchase year, a loan-to-value ratio and a mortgage rate. The chart then plots, quarter by quarter from the purchase date:

- the **unlevered equity multiple**, what one unit of money invested in the home has become for a cash buyer (the price index divided by its value at purchase);
- the **levered equity multiple**, what one unit of the buyer's own money, the down payment, has become after the loan and the interest paid on it are deducted;
- a **negative-equity band** below zero, where the home is worth less than the loan plus the interest paid.

The headline, the story sentence and the hypothesis line are recomputed from the selection. Default view: Switzerland, purchase in 2010, loan-to-value 80 %, mortgage rate 2.79 %: the down payment has become 2.51× against 1.66× for a cash buyer.

## The model behind the lines

Let P_0 be the real price index at purchase and P_t its value in quarter t. With loan-to-value L and a constant annual mortgage rate r on an interest-only loan:

- unlevered multiple = P_t / P_0
- levered multiple = (P_t − L·P_0 − cumulative interest paid up to t) / ((1 − L)·P_0)

The denominator is the down payment, so the levered multiple is the buyer's wealth per unit of own money. Negative equity is a levered multiple below zero.

Simplifications, stated on the page: interest-only loan at a constant rate (no amortisation), no taxes, no transaction costs, no rent yield or rent saved, and a nominal mortgage rate applied to a real (inflation-adjusted) price index. The chart is a teaching device for the effect of leverage, not a valuation tool.

## Data

- House prices: Bank for International Settlements (BIS), "Residential property prices: selected series" (dataset WS_SPP), real index, 2010 annual average = 100, quarterly. https://data.bis.org/topics/RPP (bulk file https://data.bis.org/static/bulk/WS_SPP_csv_flat.zip). Source attribution as required by the BIS terms of use: "Source: BIS".
- Default mortgage rate: Swiss National Bank (SNB) data portal, cube zikrepro, published interest rates on variable-rate mortgages, mean value, latest month 2026-06. https://data.snb.ch/en/topics/ziredev/cube/zikrepro
- Both series are embedded in `index.html` as JSON (data accessed 2026-08-28 and 2026-08-30); the page makes no data requests at run time.

## Files and technology

- `index.html`: the whole application in one file: HTML, CSS, JavaScript and the embedded data. The only external resource is Plotly.js 3.5.1, loaded from cdnjs (https://cdnjs.cloudflare.com/ajax/libs/plotly.js/3.5.1/plotly.min.js, MIT licence), so an internet connection is needed for the chart library.
- Hosting: GitHub Pages, served from this repository.

To run it locally, open `index.html` in a browser.

## Use of generative AI

Claude (Anthropic) assisted in writing and refining the data-preparation script, the page and its tests from Eray AKYOL's specification. The hypothesis, the return model and its stated simplifications, the data sets, the country list, the default view and the deployment are his; every version was reviewed and approved by him. The full per-graph disclosure is on the reference page of the portfolio.

## Licence

Code and text of this repository: © 2026 Eray AKYOL, provided for the course submission; reuse with attribution. Data: BIS and SNB terms of use (free reuse with source citation).
