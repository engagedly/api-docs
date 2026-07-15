---
title: Engagedly API — Changelog
search: true
---

<!-- API/endpoint-facing changes only. The COMPLETE changelog — including docs-site,
     navigation, tooling, dependency, and build changes — lives in the repository's
     CHANGELOG.md. Do not mirror those non-API entries here. -->

# Changelog

Notable changes to the Engagedly API, newest first. This page lists only changes
that affect the API itself — new or changed endpoints, parameters, responses,
authentication, rate limits, and error contracts. Documentation-site, tooling,
dependency, and build changes are recorded in the repository's `CHANGELOG.md`.

**Versioning:** follows [Semantic Versioning](https://semver.org/); a version is
assigned only when a change is released. The API is currently served at the
`/beta` endpoint, independently of the changelog version.

## 1.2.0 — Unreleased

- **Added** — an Error Codes reference table (in HTTP Status Codes) documenting `missing_field` and `duplicate_value`.
- **Added** — Learning endpoints on the `/beta` surface: `GET /beta/learning/resources` (list courses and playlists), `GET /beta/learning/resources/{id}/contents` (course/playlist content hierarchy), and `GET /beta/learning/learner_reports` (org-wide learner report).
- **Added** — rate limiting on the `/beta` APIs: 200 requests/minute per API credential (`ClientKey`), shared across all `/beta` endpoints, `X-RateLimit-*` response headers, and `429 Too Many Requests` with an escalating cooldown (starting at 1 minute) and a `Retry-After` header.

## 1.1.0 — 2026-07-08

_No API-related changes in this release._

## 1.0.0 — 2026-07-08

_No API-related changes in this release._

## 0.1.0 — Initial development (2017–2025)

Pre-1.0 history, before changes were formally versioned. Notable API additions, newest first:

- **2025-12-15** — Custom fields support in the User APIs.
- **2023-10-18** — User PATCH API for partially updating a user.
- **2023-06-21** — Endpoint for block reason codes; deactivation accepts a `block_reason_code`.
- **2020-12-14** — Additional email filter for the List Users API.
- **2020-10-29** — Business Unit CRUD endpoints and Business Unit support in the Users API.
- **2020-02-14** — `manager_id` added to User Attributes and the Users API.
- **2019-10-23** — Updated the Praises API response.
- **2019-10-17** — Pagination for the Praises API; additional user attributes.
- **2017-11-21** — Permissions API and profile-picture API.
- **2017-06-13** — Departments, Job Titles, and Locations APIs.
- **2017-05-04** — Initial Engagedly API documentation.
