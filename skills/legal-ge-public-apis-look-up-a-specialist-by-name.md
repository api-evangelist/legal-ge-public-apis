---
generated: '2026-08-09'
method: generated
name: Look up a specialist by name and reveal a contact field
description: Find a named Georgian legal specialist or firm, then reveal one opt-in contact field — carefully, one field at a time, inside a deliberately tight throttle.
api: openapi/legal-ge-public-apis-openapi.yml
operations: [searchSpecialistsByName, revealSpecialistContact]
source: >-
  Grounded in openapi/legal-ge-public-apis-openapi.yml (OpenAPI 3.1.0). Both operationIds verified in
  the spec. Consent and throttle semantics quoted from the operation descriptions.
---

# Look up a specialist by name and reveal a contact field

Use this only when the user already knows **who** they are looking for. To go from a legal *problem*
to a person, use `legal-ge-public-apis-find-a-verified-specialist.md` instead.

> **This is the PII surface of the API.** Neither operation is exposed as an MCP tool — the
> provider's own agent surface deliberately omits them. Treat that as a signal, not an oversight.

## Auth
- **None.** Public and keyless — but access is gated by *consent* plus a hard throttle, not a key.
- Base URL: `https://legal.ge`.

## Steps
1. **Search by name** — `searchSpecialistsByName` (`GET /api/specialists/search?q=<name>&locale=`).
   `q` requires at least 3 characters. Returns up to 20 results:
   `{id, full_name, avatar_url, slug, info_activate}`. **No contact data is included.**
2. **Check `info_activate`.** If it is `false`, the specialist has *not* opted into public contact
   display. Stop — do not call step 3. Direct the user to sign in on legal.ge to message them.
3. **Reveal one field** — `revealSpecialistContact`
   (`GET /api/specialists/{id}/contact?field=phone|email`) with the UUID `id` from step 1. It returns
   only the single requested field. Despite the path name it also accepts `COMPANY`-role ids, because
   company contact info lives on the same profiles row.

## Rules that matter
- **10 requests per minute per IP.** The operation description states this cap exists "to make bulk
  PII harvest impractical". Do not batch, do not loop over a result set, do not pre-fetch contacts
  you were not asked for. Reveal on explicit user intent only.
- **One field per call.** `field` is a required enum of `phone` or `email`. Request the one the user
  asked for; do not call twice to collect both by default.
- **A `404` is ambiguous on purpose.** "Not found", "not opted in" and "no value for that field"
  collapse into one status so opt-out state is not leaked. Report it as "that contact detail is not
  publicly available" — never as "this specialist does not exist".
- **Do not persist or re-publish revealed contact data.** It was opted in for direct contact, not for
  redistribution.
- `searchSpecialistsByName` is rate-limited at 30 requests/minute per IP.

## Errors
- `400` — invalid `id` (must be a UUID) or invalid `field` value. Declared with a description only,
  no schema, so do not assume the standard error envelope on this path.
- `404` — see above; deliberately ambiguous.
- `429 RATE_LIMITED` — honour `Retry-After`. See `rate-limits/legal-ge-public-apis-rate-limits.yml`.
