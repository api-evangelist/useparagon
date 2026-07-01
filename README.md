# Paragon (useparagon)

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
