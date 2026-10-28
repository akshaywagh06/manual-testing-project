# Test Summary Report

| Item | Detail |
|---|---|
| Project | Automation Exercise – E-commerce web application |
| URL | https://automationexercise.com |
| Test type | Functional, negative, lower-limit, UI and one mobile-width check; AI-assisted browser execution |
| Executed on | 2026-10-27 |
| Browser | Chromium-based browser; version unresolved (desktop 1366×768, mobile width 375px for TC_UI_002) |
| Portfolio owner | Akshay Wagh |
| Execution attribution | AI-assisted browser run; personal execution by the owner is not verified |

## 1. Results at a glance

| Total | Passed | Failed | Blocked | Pass rate | Bugs |
|---|---|---|---|---|---|
| 39 | 33 | 6 | 0 | 84.6% | 6 |

## 2. Module-wise results

| Module | Total | Passed | Failed |
|---|---|---|---|
| Home | 1 | 1 | 0 |
| Registration | 4 | 3 | 1 |
| Login | 6 | 6 | 0 |
| Contact Us | 2 | 2 | 0 |
| Navigation | 1 | 1 | 0 |
| Products | 2 | 2 | 0 |
| Search | 3 | 1 | 2 |
| Filters | 2 | 2 | 0 |
| Subscription | 2 | 2 | 0 |
| Cart | 7 | 5 | 2 |
| Checkout | 5 | 4 | 1 |
| Reviews | 1 | 1 | 0 |
| UI | 2 | 2 | 0 |
| Account | 1 | 1 | 0 |

## 3. Defect summary

| Severity | Count |
|---|---|
| Critical | 2 |
| High | 2 |
| Medium | 1 |
| Low | 1 |

## 4. Key observations

1. **Business-rule gaps in the cart** – quantity 0 and negative quantities are accepted, producing a negative order total (BUG-001, BUG-003). This is the highest-risk area.
2. **Invalid payment inputs** – the listed card number, CVC and expiry reached simulated order confirmation (BUG-002). Other inputs and real payment processing were not established.
3. **Password-policy concern** – a one-character password was accepted (BUG-004); no approved policy was supplied. Login correctly uses a generic error message and does not reveal whether an email exists (TC_LOGIN_003 passed).
4. **Search clarification** – the results included names without the keyword, which may reflect category/description matching; an unmatched search had no empty-state message (BUG-005, BUG-006).
5. Core happy paths – registration, login/logout, cart, end-to-end order, contact form, filters, subscription and account deletion – all work as expected.

## 5. Recommendation

For a production e-commerce application, quantity limits and payment-input checks would warrant investigation before release. This practice-site run does not justify a formal release decision or a claim that a real payment gateway is vulnerable. Confirm the intended rules, then repeat affected cases. The original severity labels remain local portfolio assessments.

## 6. Exit criteria check

| Criterion | Met? |
|---|---|
| 100% of planned test cases executed | Yes (39/39) |
| No open Critical defects | No (2 open) |
| All defects logged with evidence | Yes |

## 7. Record limitations

Defined-requirement coverage is 16/16; full website coverage is not claimed.
