# Requirement Traceability Matrix (RTM)

The REQ entries are test expectations derived from visible features and common e-commerce behaviour. No approved specification was supplied. Password, search and payment expectations need confirmation from the site owner.

| Req ID | Requirement | Test Cases | Result |
|---|---|---|---|
| REQ-01 | Home page and site navigation | TC_HOME_001, TC_NAV_001 | Passed |
| REQ-02 | New user registration | TC_REG_001, TC_REG_002, TC_REG_003 | Passed |
| REQ-03 | Password security policy | TC_REG_004 | Failed |
| REQ-04 | User login | TC_LOGIN_001, TC_LOGIN_002, TC_LOGIN_003, TC_LOGIN_004, TC_LOGIN_005 | Passed |
| REQ-05 | Logout and account deletion | TC_LOGIN_006, TC_ACC_001 | Passed |
| REQ-06 | Contact Us form | TC_CONTACT_001, TC_CONTACT_002 | Passed |
| REQ-07 | Product listing and details | TC_PROD_001, TC_PROD_002 | Passed |
| REQ-08 | Product search | TC_SEARCH_001, TC_SEARCH_002, TC_SEARCH_003 | Failed |
| REQ-09 | Category and brand filters | TC_FILTER_001, TC_FILTER_002 | Passed |
| REQ-10 | Newsletter subscription | TC_SUB_001, TC_SUB_002 | Passed |
| REQ-11 | Shopping cart management | TC_CART_001, TC_CART_002, TC_CART_006, TC_CART_007 | Passed |
| REQ-12 | Product quantity validation | TC_CART_003, TC_CART_004, TC_CART_005 | Failed |
| REQ-13 | Checkout flow | TC_CHK_001, TC_CHK_002, TC_CHK_005 | Passed |
| REQ-14 | Payment validation | TC_CHK_003, TC_CHK_004, TC_CHK_005 | Failed |
| REQ-15 | Product reviews | TC_REV_001 | Passed |
| REQ-16 | UI behaviour and responsiveness | TC_UI_001, TC_UI_002 | Passed |

**Defined-requirement coverage:** 16/16 entries have linked cases. This is not 100% coverage of the website. Result labels reproduce the original run; a mixed group is Failed when at least one linked case failed.
