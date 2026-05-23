# Automated Test Matrix

This matrix maps the automation work to user-facing risk areas. It is written as portfolio evidence without publishing the private source code.

## UI Automation Coverage

| ID | Area | Scenario | Expected result | Automated |
| --- | --- | --- | --- | --- |
| UI-SMOKE-001 | Public routes | Open home page | Home content and brand load | Yes |
| UI-SMOKE-002 | Public routes | Navigate from home to marketplace | Marketplace page loads | Yes |
| UI-SMOKE-003 | Responsive | Open home and marketplace on mobile viewport | Pages render without blocking errors | Yes |
| UI-AUTH-001 | Login | Open login page | Email and password fields are visible and required | Yes |
| UI-AUTH-002 | Registration | Open customer registration page | Required customer fields are visible | Yes |
| UI-AUTH-003 | Registration | Open provider registration intent | Provider account copy is shown | Yes |
| UI-AUTH-004 | Registration | Switch customer role to labour | Labour account copy is shown | Yes |
| UI-AUTH-005 | Login | Use provider login with redirect | Alternate auth link preserves role and redirect values | Yes |
| UI-GUEST-001 | Guest access | Open address manager without login | Login/create-account prompt is shown | Yes |
| UI-GUEST-002 | Guest navigation | Open guest menu | Public navigation links are available | Yes |
| UI-I18N-001 | Localization | Switch shell language to Hindi | Language selector changes page text state | Yes |
| UI-MKT-001 | Marketplace | Search keyword `Plumber` | URL contains keyword query | Yes |
| UI-MKT-002 | Marketplace | Select Cleaning shortcut | Discovery filter is applied | Yes |
| UI-MKT-003 | Marketplace | Apply verified-only filter | URL contains `verifiedOnly=true` | Yes |
| UI-MKT-004 | Marketplace | Sort by lowest price | URL contains `sort=price-low` | Yes |
| UI-MKT-005 | Marketplace | Clear all filters | Query filters are removed | Yes |

## Automation Design

| Layer | Purpose |
| --- | --- |
| Base test setup | Browser creation, base URL handling, viewport handling, cleanup |
| Page objects | Encapsulate page-specific selectors and actions |
| UI actions helper | Central reusable Selenium actions and waits |
| Failure extension | Screenshot capture when a UI test fails |
| Runner script | Starts local frontend and runs the Maven/JUnit suite |

## Manual Tests Still Planned

| ID | Area | Scenario | Priority |
| --- | --- | --- | --- |
| MAN-AUTH-001 | Auth | Register a new customer and verify session state | P0 |
| MAN-AUTH-002 | Auth | Login seeded admin, provider, and customer users | P0 |
| MAN-BOOK-001 | Booking | Customer creates address and books a listed service | P0 |
| MAN-BOOK-002 | Booking | Provider accepts booking and changes status | P1 |
| MAN-PAY-001 | Payments | Customer opens checkout and confirms simulated payment | P1 |
| MAN-REVIEW-001 | Reviews | Customer can review only after completed booking | P1 |
| MAN-ADMIN-001 | Admin | Admin can view finance, provider, dispute, and audit areas | P1 |
