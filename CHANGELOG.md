# Engagedly API — Changelog

All notable changes to the Engagedly API and its documentation are recorded here, newest first.
Format follows [Keep a Changelog](https://keepachangelog.com/) and [Semantic Versioning](https://semver.org/).

> This is the **complete** changelog (endpoints, docs-site, tooling, dependencies, build). The
> published changelog on the docs site (`source/changelog.html.md`) is a curated subset listing
> only **API/endpoint-facing** changes. The two are intentionally not mirrors — do not sync them.

**Versioning:** `0.1.0` captures the pre-1.0 development history (2017–2025, before changes were formally versioned). `1.0.0` onward is actively versioned. A version is assigned only when a change is **released**; roadmap items that aren't built yet stay under **Planned** with no version. These numbers version the Engagedly API and its documentation as published here; the API itself is currently served at the `/beta` endpoint, independently of the changelog version.

## [1.2.0] — Unreleased
### Added
- A site favicon (the Engagedly brand icon).
- An **Error Codes** reference table (in HTTP Status Codes) documenting `missing_field` and `duplicate_value`.
- A top navigation **header** (logo + **Guides / API Reference / Changelog** tabs, plus LinkedIn and engagedly.com icon links); logo moved from the sidebar into the header. Split into multiple pages: **Guides** is the landing (`/` redirects to it), and **Changelog** was added as its own page.
- **Learning** endpoints documented on the `/beta` surface: `GET /beta/learning/resources` (list courses and playlists), `GET /beta/learning/resources/{id}/contents` (course/playlist content hierarchy), and `GET /beta/learning/learner_reports` (org-wide learner report), on the API Reference and Postman collection.
- **Rate limiting** on the `/beta` APIs: 100 requests/minute per API credential per endpoint, `X-RateLimit-Limit`/`X-RateLimit-Remaining`/`X-RateLimit-Reset` response headers, and `429 Too Many Requests` with an escalating cooldown (starting at 1 minute) and a `Retry-After` header. Documented in the API Reference and Postman collection.
### Changed
- **API Reference** is now rendered directly from the OpenAPI 3.0 spec via Redoc (themed to match the site), replacing the previous hand-authored Slate page; downloadable **OpenAPI spec** and **Postman collection** links are on the page. The Redoc sidebar groups *Getting Started* (Authentication, Requests, Responses & pagination, Rate limiting, HTTP status codes, Errors) under one collapsible parent, matching the prior page's structure.
- Replaced the header's **GitHub** icon link with **LinkedIn**.
### Removed
- The standalone **OpenAPI** tab — its Redoc-rendered content now lives at **API Reference** directly. The previous hand-authored API Reference content still exists at `/old_page.html`, unlinked from navigation (direct URL only), kept for reference during the transition.

## [1.1.0] — 2026-07-08
### Changed
- Upgraded **Ruby 2.3.1 → 3.4.9** and **Middleman 4.2.1 → 4.6.3**, modernizing the full gem stack (activesupport, nokogiri, rack, rouge, redcarpet, haml, …); moved to Bundler 2.
- Replaced the IcoMoon icon **webfont with inline-SVG icons** (CSS `mask` + `currentColor`) for the notice/warning callouts and search box.
### Security
- Updated nokogiri, rack, and redcarpet to patched releases, resolving the outstanding Dependabot advisories.
- Resolved the ActiveSupport XSS advisory (CVE-2026-33170 / GHSA-89vf-4333-qx8v) — activesupport now 8.1.3 (past the patched 8.1.2.1).
### Added
- RuboCop linting.
### Removed
- Unused `therubyracer`/`libv8` dependency, and redundant repo files (`.travis.yml`, `_config.yml`, `deploy.sh`, `Vagrantfile`, `lib/nesting_unique_head.rb`).

## [1.0.0] — 2026-07-08
### Changed
- Updated deployment configuration (automated build & deploy via GitHub Actions to GitHub Pages).

## [0.1.0] — Initial development (2017–2025)

Pre-1.0 history, before changes were formally versioned. Notable changes, newest first:

- **2025-12-15** — Custom fields support in the User APIs.
- **2023-10-18** — User **PATCH** API for partially updating an existing user.
- **2023-06-21** — Endpoint to retrieve block reason codes; user deactivation now accepts a `block_reason_code`.
- **2020-12-14** — Additional email filter for the List Users API.
- **2020-10-29** — Business Unit CRUD endpoints, and Business Unit support in the Users API.
- **2020-02-14** — `manager_id` field added to the User Attributes list and the Users API.
- **2019-10-23** — Updated the Praises API response.
- **2019-10-17** — Pagination for the Praises API; additional attributes in the Users and Update User APIs.
- **2017-11-21** — Permissions API and profile-picture API; Users API enhancements.
- **2017-07-14** — Updated API endpoints.
- **2017-06-13** — Departments, Job Titles, and Locations APIs.
- **2017-05-04** — Initial Engagedly API documentation (Users and core resources).

<!--
"## Planned"               = roadmap items not yet built (no version).
"## [x.y.z] — Unreleased"  = code built but not yet released (add the date on release).
"## [x.y.z] — YYYY-MM-DD"  = a released version (newest first).
Subheadings as needed: Added, Changed, Deprecated, Removed, Fixed, Security.
-->
