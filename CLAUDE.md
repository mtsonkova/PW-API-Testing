# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

No npm scripts are defined yet. Use Playwright CLI directly:

```bash
npx playwright test                        # Run all tests
npx playwright test tests/example.spec.ts  # Run a single test file
npx playwright test --headed               # Run with visible browser
npx playwright test --debug                # Interactive debug mode
npx playwright show-report                 # Open HTML test report
```

## Architecture

This is a Playwright test automation project (TypeScript) focused on API and browser testing.

**Configuration** (`playwright.config.ts`):
- Tests live in `./tests/`
- `fullyParallel: true` — all tests run in parallel by default
- CI mode (detected via `process.env.CI`): 2 retries, single worker, `forbidOnly` enforced
- Local mode: no retries, unlimited workers
- Browsers: Chromium, Firefox, WebKit
- Reporter: HTML (`playwright-report/`)
- Tracing: enabled on first retry for debugging
- `baseURL` and web server startup are currently commented out in config — set these when testing against a specific app

**Test structure**: Tests go in `./tests/*.spec.ts`. The existing `example.spec.ts` contains placeholder tests from Playwright's default setup.
