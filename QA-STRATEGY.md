# QA Strategy

This document explains the testing approach used for the private COB Platform project while keeping implementation details protected.

## Testing Goals

- Validate high-risk public user journeys before deeper authenticated flows.
- Keep the local regression suite fast enough for repeated execution.
- Use UI automation where browser behavior, routing, forms, and query parameters matter.
- Keep manual candidates documented for flows that require stable backend state and seeded accounts.

## Risk-Based Prioritization

| Priority | Area | Why it matters |
| --- | --- | --- |
| P0 | Public route smoke | Broken public pages block all users and recruiters from seeing the product |
| P0 | Auth forms | Login/register are entry points for every role |
| P0 | Marketplace search/filter | Core discovery journey for customers |
| P1 | Guest access | Unauthorized users should see clear login/create-account prompts |
| P1 | Localization | Language selector should not break shell rendering |
| P1 | Responsive rendering | Mobile viewport issues affect real user traffic |
| P2 | Full booking/payment | Needs stable test data and backend orchestration |

## What Was Automated First

- Public route smoke coverage.
- Login and registration form structure.
- Role intent behavior for registration/login.
- Guest prompts and public navigation.
- Marketplace search, shortcut, filter, sort, and clear-filter behavior.
- Mobile viewport checks for public pages.

## What Was Kept Manual For Now

- Full customer registration with persisted session.
- Seeded role login for customer, provider, and admin.
- Address creation.
- Service detail to booking flow.
- Provider booking acceptance.
- Payment and review eligibility.

## Automation Standards

| Standard | Practice |
| --- | --- |
| Maintainability | Page Object Model for selectors and page behavior |
| Stability | Explicit waits for visible elements and dynamic copy |
| Debugging | Screenshot capture on failed UI tests |
| Repeatability | Local runner starts frontend and runs Maven/JUnit suite |
| Evidence | Execution logs, test matrix, and bug/fix notes documented |

## Expansion Plan

1. Add API setup for seeded users and test data.
2. Add authenticated customer address flow.
3. Add service booking flow.
4. Add provider accept/reject booking flow.
5. Add admin dashboard smoke checks.
6. Add CI execution once the project is ready to expose workflow metadata safely.
