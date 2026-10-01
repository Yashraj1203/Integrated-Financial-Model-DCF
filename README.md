# Titan Company Limited: Integrated Financial Model & DCF Valuation

**FY22A-FY26A actuals, FY27E-FY31E forecast**

A fully linked three-statement model of Titan Company Limited with working-capital, fixed-asset, debt / gold-on-loan / lease schedules, a WACC-based DCF, sensitivity and scenario analysis, integrity checks and a Power BI export.

> Educational / portfolio project. Forecasts and valuation outputs are model-derived from my assumptions. They are not Titan management guidance, investment advice, a research recommendation or a price target.

---

## Deliverables

| File | Description |
|---|---|
| `Titan_Integrated_Financial_Model.xlsx` | The model (2,595 formulas, zero error cells, 23 integrity checks) |
| `Titan_Model_Report.pdf` | 9-page report: architecture, history, forecast, statements, DCF, sensitivities, audit |
| `Titan_PowerBI_Analytics_FY22_FY31_V8.csv` | Flat table exported from the model's `PowerBI_Export` sheet (Base case) |
| `README.md` | This file |

Repository layout:

```text
Titan-Financial-Model/
├── README.md
├── Model/    Titan_Integrated_Financial_Model.xlsx
├── Data/     Titan_PowerBI_Analytics_FY22_FY31.csv
├── Reports/  Titan_Model_Report.pdf
└── Sources/  Titan annual reports FY2022-FY2026 
```

---

## Workbook map

| Sheet | Purpose |
|---|---|
| `Cover`, `Summary` | Navigation, headline outputs, key metrics, charts |
| `Inputs` | **Every assumption**: scenario selector, gold-on-loan switch, valuation inputs, Bear/Base/Bull drivers by year |
| `IS`, `BS`, `CF` | Income statement, balance sheet, cash flow, FY22A-FY31E |
| `Schedules` | Working capital and gold on loan; PP&E, right-of-use and intangibles; borrowings, gold-on-loan interest and leases; treasury and other income; equity roll-forward; ratios |
| `DCF` | WACC, unlevered FCF, 5-year fade, terminal value, equity bridge, exit-multiple cross-check, reverse DCF |
| `Sensitivity` | WACC x terminal growth and WACC x exit multiple (live formulas) |
| `Scenarios` | Bear / Base / Bull comparison (stored snapshot plus live column) |
| `Checks` | Integrity checks and overall status |
| `PowerBI_Export` | Flat, formula-linked table for Power BI |
| `Hist_Data`, `Notes` | As-reported source data; methodology, judgements, sources, defect log |

## Architecture

```text
Inputs -> IS drivers -> Schedules -> CF -> BS -> DCF -> Sensitivity / Scenarios -> Checks / Summary / PowerBI_Export
```

- **One timeline:** columns C-G are FY22A-FY26A and H-L are FY27E-FY31E on every time-series sheet.
- **No plug:** cash comes only from the cash flow statement. Short-term borrowings act as the revolver to hold minimum cash. The balance sheet balances by construction and `Checks` proves it.
- **No circularity:** interest is charged on opening balances; no iterative calculation is needed.
- **Colour code:** blue = input, black = formula, green = cross-sheet link, yellow fill = key control.


## Base-case results (at delivery)

| | Bear | Base | Bull |
|---|---|---|---|
| Revenue FY31E (INR cr) | 128,657 | 166,964 | 188,412 |
| PAT FY31E (INR cr) | 5,711 | 10,454 | 13,676 |
| Value per share, Gordon growth (INR) | 486 | 995 | 1,347 |
| Value per share, exit multiple (INR) | 1,374 | 2,861 | 4,350 |

WACC 11.3%, terminal growth 5.0%, market price INR 4,798.5 (NSE close 21 Sep 2026, from a public quote page; refresh before use). At the model WACC the market price implies an FY31E exit multiple of about 42x EV/EBITDA versus 25x in the Base case, and terminal value is roughly two-thirds of enterprise value, so the result is highly sensitive to WACC, growth and margins.

## Key modelling judgements

- **Gold on loan** is treated as operating by default (netted in working capital, interest deducted from EBIT, not deducted in the equity bridge). Test the debt-like alternative with the switch.
- **EBITDA / EBIT exclude other income.** Treasury assets are added in the equity bridge instead.
- **Leases (Ind AS 116):** lease liabilities are deducted in the bridge and new leases are deducted in unlevered FCF, so lease funding is counted once.
- **Fade period:** five explicit years, then a five-year value-driver fade (growth to terminal rate, reinvestment = g / RONIC), then Gordon growth.
- **Discounting:** year-end convention from the 31-Mar-2026 balance sheet date.


## Sources

- Titan Company Limited Annual Reports FY2021-22 to FY2025-26: consolidated balance sheet, statement of profit and loss, statement of cash flow. FY25 and FY26 re-verified against the FY2025-26 report; Notes 24 and 25 used for calibration.
- Market price and share count are user inputs and should be verified.

## Limitations

- Forecast drivers are illustrative.
- Consolidated only: no segment (jewellery, watches, eyecare) build.
- Q1 FY27 results (reported 7 Aug 2026) are not included.
- Share count (88.78 crore) is approximate; confirm against Note 28 of the annual report.
- Bear / Base / Bull columns are stored values and go stale when inputs change.

## Requirements

Excel 2010 or later (or LibreOffice). No macros, add-ins or iterative calculation. Power BI Desktop is optional for the CSV.

## Disclaimer

This project is for educational and portfolio purposes only. It is not investment advice, a research recommendation, a price target or a representation of Titan Company Limited management forecasts.

## 📄 License

Released under the [MIT License](LICENSE).

---

*Developed by [Yashraj1203](https://github.com/Yashraj1203) — for educational and portfolio purposes only.*
