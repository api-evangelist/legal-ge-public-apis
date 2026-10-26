# legal.ge Public APIs (legal-ge-public-apis)

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
