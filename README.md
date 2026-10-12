# Accessibility Audit: designinfo.in (Home Page)

12 October 2026 | Automated: axe DevTools (axe-core 4.13.0), WCAG 2.1 AA | Manual: browser zoom, keyboard-only, NVDA

This is a learning audit of one public page. Findings describe the page as tested on that date; they are not a complete conformance assessment.

## Summary
The home page returned 96 axe issue instances from 5 distinct rules, plus one manual finding. Three results are WCAG failures and three are best-practice findings. Zoom, reflow and hamburger-menu checks passed.

| # | Issue | Instances | WCAG / type | Found by |
|---|---|---|---|---|
| 1 | Insufficient color contrast | 66 | 1.4.3 (AA) | axe |
| 2 | Links without discernible text | 27 | 2.4.4, 4.1.2 (A) | axe |
| 3 | WhatsApp chat button has no accessible name | 1 | 4.1.2 (A) | NVDA |
| 4 | Heading levels skip (h6) | 1 | Best practice | axe |
| 5 | Landmarks not uniquely labelled | 1 | Best practice | axe |
| 6 | No level-one heading | 1 | Best practice | axe |

## Findings
1. **Color contrast (66, WCAG 1.4.3 AA).** Example: the Shipping heading is `#7a7a7a` on white, 4.29:1; 4.5:1 is required. Likely cause: a light grey reused across many elements. Fix: darken the shared grey (e.g. `#757575` or darker) and re-check each color pair.
2. **Links without discernible text (27, WCAG 2.4.4 and 4.1.2, A).** The camera image link has an empty accessible name and `tabindex="-1"`. Likely cause: image-only links duplicating the caption link. Fix: add alt text, merge with the caption link, or hide the duplicate.
3. **WhatsApp button has no accessible name (1, WCAG 4.1.2 A).** NVDA announces only "button". The element is an `<a role="button">` with the label in a nested div. Fix: remove `role="button"` and add `aria-label="Chat on WhatsApp"`. axe did not flag this; it was found manually.
4. **Heading levels skip (best practice).** Feature titles are `<h6>`. Use heading levels in order and style with CSS.
5. **Landmarks not uniquely labelled (best practice).** A `nav` with `aria-label="Menu"` shares its label with another landmark.
6. **No level-one heading (best practice).** Mark up the main page title as an `<h1>`.

## Passed checks
- Resize text at 200% (1.4.4 AA): readable, nothing cut off, all controls work.
- Reflow at 400% (1.4.10 AA): single column, vertical scroll only; nav collapses into a hamburger menu with all items reachable.
- Hamburger menu button (4.1.2 A): NVDA announces "menu toggle button, collapsed" and "expanded" when opened.
- Hamburger menu items (2.1.1, 2.4.7): Tab reaches the items with a visible focus outline; NVDA reads them.

## Observation
At default zoom the fixed WhatsApp button covers page text in the viewport; at 200% nothing was hidden. This is a usability observation, not a WCAG failure, unless keyboard focus is hidden behind it (2.4.11).

## Not tested
Whether focus is ever hidden behind the WhatsApp button; NVDA testing of headings, forms and the 27 unnamed image links; pages other than the home page; axe Guided and Manual checks.

## Files
- `designinfo-audit-scorecard.xlsx`: findings table and counts.
