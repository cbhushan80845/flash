# Bug And Fix Log

This file records real testing problems found while building the automation suite. It is included to show hands-on QA thinking, not only final pass results.

## BF-001: Registration Role Switch Test Was Fragile

| Field | Detail |
| --- | --- |
| Area | Registration page |
| Type | Automation stability issue |
| Symptom | Role-switch test sometimes failed after selecting Labour from a customer registration URL |
| Root cause | The page object clicked by visible text, which is weaker when the page has repeated navigation/auth labels |
| Fix | Updated the page action to target the exact role query link and wait until the expected role copy appears |
| QA value | Reduced flaky behavior and made the test closer to user intent |

## BF-002: UI Test Runner Waited On The Wrong Startup Condition

| Field | Detail |
| --- | --- |
| Area | Local test execution |
| Type | Environment and runner stability |
| Symptom | Frontend startup check timed out before Selenium tests could begin |
| Root cause | The runner needed strict loopback binding and better frontend startup visibility |
| Fix | Bound the local frontend test server to `127.0.0.1` and added frontend log capture |
| QA value | Made the runner repeatable for local regression execution |

## BF-003: Browser Session Started After Frontend Process Ended

| Field | Detail |
| --- | --- |
| Area | End-to-end test orchestration |
| Type | Test infrastructure issue |
| Symptom | Selenium reported connection refused for all UI tests |
| Root cause | The app server and test execution were not kept in the same controlled session during verification |
| Fix | Verified the reusable runner end to end and hardened it so it starts, waits, runs, and cleans up in one flow |
| QA value | Prevented false test failures caused by test infrastructure instead of product behavior |

## BF-004: Public Portfolio Risk

| Field | Detail |
| --- | --- |
| Area | Resume and LinkedIn sharing |
| Type | Security and ownership |
| Symptom | A normal public repository could expose source code and make the project easy to copy |
| Root cause | Portfolio links often mix proof and implementation |
| Fix | Created a separate documentation-only showcase repository with no app source code |
| QA value | Shows project evidence while protecting implementation ownership |

## What This Demonstrates

- I did not only write happy-path tests.
- I debugged runner, browser, selector, and environment issues.
- I separated product bugs, automation bugs, and infrastructure issues.
- I documented fixes in a way that can be discussed during interviews.
