# Verification record

Snapshot: October 4, 2026. Results refer to the private application implementation,
not executable code in this documentation-only repository.

## Latest implementation checkpoint

| Check | Observed result |
| --- | --- |
| Backend regression suite | 368 tests passed; 1 test had a setup error in the main run |
| Isolated rerun of affected backend test | Passed; the original error was a disk-I/O failure in a Windows-mounted test SQLite database |
| Frontend tests | 24 passed |
| Frontend production build | TypeScript and Vite build passed |
| Local API health during showcase capture | Reported healthy |
| Existing city feed during capture | 209 upcoming records returned |
| University of Waterloo feed during capture | 41 upcoming records returned |

In total, 369 backend cases were covered across the main run and isolated retry.
This is not presented as a clean 369-pass single invocation, a coverage percentage,
or a guarantee of production behavior. No test logs or database dumps are published.

## Areas exercised by regression work

- Source verification, individual-event extraction, and rejection of non-event content.
- Source-backed dates, recurring schedules, title quality, and duplicate handling.
- Campus calendars, affiliation checks, feed isolation, and discovery failure handling.
- AI/provider quotas, fallback routing, batching, and truncated-output handling.
- Thumbnail source selection and curated fallback assignment.
- Frontend location preferences, event-location display, and dropdown behavior.

Screenshots were captured from existing live-demo records. No new scraping run,
AI spend, invented event, private-account access, or database reset was needed to
produce them. The displayed listing counts are a point-in-time observation, not
a completeness benchmark.

## Reproducibility boundary

The full application's private README documents Docker Compose startup and
configuration. This showcase intentionally excludes source, environment files,
container definitions, credentials, detailed fixtures, and runnable application
packages. A recruiter can request a walkthrough through the owner's GitHub profile.

For a future production launch, provider integration tests, load tests, security
review, accessibility review, and source-permission checks would supplement these
development checks.
