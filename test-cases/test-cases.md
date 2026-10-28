# Test Cases – Automation Exercise

> Executed on **2026-10-27** · **Chromium-based browser; version unresolved** · desktop 1366×768.
> These are historical results from an AI-assisted browser run, not a newly completed personal run. The conflicting browser versions are documented in the README.
> The same data is available as a filterable Excel sheet: [`AutomationExercise_Test_Cases.xlsx`](AutomationExercise_Test_Cases.xlsx).

## Home

### TC_HOME_001 – Verify home page loads with navigation

| Field | Detail |
|---|---|
| Requirement | REQ-01 |
| Priority | High |
| Technique | Smoke |
| Precondition | None |
| Steps | 1. Open https://automationexercise.com |
| Test data | - |
| Expected | Page title is 'Automation Exercise'; header menu visible |
| Actual | Page title was 'Automation Exercise' and the header navigation was visible. |
| Status | Pass |
| Evidence | [TC_HOME_001.png](../evidence/screenshots/TC_HOME_001.png) |

## Registration

### TC_REG_001 – Register a new user with valid details

| Field | Detail |
|---|---|
| Requirement | REQ-02 |
| Priority | High |
| Technique | Positive |
| Precondition | Email not registered |
| Steps | 1. Click Signup / Login<br>2. Enter name + new email, click Signup<br>3. Fill all account and address fields<br>4. Click Create Account<br>5. Click Continue |
| Test data | Name: Akshay QA; Email: unique; Pwd: Test@12345; City: Pune; Zip: 411001 |
| Expected | 'ACCOUNT CREATED!' shown; header shows 'Logged in as <name>' |
| Actual | 'Account Created!' shown, header shows 'Logged in as Akshay QA 095509' |
| Status | Pass |
| Evidence | [TC_REG_001.png](../evidence/screenshots/TC_REG_001.png) |

### TC_REG_002 – Register with an already registered email

| Field | Detail |
|---|---|
| Requirement | REQ-02 |
| Priority | High |
| Technique | Negative |
| Precondition | Account exists |
| Steps | 1. Open Signup / Login<br>2. Enter name and the existing email<br>3. Click Signup |
| Test data | Existing email |
| Expected | Error 'Email Address already exist!' is shown |
| Actual | Error 'Email Address already exist!' displayed |
| Status | Pass |
| Evidence | [TC_REG_002.png](../evidence/screenshots/TC_REG_002.png) |

### TC_REG_003 – Signup with invalid email format

| Field | Detail |
|---|---|
| Requirement | REQ-02 |
| Priority | Medium |
| Technique | Negative / EP |
| Precondition | None |
| Steps | 1. Open Signup / Login<br>2. Enter email without '@'<br>3. Click Signup |
| Test data | akshay.invalid |
| Expected | Form not submitted; email format validation message shown |
| Actual | Browser validation: 'Please include an '@' in the email address. 'akshay.invalid' is missing an '@'.'; stayed on https://automationexercise.com/login |
| Status | Pass |
| Evidence | [TC_REG_003.png](../evidence/screenshots/TC_REG_003.png) |

### TC_REG_004 – Password strength rule on signup

| Field | Detail |
|---|---|
| Requirement | REQ-03 |
| Priority | High |
| Technique | Negative / BVA |
| Precondition | None |
| Steps | 1. Start signup with a new email<br>2. Enter password '1'<br>3. Fill other fields and Create Account |
| Test data | Password: 1 |
| Expected | Weak password rejected with a password policy message |
| Actual | Registration accepted the one-character password '1'; the approved password policy was not supplied. |
| Status | Fail → BUG-004 |
| Evidence | [TC_REG_004.png](../evidence/screenshots/TC_REG_004.png) |

## Login

### TC_LOGIN_001 – Login with valid credentials

| Field | Detail |
|---|---|
| Requirement | REQ-04 |
| Priority | High |
| Technique | Positive |
| Precondition | Registered user |
| Steps | 1. Open Signup / Login<br>2. Enter valid email and password<br>3. Click Login |
| Test data | Registered email / Test@12345 |
| Expected | User logged in; 'Logged in as <name>' shown |
| Actual | Header shows 'Logged in as Akshay QA 095509' |
| Status | Pass |
| Evidence | [TC_LOGIN_001.png](../evidence/screenshots/TC_LOGIN_001.png) |

### TC_LOGIN_002 – Login with wrong password

| Field | Detail |
|---|---|
| Requirement | REQ-04 |
| Priority | High |
| Technique | Negative |
| Precondition | Registered user |
| Steps | 1. Enter valid email and wrong password<br>2. Click Login |
| Test data | Wrong@999 |
| Expected | Error 'Your email or password is incorrect!' |
| Actual | Error 'Your email or password is incorrect!' displayed |
| Status | Pass |
| Evidence | [TC_LOGIN_002.png](../evidence/screenshots/TC_LOGIN_002.png) |

### TC_LOGIN_003 – Login with unregistered email

| Field | Detail |
|---|---|
| Requirement | REQ-04 |
| Priority | Medium |
| Technique | Negative / Security |
| Precondition | None |
| Steps | 1. Enter unregistered email and any password<br>2. Click Login |
| Test data | notregistered_x@mailinator.com |
| Expected | Same generic error; site does not reveal whether email exists |
| Actual | Generic error shown (does not reveal whether email exists) |
| Status | Pass |
| Evidence | [TC_LOGIN_003.png](../evidence/screenshots/TC_LOGIN_003.png) |

### TC_LOGIN_004 – Login with empty fields

| Field | Detail |
|---|---|
| Requirement | REQ-04 |
| Priority | Medium |
| Technique | Negative |
| Precondition | None |
| Steps | 1. Leave both fields empty<br>2. Click Login |
| Test data | - |
| Expected | Required-field validation shown; no request sent |
| Actual | Browser validation on email: 'Please fill out this field.' |
| Status | Pass |
| Evidence | [TC_LOGIN_004.png](../evidence/screenshots/TC_LOGIN_004.png) |

### TC_LOGIN_005 – Login with email in upper case

| Field | Detail |
|---|---|
| Requirement | REQ-04 |
| Priority | Low |
| Technique | Exploratory |
| Precondition | Registered user |
| Steps | 1. Enter registered email in UPPER CASE with valid password<br>2. Click Login |
| Test data | AKSHAY.QA...@MAILINATOR.COM |
| Expected | Behaviour recorded (emails are commonly case-insensitive) |
| Actual | Upper-case email login rejected (informational - behaviour recorded) |
| Status | Pass |
| Evidence | [TC_LOGIN_005.png](../evidence/screenshots/TC_LOGIN_005.png) |

### TC_LOGIN_006 – Logout returns user to login page

| Field | Detail |
|---|---|
| Requirement | REQ-05 |
| Priority | High |
| Technique | Positive |
| Precondition | Logged in |
| Steps | 1. Login<br>2. Click Logout |
| Test data | - |
| Expected | Redirect to /login; 'Logged in as' no longer shown |
| Actual | Returned to the login page; the logged-in user label was absent. |
| Status | Pass |
| Evidence | [TC_LOGIN_006.png](../evidence/screenshots/TC_LOGIN_006.png) |

## Contact Us

### TC_CONTACT_001 – Submit contact form with attachment

| Field | Detail |
|---|---|
| Requirement | REQ-06 |
| Priority | Medium |
| Technique | Positive |
| Precondition | None |
| Steps | 1. Open Contact us<br>2. Fill name, email, subject, message<br>3. Upload a file<br>4. Submit and accept the confirm dialog |
| Test data | sample_upload.txt |
| Expected | 'Success! Your details have been submitted successfully.' |
| Actual | Message: 'Success! Your details have been submitted successfully.' |
| Status | Pass |
| Evidence | [TC_CONTACT_001.png](../evidence/screenshots/TC_CONTACT_001.png) |

### TC_CONTACT_002 – Submit contact form without email

| Field | Detail |
|---|---|
| Requirement | REQ-06 |
| Priority | Medium |
| Technique | Negative |
| Precondition | None |
| Steps | 1. Fill only name<br>2. Click Submit |
| Test data | - |
| Expected | Required-field validation on Email |
| Actual | Browser validation on email: 'Please fill out this field.' |
| Status | Pass |
| Evidence | [TC_CONTACT_002.png](../evidence/screenshots/TC_CONTACT_002.png) |

## Navigation

### TC_NAV_001 – Open Test Cases page from header

| Field | Detail |
|---|---|
| Requirement | REQ-01 |
| Priority | Low |
| Technique | Positive |
| Precondition | None |
| Steps | 1. Click 'Test Cases' in header |
| Test data | - |
| Expected | /test_cases page opens |
| Actual | Navigated to https://automationexercise.com/test_cases |
| Status | Pass |
| Evidence | [TC_NAV_001.png](../evidence/screenshots/TC_NAV_001.png) |

## Products

### TC_PROD_001 – View all products list

| Field | Detail |
|---|---|
| Requirement | REQ-07 |
| Priority | High |
| Technique | Positive |
| Precondition | None |
| Steps | 1. Click Products |
| Test data | - |
| Expected | 'ALL PRODUCTS' heading with product cards |
| Actual | Heading 'ALL PRODUCTS', 34 products listed |
| Status | Pass |
| Evidence | [TC_PROD_001.png](../evidence/screenshots/TC_PROD_001.png) |

### TC_PROD_002 – View product detail page

| Field | Detail |
|---|---|
| Requirement | REQ-07 |
| Priority | High |
| Technique | Positive |
| Precondition | None |
| Steps | 1. Open Products<br>2. Click 'View Product' on first item |
| Test data | Product id 1 |
| Expected | Name, category, price, availability, condition, brand shown |
| Actual | All fields shown: name, category, price, availability, condition, brand |
| Status | Pass |
| Evidence | [TC_PROD_002.png](../evidence/screenshots/TC_PROD_002.png) |

## Search

### TC_SEARCH_001 – Search results match keyword

| Field | Detail |
|---|---|
| Requirement | REQ-08 |
| Priority | High |
| Technique | Positive |
| Precondition | None |
| Steps | 1. Open Products<br>2. Search 'Top' |
| Test data | Top |
| Expected | Every result is related to 'Top' |
| Actual | 14 results; results whose name lacks 'top': ['Little Girls Mr. Panda Shirt', 'Colour Blocked Shirt – Sky Blue'] |
| Status | Fail → BUG-005 |
| Evidence | [TC_SEARCH_001.png](../evidence/screenshots/TC_SEARCH_001.png) |

### TC_SEARCH_002 – Search with no matching product

| Field | Detail |
|---|---|
| Requirement | REQ-08 |
| Priority | Medium |
| Technique | Negative |
| Precondition | None |
| Steps | 1. Open Products<br>2. Search 'xyzqwe123' |
| Test data | xyzqwe123 |
| Expected | 0 results and a 'No products found' message |
| Actual | No products were listed and no empty-results message was shown. |
| Status | Fail → BUG-006 |
| Evidence | [TC_SEARCH_002.png](../evidence/screenshots/TC_SEARCH_002.png) |

### TC_SEARCH_003 – Search with empty keyword

| Field | Detail |
|---|---|
| Requirement | REQ-08 |
| Priority | Low |
| Technique | Exploratory |
| Precondition | None |
| Steps | 1. Open Products<br>2. Click search with empty box |
| Test data | (empty) |
| Expected | Behaviour recorded |
| Actual | Empty search submitted; page shows 34 products (informational) |
| Status | Pass |
| Evidence | [TC_SEARCH_003.png](../evidence/screenshots/TC_SEARCH_003.png) |

## Filters

### TC_FILTER_001 – Filter by category Women > Dress

| Field | Detail |
|---|---|
| Requirement | REQ-09 |
| Priority | Medium |
| Technique | Positive |
| Precondition | None |
| Steps | 1. Open Products<br>2. Expand Women<br>3. Click Dress |
| Test data | - |
| Expected | Heading 'WOMEN - DRESS PRODUCTS' |
| Actual | Heading 'WOMEN - DRESS PRODUCTS' |
| Status | Pass |
| Evidence | [TC_FILTER_001.png](../evidence/screenshots/TC_FILTER_001.png) |

### TC_FILTER_002 – Filter by brand Polo

| Field | Detail |
|---|---|
| Requirement | REQ-09 |
| Priority | Medium |
| Technique | Positive |
| Precondition | None |
| Steps | 1. Open Products<br>2. Click brand Polo |
| Test data | - |
| Expected | Heading 'BRAND - POLO PRODUCTS' and Polo products |
| Actual | Heading 'BRAND - POLO PRODUCTS', 6 products |
| Status | Pass |
| Evidence | [TC_FILTER_002.png](../evidence/screenshots/TC_FILTER_002.png) |

## Subscription

### TC_SUB_001 – Subscribe with valid email

| Field | Detail |
|---|---|
| Requirement | REQ-10 |
| Priority | Low |
| Technique | Positive |
| Precondition | None |
| Steps | 1. Scroll to footer<br>2. Enter email, click arrow |
| Test data | akshay.sub@mailinator.com |
| Expected | 'You have been successfully subscribed!' |
| Actual | Message: 'You have been successfully subscribed!' |
| Status | Pass |
| Evidence | [TC_SUB_001.png](../evidence/screenshots/TC_SUB_001.png) |

### TC_SUB_002 – Subscribe with invalid email

| Field | Detail |
|---|---|
| Requirement | REQ-10 |
| Priority | Low |
| Technique | Negative |
| Precondition | None |
| Steps | 1. Enter 'abc' in subscription<br>2. Click arrow |
| Test data | abc |
| Expected | Email format validation shown |
| Actual | Browser validation: 'Please include an '@' in the email address. 'abc' is missing an '@'.' |
| Status | Pass |
| Evidence | [TC_SUB_002.png](../evidence/screenshots/TC_SUB_002.png) |

## Cart

### TC_CART_001 – Add two products to cart

| Field | Detail |
|---|---|
| Requirement | REQ-11 |
| Priority | High |
| Technique | Positive |
| Precondition | None |
| Steps | 1. Products > Add to cart (item 1) > Continue<br>2. Add item 2<br>3. Open Cart |
| Test data | Items 1, 2 |
| Expected | Both products listed in cart |
| Actual | 2 rows in cart |
| Status | Pass |
| Evidence | [TC_CART_001.png](../evidence/screenshots/TC_CART_001.png) |

### TC_CART_002 – Cart total = price x quantity

| Field | Detail |
|---|---|
| Requirement | REQ-11 |
| Priority | High |
| Technique | Positive |
| Precondition | Items in cart |
| Steps | 1. Add items 1 and 2<br>2. Open Cart<br>3. Compare price, quantity, total |
| Test data | - |
| Expected | Total equals price x quantity for each row |
| Actual | Price x Qty = Total: 500x1=500, 400x1=400 |
| Status | Pass |
| Evidence | [TC_CART_002.png](../evidence/screenshots/TC_CART_002.png) |

### TC_CART_003 – Add product with quantity 4

| Field | Detail |
|---|---|
| Requirement | REQ-12 |
| Priority | Medium |
| Technique | Positive / BVA |
| Precondition | None |
| Steps | 1. Open product 1<br>2. Set quantity 4<br>3. Add to cart, open Cart |
| Test data | Qty 4 |
| Expected | Cart shows quantity 4 |
| Actual | Cart quantity = 4 |
| Status | Pass |
| Evidence | [TC_CART_003.png](../evidence/screenshots/TC_CART_003.png) |

### TC_CART_004 – Add product with quantity 0

| Field | Detail |
|---|---|
| Requirement | REQ-12 |
| Priority | High |
| Technique | Negative / BVA |
| Precondition | None |
| Steps | 1. Open product 1<br>2. Set quantity 0<br>3. Add to cart, open Cart |
| Test data | Qty 0 |
| Expected | Rejected with validation; nothing added |
| Actual | The added-to-cart message appeared; one cart row showed quantity 0. |
| Status | Fail → BUG-003 |
| Evidence | [TC_CART_004.png](../evidence/screenshots/TC_CART_004.png) |

### TC_CART_005 – Add product with negative quantity

| Field | Detail |
|---|---|
| Requirement | REQ-12 |
| Priority | High |
| Technique | Negative / BVA |
| Precondition | None |
| Steps | 1. Open product 1<br>2. Set quantity -3<br>3. Add to cart, open Cart |
| Test data | Qty -3 |
| Expected | Rejected; cart never shows negative quantity or total |
| Actual | One cart row showed quantity -3 and a total of Rs. -1500. |
| Status | Fail → BUG-001 |
| Evidence | [TC_CART_005.png](../evidence/screenshots/TC_CART_005.png) |

### TC_CART_006 – Remove product from cart

| Field | Detail |
|---|---|
| Requirement | REQ-11 |
| Priority | High |
| Technique | Positive |
| Precondition | Item in cart |
| Steps | 1. Add item<br>2. Open Cart<br>3. Click X |
| Test data | - |
| Expected | 'Cart is empty!' shown |
| Actual | 'Cart is empty!' shown |
| Status | Pass |
| Evidence | [TC_CART_006.png](../evidence/screenshots/TC_CART_006.png) |

### TC_CART_007 – Add recommended item from home

| Field | Detail |
|---|---|
| Requirement | REQ-11 |
| Priority | Low |
| Technique | Positive |
| Precondition | None |
| Steps | 1. Scroll to Recommended Items<br>2. Add to cart > View Cart |
| Test data | - |
| Expected | Item appears in cart |
| Actual | 1 recommended item(s) in cart |
| Status | Pass |
| Evidence | [TC_CART_007.png](../evidence/screenshots/TC_CART_007.png) |

## Checkout

### TC_CHK_001 – Checkout without login

| Field | Detail |
|---|---|
| Requirement | REQ-13 |
| Priority | High |
| Technique | Negative |
| Precondition | Item in cart, logged out |
| Steps | 1. Open Cart<br>2. Click Proceed To Checkout |
| Test data | - |
| Expected | Modal asks to Register / Login |
| Actual | Modal: ' Checkout  Register / Login account to proceed on checkout.  Register / Login  Continue On Cart' |
| Status | Pass |
| Evidence | [TC_CHK_001.png](../evidence/screenshots/TC_CHK_001.png) |

### TC_CHK_002 – Delivery address matches registration

| Field | Detail |
|---|---|
| Requirement | REQ-13 |
| Priority | High |
| Technique | Positive |
| Precondition | Logged in, item in cart |
| Steps | 1. Login, add item<br>2. Proceed To Checkout<br>3. Check delivery address |
| Test data | Pune 411001 |
| Expected | Address equals registration details |
| Actual | Delivery address matches registration (Pune 411001) |
| Status | Pass |
| Evidence | [TC_CHK_002.png](../evidence/screenshots/TC_CHK_002.png) |

### TC_CHK_003 – Pay with empty card fields

| Field | Detail |
|---|---|
| Requirement | REQ-14 |
| Priority | High |
| Technique | Negative |
| Precondition | Logged in |
| Steps | 1. Open payment page<br>2. Click Pay and Confirm Order |
| Test data | - |
| Expected | Required-field validation on card fields |
| Actual | Browser validation on Name on Card: 'Please fill out this field.' |
| Status | Pass |
| Evidence | [TC_CHK_003.png](../evidence/screenshots/TC_CHK_003.png) |

### TC_CHK_004 – Pay with invalid card details

| Field | Detail |
|---|---|
| Requirement | REQ-14 |
| Priority | Critical |
| Technique | Negative / BVA |
| Precondition | Logged in |
| Steps | 1. Open payment page<br>2. Enter invalid card data<br>3. Click Pay |
| Test data | Card 12, CVC 1, Month 99, Year 1990 |
| Expected | Payment rejected with card validation errors |
| Actual | Order confirmation was shown for card '12', CVC '1', month '99' and year '1990'. |
| Status | Fail → BUG-002 |
| Evidence | [TC_CHK_004.png](../evidence/screenshots/TC_CHK_004.png) |

### TC_CHK_005 – Place order end-to-end

| Field | Detail |
|---|---|
| Requirement | REQ-13, REQ-14 |
| Priority | Critical |
| Technique | Positive / E2E |
| Precondition | Logged in, item in cart |
| Steps | 1. Cart > Checkout<br>2. Add comment, Place Order<br>3. Enter valid card, Pay |
| Test data | 4111111111111111 / 123 / 12 / 2030 |
| Expected | 'ORDER PLACED!' shown with Download Invoice |
| Actual | The order confirmation and Download Invoice link were shown; no real charge was verified. |
| Status | Pass |
| Evidence | [TC_CHK_005.png](../evidence/screenshots/TC_CHK_005.png) |

## Reviews

### TC_REV_001 – Submit product review

| Field | Detail |
|---|---|
| Requirement | REQ-15 |
| Priority | Low |
| Technique | Positive |
| Precondition | None |
| Steps | 1. Open product 2<br>2. Fill name, email, review<br>3. Submit |
| Test data | - |
| Expected | 'Thank you for your review.' |
| Actual | Message: 'Thank you for your review.' |
| Status | Pass |
| Evidence | [TC_REV_001.png](../evidence/screenshots/TC_REV_001.png) |

## UI

### TC_UI_001 – Scroll-up arrow returns to top

| Field | Detail |
|---|---|
| Requirement | REQ-16 |
| Priority | Low |
| Technique | Positive |
| Precondition | None |
| Steps | 1. Scroll to bottom of home<br>2. Click arrow |
| Test data | - |
| Expected | Page scrolls to top |
| Actual | After clicking arrow, scrollY = 0 |
| Status | Pass |
| Evidence | [TC_UI_001.png](../evidence/screenshots/TC_UI_001.png) |

### TC_UI_002 – Home page at mobile width 375px

| Field | Detail |
|---|---|
| Requirement | REQ-16 |
| Priority | Medium |
| Technique | Compatibility |
| Precondition | None |
| Steps | 1. Set viewport 375 x 812<br>2. Open home |
| Test data | - |
| Expected | No horizontal scrolling |
| Actual | At 375px width page scrollWidth = 375px (horizontal scroll absent) |
| Status | Pass |
| Evidence | [TC_UI_002.png](../evidence/screenshots/TC_UI_002.png) |

## Account

### TC_ACC_001 – Delete account

| Field | Detail |
|---|---|
| Requirement | REQ-05 |
| Priority | High |
| Technique | Positive |
| Precondition | Logged in |
| Steps | 1. Login<br>2. Click Delete Account<br>3. Try to login again |
| Test data | - |
| Expected | 'ACCOUNT DELETED!'; re-login fails |
| Actual | The account deletion confirmation appeared and another login attempt was rejected. |
| Status | Pass |
| Evidence | [TC_ACC_001.png](../evidence/screenshots/TC_ACC_001.png) |


## Reading the status labels

Pass and Fail preserve the original run. TC_LOGIN_005 and TC_SEARCH_003 were informational behaviour checks: Pass means the observation was recorded, not that a confirmed requirement was satisfied. Failures against password, payment and search expectations need specification review.
