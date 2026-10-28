# Automation Exercise: QA test portfolio

This repository documents a functional test cycle for [Automation Exercise](https://automationexercise.com), a public e-commerce practice website. It covers account registration, product browsing, cart calculations and the simulated checkout flow.

The useful part of this project is the trail from a test expectation to an observed result: each case has an ID, recorded outcome and screenshot; failed cases link to a report with reproduction steps.

## Recorded results

| Measure | Result |
|---|---:|
| Execution date recorded in the original files | 27 October 2026 |
| Test cases | 39 |
| Passed | 33 |
| Failed | 6 |
| Blocked | 0 |
| Pass rate | 84.6% |
| Logged findings | 6 |
| Feature groups | 14 |
| Defined test requirements with linked cases | 16 of 16 |

These figures describe the supplied execution record, not a new test run. The execution used an AI-assisted browser workflow. This documentation revision does not establish that Akshay personally ran the cases. Personal retesting should be recorded as a separate run, with its own date and evidence.

## What was tested

- Registration, duplicate-email handling, login errors, logout and account deletion.
- Product listings, product details, search, category filters and brand filters.
- Adding and removing cart items, line totals, zero quantity and negative quantity.
- Checkout access, delivery address, required payment fields and a simulated order.
- Contact-form validation, an attachment submission, subscription and a product review.
- Scroll-to-top behaviour and one home-page check at a 375-pixel viewport width.

This is a scoped practice exercise, not coverage of every possible e-commerce case. It does not establish real payment processing, email delivery, full accessibility, load capacity or real-device compatibility.

## Findings worth reviewing

| ID | Recorded observation | Interpretation |
|---|---|---|
| [BUG-001](bug-reports/bug-reports.md#bug-001-cart-accepts-negative-quantity-and-shows-negative-total-rs--1500) | Quantity `-3` produced a cart total of `Rs. -1500`. | Cart validation concern. No refund or financial exploit was tested. |
| [BUG-002](bug-reports/bug-reports.md) | Card `12`, CVC `1`, month `99` and year `1990` reached the order confirmation screen. | Input-validation concern in a simulated checkout, not evidence of a payment-gateway bypass. |
| [BUG-003](bug-reports/bug-reports.md) | Quantity `0` was added to the cart. | Lower quantity limit was not enforced for this input. |
| [BUG-004](bug-reports/bug-reports.md) | Registration accepted the password `1`. | Password-policy review needed; an approved policy was not supplied. |
| [BUG-005](bug-reports/bug-reports.md) | Search for `Top` included two products without “top” in their names. | Search behaviour needs clarification; category or description matching may explain these results. |
| [BUG-006](bug-reports/bug-reports.md) | An unmatched search left an empty results area without a message. | Empty-state usability improvement. |

The original severity and priority labels are retained in the reports for traceability. They are portfolio assessments, not ratings accepted by the website owner.

## Repository layout

```text
automationexercise-manual-testing/
├── README.md
├── docs/
│   ├── test-plan.md
│   ├── test-scenarios.md
│   └── requirement-traceability-matrix.md
├── test-cases/
│   ├── AutomationExercise_Test_Cases.xlsx
│   └── test-cases.md
├── bug-reports/
│   └── bug-reports.md
├── evidence/screenshots/
├── reports/
│   └── test-summary-report.md
├── CHANGELOG.md
└── LICENSE
```

## Reviewing the evidence

1. Read the [test plan](docs/test-plan.md) for scope and the basis of the expected results.
2. Open the [test cases](test-cases/test-cases.md), or download the [workbook](test-cases/AutomationExercise_Test_Cases.xlsx) and filter the **Status** column to **Fail**.
3. Follow each failed case to the [finding report](bug-reports/bug-reports.md). Compare the recorded actual result with its screenshot.
4. Use the [traceability matrix](docs/requirement-traceability-matrix.md) to find related cases. Finish with the [summary report](reports/test-summary-report.md) for limitations and follow-up work.

Screenshots capture page states; they do not independently prove every preceding step, submitted input or network event. No fresh execution was performed for this revision.

## Environment and test data

| Item | Record |
|---|---|
| Site | https://automationexercise.com |
| Browser family | Chromium-based browser |
| Browser version | Unresolved: original files contain both `141.0.7390.37` and `156.0.8078.48`. The original runner record is not included. |
| Desktop viewport | 1366 × 768 |
| Mobile-width viewport | 375 × 812; browser viewport check, not a physical phone |
| Account data | Disposable practice accounts and email addresses |
| Payment data | Dummy card values; no real payment credentials required |

## Test-design notes

Quantity `0` tests the lower limit; `-3` tests a negative input. Quantity `4` checks an ordinary valid quantity, not an upper boundary. Card month `99` and year `1990` are invalid-value tests, not adjacent boundary values. The upper-case email and empty-search cases record behaviour only; their Pass labels do not certify an approved business rule.

## Ownership and use

Portfolio owner: **Akshay Wagh**. The site and its product content belong to their respective owners. This repository is an independent learning exercise and does not imply employment by, or approval from, Automation Exercise.


