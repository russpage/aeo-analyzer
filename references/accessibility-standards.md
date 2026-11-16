# Accessibility standards and implementation checks

## Review target and evidence

Use WCAG 2.2 Level A and AA as the default review target; honor an explicitly requested version or level. Verify W3C publication status at audit time; do not silently adopt an editor's draft as a conformance standard. This is a bounded accessibility review within an AEO audit, not a complete conformance evaluation or legal certification.

Separate normative WCAG success criteria and applicable WAI-ARIA requirements from informative Understanding documents, techniques, and ARIA Authoring Practices Guide (APG) patterns. APG examples illustrate patterns; they are not production-ready drop-ins or the only way to satisfy WCAG. Cite the exact applicable criterion and guidance, rather than the W3C homepage.

For every finding record: URL/component, tested state and viewport, evidence surface, status (pass/partial/fail/untested/not applicable), criterion number/title/level and full URL, reproducible test, user consequence, confidence, integration-aware fix, and acceptance test. Call a failure confirmed only when evidence establishes the criterion's applicability and failure. Missing attributes alone do not establish a failure when an equivalent valid mechanism exists. Report optional improvements separately. Keep accessibility benefits distinct from hypotheses about agent usability or AI visibility.

## Checks to select for the sampled journeys

These checks are a minimum relevant selection, not an exhaustive A/AA checklist. Include additional applicable criteria for the actual content and journey. Full WCAG 2.2: https://www.w3.org/TR/WCAG22/

| Area | Criteria (level) | What to inspect and test |
| --- | --- | --- |
| Informative and functional images | 1.1.1 Non-text Content (A) | Purpose-appropriate alternatives; functional icon names; decorative images ignored; equivalent descriptions for complex images. Missing alt is a candidate until purpose and accessible alternative are checked. |
| Structure and reading order | 1.3.1 Info and Relationships (A); 1.3.2 Meaningful Sequence (A) | Headings, lists, landmarks and tables express relationships; reading order preserves meaning. A skipped heading number alone is not proof of failure. |
| Keyboard | 2.1.1 Keyboard (A); 2.1.2 No Keyboard Trap (A) | Operate sampled navigation, dialogs, accordions, variant pickers and forms without a pointer; verify a keyboard path out. |
| Focus | 2.4.3 Focus Order (A); 2.4.7 Focus Visible (AA); 2.4.11 Focus Not Obscured (Minimum) (AA) | Logical focus order, visible indicator, no complete author-created obstruction; opening and closing behavior matches the chosen pattern. |
| Navigation and labels | 2.4.1 Bypass Blocks (A); 2.4.2 Page Titled (A); 2.4.4 Link Purpose (In Context) (A); 2.4.6 Headings and Labels (AA); 2.5.3 Label in Name (A) | Identify purpose in permitted context; accessible names include visible labels where applicable; test skip navigation. |
| Controls and state | 4.1.2 Name, Role, Value (A) | Inspect computed names, roles and states; expanded/selected/checked state matches actual UI; valid relationships. An aria-label is one naming mechanism, not universally required. |
| Forms and feedback | 3.3.1 Error Identification (A); 3.3.2 Labels or Instructions (A); 4.1.3 Status Messages (AA) | Labels, required instructions, understandable errors and announced qualifying status updates. Do not submit real customer data or purchase forms solely to test. |
| Visual presentation | 1.4.3 Contrast (Minimum) (AA); 1.4.11 Non-text Contrast (AA); 1.4.4 Resize Text (AA); 1.4.10 Reflow (AA) | Measure applicable text and control contrast; inspect at 200% text resize and reflow conditions including 320 CSS px width, accounting for exceptions. Do not infer contrast from HTML or a screenshot without measurement. |
| Pointer use | 2.5.8 Target Size (Minimum) (AA) | Check 24 by 24 CSS px targets or applicable spacing/other exceptions. Do not label every smaller icon a failure; measure the entire interactive target. |
| Conditional content | 1.4.13 Content on Hover or Focus (AA) | When applicable, test dismissibility, persistence and hoverability with criterion exceptions. |

Construct exact criterion citations from the relevant anchors in the current WCAG document, for example https://www.w3.org/TR/WCAG22/#name-role-value . Inspect the cited criterion before making a normative finding. Do not cite obsolete 4.1.1 Parsing as a WCAG 2.2 requirement.

## Hamburger and disclosure integration

1. Determine whether the control toggles inline navigation, opens a modal drawer, or navigates to another URL. Select the corresponding disclosure, dialog or link pattern; do not prescribe focus trapping for ordinary disclosures.
2. Inspect framework/component code and existing CSS/JS hooks where available. Prefer native buttons for actions and links for navigation. Preserve behavior and styling when changing the element; account for default button styles, form submission (type="button"), delegated listeners and breakpoint behavior.
3. Check the computed accessible name before declaring it missing: visible text, visually hidden text, aria-labelledby, aria-label or an appropriate SVG title may already provide one. Screenshot-only source does not establish the final accessibility tree.
4. For a disclosure button, expose aria-expanded synchronized with actual visibility. aria-controls is optional in the APG disclosure pattern; if supplied it must reference the correct existing element. A stable descriptive label such as "Main navigation" with expanded state is valid; switching "Open menu" to "Close menu" is optional, not a conformance requirement.
5. Prefer native semantics; do not add redundant role="button" to a button or role="menu"/"menuitem" to ordinary site-navigation links. ARIA does not create keyboard behavior. Hide a decorative icon from assistive technology only after its parent has an accessible name; never hide focusable interactive content with aria-hidden.
6. Use the existing component's state as the single source for visibility and ARIA. Never add a second click handler or separately maintained state to an unknown component. Label snippets illustrative when integration code is unavailable; do not assume an arbitrary menu ID already exists.
7. Acceptance: Tab reaches the control; Enter and Space activate a native button; expansion state matches the visible panel; collapsed links cannot receive focus; navigation remains ordinary links; pointer and mobile behavior still work; relevant focus/close/return behavior follows the selected pattern. Test responsive transitions, dismissal and actual supported browser/assistive-technology combinations when available. Record each unavailable check as untested.

## Test surfaces and limits

Use automated tooling (for example axe-core or an accessibility inspector) when available, recording version, ruleset, tested state and results. Do not install tools or claim scans without running them. Combine automation with manual keyboard, computed accessibility, visual and relevant assistive-technology testing. An automated zero-violation result is not a conformance pass. Evaluate multiple states of the same component, not just its initial markup.

If only raw HTML is available, report source-level candidates and provable source issues; leave computed names, focus, behavior, contrast and assistive-technology output untested. Preserve different public/draft themes and authenticated sessions as separate evidence surfaces.

## Primary guidance

- WCAG 2.2 normative criteria: https://www.w3.org/TR/WCAG22/
- WCAG quick reference and techniques: https://www.w3.org/WAI/WCAG22/quickref/
- APG principles and integration cautions: https://www.w3.org/WAI/ARIA/apg/practices/read-me-first/
- Disclosure pattern: https://www.w3.org/WAI/ARIA/apg/patterns/disclosure/
- Disclosure navigation example and limitations: https://www.w3.org/WAI/ARIA/apg/patterns/disclosure/examples/disclosure-navigation/
- Modal dialog pattern, only when applicable: https://www.w3.org/WAI/ARIA/apg/patterns/dialog-modal/
- Preliminary checks and their limits: https://www.w3.org/WAI/test-evaluate/preliminary/
