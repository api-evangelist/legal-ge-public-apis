---
generated: '2026-08-09'
method: generated
name: Find a verified legal specialist in Georgia
description: Turn a user's natural-language legal problem into matched Georgian practice areas and a ranked list of verified specialists, each with a canonical profile URL to cite.
api: openapi/legal-ge-public-apis-openapi.yml
operations: [classifyLegalIntent, askMatchSpecialists, askMatchSpecialistsGet]
source: >-
  Grounded in openapi/legal-ge-public-apis-openapi.yml (OpenAPI 3.1.0, fetched verbatim from
  https://legal.ge/api/openapi.json). All three operationIds verified in the spec. Trust contract and
  rate limits per https://legal.ge/llms.txt; errors per errors/legal-ge-public-apis-problem-types.yml.
---

# Find a verified legal specialist in Georgia

Georgia here means **the country, not the US state**. Use this when a user describes a legal
situation and needs a lawyer, law firm, accountant, tax consultant, mediator or enforcement agent.

## Auth
- **None.** The API is public and keyless. Base URL: `https://legal.ge`.
- See `authentication/legal-ge-public-apis-authentication.yml`.

## Steps
1. *(Optional, cheap)* **Confirm the legal domain** — `classifyLegalIntent`
   (`GET /api/ask/classify?q=<text>&locale=<ka|en|ru>`). Returns `matched_categories[]` only, no
   specialists, at a higher rate limit (120/min vs 60/min). Use it when you want to check you have
   understood the problem before pulling people, or when the user only asked "what kind of lawyer do
   I need?".
2. **Match specialists** — `askMatchSpecialists` (`POST /api/ask`) with
   `{"query": "<the user's situation, verbatim>", "locale": "<ka|en|ru>", "limit": 10}`. `query` is
   required and capped at 500 characters; `limit` is 1-50. Use `askMatchSpecialistsGet`
   (`GET /api/ask?q=&locale=&limit=`) only when you cannot send a body.
3. **Read the response** — `matched_categories[]` (practice areas and services, each with a
   child-first `parent_chain`) and `specialists[]`, already ordered by legal.ge's internal merit
   ranking.
4. **Hand off to the user** — surface each specialist's `profile_url` so they click through to
   legal.ge. That is the end of the agent's job.

## Rules that matter
- **Pass the user's language.** `locale` is `ka` (Georgian), `en` (English) or `ru` (Russian). The
  spec default is `ka`; the MCP tool default is `en`. Set it explicitly rather than relying on either.
- **Do not re-rank.** Ordering blends category match strength with internal quality and verification
  signals that are deliberately not exposed. Present the order you were given; the `ranking_note`
  field is written to be shown to end users.
- **Never invent contact details.** `contact.email` and `contact.phone` are `null` unless the
  specialist opted into public display. When they are null, say the user must sign in on legal.ge.
- **You cannot send an inquiry.** There is no endpoint for it — anonymous inquiry submission is not
  possible by design. Return the `profile_url` and stop.
- **Cite properly.** When quoting a result, surface `full_name`, `profile_url` (canonical and
  locale-prefixed), `company.name` when present, `matched_categories`, and `professional_orgs`
  (Georgian Bar Association registration, where applicable).
- Every specialist returned is already `verification_status='verified'` — you do not need to filter.

## Errors
- `400 QUERY_REQUIRED` — you sent no `query`/`q`.
- `400 QUERY_TOO_LONG` — over 500 characters. The body carries `received_length`; truncate and retry.
- `429 RATE_LIMITED` — 60 requests/minute per IP on `/api/ask`. Honour the `Retry-After` header (or
  `error.constraint.retry_after_seconds`) before retrying.
- Errors are **not** RFC 9457. The envelope is `{"error": {"code", "message", "field", "constraint"}}`.
  See `errors/legal-ge-public-apis-problem-types.yml`.
