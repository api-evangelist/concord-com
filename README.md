# Concord (concord-com)

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
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Concord is a contract lifecycle management (CLM) platform for creating, negotiating, redlining, e-signing, storing, and tracking agreements in one place, with unlimited electronic signatures, automated templates, approval workflows, and reporting.

**Access model (read this first):** Concord exposes a documented REST API at `https://api.concordnow.com/api/rest/1` (UAT/sandbox at `https://uat.concordnow.com/api/rest/1`), authenticated with an API key sent in the `X-API-KEY` header. **API key generation is offered on paid plans only** - free trial / sandbox (UAT) accounts must be upgraded before a key can be issued. Concord's public developer reference is a rendered documentation portal ([api.doc.concordnow.com](https://api.doc.concordnow.com/)) and does **not** publish a machine-readable OpenAPI file, so the OpenAPI in this repo is authored from documented behavior and connector mappings; response schemas and one write operation are modeled and flagged as such. The confirmed endpoints below were validated against the live host, which returns `401 {"statusCode":401,"restCode":"unauthorized"}` without a valid key.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/concord-com/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/concord-com/refs/heads/main/apis.yml)

## Tags

- Contract Management
- Contract Lifecycle Management
- CLM
- Contracts
- Agreements
- E-Signature
- Document Management
- Legal
- Workflow

## Timestamps

- **Created:** 2026-07-12
- **Modified:** 2026-07-12

## APIs

### Concord Agreements API

List an organization's agreements (contracts) and retrieve a single agreement's attachments and members. Read access is confirmed against the live API; write/create operations are not documented in the public developer reference.

- **Human URL:** [https://help.concord.app/concord-api](https://help.concord.app/concord-api)
- **Base URL:** `https://api.concordnow.com/api/rest/1`
- **Confirmed:** `GET /user/me/organizations/{organizationId}/agreements`, `GET /organizations/{organizationId}/agreements/{agreementUid}/attachments`, `GET /organizations/{organizationId}/agreements/{agreementUid}/members`

#### Tags

- Agreements
- Contracts
- CLM

#### Properties

- [Documentation](https://help.concord.app/concord-api)
- [API Reference](https://api.doc.concordnow.com/)
- [OpenAPI](openapi/concord-com-openapi.yml)
- [Postman Collection](collections/concord-com.postman_collection.json)
- [Open Collection](collections/concord-com.opencollection.json)

### Concord Organizations & Users API

Read the authenticated user (`/user/me`), the organizations that user belongs to (`/user/me/organizations`), and per-organization reports, groups, and tags. Concord does not publish a user CRUD or SCIM provisioning API; user identity is surfaced read-only.

- **Human URL:** [https://help.concord.app/concord-api](https://help.concord.app/concord-api)
- **Base URL:** `https://api.concordnow.com/api/rest/1`
- **Confirmed:** `GET /user/me`, `GET /user/me/organizations`, `GET /organizations/{organizationId}/reports`, `GET /organizations/{organizationId}/groups`, `GET /organizations/{organizationId}/tags`

#### Tags

- Organizations
- Users
- Accounts

#### Properties

- [Documentation](https://help.concord.app/concord-api)
- [API Reference](https://api.doc.concordnow.com/)
- [OpenAPI](openapi/concord-com-openapi.yml)
- [Postman Collection](collections/concord-com.postman_collection.json)
- [Open Collection](collections/concord-com.opencollection.json)

### Concord Documents & Attachments API

Retrieve the files (attachments) associated with an agreement. In Concord's model a document is an agreement plus its attachments.

- **Human URL:** [https://help.concord.app/concord-api](https://help.concord.app/concord-api)
- **Base URL:** `https://api.concordnow.com/api/rest/1`
- **Confirmed:** `GET /organizations/{organizationId}/agreements/{agreementUid}/attachments`

#### Tags

- Documents
- Attachments
- Files

#### Properties

- [Documentation](https://help.concord.app/concord-api)
- [OpenAPI](openapi/concord-com-openapi.yml)
- [Postman Collection](collections/concord-com.postman_collection.json)
- [Open Collection](collections/concord-com.opencollection.json)

### Concord Templates API

Generate a document from an automated (Excel-driven) template using an API key and the template UID. **Modeled / unconfirmed:** Concord documents that this capability exists, but the exact request path and body are not published in the crawlable public reference, so the operation is flagged `x-concord-modeled: true` in the OpenAPI and must be verified against a live account.

- **Human URL:** [Create a Document from an Automated Template with the API](https://help.concord.app/hc/en-us/articles/207854166-Create-a-Document-from-an-Automated-Template-with-the-API)
- **Base URL:** `https://api.concordnow.com/api/rest/1`

#### Tags

- Templates
- Document Generation
- Automation

#### Properties

- [Documentation](https://help.concord.app/hc/en-us/articles/207854166-Create-a-Document-from-an-Automated-Template-with-the-API)
- [OpenAPI](openapi/concord-com-openapi.yml)

### Concord Webhooks (Outbound Events)

Concord sends outbound HTTP POST webhooks to a URL you configure in the **Automations > Integrations** UI, firing on agreement lifecycle events - document fully approved, document fully signed, document expired, and signature provided. Webhooks are configured in the UI, **not** via a REST management endpoint; payloads carry the impacted agreement plus the triggering user.

- **Human URL:** [Create a Webhook Integration](https://help.concord.app/hc/en-us/articles/4417525871508-create-a-webhook-integration)
- **Base URL:** `https://api.concordnow.com/api/rest/1`

#### Tags

- Webhooks
- Events
- Notifications

#### Properties

- [Documentation](https://help.concord.app/hc/en-us/articles/4417525871508-create-a-webhook-integration)

## Common Properties

- [Domain Security](security/concord-com-domain-security.yml)
- [Authentication](authentication/concord-com-authentication.yml)
- [Website](https://www.concord.app)
- [Documentation](https://help.concord.app/concord-api)
- [LinkedIn](https://www.linkedin.com/company/concordnow)
- [Plans](plans/concord-com-plans-pricing.yml)
- [Rate Limits](rate-limits/concord-com-rate-limits.yml)
- [Fin Ops](finops/concord-com-finops.yml)

## Authentication

API key in the `X-API-KEY` header. Keys are generated inside a Concord account on **paid plans only**. The live production host returns `401 {"statusCode":401,"restCode":"unauthorized"}` when called without a valid key.

## WebSocket Review

**Does Concord expose a documented public WebSocket API? No.** Concord's own public API is request/response REST over HTTPS plus UI-configured outbound webhooks (HTTP POST). No `ws://`/`wss://` endpoint is documented, and no AsyncAPI document was authored. See [review.yml](review.yml).

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
