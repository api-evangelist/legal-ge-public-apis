# legal.ge Public APIs (legal-ge-public-apis)

Georgia's (the country's) legal marketplace, exposing a public, keyless, read-only REST API that turns a natural-language description of a legal problem into matched practice areas and a ranked list of verified specialists — lawyers, law firms, accountants, tax consultants, mediators and enforcement agents — each with a canonical, locale-prefixed profile URL. The surface is deliberately agent-first: an OpenAPI 3.1 contract at /api/openapi.json, an APIs.json 0.19 index at /apis.json, an llms.txt trust contract at /llms.txt, a robots.txt that names and allows eleven AI crawlers on the public API paths, and an installable MCP server (@legalge/mcp, MIT) exposing find_legal_specialists and classify_legal_intent to Claude Desktop, Cursor and any MCP-aware client. Trilingual across Georgian, English and Russian; every specialist returned is verification-checked, and contact details are opt-in only.

**APIs.json:** [https://legal-ge-public-apis.apievangelist.com/apis.yml](https://legal-ge-public-apis.apievangelist.com/apis.yml)

## Tags

- legal
- law
- legal-services
- directory
- georgia
- ai-agents
- mcp
- model-context-protocol
- specialists
- professional-services
- marketplace
- multilingual
- legal-tech

## Timestamps

- **Created:** 2026-08-09
- **Modified:** 2026-08-09

## APIs

### legal.ge Public APIs Directory API

Look up services, practice areas and verified specialists on legal.ge.

- **Human URL:** [https://legal.ge](https://legal.ge)
- **Base URL:** `https://legal.ge`

#### Tags

- Directory

#### Properties

- [OpenAPI](openapi/legal-ge-public-apis-directory-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/legal-ge-public-apis-directory-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/legal-ge-public-apis-directory-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Documentation](https://legal.ge/llms.txt)
- [Authentication](authentication/legal-ge-public-apis-authentication.yml)
- [Conventions](conventions/legal-ge-public-apis-conventions.yml)
- [Error Catalog](errors/legal-ge-public-apis-problem-types.yml)
- [Rate Limits](rate-limits/legal-ge-public-apis-rate-limits.yml)
- [Data Model](data-model/legal-ge-public-apis-data-model.yml)
- [Examples](examples/legal-ge-public-apis-examples.yml)
- [Terms of Service](https://legal.ge/terms)
- [Tool Crosswalk](mcp/legal-ge-public-apis-tool-crosswalk.yml)
- [Documentation](https://github.com/infolegalge/legal.ge-mcp)
- [Packages](https://www.npmjs.com/package/@legalge/mcp)

### legal.ge Public APIs Matching API

Map a free-text legal question to practice areas, and optionally to ranked verified specialists.

- **Human URL:** [https://legal.ge](https://legal.ge)
- **Base URL:** `https://legal.ge`

#### Tags

- Matching

#### Properties

- [OpenAPI](openapi/legal-ge-public-apis-matching-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/legal-ge-public-apis-matching-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/legal-ge-public-apis-matching-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Documentation](https://legal.ge/llms.txt)
- [Authentication](authentication/legal-ge-public-apis-authentication.yml)
- [Conventions](conventions/legal-ge-public-apis-conventions.yml)
- [Error Catalog](errors/legal-ge-public-apis-problem-types.yml)
- [Rate Limits](rate-limits/legal-ge-public-apis-rate-limits.yml)
- [Data Model](data-model/legal-ge-public-apis-data-model.yml)
- [Examples](examples/legal-ge-public-apis-examples.yml)
- [Terms of Service](https://legal.ge/terms)
- [Tool Crosswalk](mcp/legal-ge-public-apis-tool-crosswalk.yml)
- [Documentation](https://github.com/infolegalge/legal.ge-mcp)
- [Packages](https://www.npmjs.com/package/@legalge/mcp)

## Common Properties

- [Domain Security](security/legal-ge-public-apis-domain-security.yml)
- [Agentic Access](agentic-access/legal-ge-public-apis-agentic-access.yml)
- [Documentation](https://legal.ge/llms.txt)
- [API Reference](https://legal.ge/api/openapi.json)
- [GitHub Organization](https://github.com/infolegalge)
- [Support](https://legal.ge/en/contact)
- [Blog](https://legal.ge/en/news)
- [Pricing](https://legal.ge/en/pricing)
- [Sign Up](https://legal.ge/en/register)
- [Login](https://legal.ge/en/login)
- [Terms of Service](https://legal.ge/terms)
- [Privacy Policy](https://legal.ge/privacy)
- [OpenAPI](openapi/_original/legal-ge-public-apis-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [L L Ms Txt](llms/legal-ge-public-apis-llms.txt)
- [M C P Server](mcp/legal-ge-public-apis-mcp.yml)
- [Tool Crosswalk](mcp/legal-ge-public-apis-tool-crosswalk.yml)
- [Agent Skill](skills/_index.yml)
- [Authentication](authentication/legal-ge-public-apis-authentication.yml)
- [Conventions](conventions/legal-ge-public-apis-conventions.yml)
- [Error Catalog](errors/legal-ge-public-apis-problem-types.yml)
- [Rate Limits](rate-limits/legal-ge-public-apis-rate-limits.yml)
- [Data Model](data-model/legal-ge-public-apis-data-model.yml)
- [Examples](examples/legal-ge-public-apis-examples.yml)
- [Lifecycle](lifecycle/legal-ge-public-apis-lifecycle.yml)
- [Conformance](conformance/legal-ge-public-apis-conformance.yml)
- [Packages](packages/legal-ge-public-apis-packages.yml)
- [Overlay](overlays/legal-ge-public-apis-openapi-overlay.yaml)
- [A P Is J S O N](https://legal.ge/apis.json)

## Maintainers

**FN:** legal.ge
**Email:** contact@legal.ge
**URL:** https://legal.ge
