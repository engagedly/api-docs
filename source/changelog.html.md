---
title: Engagedly API — Changelog
search: true
---

<!-- Mirrors the repo-root CHANGELOG.md for API consumers; keep the two in sync. -->

# Changelog

All notable changes to the Engagedly API and its documentation, newest first.
Format follows [Keep a Changelog](https://keepachangelog.com/) and [Semantic Versioning](https://semver.org/).

**Versioning:** `0.1.0` captures the pre-1.0 history (2017–2025). `1.0.0` onward is actively versioned; a version is assigned only when a change is released. Roadmap items that aren't built yet sit under **Planned** with no version. These numbers version the API and its docs as published here; the API is currently served at the `/beta` endpoint, independently of the changelog version.

## Planned

- **Rate limits** — a request-throttling policy (limits, `X-RateLimit-*` response headers, and `429 Too Many Requests` behavior). Docs will follow once the policy is finalized.

## 1.2.0 — Unreleased

- **Added** — a site favicon (the Engagedly brand icon).
- **Added** — an Error Codes reference table (in HTTP Status Codes) documenting `missing_field` and `duplicate_value`.
- **Added** — a navigation header (logo + Guides / API Reference / Changelog / OpenAPI tabs, plus GitHub and engagedly.com icon links). Guides is now the landing page, the API Reference moved to `/references.html`, and Changelog and OpenAPI pages were added.
- **Added** — an OpenAPI tab rendering an OpenAPI 3.0 spec of the full API (via Redoc), with downloadable OpenAPI spec and Postman collection.
- **Added** — Learning endpoints documented on the `/beta` surface: `GET /beta/learning/resources` (list courses and playlists) and `GET /beta/learning/resources/{id}/contents` (course/playlist content hierarchy), across the API Reference, OpenAPI, and Postman collection.
- **Changed** — moved the Introduction onto the Guides landing page; the API Reference now opens at Getting Started.
- **Changed** — migrated the Learner Report from `GET /learning/v1/reports` to `GET /beta/learning/learner_reports`; the internal `type`/`filter`/`scope` parameters are no longer part of the request.

## 1.1.0 — 2026-07-08

- **Changed** — upgraded Ruby 2.3.1 → 3.4.9 and Middleman 4.2.1 → 4.6.3; modernized the full gem stack; moved to Bundler 2.
- **Changed** — replaced the icon webfont with inline-SVG icons.
- **Security** — patched nokogiri, rack, and redcarpet; resolved the ActiveSupport `SafeBuffer#%` XSS advisory (activesupport 8.1.3).
- **Added** — RuboCop linting.
- **Removed** — the unused `therubyracer`/`libv8` dependency and several redundant repo files.

## 1.0.0 — 2026-07-08

- **Changed** — automated build & deploy via GitHub Actions to GitHub Pages.

## 0.1.0 — Initial development (2017–2025)

Pre-1.0 history, before changes were formally versioned. Notable additions, newest first:

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
