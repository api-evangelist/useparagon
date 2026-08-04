# Paragon (useparagon)

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

Paragon is an embedded integration platform (embedded iPaaS) that lets B2B SaaS companies build and ship native, third-party integrations inside their own product. Developers use the Connect SDK/Portal plus a REST API (Connect API, ActionKit, and Managed Sync) to authenticate end users into 130+ SaaS providers, trigger workflows, run agentic actions, and ingest normalized third-party data.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/useparagon/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/useparagon/refs/heads/main/apis.yml)

Nearly all requests are authenticated with a Paragon User Token — an RS256-signed JWT that your application signs with the private signing key from the Paragon dashboard (Settings > SDK Setup) and that Paragon verifies with the matching public key. In production, most developers use Paragon's Connect SDK and Connect Portal, which sit in front of these APIs; the raw HTTP surface documented here is used for server-side and headless integrations.

## Tags

- Integration
- iPaaS
- Embedded Integrations
- Workflows
- ActionKit
- Managed Sync
- AI Agents

## Timestamps

- **Created:** 2026-07-01
- **Modified:** 2026-07-01

## APIs

### Paragon Connect API

The Connect API manages authenticated end users and their connected third-party credentials for a Paragon project. Requests are authenticated with a Paragon User Token (an RS256-signed JWT) and target `/projects/{projectId}/sdk/...` paths for resource connection and user state. In practice the Connect SDK and Connect Portal are the primary front-ends over this API.

- **Human URL:** [https://docs.useparagon.com/api/making-api-requests](https://docs.useparagon.com/api/making-api-requests)
- **Base URL:** `https://zeus.useparagon.com`

#### Tags

- Connect
- Authentication
- Credentials

#### Properties

- [Documentation](https://docs.useparagon.com/api/making-api-requests)
- [API Reference](https://docs.useparagon.com/resources/api-resources)
- [OpenAPI](openapi/useparagon-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/useparagon.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/useparagon.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Paragon Integrations API

Returns the list of integrations enabled for a Paragon project, including Connect Portal configuration and associated workflows, so applications can render available connectors and their state.

- **Human URL:** [https://docs.useparagon.com/resources/api-resources](https://docs.useparagon.com/resources/api-resources)
- **Base URL:** `https://zeus.useparagon.com`

#### Tags

- Integrations
- Connectors
- Metadata

#### Properties

- [Documentation](https://docs.useparagon.com/resources/api-resources)
- [OpenAPI](openapi/useparagon-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/useparagon.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/useparagon.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Paragon Users API

Retrieves the currently authenticated user and their connected integration state (the same data surfaced by the SDK `getUser()` method), keyed by the user id embedded in the Paragon User Token.

- **Human URL:** [https://docs.useparagon.com/resources/api-resources](https://docs.useparagon.com/resources/api-resources)
- **Base URL:** `https://zeus.useparagon.com`

#### Tags

- Users
- Connected Accounts
- State

#### Properties

- [Documentation](https://docs.useparagon.com/resources/api-resources)
- [OpenAPI](openapi/useparagon-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/useparagon.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/useparagon.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Paragon Workflows API

Triggers Paragon workflows over HTTP (API Trigger) and checks workflow execution status. Workflows can be started from application events, CRON schedules, third-party webhooks, or an authenticated HTTP request carrying a Paragon User Token.

- **Human URL:** [https://docs.useparagon.com/workflows/triggers](https://docs.useparagon.com/workflows/triggers)
- **Base URL:** `https://zeus.useparagon.com`

#### Tags

- Workflows
- Triggers
- Automation

#### Properties

- [Documentation](https://docs.useparagon.com/workflows/triggers)
- [OpenAPI](openapi/useparagon-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/useparagon.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/useparagon.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Paragon Proxy API

A passthrough proxy that forwards requests to a connected user's third-party API without your application handling that provider's OAuth tokens. Requests go to `/projects/{projectId}/sdk/proxy/{integrationType}/{apiPath}` and Paragon injects the user's stored credentials. Also available at `proxy.useparagon.com`.

- **Human URL:** [https://docs.useparagon.com/api/making-api-requests](https://docs.useparagon.com/api/making-api-requests)
- **Base URL:** `https://zeus.useparagon.com`

#### Tags

- Proxy
- Passthrough
- Third-Party APIs

#### Properties

- [Documentation](https://docs.useparagon.com/api/making-api-requests)
- [OpenAPI](openapi/useparagon-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/useparagon.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/useparagon.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Paragon ActionKit API

ActionKit exposes thousands of prebuilt, LLM-ready actions across 130+ SaaS providers as a single API for AI agents. List available actions with `GET /projects/{projectId}/actions` and execute one with `POST /projects/{projectId}/actions/run` by passing an action name (e.g. `SLACK_SEND_MESSAGE`) and parameters.

- **Human URL:** [https://docs.useparagon.com/actionkit/overview](https://docs.useparagon.com/actionkit/overview)
- **Base URL:** `https://actionkit.useparagon.com`

#### Tags

- ActionKit
- AI Agents
- Actions

#### Properties

- [Documentation](https://docs.useparagon.com/actionkit/overview)
- [OpenAPI](openapi/useparagon-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/useparagon.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/useparagon.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Paragon Managed Sync API

Managed Sync provides fully managed, normalized third-party data ingestion pipelines. The Sync API enables full CRM, ticketing, file-storage, and accounting ingestions with a couple of calls (create sync, pull records) plus `record_updated` webhooks for change data capture; requests target `sync.useparagon.com` / `managed-sync.useparagon.com`.

- **Human URL:** [https://docs.useparagon.com/learn/managed-sync](https://docs.useparagon.com/learn/managed-sync)
- **Base URL:** `https://sync.useparagon.com`

#### Tags

- Managed Sync
- Data Ingestion
- CDC

#### Properties

- [Documentation](https://docs.useparagon.com/learn/managed-sync)
- [OpenAPI](openapi/useparagon-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/useparagon.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/useparagon.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Paragon Permissions API

The Permissions API enforces the underlying source-of-truth access control on data ingested through Managed Sync, letting applications check whether a user/role can access a given object before surfacing synced records (for example, to power permission-aware RAG).

- **Human URL:** [https://www.useparagon.com/product/permissions-api](https://www.useparagon.com/product/permissions-api)
- **Base URL:** `https://managed-sync.useparagon.com`

#### Tags

- Permissions
- Access Control
- Managed Sync

#### Properties

- [Documentation](https://www.useparagon.com/product/permissions-api)
- [OpenAPI](openapi/useparagon-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/useparagon.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/useparagon.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Paragon Events and Webhooks API

Paragon delivers outbound event webhooks (such as `record_updated` from Managed Sync and workflow/integration lifecycle events) to your application's registered endpoints so you can react to changes in connected accounts and synced data. This surface is webhook/event-driven rather than a request/response REST resource.

- **Human URL:** [https://docs.useparagon.com/resources/api-resources](https://docs.useparagon.com/resources/api-resources)
- **Base URL:** `https://zeus.useparagon.com`

#### Tags

- Events
- Webhooks
- Notifications

#### Properties

- [Documentation](https://docs.useparagon.com/resources/api-resources)
- [OpenAPI](openapi/useparagon-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/useparagon.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/useparagon.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [GitHub Organization](https://github.com/useparagon)
- [LinkedIn](https://www.linkedin.com/company/useparagon)
- [Website](https://www.useparagon.com/)
- [Documentation](https://docs.useparagon.com/)
- [Plans](plans/useparagon-plans-pricing.yml)
- [Rate Limits](rate-limits/useparagon-rate-limits.yml)
- [Fin Ops](finops/useparagon-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
