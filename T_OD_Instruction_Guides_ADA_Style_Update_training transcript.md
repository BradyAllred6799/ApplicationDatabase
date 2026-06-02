# T&OD Instruction Guides ADA Style Update Training

**Meeting Recording — November 21, 2025, 6:09 PM**

*Transcription started by Allred, Brady*

---

## Participants

- **Allred, Brady** (presenter)
- **Cadwallader, Gwynn**
- **Deleveaux, Dwan D**
- **Galloway, Mitchell Loudon (Mitch)**
- **Nichols, Heather**
- **Prange, Kelsey L**

---

## Overview: Why This Change is Happening

**Brady [0:03]:** Today we're walking through changes to how we create instruction guides due to **WCAG 2.2 AA** being mandated by the state for all online resources. This applies to every outward-facing online resource that can be accessed by someone outside our group. Internal documents and Teams content don't necessarily fall under this category, but anything we publish and distribute externally does.

### What is WCAG 2.2?

**Web Content Accessibility Guidelines (WCAG)** is a standardized framework for making online resources accessible to anyone with a disability or vision impairment. The four principles are:

- **Perceivable**
- **Operable**
- **Understandable**
- **Robust**

**Level AA** refers to the tier at which content must be accessible. Previously, level A required alternatives for everything. Now, we aim to make everything accessible in and of itself.

### Why We're Moving Away from PDFs

- PDFs are not inherently accessible — making them accessible requires significant extra work (essentially doing everything twice).
- We are moving to a **Word document format (read-only)**.
- **Deadline: Every guide must be accessible by March 2026.**
- Compliance is the floor — we're really aiming for **equity**, ensuring resources are accessible to anyone regardless of their circumstances.

**Benefits:** Quick quality control, uniformity, and easier navigation.

---

## Microsoft Word Styles

Word styles apply invisible labels to text that format it uniformly and structure documents so they can be read effectively by screen readers.

### Key Styles Used

| Style | When to Use |
|---|---|
| **Heading 1** | Document title |
| **Heading 2** | Major sections |
| **Heading 3** | Subsections within Heading 2 |
| **Heading 4** | Subsections within Heading 3 (if needed) |
| **Normal** | Regular body text |
| **Strong** | Use instead of bold (Ctrl+B is not compliant) |
| **Intense Emphasis** | Bold and italicized text |
| **Emphasis** | Italicized text only |
| **Bulleted List** | Unordered lists (use instead of the paragraph bullet tool) |
| **Ordered List / Numbered Steps** | Step-by-step processes |
| **Note** | Pop-ups, warnings, or anything requiring extra attention |
| **Clicks** | UI elements a user clicks (e.g., navigation paths like myUFL links, button names) |
| **Normal Image** | Centers images uniformly on the page |

> **Important:** Do not use bold (Ctrl+B), italics (Ctrl+I), or underline (Ctrl+U) directly. These do not send the correct tags to screen readers. Use the **Strong**, **Intense Emphasis**, and **Emphasis** styles instead.

> **Note style:** Type "Note:", "Warning:", or "Attention:" at the start. Make that lead word **Strong**. Avoid bulleted lists within Note boxes — they tend to break formatting.

> **Clicks style:** Apply only to the noun (the thing being clicked), not the verb. For example: click **OK** — apply Clicks style to "OK," not "click."

---

## Document Requirements for Compliance

Every accessible document must have:

1. **Heading structure and hierarchy** (Heading 1 → 2 → 3 as appropriate)
2. **Numbered steps** for any process descriptions
3. **Bulleted guidance** using the Bulleted List style
4. **Auto Table of Contents** (required if the document is more than 3 pages)
5. **Sufficient text/color contrast** for users with color blindness or vision impairment
6. **No emphasis via color alone** — no highlights or font color changes without using styles
7. **Compliant images** (see Images section below)
8. **Compliant tables** (see Tables section below)
9. **Descriptive hyperlinks** (see Hyperlinks section below)
10. **Metadata title** set in File > Info
11. **Standardized T&OD header and footer**
12. **Saved as read-only**

---

## Images

- **Avoid images with text** where possible. When screenshots must include text, write a real-text description alongside the image.
- **All images must be inline with text** — no text wrapping (right-click image > Wrap Text > In Line with Text). Screen readers do not read floating elements.
- **Decorative images** (those conveying no information) should be marked as decorative in the alt text panel — do not write alt text for these.
- **Alt text** is required for all informational images. Best practice:
  - 150 characters or less
  - Describe what is *seen*, not that it's "a picture of…"
  - Example: instead of "picture of bread, knife, peanut butter," write "2 slices of white bread aligned in a row with a plate, peanut butter, jelly, and a butter knife"
- **All images should have a black border**, weight **2¼ pt**, for visual separation from surrounding text.
- Apply the **Normal Image** style to center images (appropriate in most cases; large images may be left-aligned).

To add alt text: right-click the image > View Alt Text.

---

## Tables

Tables should **only be used for data** — not for page layout or visual organization.

### Table Requirements

- **No merged cells** — every cell must be its own individual cell
- **No lists or images inside cells**
- **Header Row** must be enabled (Table Design > check Header Row)
- **Banded Rows** are encouraged
- **Text wrapping must be set to None** (Table Properties > Text Wrapping > None)
- In Table Properties > Row:
  - Check **Repeat as header row at top of each page**
  - Uncheck **Allow row to break across pages**
- **Alt text is required** for tables (Table Properties > Alt Text):
  - Provide a **Title** (e.g., "Ingredients List")
  - Provide a **Description** of the table contents (can be longer than image alt text)

> Both the table itself and the alt text are required — screen readers may read both.

Brady's note: *"I don't ever really want to use tables unless they're absolutely necessary — they're a real pain and don't always look great after all the formatting requirements."*

---

## Hyperlinks

- **Do not paste raw URLs.** Screen readers will read every character of the URL aloud.
- Use **descriptive display text** instead. Right-click the link > Edit Hyperlink > change the "Text to display" field to a meaningful label (e.g., "T&OD PBJ Toolkit" instead of the full URL).
- **Email addresses** should be hyperlinked with a `mailto:` link. Word often does this automatically. Verify via right-click > Edit Hyperlink > Email Address tab. The text to display should be the email address itself.

---

## Table of Contents

- Required if the document is **more than 3 pages long** (best practice is to always include it).
- Insert via: References > Table of Contents > select either Automatic Table 1 or 2.
- Place the TOC **after the title and any opening paragraph**, on its own page.
- If page order changes after inserting the TOC, click **Update Table > Update entire table**.

---

## Header and Footer

- Use the **T&OD header** from the template (Insert > Header > select TNODIG header from dropdown). This is text-based, so no alt text is needed.
- **Footer format:**
  - Line 1: Department | Unit (e.g., "Procurement Systems | UF GO Travel & PCard System")
  - Line 2: Name of the guide
  - Keep footer on one line where possible — delete unnecessary spaces to prevent wrapping.

---

## Metadata and Read-Only Settings

### Metadata Title

- Go to **File > Info**.
- Set the **Title field** to exactly match the Heading 1 title of the document.
- The file name can differ, but the metadata title must match the guide's heading.

### Read-Only

- Go to **File > Info > Protect Document > Always Open Read-Only**.
- This does not password-protect the file. It simply opens in read-only mode by default so users don't accidentally edit instructions. Users can turn this off if they download and want to edit their own copy.

---

## Accessibility Checker

Run after all formatting, alt text, and tables are complete.

- Access via: **Review > Check Accessibility**, or the accessibility button at the bottom of the screen.
- The checker is not comprehensive — it is a basic spot-check, not a full audit.
- It will flag issues such as:
  - Hard-to-read text contrast
  - Missing alt text
  - Other structural issues

### Color Contrast

- Use the **[WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/)** to verify text/background contrast ratios.
- Get the hex color value from Word: Home > Font Color > More Colors.
- The document must pass **WCAG AA** for normal, large, and bold text.
- **No red text** — red is difficult for colorblind users to see. A darker red for callout annotations on images is acceptable, but never pure red for body text.

**Gwynn [41:12]:** Red and green are the number one colors not seen by colorblind people.

---

## Scope: What Documents Must Be Compliant?

**Gwynn [15:16]:** If a document is posted on any UF domain website, it must follow these standards. Additionally, if we send a handout for a course via email, or share it in a Zoom chat for people to open, it must also follow these standards.

**Dwan [14:29] / Gwynn [15:00]:** Internal documents and Teams files used only within the team don't necessarily fall under this mandate, but anything distributed externally does. Dwan noted she would follow up separately given the high volume of stakeholder-facing materials her area produces.

---

## Workflow Recommendations

- Work in the **Microsoft 365 desktop app** — not inside Teams or a web browser, as features don't work reliably in those environments.
- Do not convert to PDF — many accessibility settings are lost in the conversion, and PDFs are being phased out.
- Use the **T&OD Word template** as your starting point. All styles and the header/footer will be pre-configured.
- T&OD can set up the styles on individual computers (approximately 5 minutes per person) so the styles are available in every new Word document.

---

## Q&A Highlights

**Heather [43:50]:** Where will files live going forward — will Teams still be used?

**Gwynn:** For now, continue the existing workflow (Teams editing, notify T&OD, they verify accessibility and move to the website). As Workday approaches, we'll determine the longer-term storage strategy together. Send any pending changes to **Gwynn** so she can route them to someone with capacity.

**Kelsey [47:11]:** For high-volume teams (UF GO), it would be helpful to have the tools and template so guides can be made as accessible as possible before sending to T&OD, reducing rework.

**Gwynn:** Agreed — next step is for Brady/Mitch to schedule an **in-person visit** to set up styles on team computers. Heather's team is available; Kelsey's team will send available windows. In the meantime, Brady will send the **PDF summary and template** as soon as possible.

---

## Next Steps

- [ ] Brady to send the **PDF checklist and Word template** to Heather's team.
- [ ] Gwynn/Brady/Mitch to **schedule in-person visit** to set up Word styles on team computers (Kelsey's team to send availability).
- [ ] All outward-facing instruction guides to be **accessible by March 2026**.
- [ ] Teams continue current workflow (edit in Teams > notify Gwynn) until further notice.
- [ ] T&OD communication team will notify end users when updated resources go live (users may push back on the switch from PDFs — teams should be ready to explain the rationale).
