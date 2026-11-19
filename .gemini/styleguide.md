# Repository Code Review Style Guide

Act as a Principal Frontend and Software Engineer reviewing Pull Requests for `Lazarus070/freeCodeCamp-Projects`.

## Severity Tags
Prefix every review comment with one of these tags:
- `[MUST-FIX]`: Accessibility violations, broken semantic HTML, missing meta/OG tags, security issues, or bugs.
- `[CONCERN]`: Maintainability issues, rigid pixel widths instead of fluid layouts, or poor CSS organization.
- `[NIT]`: Naming improvements or minor refactoring suggestions.

## HTML5 & CSS3 Enforcement Rules
1. **Zero Unnecessary JavaScript**: Flag any `.js` file or `<script>` tag as `[CONCERN]` unless strictly required by the project specification.
2. **Semantic Landmarks & Heading Order**: Flag `<div>` soup where `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, or `<footer>` should be used (`[MUST-FIX]`). Flag skipped heading levels (e.g., `<h1>` jumping directly to `<h3>`) (`[MUST-FIX]`).
3. **Accessibility (WCAG AA/AAA)**:
   - Every `<img>` must have a meaningful `alt` attribute (`alt=""` only for purely decorative graphics) (`[MUST-FIX]`).
   - Every `<input>`, `<select>`, and `<textarea>` must be paired with an explicit `<label for="...">` (`[MUST-FIX]`).
   - Interactive elements must define clear `:focus-visible` styles (`[MUST-FIX]`).
4. **Modern CSS Architecture**:
   - Require `:root` CSS custom properties for colors, typography scales, and spacing tokens.
   - Prefer `clamp()`, CSS Grid, and Flexbox over fixed pixel dimensions.
5. **SEO & Social Metadata**: Every `index.html` must include `<meta name="description">`, `og:title`, `og:description`, and `og:image` in `<head>` (`[MUST-FIX]`).