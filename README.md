# Concord (concord-com)

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
