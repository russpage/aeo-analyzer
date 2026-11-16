# Audit framework

## Checks

| Dimension | Inspect | Evidence and acceptance examples |
|---|---|---|
| Access and eligibility | HTTP status, redirect loops, robots groups and path matching, meta/X-Robots-Tag, canonicals, sitemap URLs, discoverable internal links, login/WAF/CDN barriers | Public target returns expected content; relevant crawler policy permits intended paths; no unintended noindex or conflicting canonical; distinguish permission from observed indexing |
| Content availability | Initial HTML versus rendered DOM versus interaction-required text; critical price/spec/proof availability; image-only information; link destinations | Verified product fact appears in response HTML or document a tested engine-specific rendering path; accordion behavior and extraction tested separately |
| Semantics and agent usability | Landmarks, headings, navigation links, native action buttons, icon names, form label associations, keyboard access, focus, aria-expanded, meaningful image alternatives | Inspect computed names/roles/states when possible; menu and key controls operable without submitting a real form; decorative images have empty alt; complex diagrams have meaningful text equivalents |
| Answer quality and fit | Definition, audience, outcomes, direct answer, use cases, exclusions, comparisons, pricing units/currency/fees/terms, supporting detail | Reader can answer target question from a self-contained passage with context; comparison has factual tradeoffs and appropriate alternatives |
| Evidence and entity clarity | Organization/product identities, authorship where relevant, contact/about, original research, methodology, named sources, dated proof, consistency across owned and independent sources | Claims trace to a source, scope, and verification date; attributed testimonial remains readable text; distinguish self-reported from independently corroborated facts |
| Maintenance and discovery | Verified price/feature/review dates, real publication/update dates, content ownership, broken key links, stale redirects, schema-visible content consistency | Changes trigger review; broken links confirmed with GET where HEAD is ambiguous; sitemap lastmod reflects substantive changes; no invented freshness |

For accessibility, apply `accessibility-standards.md`: include criterion/level/source, tested state, surface and method in findings. Distinguish normative failures from optional pattern improvements; publish coverage and untested criteria, not a blanket WCAG conformance claim.

Inspect structured data syntax, eligible type, required properties, entity IDs, and parity with visible content. Do not mark markup valid or rich-result eligible without an appropriate validator. Do not recommend FAQ schema as a universal visibility tactic. Do not treat structured-data scripts as missing visible prose: assess both separately.

For local/service businesses, check service geography, eligibility, contact details, business profile consistency, and real service evidence. For commerce, check variants, availability, shipping, returns, identifiers, and price context. For B2B, check deployment, integrations, security evidence, implementation, procurement, and pricing basis. Use only relevant checks.

## Diagnostic scoring

Use categorical statuses by default: pass, partial, fail, untested, not applicable. A pass means the named check passed on the inspected surface, never guaranteed visibility.

If a score is requested, use a transparent internal readiness index: access 25, availability 20, semantics 15, answer quality 20, evidence 15, maintenance 5. Define applicable checks before assigning results. Score pass=1, partial=0.5, fail=0. Exclude untested and not-applicable checks from observed denominators. Report coverage as tested applicable checks / all applicable checks, both overall and per dimension. Calculate each observed dimension percentage from tested checks; weight only tested dimensions and disclose omitted weights. With coverage below 70%, label the result provisional and do not rank sites against each other. Never treat this index as an engine metric, ranking probability, or measured citation likelihood. Show critical blockers independently of the average.

## Priority

- P0: confirmed critical access/index eligibility defect on a commercially important page. Name affected engine/path and do not generalize.
- P1: missing or misleading decision facts, key answer gaps, inaccessible essential controls, unsupported major claims.
- P2: supporting evidence, discovery, template consistency, maintenance improvements.
- Experiment: plausible tactic without established causal evidence; define success metric and test.

Rank within tiers by customer/business importance, affected scope, severity, evidence confidence, and effort. Use high/medium/low impact estimates, not invented revenue forecasts. Separate confirmed faults from recommended investigations.

## Output contract

1. Executive summary: readiness versus observed visibility; top three actions; material scope limit.
2. Coverage ledger: URL | page role | HTTP/raw | DOM | accessibility | search/answer | timestamp | limitation. Use untested explicitly.
3. Question map: question | customer intent | current page | answer/proof gap | priority.
4. Findings/backlog: ID | URL/template | observed evidence and source | consequence | confidence | priority | exact fix | owner | effort | acceptance test.
5. Three implementation-ready drafts with facts, unknown placeholders, and acceptance tests.
6. Measurement: baseline, fixed prompts, repeats, citation/accuracy/fit metrics, business outcomes, retest conditions.
7. Sources and limits: full URLs; tested versus inferred; inaccessible resources.

Keep a compact executive output when requested, but preserve coverage and critical limitations. For a single page, reduce the question map and number of drafts appropriately rather than invent additional pages.

## Measurement definitions

Report counts and denominators: brand mentions / completed runs; valid citations to audited domain / completed runs; suitable recommendations / completed runs; correct checked facts / checked facts. Report failed/inaccessible runs separately. Distinguish citation count from unique cited URLs and independent recommending engines. Use at least three repetitions per prompt/engine for an exploratory baseline when feasible; label small samples and variability. Do not assert a repeatable ranking from one answer. Record referrals under a documented channel definition and qualify unattributed traffic; assistants may not send referrers. Preserve temporal comparability and note engine/product changes.
