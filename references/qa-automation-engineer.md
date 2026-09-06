# QA Automation Engineer / QA Senior Engineer

## Core responsibilities

- Define the overall test strategy for a feature or product: what's covered by unit, integration, end-to-end, and manual testing, and why.
- Build and maintain automation frameworks that the wider team can extend, not just write one-off scripts.
- Integrate automated tests into CI/CD so failures block bad releases rather than being discovered after the fact.
- Balance automation coverage against maintenance cost — not everything should be automated, especially flaky, low-value UI paths.
- Own test data management and environment stability, which is often the real source of "flaky tests."
- (Senior) Set quality standards and metrics for the org, mentor other QA engineers, and represent quality risk in release decisions.

## Key competencies

- **Test pyramid thinking**: many fast unit tests, fewer integration tests, a small number of high-value end-to-end tests — and knowing when a team has inverted this (an "ice cream cone" of slow, flaky UI tests) and why that's a problem.
- **UI automation**: Selenium, Playwright, or Cypress — page object model or component-based patterns to keep tests maintainable as the UI changes.
- **API automation**: REST Assured, Postman/Newman, or equivalent — testing contracts, status codes, schema validation, and negative/error cases, not just the happy path.
- **BDD where it adds value**: Cucumber/Gherkin for tests that benefit from being readable by non-engineers (e.g. product/business stakeholders), used deliberately rather than everywhere.
- **Performance and load testing**: JMeter, Gatling, or k6 — defining realistic load profiles and meaningful pass/fail thresholds (latency percentiles, not just averages).
- **CI/CD integration**: running the right test subset at the right stage (fast tests on every commit, full regression before release), Jenkins/GitHub Actions/Azure DevOps/GitLab CI pipelines.
- **Test data management**: synthetic data generation, data seeding/teardown strategy, avoiding tests that depend on shared mutable state.
- **Defect management**: writing reproducible bug reports, triaging severity/priority, tracking escape rate (bugs that reached production despite testing).
- **Shift-left practices**: involving QA in design/requirements review so testability is designed in, not bolted on.

## Checklist for reviewing a test strategy or automation suite

- [ ] Does the test pyramid shape make sense for this system, or is there over-reliance on slow, flaky end-to-end tests?
- [ ] Are tests independent and repeatable (no shared state, no execution-order dependency)?
- [ ] Do API tests cover negative cases and error responses, not just the 200 OK path?
- [ ] Is there a clear owner and process for fixing flaky tests, rather than letting them get silently skipped or ignored?
- [ ] Are tests running in CI, and do they actually block merge/release on failure?
- [ ] Is test data isolated per test/run, avoiding collisions between parallel test executions?
- [ ] For performance tests: are thresholds based on real SLAs/percentiles, not arbitrary numbers?

## Common interview topics at this level

- Designing a test strategy for a given feature (what to automate, what to leave manual, and why).
- Debugging a flaky test — likely causes and how to fix each one.
- API testing scenario: what would you test on a given endpoint besides the happy path?
- Framework design: how to structure a Selenium/Playwright suite so it survives UI changes.
- Metrics: how do you measure whether QA/automation is actually working (escape rate, coverage, flake rate, cycle time)?

## Expected deliverable shape

A test strategy document (scope, test levels, tools, environments, entry/exit criteria) for anything non-trivial, plus the automation code itself for concrete asks. Feedback given "as" this role should call out specific coverage gaps (e.g. "no negative test for an expired token on this endpoint") and flag maintainability risk in the automation code itself, not just missing test cases.
