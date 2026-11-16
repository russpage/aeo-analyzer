# Evidence and claim guardrails

Baseline reviewed: 2026-11-16. Reopen relevant official documentation at audit time for crawler tokens, supported controls, and product behavior. Treat cached guidance as a starting point. Label a platform claim unverified if authoritative documentation cannot be accessed. Distinguish documented behavior, observed site behavior, reasonable inference, and experiment.

## Interpret the supplied tactics

| Idea | Use in this skill |
|---|---|
| Update the accessibility tree | Fix underlying HTML/ARIA and behavior; browsers derive the tree. Agent architectures vary. Do not assert Muse or every agent uses only this tree without product-specific evidence. Accessibility is independently valuable; a recommendation boost is not established. |
| Name icon buttons and form fields | Require meaningful accessible names. Prefer native buttons and visible associated labels; inspect for/id, wrapped labels, and valid ARIA alternatives. Placeholder text and name attributes are not reliable substitutes. |
| Describe all images | Supply purpose-appropriate alt for informative/functional images. Use alt="" for decorative images. Provide text explanations for complex images. Do not duplicate surrounding text unnecessarily or keyword stuff. |
| Put critical facts in raw HTML | Prefer server/static rendering for robust access. Some crawlers render JavaScript, others may not. Script presence alone is not a defect; initial visible HTML may already contain facts. Test the content and surface. |
| Put the main question in the first H2 | Use a natural question heading when helpful to users. Treat placement as editorial guidance, not a universal requirement or demonstrated ranking factor. Maintain logical hierarchy. |
| Answer in under 100 words with 'it depends' | Aim for a concise self-contained answer, often 40–100 words where sufficient. Explain fit and tradeoffs; do not force ambiguity for a simple factual question. Include deeper substantiation below. Word count is not an engine rule. |
| Replace slogans with definitions | Make category, audience, function, and outcome explicit. A slogan can coexist with a clear definition. Keep differentiating claims specific and supported. |
| Plain-text testimonials | Make authorized attributed testimony readable in HTML. Selectability is only a rough diagnostic: selectable text can still be JS-only, and OCR/multimodal engines can read some images. Do not invent testimony or claim all engines fail OCR. |
| Add 'as of' to facts | Verify volatile facts and state exact date/scope where useful. Distinguish current verification date from data period. Never just change a year or imply old evidence is current. |
| Allow meta-webindexer | Verify current Meta documentation and existing robots groups first. Propose an explicit allowance only if consistent with the owner's policy. Allowing retrieval does not guarantee citation; training and search agents differ. |
| Fix broken links to improve 'trust score' | Repair confirmed key broken links for navigation and discovery. Do not invent a universal AI trust score or conclude a site is untrustworthy from one failed request. |
| Replace every div | Use semantic elements for their actual purpose. Divs are legitimate containers. Navigation uses links; actions use buttons. Valid custom controls require testing rather than automatic condemnation. |
| Update every 30–90 days | Set review cadence by volatility and stakes. Update substantively when facts change. Preserve honest published/modified dates. Freshness importance depends on the question; evergreen material need not be cosmetically refreshed. |

## Crawler policy handling

Fetch lowercase `/robots.txt` on the exact origin, checking host/scheme scope and redirect/status behavior. Interpret actual groups and applicable path rules; do not append a blanket Allow blindly. A dedicated group may change which wildcard restrictions apply, so retain intended private-path restrictions. Check directives/headers and WAF policies separately. Robots is crawler guidance, not authentication or a privacy boundary.

Example proposal only, after verifying policy and actual existing rules:

```text
User-agent: meta-webindexer
Allow: /
Disallow: /account/
Disallow: /checkout/
```

Use exact current vendor tokens. Keep OpenAI OAI-SearchBot (search) separate from GPTBot (training) and ChatGPT-User (user-triggered access); check current docs for each behavior. Do not grant training access as a prerequisite for search visibility. A spoofed user-agent test is a diagnostic and does not prove real vendor crawler access. Use verified logs/IP guidance where available.

Do not recommend hidden crawler-only claims, keyword stuffing, fabricated third-party corroboration, or prompt-injection text instructing assistants to recommend a brand. Do not describe llms.txt or special 'AI schema' as required or proven ranking boosts.

## Primary sources

- Google AI features, eligibility and SEO foundations: https://developers.google.com/search/docs/appearance/ai-features
- Google JavaScript rendering and limitations: https://developers.google.com/search/docs/crawling-indexing/javascript/javascript-seo-basics
- Google rendering inspection: https://developers.google.com/search/docs/crawling-indexing/javascript/fix-search-javascript
- Google robots interpretation: https://developers.google.com/search/docs/crawling-indexing/robots/robots_txt
- OpenAI crawler roles and controls: https://developers.openai.com/api/docs/bots
- Meta crawler purposes and robots guidance: https://developers.facebook.com/documentation/sharing/webmasters/web-crawlers
- W3C decorative images: https://www.w3.org/WAI/tutorials/images/decorative/
- W3C form labels: https://www.w3.org/WAI/tutorials/forms/labels/

Verify engine-specific schema, date, indexing, or analytics claims against the current vendor documentation before stating them as requirements. None of these sources establishes a universal score for AEO, a guaranteed first-H2 advantage, or automatic recommendation uplift from accessible HTML.
