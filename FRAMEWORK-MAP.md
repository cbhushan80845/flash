# Framework Map

Last updated: 2026-05-23

This map explains the private QA automation framework without exposing source code.

## High-Level Structure

```text
qa-automation
  pom.xml
  run-ui-tests.ps1
  src/test/java/com/cob/qa
    core
      BaseUiTest
      UiActions
      ScreenshotOnFailureExtension
    pages
      AddressPage
      AuthPage
      HomePage
      MarketplacePage
      ShellPage
    tests
      AuthFormTest
      AuthRoleIntentTest
      GuestAccessTest
      GuestNavigationTest
      LocalizationTest
      MarketplaceSearchTest
      PublicRouteSmokeTest
```

## Flow Of One UI Test Run

```text
PowerShell runner
  -> starts local frontend
  -> waits for http://127.0.0.1:3202
  -> runs Maven/JUnit tests
  -> creates browser session
  -> opens target route
  -> uses page object methods
  -> performs assertions
  -> captures screenshot if failed
  -> closes browser
  -> stops frontend process
```

## Why This Framework Design Matters

| Design choice | Reason |
| --- | --- |
| Page Object Model | Keeps selectors and page actions away from test assertions |
| Reusable UI actions | Reduces repeated Selenium code and centralizes waits |
| Base test class | Standardizes browser setup, base URL, viewport, and cleanup |
| Screenshot extension | Gives debugging evidence when UI tests fail |
| Local runner | Lets the suite run without deployment |
| Public showcase repo | Provides proof without exposing private source code |

## QA Engineering Decisions

- Used explicit waits for page readiness and dynamic text.
- Kept smoke tests small enough for frequent local execution.
- Split marketplace scenarios into search, shortcut, filter, sort, and clear-filter checks.
- Kept authenticated booking flows as planned manual/next automation because they require stable seeded accounts.
- Protected generated test reports from public sharing because they can expose local machine paths.
