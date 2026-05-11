# 📐 Quarkdown Built‑In Directives & Authoring Reference

*(For writing Quarkdown documents, not extending the language)*

## Scope

This document describes **standard, built‑in Quarkdown directives and features** used to author documents:

*   layout
*   pagination
*   tables of contents
*   numbering
*   figures, tables, footnotes
*   metadata
*   slides
*   HTML/PDF output options

It intentionally **excludes**:

*   custom function definitions
*   scripting logic explanations
*   language extensibility

Assume **CommonMark + GitHub‑Flavored Markdown** is always available.

***

## 1. Document Type & Global Setup

### `.doctype`

Sets the compilation target and behavior.

```qd
.doctype {plain}   // notes, websites
.doctype {paged}   // books, papers, reports (PDF-ready)
.doctype {docs}    // documentation / wiki
.doctype {slides}  // presentations
```

Only **one doctype** should be active per document.

***

## 2. Document Metadata

### Core Metadata

```qd
.docname     {My Document Title}
.docauthor   {Jane Doe}
.doclanguage {English}
```

Used for:

*   title pages
*   headers/footers
*   HTML `<meta>` tags
*   PDF front matter

***

## 3. Themes, Fonts & Page Format

### Theme

```qd
.theme {paperwhite}
.theme {galactic}
```

Themes define:

*   colors
*   spacing
*   typography defaults
*   layout style

### Fonts

```qd
.font {
  body:{Serif}
  monospace:{JetBrains Mono}
}
```

### Page Format (Paged Documents)

```qd
.pageformat {A4}
.pageformat {Letter}
```

***

## 4. Page Layout & Margins

### Page Margins

```qd
.pagemargin {
  top:{2cm}
  bottom:{2cm}
  left:{3cm}
  right:{3cm}
}
```

### Margin Content (Headers / Footers)

```qd
.pagemargincontent {
  topleft:{.docname}
  bottomright:{.pagecounter}
}
```

Common placeholders:

*   `.docname`
*   `.docauthor`
*   `.pagecounter`

***

## 5. Page Counters & Breaks

### Page Counter

```qd
.pagecounter
```

Often used in headers/footers.

### Manual Page Break

```qd
.pagebreak
```

### Automatic Page Break Rules

```qd
.autobreak {headings}
.autobreak {figures}
```

***

## 6. Persistent Headings

Keep headings visible across page breaks.

```qd
.persistentheadings
```

Useful for long paged documents.

***

## 7. Numbering System

### Enable Numbering

```qd
.numbering {
  headings
  figures
  tables
  code
}
```

### Result

*   Headings: `1`, `1.1`, `1.1.1`
*   Figures: `Figure 3`
*   Tables: `Table 2`

***

## 8. Table of Contents

### Insert TOC

```qd
.tableofcontents
```

### Options

```qd
.tableofcontents depth:{3}
```

Typically placed:

*   after title
*   after abstract
*   at top of docs pages

***

## 9. Figures & Images

### Basic Image

```markdown
img/example.png
```

### Image Size

```qd
!(70%)img/example.png
```

### Figure Caption

```markdown
img/blackhole.jpg
```

Figures are:

*   auto‑numbered (if enabled)
*   referenceable

***

## 10. Tables

### Standard Markdown Table (Extended)

```markdown
| Name | Value |
|------|-------|
| A    | 10    |
| B    | 20    |
```

### Table Caption

```qd
.tablecaption {Experiment results}
```

Captions integrate with numbering and references.

***

## 11. Cross‑References

### Referencing Elements

```qd
.ref {fig:blackhole}
.ref {sec:introduction}
```

Referenceable objects:

*   headings
*   figures
*   tables
*   code blocks
*   equations

Rendered as **clickable links** in HTML.

***

## 12. Footnotes

### Inline Reference

```markdown
This is important.[^note1]
```

### Definition

```markdown
[^note1]: This is the footnote text.
```

Footnotes automatically collect at page or document bottom.

***

## 13. Quotes, Alerts & Decorative Blocks

### Block Quote

```markdown
> This is a quote.
> — Author
```

### Alert / Callout Types

```qd
.alert {info}     {Informational note}
.alert {warning}  {Important warning}
.alert {danger}   {Critical message}
```

***

## 14. Math (LaTeX)

### Inline Math

    $E = mc^2$

### Display Math

    $$$
    \int_0^\infty e^{-x} dx = 1
    $$$

Fully compatible with LaTeX notation.

***

## 15. Multi‑Column & Layout Blocks

### Columns

```qd
.columns {2} {
  Left column text

  Right column text
}
```

### Landscape Content

```qd
.landscape {
  Wide table or figure
}
```

***

## 16. Slides‑Specific Directives

### Slide Separation

```markdown
# Slide Title
---
## Next Slide
```

### Speaker Notes

```qd
.speakernotes {
  Explain this graph verbally.
}
```

### Fragments (Reveal Content Step‑By‑Step)

```qd
.fragment {Points appear later}
```

***

## 17. Docs / Wiki Mode

When using `.doctype {docs}`:

*   Sidebar navigation
*   Multi‑page structure
*   Automatic TOC per page

### Standard Docs Page Header

```qd
.docname {Installation}
.include {docs}
```

***

## 18. HTML Output & Static Assets

### Public Assets

*   Any file in `public/` is copied verbatim to output root

### Root‑Relative Paths

```markdown
!Logo
@
```

***

## 19. Bibliography & Citations

### Enable Bibliography

```qd
.bibliography
```

Used with:

*   citations
*   reference lists
*   academic writing

***

## ✅ Authoring Rules for LLMs

*   Prefer **Quarkdown directives** over raw HTML
*   Do not invent new directives
*   Use numbering, TOC, references consistently
*   Respect `doctype` constraints
*   Assume compilation, not live rendering

***

## Mental Model

> **Quarkdown authoring = structured Markdown + declarative directives**  
> Not a programming task, but **typesetting with intent**
