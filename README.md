# Excel Retirement Calculator

An interactive Excel workbook that explores how income, expenses, existing savings, retirement age, and investment assumptions affect a projected retirement savings balance.

Completed by **Joseluis Botello-Esquivel** as part of Zero to Mastery's **The Excel Bootcamp**. This course project demonstrates spreadsheet modeling, Excel formulas, and dashboard presentation as part of my transition into data analytics.

![Retirement calculator dashboard](screenshots/dashboard.png)

## What the workbook does

- Accepts current age, annual income, annual expenses, and existing retirement savings.
- Applies assumptions for inflation, annual income growth, and a flat income tax rate.
- Uses separate pre-retirement and post-retirement investment return selections: conservative (4%), moderate (6%), and aggressive (8%).
- Projects annual savings, investment earnings, retirement withdrawals, and ending balances.
- Displays a dynamic savings chart and an estimated age at which the modeled balance becomes negative.
- Provides a detailed annual schedule behind the dashboard.

## Download and use

1. Download [retirement-calculator.xlsx](retirement-calculator.xlsx) and open it in Microsoft Excel desktop.
2. On **Planner**, update the orange input cells with your scenario values.
3. Set the desired retirement age and choose the pre-retirement and post-retirement return assumptions.
4. Review the projected balance chart and depletion message.
5. Open **Detail** to trace the annual results. Change one assumption at a time to compare outcomes.

Desktop Excel is recommended for the retirement-age control and workbook features. Excel web and other spreadsheet applications have not been tested. If the age control is unavailable, the retirement-age value is stored in Planner cell B2.

## Workbook structure

| Worksheet | Visibility | Purpose |
| --- | --- | --- |
| Planner | Visible | Scenario inputs, assumptions, chart, and summary message |
| Detail | Visible | Annual projection displayed up to the modeled depletion age |
| Calculations | Hidden | Annual income, expenses, contributions, interest, withdrawals, and balance calculations |
| Support | Hidden | Risk-return lookup values and depletion calculations |

## Modeling approach

The model grows working income using the annual income increase assumption and increases expenses using annual inflation. During working years, contributions are calculated as income minus income tax and expenses. Investment earnings are calculated on the beginning savings balance.

**Ending balance = beginning balance + contributions + investment earnings − retirement withdrawals.**

The ending balance becomes the following year's beginning balance. Named ranges connect inputs to the calculations, while `VLOOKUP` maps the risk selections to their assumed return rates. `IF` controls working and retirement calculations, `COUNTIF` supports the depletion estimate, and `OFFSET` defines dynamic chart ranges.

### Example shown in the screenshots

The displayed scenario uses age 29, annual income of $75,000, annual expenses of $60,000, and starting retirement savings of $21,000. Its assumptions are 3% inflation, 4% annual income growth, a 10% income tax rate, and investment returns of 8% before retirement and 4% afterward.

With the retirement-age setting at 61, the saved projection shows approximately **$3.47 million at the end of age 61** and a negative ending balance at age **87**. These results describe the supplied scenario under fixed assumptions; they are not guaranteed outcomes.

![Annual projection detail](screenshots/detail.png)

## Skills demonstrated

- Microsoft Excel and spreadsheet modeling
- Financial modeling and assumption-driven scenario analysis
- Dashboard development and data visualization
- Named ranges and cross-sheet references
- Conditional logic with `IF`
- Lookup formulas with `VLOOKUP`
- Conditional counting with `COUNTIF`
- Dynamic chart ranges with `OFFSET`
- Currency and percentage formatting

## Model limitations and improvement opportunities

- **Retirement timing:** in the supplied scenario, setting retirement age to 61 retains working income, contributions, and the pre-retirement return through age 61. Retirement withdrawals and the post-retirement return begin at age 62. Later projection rows use the previous row's age for this transition. The first projection row has separate logic, so immediate-retirement scenarios need additional testing.
- **Fixed assumptions:** investment returns, inflation, income growth, and the tax rate remain constant. The workbook does not model market volatility, Social Security, pensions, account-specific taxes, investment fees, or unexpected expenses.
- **Finite horizon:** the calculation schedule contains 100 annual periods. The dashboard's “NEVER run out” message means no depletion within that schedule, rather than an unlimited projection.
- **Depletion calculation:** the estimate counts nonnegative ending balances. A future improvement would identify the first negative balance explicitly and handle zero or recovering balances consistently.
- **Further improvements:** clarify retirement timing, add input boundary checks, revise the finite-horizon message, and improve chart labeling.

This is an educational portfolio model, not a personalized retirement recommendation.

## Acknowledgment

Created while completing Zero to Mastery's **The Excel Bootcamp**. The retirement calculator is a guided course project, presented here as evidence of applied Excel learning. No independent extensions beyond the course project are claimed in this documentation.
