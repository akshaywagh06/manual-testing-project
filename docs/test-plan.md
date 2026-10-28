# Test Plan – Automation Exercise

**Version:** 1.1 · **Portfolio owner:** Akshay Wagh · **recorded execution date:** 2026-10-27

## 1. Objective
Check selected customer journeys on a public practice site and document observable validation behaviour. This is not a commissioned release assessment.

## 2. Application under test
- **URL:** https://automationexercise.com – a public practice e-commerce site (clothing store).
- **Modules:** Home, Registration, Login/Logout, Products, Search, Filters, Cart, Checkout & Payment, Contact Us, Subscription, Reviews, Account deletion.

## 3. Scope
**In scope:** functional testing of the modules above, positive and negative scenarios, boundary values for quantity and card fields, basic UI behaviour, one mobile-width check.

**Out of scope:** performance/load testing, real payment gateway, API testing, email delivery, third-party ads, accessibility audit, cross-OS testing.

## 4. Test approach
| Technique | Where used |
|---|---|
| Equivalence partitioning | Email formats, search keywords |
| Lower-limit and invalid-value checks | Quantity 0 and -3; one-character password; invalid expiry month 99 and year 1990. Quantity 4 is a valid-value check, not an upper boundary. |
| Positive / negative testing | Selected account, contact, subscription, cart and payment inputs |
| End-to-end scenario | Register → login → cart → checkout → payment → order placed → delete account |
| Exploratory | Upper-case email login, empty search |

## 5. Environment
| Item | Value |
|---|---|
| Browser | Chromium-based browser; version (156.0.8078.48) | 
| Screen | 1366×768 desktop, 375×812 mobile width |
| Test data | Disposable mailinator.com emails, dummy card 4111 1111 1111 1111 |
| Tools | AI-assisted browser execution; workbook and Markdown reporting; captured screenshots |

## 6. Entry criteria
- Site reachable, test cases reviewed, test data ready.

## 7. Exit criteria
- All planned test cases executed; every failure logged as a bug with evidence; summary report published.

## 8. Defect management
Each bug has ID, summary, severity, priority, steps, expected, actual, environment and screenshot. Severity: Critical / High / Medium / Low. Priority: P1–P3 are suggested relative priorities, not delivery commitments.

## 9. Deliverables
Test plan, test cases (Excel + Markdown), RTM, bug reports, screenshots, test summary report.

## 10. Risks
| Risk | Mitigation |
|---|---|
| Public site may change or go down | Results dated; evidence captured at execution time |
| Ads overlay page elements | Close/skip ads; re-run if blocked |
| Shared test data | Unique email per run; account deleted after test |

