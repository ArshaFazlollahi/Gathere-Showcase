# Engineering case study

## Problem

Local plans are spread across venue calendars, student organizations, event
platforms, articles, and public social posts. A useful discovery interface needs
more than search-result snippets: it needs specific activities, believable
schedules, usable locations, clear summaries, and links back to evidence.

I built Gathere to explore that problem in a local full-stack demo. The initial coverage is
Ontario, with separate city and campus discovery experiences.

## Design decisions and lessons

### 1. Source facts before AI polish

Search and model availability are unreliable external dependencies. The pipeline
therefore preserves conservative records supported by explicit publisher facts,
then applies AI enrichment to make them easier to understand. Partial enrichment
does not have to mean an empty feed. The UI communicates degraded discovery
instead of representing a failed provider call as complete coverage.

### 2. A calendar is not an event

A month guide or "things to do" article can contain many activities. Treating
the document as a single event produces misleading titles and sprawling
descriptions. Validation and extraction work at the individual activity level,
while keeping the source article as evidence where a direct event link is absent.
Regression cases cover generic/date-only titles and grouped event descriptions.

### 3. Identity and schedule are separate problems

One event can appear on multiple sites with different subsets of its dates.
Deduplication cannot rely solely on matching a title and one date. Conversely,
related events should not be collapsed simply because they share a festival or
venue. Publisher-backed occurrences and provenance are retained separately, and
the card selects an upcoming occurrence as time advances.

### 4. Campus discovery needs its own context

A school selection is not just a city filter. Public institution and student-life
sources must support affiliation, and campus-life categories differ from general
city browsing. The backend preserves these affiliations and keeps campus-linked
events out of the city feed. The interface maintains independent view state.

### 5. A varied thumbnail can still be the wrong thumbnail

Official photography is preferred. When it is missing or unusable, a hand-curated
catalog provides illustrative defaults. Category alone is too broad: food photos,
for example, should not indiscriminately substitute ice cream for a BBQ. Topic
compatibility is considered before balancing usage across suitable alternatives.
Default assignments aim to remain stable rather than reshuffling every refresh.

### 6. Free-tier reliability is a resource-management problem

Model output truncation, a slow batch, per-model exhaustion, and a provider-wide
quota are different failure modes. The routing layer distinguishes them, can use
ranked alternatives across OpenRouter, Groq, and Mistral, and bounds retries.
Free-tier eligibility and limits remain provider-controlled; the application
cannot guarantee permanent free availability or unrestricted extraction.

## Product and technical scope

The demo combines a dark-first React/TypeScript interface with Python/FastAPI,
PostgreSQL, and Docker Compose. It includes live refresh progress, source links,
filters, sorting, saved plans, theme switching, and responsive layouts.

It is not a production deployment. Public-only coverage can miss events, source
layouts can change, image URLs can fail, and organizer details can be updated.
Authentication, production monitoring, legal review of data usage, deployment
hardening, and load testing would require additional work before a public launch.

I developed the application with AI-assisted tooling and assessed it through
automated regression tests and manual source/UI checks. My [verification record](verification.md)
states what I checked and its limitations.
