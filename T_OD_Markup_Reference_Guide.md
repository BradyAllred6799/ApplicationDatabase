# T&OD Markup Reference Guide

This guide explains how to write instruction guide markup manually so you can paste it directly into the T&OD Document Generator and convert it to a formatted Word document.

---

## Overview

The converter reads plain text markup and maps each element to the correct style in the T&OD Word template. You do not need to use the AI at all — you can write the markup yourself and paste it straight into the converter.

Every block element must be separated by a blank line.

---

## Headings

Use hash symbols to create headings. The number of symbols sets the heading level.

```
# Heading 1 — use for the document title only
## Heading 2 — use for major sections
### Heading 3 — use for subsections
#### Heading 4 — use for sub-subsections
```

Always put a blank line after a heading before any content.

---

## Body Paragraphs

Plain text with no special characters becomes a Normal paragraph.

```
Write your paragraph text here. Keep it to one topic per paragraph.

Leave a blank line between paragraphs.
```

---

## Lists

### Unordered Lists

Use a hyphen or asterisk followed by a space for bulleted lists.

```
- First item
- Second item
- Third item
```

Use unordered lists for non-sequential items, options, or reference information.

### Ordered Lists

Use numbers followed by a period and a space for numbered lists.

```
1. First step
2. Second step
3. Third step
```

Use ordered lists for sequential procedures where the order matters. Do not manually bold the numbers — the converter handles numbering automatically.

### Continuing a List After an Interruption

If a note or image placeholder interrupts a numbered list, resume with the correct next number.

```
1. First step
2. Second step
3. Third step
[NOTE] This is important information about step 3.
4. Fourth step
5. Fifth step
```

---

## Callouts

Callouts must be standalone blocks separated by blank lines. They cannot appear inside a list.

```
[NOTE] Use for important information the reader should be aware of.
[WARNING] Use for information that could cause errors or problems if ignored.
[TIP] Use for helpful suggestions or shortcuts.
```

---

## Screenshot Placeholders

Use `IMAGE` blocks where a screenshot would help the reader. Write a specific description of what the screenshot should show.

```
[IMAGE] The completed form with all required fields filled in and the Submit button visible.
```

Do not add an `IMAGE` block after every step — only where a visual meaningfully helps.

---

## Inline Styles

Inline styles apply within any block of text.

- `**Bold text**` — wrap with double asterisks.
- `_Italic text_` — wrap with single underscores.
- `***Bold and italic text***` — wrap with triple asterisks.
- `[Clicks:Button Name]` — use for all UI elements such as buttons, menus, fields, tabs, links, and application names.
- `[SubtleRef:reference text]` — use for subtle reference text.
- `[IntenseRef:reference text]` — use for intense reference text.
- `[BookTitle:Book Name]` — use for book titles.

---

## Complete Example

```
# How to Submit a Travel Request

This guide walks you through submitting a travel request in [Clicks:Concur].

## Before You Begin

- Confirm your travel dates with your supervisor.
- Have your cost center number available.

## Submitting the Request

1. Log in to [Clicks:Concur].
2. Select [Clicks:Travel] from the top navigation menu.
3. Click [Clicks:New Request].

[IMAGE] The New Request form in Concur with all required fields visible.

[NOTE] All fields marked with an asterisk are required before the request can be submitted.

4. Complete all required fields.
5. Enter your travel dates in the [Clicks:Date] fields.
6. Click [Clicks:Submit].

[IMAGE] The confirmation screen showing the submitted request number.

## After Submitting

Your request will be routed to your supervisor for approval. You will receive an email
notification when the request has been reviewed.

[TIP] You can check the status of your request at any time by selecting [Clicks:Requests]
from the top navigation menu.
```

---

## Quick Reference

| Syntax | Result |
|---|---|
| `# Text` | Heading 1 |
| `## Text` | Heading 2 |
| `### Text` | Heading 3 |
| `- item` | Bulleted list item |
| `1. item` | Numbered list item |
| `[NOTE] text` | Note callout |
| `[WARNING] text` | Warning callout |
| `[TIP] text` | Tip callout |
| `[IMAGE] description` | Screenshot placeholder |
| `**text**` | Bold |
| `_text_` | Italic |
| `***text***` | Bold and italic |
| `[Clicks:Name]` | UI element reference |
