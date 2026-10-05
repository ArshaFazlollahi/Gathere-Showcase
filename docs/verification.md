# Verification record

Snapshot: October 4, 2026. Results refer to my private application implementation,
not executable code in this documentation-only repository.

## Latest implementation checkpoint

| Check | Observed result |
| --- | --- |
| Backend regression suite | 368 tests passed; 1 test had a setup error in the main run |
| Isolated rerun of affected backend test | Passed; the original error was a disk-I/O failure in a Windows-mounted test SQLite database |
| Frontend tests | 24 passed |
| Frontend production build | TypeScript and Vite build passed |
| Local API health during showcase capture | Reported healthy |
| Existing city feed during desktop capture | 208 upcoming records displayed |
| University of Waterloo feed during capture | 41 upcoming records returned |
| Desktop screenshot gallery | 7 landscape captures from a 1440 × 900 browser viewport |

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

I captured screenshots using existing live-demo records. I did not need a new
scraping run, AI spend, invented event, private-account access, or database reset
to produce them. The displayed listing counts are a point-in-time observation, not
a completeness benchmark.

## Reproducibility boundary

My full application's private README documents Docker Compose startup and
configuration. I intentionally exclude source, environment files, container
definitions, credentials, detailed fixtures, and runnable application packages
from this showcase. Recruiters can [contact me on GitHub](https://github.com/ArshaFazlollahi)
to request a walkthrough.

For a future production launch, provider integration tests, load tests, security
review, accessibility review, and source-permission checks would supplement these
development checks.
