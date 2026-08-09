---
generated: '2026-08-09'
method: generated
name: Classify a legal question into Georgian practice areas
description: Map free text to legal.ge practice areas and services without pulling any specialists, then browse the published taxonomy around the match.
api: openapi/legal-ge-public-apis-openapi.yml
operations: [classifyLegalIntent, searchServicesAndCategories]
source: >-
  Grounded in openapi/legal-ge-public-apis-openapi.yml (OpenAPI 3.1.0). Both operationIds verified in
  the spec. Taxonomy semantics per data-model/legal-ge-public-apis-data-model.yml.
---

# Classify a legal question into Georgian practice areas

Use this when you need the **legal domain** of a question — for routing, triage, tagging, or
answering "what area of law is this?" — and you do not want to pull people.

## Auth
- **None.** Public and keyless. Base URL: `https://legal.ge`.

## Steps
1. **Classify** — `classifyLegalIntent` (`GET /api/ask/classify?q=<text>&locale=<ka|en|ru>`).
   `q` is required, max 500 characters. Returns `matched_categories[]` and
   `meta.fallback_used` — nothing else, no personal data.
2. **Read the match quality** — each entry carries:
   - `kind` — `category` (a practice area at some depth) or `service` (the deepest node the matcher
     considers).
   - `level` — 1 = top-level practice area, 2/3 = sub-areas, 4+ = services.
   - `match_confidence` — `curated` means an admin-curated keyword fired (**strong**);
     `name_fallback` means only a token overlap with the node name (**weak** — treat as a guess).
   - `matched_keywords` — the query tokens that triggered the match.
   - `parent_chain` — ancestors in **child-first** order (closest parent first, root last), so you
     can cite the broad practice area without a second call.
3. *(Optional)* **Browse the taxonomy** — `searchServicesAndCategories`
   (`GET /api/service-search?q=<text>&locale=`). `q` requires at least 2 characters. Returns
   `{id, type, displayName, href, categoryName}` items you can link directly.

## Rules that matter
- **Prefer `curated` over `name_fallback`.** If every match is `name_fallback`, say the classifier
  was unsure rather than asserting a practice area.
- **Cite the level you actually matched.** A level-4 service ("LLC Formation") is a much more
  specific claim than its level-1 root ("Corporate & Commercial Law"). Use `parent_chain` to widen
  deliberately, not accidentally.
- **Expect cross-domain matches.** One query legitimately fans out across several level-1 areas — a
  company-registration question can match Corporate, Tax and Blockchain law at once. See the captured
  live response in `examples/legal-ge-public-apis-classify-response.json`.
- `meta.fallback_used: true` means the matcher fell back rather than matching cleanly — lower your
  confidence accordingly.

## Errors
- `400 QUERY_REQUIRED` / `400 QUERY_TOO_LONG` (500-character cap) on `classifyLegalIntent`.
- `429 RATE_LIMITED` — 120 requests/minute per IP, the highest limit on the API. Honour `Retry-After`.
- `searchServicesAndCategories` declares **only** a 200 response in the spec — its error behaviour is
  unstated, so handle non-200 defensively. See `errors/legal-ge-public-apis-problem-types.yml`.
