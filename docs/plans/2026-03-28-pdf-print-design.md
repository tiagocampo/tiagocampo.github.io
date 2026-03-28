# PDF Export Redesign — Print-Based Approach

## Problem

The "Download PDF" button uses `html2pdf.js` (html2canvas + jsPDF), which:
- Fails silently on Firefox (button restores but no PDF generated)
- Produces rasterized output (JPEG inside PDF — blurry, non-selectable text)
- Poor print quality for professional use

## Solution

Replace with `window.print()` + enhanced `@media print` CSS. Zero dependencies, native browser PDF engine.

## Changes

### Remove
- `html2pdf.js` CDN `<script>` tag
- `generatePDF()` function

### Modify
- Button `onclick` → `window.print()`
- Button label → "Print / Save PDF"
- `@media print` block → comprehensive single-column print layout

### Print Layout (single-column)
1. Header: name, title, tagline, compact avatar
2. Contact line: email | LinkedIn | GitHub (horizontal)
3. Education: compact list
4. Main sections: full-width stacked (Profile, Experience, Skills, Projects, Publications, Conferences, Certifications)
5. No sidebar background color — no "enable backgrounds" requirement
6. Page break control: `break-inside: avoid` on cards/items, `break-before: page` before major sections

### Print CSS Details
- Force all `.fade-in` visible (no hidden elements)
- Remove sticky positioning from sidebar
- Flatten grid to single column (`grid-template-columns: 1fr`)
- Hide the PDF button itself
- Ensure avatar image prints
- Disable all hover transitions
- `print-color-adjust: exact` on accent elements (orange markers, pill borders)
