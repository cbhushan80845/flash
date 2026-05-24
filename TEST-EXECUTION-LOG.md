# Test Execution Log

This is a short execution summary from the local Selenium/JUnit run. Machine-specific paths and generated reports are not included in the public repository.

## Command

```powershell
powershell -ExecutionPolicy Bypass -File .\run-ui-tests.ps1
```

## Result Summary

```text
Running AuthFormTest
Tests run: 2, Failures: 0, Errors: 0, Skipped: 0

Running AuthRoleIntentTest
Tests run: 3, Failures: 0, Errors: 0, Skipped: 0

Running GuestAccessTest
Tests run: 1, Failures: 0, Errors: 0, Skipped: 0

Running GuestNavigationTest
Tests run: 1, Failures: 0, Errors: 0, Skipped: 0

Running LocalizationTest
Tests run: 1, Failures: 0, Errors: 0, Skipped: 0

Running MarketplaceSearchTest
Tests run: 5, Failures: 0, Errors: 0, Skipped: 0

Running PublicRouteSmokeTest
Tests run: 2, Failures: 0, Errors: 0, Skipped: 0

Results:
Tests run: 15, Failures: 0, Errors: 0, Skipped: 0
BUILD SUCCESS
```

## Notes

- The test suite was executed against a locally started frontend server.
- Generated reports and screenshots are kept out of this public repository.
- Chrome CDP warnings were non-blocking and did not affect the final result.
