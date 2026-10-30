# Localytics

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Localytics is a mobile analytics and customer-engagement platform that turns the behavioral signals a mobile app already produces into real-time analytics and personalized, data-driven campaigns across push notifications, in-app messages, and inbox messaging. It serves product, marketing, and engineering teams with segmentation, audience building, and campaign management. Its developer surface is broad but unevenly specified: two real OpenAPI 3.0.3 documents (a Campaigns & Audience API and a Transactional Push API served live at messaging.localytics.com/swagger.json), an MIT-licensed proto3 definition for a bidirectional streaming gRPC push service, and a published JSON Schema for Events API requests — alongside six further production REST APIs (Query/Reporting in HAL+JSON, Profile, Events, Exports, Imports, Places) that are documented only in prose. Everything authenticates with one organization-level API key and secret over HTTP Basic; there is no OAuth, no scopes and no rate-limit response headers anywhere. First-party SDKs cover iOS, Android, Web, Maui, Flutter, React Native, tvOS, Xamarin, Unity, Cordova and Windows. Localytics is an Upland Software product.

**Areas:** Company · MarTech · Mobile Analytics · Push Notifications · Customer Engagement · Marketing Automation · Mobile · Segmentation · Audiences · Event Ingestion · gRPC

## Localytics on APIs.io

Everything profiled for Localytics is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/localytics/](https://apis.io/providers/localytics/)** — or go straight to one of the APIs or properties below.

### APIs (11)

- [Localytics Audiences API](https://apis.io/apis/localytics/localytics-audiences-api/) — Requests relating to audiences
- [Localytics Campaigns API](https://apis.io/apis/localytics/localytics-campaigns-api/) — Requests relating to all channel campaigns
- [Localytics Push Campaigns API](https://apis.io/apis/localytics/localytics-push-campaigns-api/) — Requests relating to push-channel campaigns
- [Localytics Query API](https://apis.io/apis/localytics/localytics-query-api/) — HAL+JSON reporting and analytics API. Run queries over apps, events, sessions, users, profiles and attribution data with metrics, dimensions and conditions;…
- [Localytics Profile API](https://apis.io/apis/localytics/localytics-profile-api/) — Read, create, update and delete user profile attributes used for targeting and segmentation, addressed by customer_id at the org, app or customer scope. No…
- [Localytics Events API](https://apis.io/apis/localytics/localytics-events-api/) — Server-side event ingestion for in-app activity that completes off-device (purchases, fulfilment, backend conversions). Accepts JSON or gzipped JSON up to…
- [Localytics Export APIs](https://apis.io/apis/localytics/localytics-export-apis/) — Bulk export of audiences, profiles and raw analytics logs. Requests return a 302 redirect to a generated export file; audiences must be enabled for export…
- [Localytics Import APIs](https://apis.io/apis/localytics/localytics-import-apis/) — Bulk import of user profiles and audience lists built in external systems (CRM, marketing cloud) into Localytics for targeting and campaign use, with an…
- [Localytics Places API](https://apis.io/apis/localytics/localytics-places-api/) — Point-of-interest sync for location-triggered messaging — upload and manage the geofence/POI set an app monitors. Rate limited to 20 requests per hour and…
- [Localytics Meta API](https://apis.io/apis/localytics/localytics-meta-api/) — Health and documentation endpoints
- [Localytics Push API](https://apis.io/apis/localytics/localytics-push-api/) — Transactional push send endpoints

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [localytics](https://apis.io/servers/localytics/localytics/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Localytics Agentic Access](https://apis.io/agentic-access/localytics/localytics-agentic-access/)

#### JSON Schema (1)

The data models the API reads and writes.

- [Events API Request V1](https://apis.io/schemas/localytics/localytics-events-api-v1/)

#### Collections (3)

Postman and Open Collection request collections.

- [Localytics Campaigns And Audience Audiences API](https://apis.io/collections/localytics/open-localytics-audiences-api/)
- [Localytics And Audience Audiences Campaigns API](https://apis.io/collections/localytics/open-localytics-campaigns-api/)
- [Localytics Campaigns And Audience Audiences Push Campaigns API](https://apis.io/collections/localytics/open-localytics-push-campaigns-api/)

#### Overlays (2)

OpenAPI overlays, including conversational phrasing for each operation.

- [Localytics Campaigns Audiences Overlay](https://apis.io/overlays/localytics/localytics-campaigns-audiences-overlay/)
- [Localytics Transactional Push Overlay](https://apis.io/overlays/localytics/localytics-transactional-push-overlay/)

#### Security (3)

Authentication, trust centre, and vulnerability disclosure.

- [Localytics Authentication](https://apis.io/security/localytics/localytics-authentication/)
- [Localytics Domain Security](https://apis.io/security/localytics/localytics-domain-security/)
- [Localytics Vulnerability Disclosure](https://apis.io/security/localytics/localytics-vulnerability-disclosure/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Localytics Plans Pricing](https://apis.io/plans/localytics/localytics-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Localytics Rate Limits](https://apis.io/rate-limits/localytics/localytics-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.localytics.com/)
- [Documentation](https://docs.localytics.com/dev/)
- [Getting started](https://docs.localytics.com/docs/resources/developer-documentation)
- [API reference](https://docs.localytics.com/campaigns_audiences_api.html)
- [Support](https://www.localytics.com/contact)
- [Blog](https://www.localytics.com/blog)
- [Security](https://www.localytics.com/security)
- [Terms of service](https://www.localytics.com/terms)
- [Privacy policy](https://www.localytics.com/privacy)
- [GitHub](https://github.com/localytics)
- [Status](https://status.localytics.com/)

## API Evangelist rating

**Kin Score 47.7** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 73.2 |
| Contract quality | 49.2 |
| Contract governance | 4.5 |
| Operational transparency | 44.7 |
| Developer ergonomics | 73.2 |
| Access clarity | 27.6 |

**Agent readiness 32.5** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | documented (partial credit) |
| Error Semantics | verified |
| OpenAPI Examples | partial |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | — |
| Operation Distinctiveness | distinct |

**Regulatory alignment 30.4** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/localytics/](https://apis.io/providers/localytics/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Localytics: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/localytics/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
