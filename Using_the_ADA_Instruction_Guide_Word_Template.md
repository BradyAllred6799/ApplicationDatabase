# Guide to Using the ADA-Compliant Word Template

*University of Florida — Training & Organizational Development | Instruction Guide*

Use these instructions when creating a document using the Training & Organizational Development ADA Instruction Guide template. This will ensure you are following the ADA guidelines when creating your documents.

---

## Contents

- [Settings](#settings)
- [Document Structure](#document-structure)
- [Styles](#styles)
- [Content Elements](#content-elements)

---

# Settings

## Software

- Ensure you are using the latest version of **Office 365 Professional**.
- Edit documents by opening them in the **Word Desktop app** — not in Teams or a browser.

## Accessibility Checker

- Use Word's built-in Accessibility Checker. While not exhaustive, it will catch basic issues.
- To locate: **Review > Check Accessibility**, or select the Accessibility icon at the bottom right of the screen.

## Permissions

- Set documents to open in **read-only** by default.

---

# Document Structure

## Title and Overview

- Position the title at the top of the page under the header, formatted as: **Verb + Subject** (e.g., "Request a Catalog Change").
- Use **Heading 1** style for the title.

The overview section should include:

- What this guide **is**
- What this guide is **NOT**
- Required security roles and training for this action
- Navigation URL

## One Action = One Step (Instruction Guides)

- Separate out each step in a process.
- Even small steps such as "Continue" and "Submit Request" should be their own step.

## Styles

Styles are the most important component of an accessible document. All text must be assigned a function using Styles.

Locate the Styles menu: **Home Tab > Styles**

| Style | Use | Formatting |
|---|---|---|
| **Heading 1** | Document title | Black (#000000) |
| **Heading 2** | Section headers | Blue (#0021A5) |
| **Strong** | Notes and occasional emphasis | Black (#000000), bold |
| **Click** | Any text that is selected or clicked (buttons, dropdowns, links, "Confirm," "Continue," etc.) | Blue (#1C78BB), bold |
| **Normal** | All other body text | — |

## Headings

- Use **Heading 1** for the document title and **Heading 2** for each section thereafter.
- When naming steps in an instruction guide, use the format: **"How to [Name of IG]."**
- Ensure logical heading order (e.g., Heading 2 → Heading 3 — do not skip levels).
- Be consistent — use the same heading style for each equivalent section.
- Limit to the first six heading levels; use Headings 5 and 6 sparingly.

## Paragraphs / Normal Text

- Use the colors embedded in the styles for normal text and headings.
- **Avoid highlighting.**
- Set all text to **Calibri**: 12pt for body text, 16pt for Heading 1, 14pt for Heading 2 and all subsequent headings.
- Avoid manually formatting text with bold, italic, or font changes — use the **Strong**, **Emphasis**, and **Intense Emphasis** styles instead.

## Lists

- Use the list tools in the Paragraph section to create numbered or bulleted lists. Both default to the List style.
- Use **numbers** for sequential steps — any step-by-step process should be numbered.
- Use **bullets** for guidance outside of a step-by-step process.
- Use the standard circle bullet; use the open circle for sub-bullets.
- Avoid using hyphens or asterisks to simulate lists.

## Table of Contents

- Required for documents more than 3 pages long.
- Create via: **References > Table of Contents > Automatic Table 1 or 2**.
- To update after changes: select **Update Table**.

## Headers and Footers

- **Header:** Use the T&OD image/header.
- **Footer** should include:
  - Department | Unit
  - Title of the Instruction Guide (same as the document title)

## Spacing

- **Zero** space between title and first step.
- **Zero** space between a step and its screenshot.
- **One** space between a previous screenshot and the next step.
- Do not add extra spaces to push a step and image to the next page — it is acceptable for a step and its screenshot to appear on separate pages.

## Metadata

- Go to **File > Info > Properties > Title**.
- Enter the same title as the Heading 1 of the document.
- This title should also match the file name used for Z drive organization.
- Include the title in the footer.

---

# Content Elements

## Tables

1. Insert via **Insert > Table**.
2. Go to **Table Design > Table Style Options** (upper left) and check: **Header Row**, **Banded Rows**, **First Column**.
3. Go to **Table Layout > Table > Properties > Row**:
   - Uncheck **Allow row to break across pages**
   - Check **Repeat as header row at the top of each page**
4. Highlight the top row > select the **Table Layout** tab > select **Repeat as header row**.
5. Add a caption via **References > Insert Caption** (Label = Table).
6. Include a title and column headers for the table.
7. Add alt text (see [Alternative Text](#alternative-text) section).
8. Add a caption below the table if needed.

**Avoid:** bulleted lists inside cells, empty spaces, and merged or split cells.

## Hyperlinks

### Link to Webpage

- Highlight text > right-click > **Link** > enter the web address.
- Use descriptive link text (e.g., "[Visit UF Accessibility Resources](https://accessibility.ufl.edu/)" — not "Click Here" or "Read More").

### Link to Send Email

- Highlight text > right-click > **Link** > enter `mailto:email@address.edu`.
- Use descriptive link text (e.g., "[Email Training support](mailto:training@ufl.edu)" — not "send email").

### Link to Heading within Document

- Highlight text > right-click > **Link > Place in This Document** > select the Heading.
- Use descriptive link text (e.g., "Navigate to guidance on using heading styles" — not "jump here").

## Images and Objects

- For all images: right-click > **Wrap Text > In-Line with Text**.

**General appearance for screenshots:**

- **First screenshot:** typically a full-screen image to orient readers.
- **Subsequent screenshots:** may exclude unrelated page elements (e.g., the header/top bar).
- **Border:** solid, black, 0.75pt width.
- **Callout boxes:** 2¼ pt, red (#C00000).

## Notes Boxes

Notes are used to call out important information — they are not steps in the process. Use **"Note"** for helpful guidance and **"Warning"** for statements of caution.

**To create a Notes box:**

1. Highlight the text you want a box around.
2. Set the **Note** style on the paragraph.
3. Select the first word ("Note" or "Warning") and set it to the **Strong** style.

**Examples:**

> **Note:** Notes should not be an actual step in the step-by-step process. Instead, Notes are special tips or red flags.

> **Warning:** Use the Word app for editing. Web-view often causes errors related to formatting.

## Alternative Text

Add alt text for all meaningful images and screenshots, including images, charts, tables, and diagrams.

To add alt text: right-click the image > **View Alt Text** > enter text in the space provided.

### Best Practices for Alt Text

- Provide context explaining why the image is significant.
- Be descriptive, but concise.
- **Do not** say "picture of…" or "screenshot of…"
- Describe the image — give context, not just identification.
- For charts: provide succinct alt text plus a table or longer text alternative near the image.
- For complex images: see [W3C Complex Images resource](https://www.w3.org/WAI/tutorials/images/complex/).
- Select **Mark as decorative** for images that have no informational significance (e.g., a decorative banner).
- **Do not** use auto-generated alt text from Microsoft 365.

### Alt Text Examples

- *"An orange box emphasizing the 'activity manager' section within the activities tab of the faculty insight dashboard."*
- *"Activity Manager panel highlighted in the Faculty Insight Activities tab."*
