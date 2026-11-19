# US freelance tax data 2026

State and federal income tax figures for tax year 2026, in JSON, with an official source and a verification date for every file. It is the data behind the calculators on [HourFloor](https://hourfloor.com/), exported from the same files the site renders, so the two never drift apart.

Use it to build a calculator, check your own numbers, or write about state-by-state differences for freelancers and 1099 contractors.

> **Not tax advice.** This is planning data. Each file lists the rules the calculator does not model in `incomeTax.notes`. Check the linked official source before you rely on a figure.

## What's inside

```
federal.json         2026 federal brackets, standard deduction, self-employment tax constants, QBI and retirement limits
index.json           list of states with income tax type, verification date and file path
states/<slug>.json   one file per state (49 states + DC)
LICENSE              CC BY 4.0
```

New Hampshire is not included yet. Its Business Profits Tax and Business Enterprise Tax apply to many self-employed people and are not modeled, so the file would show $0 state tax where that is wrong.

## State files

| Field | Meaning |
| --- | --- |
| `code`, `name`, `slug` | Postal code, name, URL slug |
| `taxYear` | Tax year the file describes (2026) |
| `lastVerified` | Date the figures were last checked against the sources |
| `page` | The HourFloor page that uses this file |
| `incomeTax.type` | `none`, `flat` or `progressive` |
| `incomeTax.base` | What the rate applies to: `federalAGI`, `federalTaxableIncome`, `stateDefinedIncome` or `none` |
| `incomeTax.brackets` | Per filing status (`single`, `mfj`, `hoh`): `over` is the income where the rate starts, `rate` is a decimal. A flat tax is one bracket starting at 0 |
| `incomeTax.standardDeduction`, `personalExemption`, `exemptionCredit` | Dollar amounts per filing status (0 if none). `exemptionCredit` is a credit against tax, not a deduction |
| `incomeTax.valuesYear` | Year the dollar amounts come from, when a state has not yet published indexed 2026 values |
| `incomeTax.notes` | Statute or form behind the figures, and what is not modeled |
| `incomeTax.*Phaseout`, `federalTaxDeduction`, `businessIncomeDeduction`, `grossReceiptsTax`, `taxBenefitRecapture`, `agiAddOnTables`, `fixedAmountOver`, `agiMinimumTax` | State-specific rules, present only where they apply. See [how they are applied](https://hourfloor.com/methodology) |
| `conformity` | Whether the state base allows the deductible half of SE tax, self-employed health insurance, SEP/solo 401(k) contributions and the federal QBI deduction, with a note |
| `localIncomeTax` | Whether cities or counties tax income; `localities` lists the ones the calculator can apply, each with its own sources |
| `estimatedTax` | Who must pay, 2026 due dates, safe harbor and form |
| `businessCosts` | LLC formation fee, annual report, franchise or minimum tax, gross receipts tax (text) |
| `sources` | Official sources (title, URL, date retrieved). Notes name the section or form line each figure comes from |

## Federal file

`selfEmploymentTax` holds the Schedule SE constants (92.35% of net profit, 12.4% Social Security up to the $184,500 wage base, 2.9% Medicare, 0.9% Additional Medicare Tax above the threshold). `incomeTax`, `qbi` and `retirement` hold the 2026 inflation-adjusted amounts. Sources: IRS Rev. Proc. 2025-32, IRS Notice 2025-67, the SSA 2026 fact sheet, IRS Publication 334 and the IRS self-employment tax page.

## Updates

The files are regenerated from the site whenever a figure changes, and every state is re-verified each year when the IRS and the states publish the next year's amounts. The 2027 data will go in a separate repository so that 2026 stays stable.

Found a figure that doesn't match its source? Open an issue with the official link, or use the [corrections page](https://hourfloor.com/corrections).

## License and attribution

[CC BY 4.0](LICENSE). Please credit **HourFloor (hourfloor.com)** with a link to https://hourfloor.com/.

Used by https://hourfloor.com/. Methodology: https://hourfloor.com/methodology.
