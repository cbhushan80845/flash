# QA Execution Summary

Environment: Local Windows machine, Chrome browser, Java 17, Maven, Selenium WebDriver

## Verified Command

The UI suite was executed through the local QA runner:

```powershell
powershell -ExecutionPolicy Bypass -File .\run-ui-tests.ps1
```

The runner starts the local frontend test server, waits for the application to become available, then executes the Selenium/JUnit suite through Maven.

## Final Selenium Result

```text
Tests run: 15, Failures: 0, Errors: 0, Skipped: 0
BUILD SUCCESS
Total time: 51.628 s
Finished at: 2026-05-23T19:01:21+05:30
```

## Test Classes Executed

| Test class | Tests | Result |
| --- | ---: | --- |
| AuthFormTest | 2 | Passed |
| AuthRoleIntentTest | 3 | Passed |
| GuestAccessTest | 1 | Passed |
| GuestNavigationTest | 1 | Passed |
| LocalizationTest | 1 | Passed |
| MarketplaceSearchTest | 5 | Passed |
| PublicRouteSmokeTest | 2 | Passed |

## Stability Fixes Made During Automation

| Issue found | Fix applied |
| --- | --- |
| Role-switch UI test was clicking by visible text and could be fragile | Updated page object to click the exact role query link and wait for expected page copy |
| UI runner waited on port 3202 while frontend startup needed stricter loopback binding | Updated runner to bind the frontend to `127.0.0.1` |
| Frontend startup failures were hard to diagnose | Added frontend stdout/stderr log capture in the runner |
| Generated test reports could expose local machine paths | Cleaned generated target output after verification and kept reports out of the public showcase |

## Non-Blocking Runtime Note

Chrome printed Selenium CDP version warnings for browser version 148. The warnings did not fail the tests, and the full suite completed successfully.

## Why Source Is Not Included

This public repository contains the case study documents only. The private project contains the application and automation source code.
