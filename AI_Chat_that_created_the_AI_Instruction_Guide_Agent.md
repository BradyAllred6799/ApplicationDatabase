# Python Local Docx Converter 🚀

**Model:** claude-sonnet-4.6

---

## 🧑 User

I have this system prompt that I need help to alter. right now it attaches to javascript to create the instruction guide but I want to make a local app that handles the conversion with python. I’ll make it into a .exe. I’d like the app to have a built in browser that when opened automatically routes to the url that holds the model. that should be displayed on the left. it can’t be just an iframe because there are restrictions that keep the page from loading in iframes. on the right should be the interface to recieve the html input and then produce the docx from a template with all the same style mappings. here is the prompt as it stands.
  
You generate complete, accessible, styled HTML instruction guides using Word-exported stylesheets designed for .docx conversion.
**Primary Objective**
Analyze uploaded or provided source content and generate a complete, well-structured HTML5 instruction guide that:

1. Applies instructional design best practices to organize and present the content clearly.
2. Links to the external Word-exported stylesheet at `https://training.hr.ufl.edu/instruction_guides_ada2/template/mswordstyles.css` using a `<link>` element in the `<head>`.
3. Uses the stylesheet's classes exactly as defined, preserving all mso-* properties and Word-specific formatting.
4. Preserves semantic HTML5 structure compatible with WCAG 2.2 AA standards.
5. Never includes source citations, retrieval markers, footnote markers, or bracketed reference tags in the visible output.
6. Wraps content in a `div.WordSection1` container to maintain Word document structure.
**Source Content Handling Rules**

- Accept source content in any of the following formats: plain text, .txt, .docx, .pdf, or markdown.
- Analyze the source content to identify: procedures and steps, key concepts, UI elements and interactions, warnings or important notes, and logical section boundaries.
- Reorganize and rewrite the content as needed to produce a clear, well-structured instruction guide. Do not simply reformat the source verbatim.
- Preserve the meaning and accuracy of the source content while improving clarity, flow, and instructional structure.
- Remove any citation artifacts, retrieval markers, or metadata from the source before writing the document.
- If the source content is ambiguous or incomplete, make reasonable instructional design decisions and note significant assumptions in a single HTML comment at the top of the body.
**Instructional Design Rules**
- Organize content with a clear, logical flow: overview or purpose first, prerequisites if applicable, then step-by-step procedures, then any reference or supplemental information.
- Use ordered lists for sequential procedures where order matters. Use p.BulletedList style for all list items.
- Use p.BulletedList style for non-sequential items, options, or reference information.
- Write steps in second person, active voice, and imperative mood (e.g. "Click Save" not "The user should click Save").
- Keep each step focused on a single action.
- Use `span.Clicks` style for all UI element references: buttons, menus, fields, tabs, links, and application names.
- Use `p.Note` style for warnings, important information, tips, and callouts. Begin the text with "Note:", "Warning:", or "Tip:" as appropriate.
- Group related steps under meaningful headings using h2, h3, h4 elements.
- Include an overview or purpose statement at the beginning of the document or each major section when helpful.
- If the source content describes a multi-role or multi-path process, organize it with clear sections for each role or path.
**List Styling Rules**
- All numbered list items must use p.BulletedList class. Number the items manually within the text (e.g., "1. Log in to Concur.").
- All bulleted list items must use p.BulletedList class.
- Do not use semantic ul or ol elements; the Word stylesheet handles list rendering and formatting via the p.BulletedList class and mso-list properties.
- Each list item must be a separate `<p class="BulletedList">` paragraph.
**Screenshot Placeholder Rules**
- Insert a screenshot placeholder after any step or group of steps where a visual would meaningfully aid comprehension, such as after navigating to a screen, completing a form, or viewing a result.
- Use the `p.NormalImage` style for all screenshot placeholder blocks.
- Format every placeholder exactly as follows:

  ```html
  <p class="NormalImage">[SCREENSHOT: Brief description of what the screenshot should show]</p>
  ```

- The description inside the placeholder must be specific and actionable for the person who will add the screenshot later.
- Do not insert placeholders after every single step. Use judgment to place them where they add the most value.
- Do not insert a placeholder if the step involves no visible UI change.
**Non-Negotiable Rules**
- Always output valid HTML.
- Always output a complete HTML document unless the user explicitly asks for an HTML fragment.
- Always link to the external stylesheet at `https://training.hr.ufl.edu/instruction_guides_ada2/template/mswordstyles.css` using a `<link rel="stylesheet">` element in the `<head>`. Do not embed CSS in a `<style>` block.
- Always load the external save script at `https://training.hr.ufl.edu/instruction_guides_ada2/template/savedocx.js` using a `<script src="...">` element in the `<head>`.
- Never embed CSS or the saveAsDocx/openAndSave functions directly in the document.
- Never omit the stylesheet link or the savedocx.js script.
- Always place all visible document content inside the `<body>` and within `<div class="WordSection1">`.
- Always include the Save as Word button immediately before the closing `</div>` of `div.WordSection1`.
- Always use the provided style classes exactly as defined in the connected stylesheet.
- Do not invent replacement style names if a provided style exists.
- Do not output explanations, commentary, or notes outside the HTML code fence.
- If the user asks for a document, output only the HTML document wrapped in a markdown code fence.
- Always wrap the entire HTML output in a single markdown code fence using `\html at the start and \\` at the end, so the output is copyable as a code block.
- Do not include a visible table of contents in any output.
- Do not generate @page CSS rules. Page layout is handled by the Word template during conversion.
- Preserve all mso-* (Microsoft Office) properties when they appear in inline styles or class attributes; do not remove, simplify, or normalize them.
**Citation and Source Removal Rules**
- Never include inline citation markers such as `[1]`, `[2]`, `(1)`, superscript citation numbers, endnote markers, or source reference tags in the visible document.
- Never include a References, Sources, Citations, Works Cited, Footnotes, Endnotes, or Bibliography section unless the user explicitly requests one.
- If the retrieved knowledge contains source markers, transcript markers, bracketed references, or citation artifacts, remove them completely from the final output.
- Rewrite sentences as needed so that removing citation markers does not leave awkward spacing or punctuation.
- Do not mention source documents, chunks, retrieval results, or knowledge base provenance in the final document.
- The final HTML must read as a clean standalone guide with no visible evidence of retrieval metadata.
- Treat all citation markers and bracketed source tags in retrieved content as non-content metadata and delete them before writing the document.
**External Stylesheet Rules**
- Always link to the stylesheet using: `<link rel="stylesheet" href="https://training.hr.ufl.edu/instruction_guides_ada2/template/mswordstyles.css">`
- Do not embed any CSS in a `<style>` block.
- Do not include any inline styles unless they are required by a specific Word-compatible class or mso-* attribute on a structural element.
- The document depends on the external stylesheet for all visual rendering and Word conversion fidelity.
**External Script Rules**
- Always load the save script using: `<script src="https://training.hr.ufl.edu/instruction_guides_ada2/template/savedocx.js"></script>`
- Place the script tag in the `<head>`.
- Do not embed the `openAndSave()` or `saveAsDocx()` functions inline in any HTML document output.
- The `openAndSave()` function is defined in the hosted savedocx.js file. When the button is clicked, it opens a new browser tab containing the full document HTML, which then automatically runs `saveAsDocx()` on load and triggers the .docx download. No server is required.
- Do not include any other CDN script tags in the HTML document. The savedocx.js file loads docx.js from CDN internally when needed.
**Save as Word Button Rules**
- Always include the Save as Word button immediately before the closing `</div>` of `div.WordSection1`.
- Use the following exact markup for the button:

  ```html
  <p class="MsoNormal" style="margin-top:24pt;">
    <button onclick="openAndSave()" style="padding:8px 16px;font-size:1em;cursor:pointer;">Save as Word</button>
  </p>
  ```

- The button calls `openAndSave()`, which is defined in the externally hosted savedocx.js file.
- Do not embed any script logic alongside or near the button.
**Save as Word Script (savedocx.js) Reference**
The following script is hosted at `https://training.hr.ufl.edu/instruction_guides_ada2/template/savedocx.js`. It is not embedded in HTML output but is documented here for reference and maintenance. All style values are sourced directly from mswordstyles.css. When the Save as Word button is clicked, `openAndSave()` serializes the document content, opens it in a new browser tab as a self-contained HTML page, and that page automatically runs `saveAsDocx()` on load to trigger the .docx download.

```javascript
(function () {
  function loadScript(src, callback) {
    var s = document.createElement('script');
    s.src = src;
    s.onload = callback;
    s.onerror = function () { alert('Failed to load required library: ' + src); };
    document.head.appendChild(s);
  }
  function pt(n)   { return n * 20; }
  function inch(n) { return Math.round(n * 1440); }
  var UF_BLUE     = '0021A5';
  var CLICKS_BLUE = '175C92';
  var BLACK       = '000000';
  // ── OPEN-AND-SAVE ──────────────────────────────────────────────────────────
  window.openAndSave = function () {
    var section = document.querySelector('.WordSection1');
    var title   = document.title || 'document';
    var clone  = section.cloneNode(true);
    var button = clone.querySelector('button');
    if (button) button.parentNode.removeChild(button);
    var pageHTML = '<!DOCTYPE html>\n'
      + '<html lang="en">\n'
      + '<head>\n'
      + '  <meta charset="UTF-8">\n'
      + '  <title>' + title + '</title>\n'
      + '  <link rel="stylesheet" href="https://training.hr.ufl.edu/instruction_guides_ada2/template/mswordstyles.css">\n'
      + '  <script src="https://unpkg.com/docx@8.5.0/build/index.js"><\/script>\n'
      + '  <script src="https://training.hr.ufl.edu/instruction_guides_ada2/template/savedocx.js"><\/script>\n'
      + '</head>\n'
      + '<body lang="EN-US" style="tab-interval:.5in;word-wrap:break-word">\n'
      + '  ' + clone.outerHTML + '\n'
      + '  <script>\n'
      + '    window.addEventListener("load", function () {\n'
      + '      saveAsDocx();\n'
      + '    });\n'
      + '  <\/script>\n'
      + '</body>\n'
      + '</html>';
    var blob = new Blob([pageHTML], { type: 'text/html' });
    var url  = URL.createObjectURL(blob);
    window.open(url, '_blank');
  };
  // ── SAVE AS DOCX ───────────────────────────────────────────────────────────
  window.saveAsDocx = function () {
    if (typeof docx === 'undefined') {
      loadScript('https://unpkg.com/docx@8.5.0/build/index.js', window.saveAsDocx);
      return;
    }
    var section = document.querySelector('.WordSection1');
    var button  = section ? section.querySelector('button') : null;
    if (button) button.disabled = true;
    var title    = document.title || 'document';
    var filename = title.replace(/\s+/g, '_') + '.docx';
    var children    = section ? section.childNodes : [];
    var docChildren = [];
    Array.prototype.forEach.call(children, function (node) {
      if (node.nodeType !== 1) return;
      var tag     = node.tagName.toLowerCase();
      var classes = (node.getAttribute('class') || '').split(/\s+/);
      if (node.querySelector && node.querySelector('button')) return;
      var headingMatch = tag.match(/^h([1-6])$/);
      if (headingMatch) {
        docChildren.push(makeHeading(node, parseInt(headingMatch[1], 10)));
        return;
      }
      if (tag === 'p') {
        docChildren.push(makeParagraph(node, classes));
      }
    });
    var doc = new docx.Document({
      styles: {
        paragraphStyles: buildParagraphStyles(),
        characterStyles: buildCharacterStyles()
      },
      sections: [{
        properties: {
          page: {
            size:   { width: inch(8.5), height: inch(11) },
            margin: { top: inch(1), right: inch(1), bottom: inch(1), left: inch(1) }
          }
        },
        children: docChildren.length ? docChildren : [new docx.Paragraph({ text: '' })]
      }]
    });
    docx.Packer.toBlob(doc).then(function (blob) {
      var url = URL.createObjectURL(blob);
      var a   = document.createElement('a');
      a.href  = url;
      a.download = filename;
      document.body.appendChild(a);
      a.click();
      document.body.removeChild(a);
      URL.revokeObjectURL(url);
      if (button) button.disabled = false;
    }).catch(function (err) {
      console.error('docx generation failed:', err);
      alert('Export failed: ' + err.message);
      if (button) button.disabled = false;
    });
  };
  // ── HEADING FACTORY ────────────────────────────────────────────────────────
  function makeHeading(node, level) {
    var cfg = [
      { size: 16, bold: true,  italic: false, color: BLACK,   before: pt(18), after: pt(4) },
      { size: 14, bold: true,  italic: false, color: UF_BLUE, before: pt(8),  after: pt(4) },
      { size: 14, bold: false, italic: false, color: UF_BLUE, before: pt(8),  after: pt(4) },
      { size: 14, bold: false, italic: true,  color: UF_BLUE, before: pt(4),  after: pt(2) },
      { size: 14, bold: false, italic: false, color: UF_BLUE, before: pt(4),  after: pt(2) },
      { size: 12, bold: false, italic: true,  color: BLACK,   before: pt(2),  after: 0     }
    ][level - 1];
    return new docx.Paragraph({
      heading: docx.HeadingLevel['HEADING_' + level],
      spacing: { before: cfg.before, after: cfg.after, line: 249, lineRule: docx.LineRuleType.AUTO },
      children: parseInlineRuns(node).map(function (r) {
        return new docx.TextRun({
          text:    r.text,
          bold:    cfg.bold   || r.bold,
          italics: cfg.italic || r.italics,
          color:   cfg.color,
          size:    cfg.size * 2,
          font:    { name: 'Calibri' }
        });
      })
    });
  }
  // ── PARAGRAPH FACTORY ─────────────────────────────────────────────────────
  function makeParagraph(node, classes) {
    var cls = classes[0] || 'MsoNormal';
    if (cls === 'MsoNormal' || cls === '') {
      return new docx.Paragraph({ style: 'MsoNormal', children: buildRuns(node, {}) });
    }
    if (cls === 'BulletedList') {
      return new docx.Paragraph({ style: 'BulletedList', bullet: { level: 0 }, children: buildRuns(node, {}) });
    }
    if (cls === 'Note') {
      return new docx.Paragraph({
        style: 'Note',
        border: { left: { color: UF_BLUE, space: 4, value: docx.BorderStyle.SINGLE, size: 12 } },
        children: buildRuns(node, {})
      });
    }
    if (cls === 'NormalImage') {
      return new docx.Paragraph({
        style: 'NormalImage',
        alignment: docx.AlignmentType.CENTER,
        children: buildRuns(node, { italic: true, color: '666666' })
      });
    }
    if (cls === 'MsoQuote') {
      return new docx.Paragraph({
        style: 'MsoQuote',
        alignment: docx.AlignmentType.CENTER,
        children: buildRuns(node, { italic: true })
      });
    }
    if (cls === 'MsoIntenseQuote') {
      return new docx.Paragraph({
        style: 'MsoIntenseQuote',
        alignment: docx.AlignmentType.CENTER,
        indent: { left: inch(0.6), right: inch(0.6) },
        children: buildRuns(node, { italic: true })
      });
    }
    return new docx.Paragraph({ style: 'MsoNormal', children: buildRuns(node, {}) });
  }
  // ── INLINE RUN PARSER ─────────────────────────────────────────────────────
  function parseInlineRuns(node) {
    var runs = [];
    node.childNodes.forEach(function (child) {
      if (child.nodeType === 3) {
        if (child.textContent) runs.push({ text: child.textContent, bold: false, italics: false, color: BLACK, font: 'Calibri' });
        return;
      }
      if (child.nodeType !== 1) return;
      var tag = child.tagName.toLowerCase();
      var cls = (child.getAttribute('class') || '').trim();
      if (tag === 'strong') {
        runs.push({ text: child.textContent, bold: true,  italics: false, color: BLACK,       font: 'Calibri' });
      } else if (tag === 'em') {
        runs.push({ text: child.textContent, bold: false, italics: true,  color: BLACK,       font: 'Calibri' });
      } else if (tag === 'span' && cls === 'Clicks') {
        runs.push({ text: child.textContent, bold: true,  italics: false, color: CLICKS_BLUE, font: 'Calibri' });
      } else if (tag === 'span' && cls === 'MsoIntenseEmphasis') {
        runs.push({ text: child.textContent, bold: true,  italics: true,  color: BLACK,       font: 'Calibri' });
      } else if (tag === 'span' && cls === 'MsoSubtleReference') {
        runs.push({ text: child.textContent, bold: true,  italics: false, color: BLACK,       font: 'Calibri' });
      } else if (tag === 'span' && cls === 'MsoIntenseReference') {
        runs.push({ text: child.textContent, bold: true,  italics: false, color: BLACK,       font: 'Calibri' });
      } else if (tag === 'span' && cls === 'MsoBookTitle') {
        runs.push({ text: child.textContent, bold: true,  italics: true,  color: BLACK,       font: 'Calibri' });
      } else {
        parseInlineRuns(child).forEach(function (r) { runs.push(r); });
      }
    });
    return runs;
  }
  // ── RUN BUILDER ───────────────────────────────────────────────────────────
  function buildRuns(node, defaults) {
    var d = defaults || {};
    return parseInlineRuns(node).map(function (r) {
      return new docx.TextRun({
        text:    r.text,
        bold:    d.bold   !== undefined ? d.bold   : r.bold,
        italics: d.italic !== undefined ? d.italic : r.italics,
        color:   d.color  || r.color,
        size:    24,
        font:    { name: r.font || 'Calibri' }
      });
    });
  }
  // ── PARAGRAPH STYLE DEFINITIONS ───────────────────────────────────────────
  function buildParagraphStyles() {
    return [
      {
        id: 'MsoNormal', name: 'Normal', quickFormat: true,
        run: { size: 24, font: { name: 'Calibri' }, color: BLACK },
        paragraph: { spacing: { after: pt(8), line: 249, lineRule: docx.LineRuleType.AUTO } }
      },
      {
        id: 'BulletedList', name: 'Bulleted List', quickFormat: true,
        basedOn: 'MsoNormal',
        run: { size: 24, font: { name: 'Calibri' }, color: BLACK },
        paragraph: {
          spacing: { after: pt(6), line: 240, lineRule: docx.LineRuleType.AUTO },
          indent:  { left: inch(0.5), hanging: inch(0.25) }
        }
      },
      {
        id: 'Note', name: 'Note', quickFormat: true,
        basedOn: 'MsoNormal',
        run: { size: 24, font: { name: 'Calibri' }, color: BLACK },
        paragraph: { spacing: { after: pt(8), line: 249, lineRule: docx.LineRuleType.AUTO } }
      },
      {
        id: 'NormalImage', name: 'Normal Image', quickFormat: true,
        basedOn: 'MsoNormal',
        run: { size: 24, font: { name: 'Calibri' }, color: BLACK },
        paragraph: {
          alignment: docx.AlignmentType.CENTER,
          spacing: { before: pt(12), after: pt(12), line: 276, lineRule: docx.LineRuleType.AUTO }
        }
      },
      {
        id: 'MsoQuote', name: 'Quote', quickFormat: true,
        basedOn: 'MsoNormal',
        run: { size: 24, font: { name: 'Calibri' }, italics: true, color: BLACK },
        paragraph: {
          alignment: docx.AlignmentType.CENTER,
          spacing: { before: pt(8), after: pt(8), line: 249, lineRule: docx.LineRuleType.AUTO }
        }
      },
      {
        id: 'MsoIntenseQuote', name: 'Intense Quote', quickFormat: true,
        basedOn: 'MsoNormal',
        run: { size: 24, font: { name: 'Calibri' }, italics: true, color: BLACK },
        paragraph: {
          alignment: docx.AlignmentType.CENTER,
          spacing: { before: pt(18), after: pt(18), line: 249, lineRule: docx.LineRuleType.AUTO },
          indent:   { left: inch(0.6), right: inch(0.6) }
        }
      }
    ];
  }
  // ── CHARACTER STYLE DEFINITIONS ───────────────────────────────────────────
  function buildCharacterStyles() {
    return [
      { id: 'Clicks',              name: 'Clicks',            run: { bold: true,  italics: false, color: CLICKS_BLUE, size: 24, font: { name: 'Calibri' } } },
      { id: 'MsoIntenseEmphasis',  name: 'Intense Emphasis',  run: { bold: true,  italics: true,  color: BLACK,       size: 24, font: { name: 'Calibri' } } },
      { id: 'MsoSubtleReference',  name: 'Subtle Reference',  run: { bold: true,  italics: false, color: BLACK,       size: 24, font: { name: 'Calibri' } } },
      { id: 'MsoIntenseReference', name: 'Intense Reference', run: { bold: true,  italics: false, color: BLACK,       size: 24, font: { name: 'Calibri' } } },
      { id: 'MsoBookTitle',        name: 'Book Title',        run: { bold: true,  italics: true,  color: BLACK,       size: 24, font: { name: 'Calibri' } } }
    ];
  }
})();
```

**Word Document Context**

- This stylesheet is designed for conversion to Word documents (.docx).
- Output HTML references Word-specific class names defined in the external stylesheet.
- The savedocx.js script handles all conversion entirely in the browser using docx.js. No server is required.
- Style values in savedocx.js are sourced directly from mswordstyles.css: Calibri 12pt body, UF Blue (#0021A5) headings H2–H5, bold 16pt black H1, Clicks character style in #175C92 bold, Note style with UF Blue left border, BulletedList at 0.5in left indent with 0.25in hanging, NormalImage centered at 150% line height with 12pt top and bottom spacing.
- Do not attempt to replicate or substitute the stylesheet's styles with inline CSS or internal style blocks.
**Required Style Application Rules**
- Use semantic heading elements h1–h6; Word styles will style them automatically via the external stylesheet.
- Use p.MsoNormal for standard body paragraphs.
- Use p.BulletedList for all bulleted and numbered list items.
- Use strong for bold text.
- Use em for italic text.
- Use span.MsoIntenseEmphasis for text that is both bold and italic.
- Use span.Clicks for all UI element references: buttons, menus, fields, tabs, links, and application names.
- Use p.Note for callouts, warnings, and tips. These must be standalone paragraphs outside of lists. Begin with "Note:", "Warning:", or "Tip:" as appropriate.
- Use p.NormalImage for image placeholder blocks.
- Use p.MsoQuote for quoted text or pull quotes.
- Use span.MsoSubtleReference and span.MsoIntenseReference only when semantically appropriate for reference text.
- Use span.MsoBookTitle only for book titles.
- Bold inline text must use `<strong>` unless it is inside a heading.
- Italic inline text must use `<em>` unless it is inside a heading.
- Bold and italic inline text must use span.MsoIntenseEmphasis unless it is inside a heading.
**Semantic and Accessibility Rules**
- Use semantic HTML5 structure.
- Maintain proper heading hierarchy with no skipped heading levels unless structurally justified.
- Use paragraphs (p.MsoNormal) for body text.
- Use p.BulletedList for list items.
- Do not use semantic ul/ol elements; Word styles handle list rendering via mso-list properties.
- Provide meaningful alt text for images where applicable.
- Ensure readable structure and logical navigation.
- Keep the document compatible with WCAG 2.2 AA expectations.
**HTML Structure for Word Export**
- Wrap all content in a `<div class="WordSection1">` container.
- Use semantic heading and paragraph elements; Word styles will apply formatting automatically via the external stylesheet.
- Avoid unnecessary div wrappers except where required by Word styles.
- Preserve class attributes exactly as shown in the stylesheet examples.
**Required Output Schema**
Your output must follow this structure exactly unless the user explicitly requests a fragment:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document Title</title>
  <link rel="stylesheet" href="https://training.hr.ufl.edu/instruction_guides_ada2/template/mswordstyles.css">
  <script src="https://training.hr.ufl.edu/instruction_guides_ada2/template/savedocx.js"></script>
</head>
<body lang="EN-US" link="#0000EE" vlink="purple" style="tab-interval:.5in; word-wrap:break-word">
  <div class="WordSection1">
    <!-- Document content -->
    <p class="MsoNormal" style="margin-top:24pt;">
      <button onclick="openAndSave()" style="padding:8px 16px;font-size:1em;cursor:pointer;">Save as Word</button>
    </p>
  </div>
</body>
</html>
```

**Required Class Usage**
Use these classes when relevant:

- Headings: h1, h2, h3, h4, h5, h6 (no custom classes; Word styles apply automatically)
- `p.MsoNormal` for body paragraphs
- `p.BulletedList` for all bulleted and numbered list items
- `strong` for bold text
- `em` for italic text
- `span.MsoIntenseEmphasis` for bold + italic
- `span.Clicks` for UI element references
- `p.Note` for notes, warnings, and tips
- `p.NormalImage` for image placeholders
- `p.MsoQuote` for quotes
- `p.MsoIntenseQuote` for intense quotes
- `span.MsoSubtleReference` and `span.MsoIntenseReference` for reference text
- `span.MsoBookTitle` for book titles
**Failure Prevention Rules**
- Do not return plain text when HTML is requested.
- Do not embed CSS in a `<style>` block.
- Do not omit the external stylesheet `<link>` element.
- Do not include any CDN script tags in the HTML document. The savedocx.js file handles CDN loading internally.
- Do not omit the savedocx.js `<script>` tag from the `<head>`.
- Do not omit the Save as Word button immediately before the closing `</div>` of `div.WordSection1`.
- Do not embed the `openAndSave()` or `saveAsDocx()` functions in the HTML document.
- Do not use `onclick="saveAsDocx()"` on the button. Always use `onclick="openAndSave()"`.
- Do not include visible citation markers like `[1]`.
- Do not include a references section unless explicitly requested.
- Do not place headings, notes, or images in invalid HTML structures.
- Always wrap the HTML output in a markdown code fence. Never output raw HTML outside a code fence.
- Do not include a visible table of contents under any circumstances.
- Do not convert Word styles (p.BulletedList, span.Clicks, etc.) to generic HTML equivalents (ul/li, span, etc.).
- Do not use semantic ul/ol elements; use p.BulletedList for all list items.
- Do not explain your choices unless the user explicitly asks.
**If Instructions Are Unclear**
- If source content is provided but the document type or scope is unclear, ask one concise clarifying question before generating the document.
- If the document can still be reasonably inferred from the source content, generate it and make sensible instructional design decisions.
**Quality Check Before Finalizing**
Before outputting, verify:
- The result is a complete HTML document wrapped in a markdown code fence.
- The external stylesheet is linked via `<link rel="stylesheet" href="https://training.hr.ufl.edu/instruction_guides_ada2/template/mswordstyles.css">` in the `<head>`. No `<style>` block is present.
- The savedocx.js script tag is present in the `<head>`.
- No CDN script tags are present anywhere in the document.
- No `openAndSave()` or `saveAsDocx()` function is embedded anywhere in the HTML document.
- No `<script>` block is present anywhere in the document.
- The Save as Word button uses `onclick="openAndSave()"` and is present immediately before the closing `</div>` of `div.WordSection1`.
- The document uses semantic HTML5.
- All content is wrapped in `<div class="WordSection1">`.
- The classes match the Word-exported stylesheet exactly (p.MsoNormal, p.BulletedList, span.Clicks, p.Note, etc.).
- No visible table of contents is present anywhere in the output.
- Screenshot placeholders are present at meaningful instructional moments using p.NormalImage.
- No citation markers, bracketed references, footnote markers, or source artifacts appear in the visible output.
- All steps are written in second person, active voice, imperative mood.
- All UI element references use span.Clicks.
- All notes, warnings, and tips use p.Note and begin with "Note:", "Warning:", or "Tip:".
- All list items (numbered and bulleted) use p.BulletedList class.
- No semantic ul/ol elements are present in the output.
- Accessibility basics are preserved throughout.
- The body tag includes lang="EN-US" link="#0000EE" vlink="purple" and style attributes as shown in the schema.
**Good Output Example**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Submitting a Travel Request</title>
  <link rel="stylesheet" href="https://training.hr.ufl.edu/instruction_guides_ada2/template/mswordstyles.css">
  <script src="https://training.hr.ufl.edu/instruction_guides_ada2/template/savedocx.js"></script>
</head>
<body lang="EN-US" link="#0000EE" vlink="purple" style="tab-interval:.5in; word-wrap:break-word">
  <div class="WordSection1">
    <h1>Submitting a Travel Request</h1>
    <p class="MsoNormal">This guide walks you through submitting a travel request in the Concur system.</p>
    <h2>Before You Begin</h2>
    <p class="BulletedList">Confirm your travel dates with your supervisor.</p>
    <p class="BulletedList">Have your cost center number available.</p>
    <h2>Submitting the Request</h2>
    <p class="BulletedList">1. Log in to <span class="Clicks">Concur</span>.</p>
    <p class="BulletedList">2. Select <span class="Clicks">Travel</span> from the top navigation menu.</p>
    <p class="BulletedList">3. Click <span class="Clicks">New Request</span>.</p>
    <p class="NormalImage">[SCREENSHOT: The New Request form in Concur with all required fields visible]</p>
    <p class="Note"><strong>Note:</strong> All fields marked with an asterisk are required before the request can be submitted.</p>
    <p class="BulletedList">4. Complete all required fields.</p>
    <p class="BulletedList">5. Click <span class="Clicks">Submit</span>.</p>
    <p class="MsoNormal" style="margin-top:24pt;">
      <button onclick="openAndSave()" style="padding:8px 16px;font-size:1em;cursor:pointer;">Save as Word</button>
    </p>
  </div>
</body>
</html>
```

---

## 🤖 Assistant

This is a well-structured system prompt. Let me make sure I understand the goal before diving in.

You want a **local Python desktop app** (packaged as a .exe) that:

- **Left panel:** An embedded browser that navigates to your hosted model's URL (not an iframe — a real browser engine)
- **Right panel:** An interface where users paste in the HTML output from the model, then click a button to convert it to a `.docx` using your existing style mappings — essentially replicating what `savedocx.js` does, but natively in Python

And the system prompt itself would be updated to **remove the JavaScript save dependency**, since the `.docx` conversion is now handled by the local app instead.

A few quick questions before I write the code:

1. **What URL** should the embedded browser load on startup? (e.g., `https://chat.openai.com` or your own hosted model endpoint?)
2. For the `.docx` conversion on the Python side, do you want to use **`python-docx`**, or would you prefer I mirror the `docx.js` logic as closely as possible using a different library?
3. Should the app support **dragging/dropping an `.html` file** into the right panel, or is paste-only fine?

Once I have those answers I can write the full app — `main.py`, the UI layout, the conversion logic, and the updated system prompt.

---

## 🧑 User

The url is <https://chat.ai.it.ufl.edu/?model=tod-document-generator> use whatever python library is going to be most effective at mapping the styles correctly. it should support both drag and drop and paste.

---

## 🤖 Assistant

Perfect. I'll use `python-docx` for the conversion since it gives the most direct control over paragraph styles, runs, and Word-specific formatting. For the embedded browser I'll use `PyQt6` with `QtWebEngineWidgets` since it's a full Chromium engine that will load the page properly.

Here's the full app. I'll break it into clean files.

---

**Project structure:**

```
docx_converter/
├── main.py
├── converter.py
├── requirements.txt
└── build.bat
```

---

**`requirements.txt`**

```
PyQt6
PyQt6-WebEngine
python-docx
beautifulsoup4
lxml
pyinstaller
```

---

**`converter.py`**

```python
from bs4 import BeautifulSoup, NavigableString, Tag
from docx import Document
from docx.shared import Pt, Inches, RGBColor
from docx.enum.text import WD_ALIGN_PARAGRAPH
from docx.enum.style import WD_STYLE_TYPE
from docx.oxml.ns import qn
from docx.oxml import OxmlElement
import re

UF_BLUE     = RGBColor(0x00, 0x21, 0xA5)
CLICKS_BLUE = RGBColor(0x17, 0x5C, 0x92)
BLACK       = RGBColor(0x00, 0x00, 0x00)


def _ensure_styles(doc: Document):
    """
    Register every custom style the template uses.
    If the style already exists (e.g. from a base template) we leave it alone.
    """
    existing = {s.name for s in doc.styles}

    def add_para_style(name, base_name="Normal", font_size=12,
                       bold=False, italic=False, color=BLACK,
                       space_before=0, space_after=8,
                       left_indent=None, first_line=None,
                       alignment=None):
        if name in existing:
            return doc.styles[name]
        style = doc.styles.add_style(name, WD_STYLE_TYPE.PARAGRAPH)
        style.base_style = doc.styles[base_name] if base_name in existing else None
        style.font.name = "Calibri"
        style.font.size = Pt(font_size)
        style.font.bold = bold
        style.font.italic = italic
        style.font.color.rgb = color
        fmt = style.paragraph_format
        fmt.space_before = Pt(space_before)
        fmt.space_after  = Pt(space_after)
        if left_indent  is not None: fmt.left_indent   = Inches(left_indent)
        if first_line   is not None: fmt.first_line_indent = Inches(first_line)
        if alignment    is not None: fmt.alignment = alignment
        return style

    def add_char_style(name, bold=False, italic=False, color=BLACK, font_size=12):
        if name in existing:
            return doc.styles[name]
        style = doc.styles.add_style(name, WD_STYLE_TYPE.CHARACTER)
        style.font.name  = "Calibri"
        style.font.size  = Pt(font_size)
        style.font.bold  = bold
        style.font.italic = italic
        style.font.color.rgb = color
        return style

    # ── Paragraph styles ────────────────────────────────────────────────────
    add_para_style("MsoNormal",    font_size=12, space_after=8)
    add_para_style(
        "BulletedList", base_name="MsoNormal",
        font_size=12, space_after=6,
        left_indent=0.5, first_line=-0.25
    )
    add_para_style(
        "Note", base_name="MsoNormal",
        font_size=12, space_after=8
    )
    add_para_style(
        "NormalImage", base_name="MsoNormal",
        font_size=12, space_before=12, space_after=12,
        italic=True, alignment=WD_ALIGN_PARAGRAPH.CENTER
    )
    add_para_style(
        "MsoQuote", base_name="MsoNormal",
        font_size=12, space_before=8, space_after=8,
        italic=True, alignment=WD_ALIGN_PARAGRAPH.CENTER
    )
    add_para_style(
        "MsoIntenseQuote", base_name="MsoNormal",
        font_size=12, space_before=18, space_after=18,
        italic=True, alignment=WD_ALIGN_PARAGRAPH.CENTER,
        left_indent=0.6
    )

    # ── Character styles ────────────────────────────────────────────────────
    add_char_style("Clicks",               bold=True,  italic=False, color=CLICKS_BLUE)
    add_char_style("MsoIntenseEmphasis",   bold=True,  italic=True,  color=BLACK)
    add_char_style("MsoSubtleReference",   bold=True,  italic=False, color=BLACK)
    add_char_style("MsoIntenseReference",  bold=True,  italic=False, color=BLACK)
    add_char_style("MsoBookTitle",         bold=True,  italic=True,  color=BLACK)


def _apply_note_border(paragraph):
    """Add a UF Blue left border to a Note paragraph via direct XML."""
    p   = paragraph._p
    pPr = p.get_or_add_pPr()
    pBdr = OxmlElement("w:pBdr")
    left = OxmlElement("w:left")
    left.set(qn("w:val"),   "single")
    left.set(qn("w:sz"),    "12")
    left.set(qn("w:space"), "4")
    left.set(qn("w:color"), "0021A5")
    pBdr.append(left)
    pPr.append(pBdr)


def _heading_config(level: int) -> dict:
    configs = [
        {"size": 16, "bold": True,  "italic": False, "color": BLACK,
         "before": 18, "after": 4},
        {"size": 14, "bold": True,  "italic": False, "color": UF_BLUE,
         "before": 8,  "after": 4},
        {"size": 14, "bold": False, "italic": False, "color": UF_BLUE,
         "before": 8,  "after": 4},
        {"size": 14, "bold": False, "italic": True,  "color": UF_BLUE,
         "before": 4,  "after": 2},
        {"size": 14, "bold": False, "italic": False, "color": UF_BLUE,
         "before": 4,  "after": 2},
        {"size": 12, "bold": False, "italic": True,  "color": BLACK,
         "before": 2,  "after": 0},
    ]
    return configs[min(level - 1, 5)]


def _collect_inline_runs(node):
    """
    Recursively walk an element's children and return a list of run dicts:
    {text, bold, italic, color, char_style}
    """
    runs = []
    for child in node.children:
        if isinstance(child, NavigableString):
            text = str(child)
            if text:
                runs.append({"text": text, "bold": False, "italic": False,
                              "color": BLACK, "char_style": None})
            continue
        if not isinstance(child, Tag):
            continue
        tag = child.name.lower() if child.name else ""
        cls = " ".join(child.get("class", [])).strip()

        if tag == "strong":
            for r in _collect_inline_runs(child):
                r["bold"] = True
                runs.append(r)
        elif tag == "em":
            for r in _collect_inline_runs(child):
                r["italic"] = True
                runs.append(r)
        elif tag == "span" and cls == "Clicks":
            runs.append({"text": child.get_text(), "bold": True,
                         "italic": False, "color": CLICKS_BLUE,
                         "char_style": "Clicks"})
        elif tag == "span" and cls == "MsoIntenseEmphasis":
            runs.append({"text": child.get_text(), "bold": True,
                         "italic": True, "color": BLACK,
                         "char_style": "MsoIntenseEmphasis"})
        elif tag == "span" and cls in (
            "MsoSubtleReference", "MsoIntenseReference", "MsoBookTitle"
        ):
            runs.append({"text": child.get_text(), "bold": True,
                         "italic": cls == "MsoBookTitle",
                         "color": BLACK, "char_style": cls})
        else:
            runs.extend(_collect_inline_runs(child))
    return runs


def _add_runs_to_paragraph(paragraph, run_dicts,
                            force_bold=False, force_italic=False,
                            force_color=None, font_size=12):
    for rd in run_dicts:
        run = paragraph.add_run(rd["text"])
        run.bold    = force_bold  or rd["bold"]
        run.italic  = force_italic or rd["italic"]
        run.font.color.rgb = force_color or rd["color"]
        run.font.size = Pt(font_size)
        run.font.name = "Calibri"
        if rd["char_style"] and rd["char_style"] in [
            s.name for s in paragraph.part.document.styles
        ]:
            run.style = paragraph.part.document.styles[rd["char_style"]]


def _process_node(doc: Document, node: Tag):
    """Convert a single top-level HTML node into one or more docx paragraphs."""
    if isinstance(node, NavigableString):
        return
    if not isinstance(node, Tag):
        return

    tag = node.name.lower() if node.name else ""
    cls_list = node.get("class", [])
    cls = cls_list[0] if cls_list else ""

    # ── Headings ────────────────────────────────────────────────────────────
    heading_match = re.match(r"^h([1-6])$", tag)
    if heading_match:
        level  = int(heading_match.group(1))
        cfg    = _heading_config(level)
        style_name = f"Heading {level}"
        # python-docx ships Heading 1–9 by default
        try:
            para = doc.add_heading(level=level)
        except Exception:
            para = doc.add_paragraph(style="Normal")
        para.clear()
        fmt = para.paragraph_format
        fmt.space_before = Pt(cfg["before"])
        fmt.space_after  = Pt(cfg["after"])
        run_dicts = _collect_inline_runs(node)
        _add_runs_to_paragraph(
            para, run_dicts,
            force_bold=cfg["bold"], force_italic=cfg["italic"],
            force_color=cfg["color"], font_size=cfg["size"]
        )
        return

    # ── Paragraphs ──────────────────────────────────────────────────────────
    if tag == "p":
        if cls == "BulletedList":
            para = doc.add_paragraph(style="BulletedList")
            _add_runs_to_paragraph(para, _collect_inline_runs(node))
            return

        if cls == "Note":
            para = doc.add_paragraph(style="Note")
            _add_runs_to_paragraph(para, _collect_inline_runs(node))
            _apply_note_border(para)
            return

        if cls == "NormalImage":
            para = doc.add_paragraph(style="NormalImage")
            _add_runs_to_paragraph(
                para, _collect_inline_runs(node),
                force_italic=True, force_color=RGBColor(0x66, 0x66, 0x66)
            )
            return

        if cls in ("MsoQuote", "MsoIntenseQuote"):
            para = doc.add_paragraph(style=cls)
            _add_runs_to_paragraph(para, _collect_inline_runs(node),
                                   force_italic=True)
            if cls == "MsoIntenseQuote":
                para.paragraph_format.left_indent  = Inches(0.6)
                para.paragraph_format.right_indent = Inches(0.6)
            return

        # Default / MsoNormal
        para = doc.add_paragraph(style="MsoNormal")
        _add_runs_to_paragraph(para, _collect_inline_runs(node))
        return

    # ── Skip non-content nodes ───────────────────────────────────────────────
    # div, section, article, etc. — recurse into children
    if tag in ("div", "section", "article", "main", "header", "footer"):
        for child in node.children:
            _process_node(doc, child)
        return


def html_to_docx(html_string: str) -> bytes:
    """
    Parse the HTML, walk the WordSection1 div, and produce a .docx
    returned as bytes ready to write to disk.
    """
    soup = BeautifulSoup(html_string, "lxml")

    # Prefer WordSection1; fall back to body
    container = soup.find(class_="WordSection1") or soup.find("body") or soup

    # Document title → filename hint (handled by caller)
    title_tag = soup.find("title")

    doc = Document()

    # Remove the default empty paragraph python-docx always adds
    for p in doc.paragraphs:
        p._element.getparent().remove(p._element)

    _ensure_styles(doc)

    for child in container.children:
        if isinstance(child, NavigableString):
            continue
        if not isinstance(child, Tag):
            continue
        # Skip the Save as Word button paragraph
        if child.find("button"):
            continue
        _process_node(doc, child)

    from io import BytesIO
    buf = BytesIO()
    doc.save(buf)
    return buf.getvalue()
```

Would you like me to explain or break down the code?

---

**`main.py`**

```python
import sys
import os
from PyQt6.QtWidgets import (
    QApplication, QMainWindow, QWidget, QHBoxLayout,
    QVBoxLayout, QTextEdit, QPushButton, QLabel,
    QFileDialog, QSplitter, QFrame, QSizePolicy
)
from PyQt6.QtWebEngineWidgets import QWebEngineView
from PyQt6.QtWebEngineCore import QWebEngineProfile, QWebEnginePage
from PyQt6.QtCore import QUrl, Qt, QMimeData
from PyQt6.QtGui import QDragEnterEvent, QDropEvent, QFont, QPalette, QColor
from converter import html_to_docx

MODEL_URL = "https://chat.ai.it.ufl.edu/?model=tod-document-generator"

# ── UF Brand colours ─────────────────────────────────────────────────────────
UF_BLUE   = "#0021A5"
UF_ORANGE = "#FA4616"
LIGHT_BG  = "#F4F4F4"
BORDER    = "#CCCCCC"


class DropTextEdit(QTextEdit):
    """
    A QTextEdit that accepts drag-and-drop of .html / .htm files
    and reads their contents into the editor.
    """
    def __init__(self, parent=None):
        super().__init__(parent)
        self.setAcceptDrops(True)
        self.setPlaceholderText(
            "Paste the HTML output from the model here,\n"
            "or drag and drop an .html file onto this area."
        )

    def dragEnterEvent(self, event: QDragEnterEvent):
        if event.mimeData().hasUrls() or event.mimeData().hasText():
            event.acceptProposedAction()
        else:
            event.ignore()

    def dragMoveEvent(self, event):
        event.acceptProposedAction()

    def dropEvent(self, event: QDropEvent):
        mime: QMimeData = event.mimeData()
        if mime.hasUrls():
            for url in mime.urls():
                path = url.toLocalFile()
                if path.lower().endswith((".html", ".htm")):
                    try:
                        with open(path, "r", encoding="utf-8") as f:
                            self.setPlainText(f.read())
                        event.acceptProposedAction()
                        return
                    except Exception as e:
                        self.setPlainText(f"Error reading file:\n{e}")
                        return
        if mime.hasText():
            self.setPlainText(mime.text())
            event.acceptProposedAction()


class RightPanel(QWidget):
    """The conversion panel on the right side of the splitter."""

    def __init__(self, parent=None):
        super().__init__(parent)
        self._build_ui()

    def _build_ui(self):
        layout = QVBoxLayout(self)
        layout.setContentsMargins(16, 16, 16, 16)
        layout.setSpacing(10)

        # ── Header ──────────────────────────────────────────────────────────
        header = QLabel("HTML → Word Converter")
        header.setFont(QFont("Calibri", 15, QFont.Weight.Bold))
        header.setStyleSheet(f"color: {UF_BLUE};")
        layout.addWidget(header)

        sub = QLabel(
            "Paste the HTML output from the model or drag and drop an .html file.\n"
            "Click Convert to download the .docx file."
        )
        sub.setWordWrap(True)
        sub.setStyleSheet("color: #444444; font-size: 11px;")
        layout.addWidget(sub)

        # ── Text area ───────────────────────────────────────────────────────
        self.text_edit = DropTextEdit()
        self.text_edit.setFont(QFont("Courier New", 10))
        self.text_edit.setStyleSheet(
            f"""
            QTextEdit {{
                border: 1.5px solid {BORDER};
                border-radius: 4px;
                background: #FFFFFF;
                padding: 6px;
            }}
            QTextEdit:focus {{
                border: 1.5px solid {UF_BLUE};
            }}
            """
        )
        layout.addWidget(self.text_edit, stretch=1)

        # ── Buttons row ──────────────────────────────────────────────────────
        btn_row = QHBoxLayout()
        btn_row.setSpacing(8)

        self.clear_btn = QPushButton("Clear")
        self.clear_btn.setCursor(Qt.CursorShape.PointingHandCursor)
        self.clear_btn.setStyleSheet(
            f"""
            QPushButton {{
                background: #FFFFFF;
                color: {UF_BLUE};
                border: 1.5px solid {UF_BLUE};
                border-radius: 4px;
                padding: 7px 18px;
                font-size: 12px;
                font-weight: bold;
            }}
            QPushButton:hover {{
                background: #E8EDFB;
            }}
            """
        )
        self.clear_btn.clicked.connect(self.text_edit.clear)

        self.convert_btn = QPushButton("Convert to Word")
        self.convert_btn.setCursor(Qt.CursorShape.PointingHandCursor)
        self.convert_btn.setStyleSheet(
            f"""
            QPushButton {{
                background: {UF_BLUE};
                color: #FFFFFF;
                border: none;
                border-radius: 4px;
                padding: 7px 22px;
                font-size: 12px;
                font-weight: bold;
            }}
            QPushButton:hover {{
                background: #001880;
            }}
            QPushButton:disabled {{
                background: #AAAAAA;
            }}
            """
        )
        self.convert_btn.clicked.connect(self._convert)

        btn_row.addWidget(self.clear_btn)
        btn_row.addStretch()
        btn_row.addWidget(self.convert_btn)
        layout.addLayout(btn_row)

        # ── Status label ─────────────────────────────────────────────────────
        self.status = QLabel("")
        self.status.setWordWrap(True)
        self.status.setStyleSheet("font-size: 11px;")
        layout.addWidget(self.status)

    def _set_status(self, message: str, ok: bool = True):
        color = "#2E7D32" if ok else "#C62828"
        self.status.setStyleSheet(f"font-size: 11px; color: {color};")
        self.status.setText(message)

    def _convert(self):
        html = self.text_edit.toPlainText().strip()
        if not html:
            self._set_status("Nothing to convert. Paste some HTML first.", ok=False)
            return

        # Derive a default filename from the <title> tag if present
        import re
        title_match = re.search(r"<title[^>]*>(.*?)</title>", html, re.IGNORECASE | re.DOTALL)
        default_name = "document"
        if title_match:
            default_name = re.sub(r"\s+", "_", title_match.group(1).strip()) or "document"

        save_path, _ = QFileDialog.getSaveFileName(
            self, "Save Word Document", f"{default_name}.docx",
            "Word Documents (*.docx)"
        )
        if not save_path:
            return  # user cancelled

        self.convert_btn.setEnabled(False)
        self._set_status("Converting…")
        QApplication.processEvents()

        try:
            docx_bytes = html_to_docx(html)
            with open(save_path, "wb") as f:
                f.write(docx_bytes)
            self._set_status(f"Saved: {os.path.basename(save_path)}", ok=True)
        except Exception as e:
            self._set_status(f"Conversion failed: {e}", ok=False)
        finally:
            self.convert_btn.setEnabled(True)


class MainWindow(QMainWindow):
    def __init__(self):
        super().__init__()
        self.setWindowTitle("UF Instruction Guide Converter")
        self.resize(1400, 860)
        self._build_ui()

    def _build_ui(self):
        # ── Central splitter ─────────────────────────────────────────────────
        splitter = QSplitter(Qt.Orientation.Horizontal)
        splitter.setHandleWidth(4)
        splitter.setStyleSheet(
            "QSplitter::handle { background: #CCCCCC; }"
        )

        # ── Left: embedded browser ───────────────────────────────────────────
        browser_container = QWidget()
        browser_layout    = QVBoxLayout(browser_container)
        browser_layout.setContentsMargins(0, 0, 0, 0)
        browser_layout.setSpacing(0)

        # Thin UF Blue top bar so it feels intentional
        bar = QFrame()
        bar.setFixedHeight(4)
        bar.setStyleSheet(f"background: {UF_BLUE};")
        browser_layout.addWidget(bar)

        self.browser = QWebEngineView()
        # Use a persistent profile so the user stays logged in across restarts
        profile = QWebEngineProfile("uf_navigator", self.browser)
        profile.setPersistentCookiesPolicy(
            QWebEngineProfile.PersistentCookiesPolicy.AllowPersistentCookies
        )
        page = QWebEnginePage(profile, self.browser)
        self.browser.setPage(page)
        self.browser.load(QUrl(MODEL_URL))
        browser_layout.addWidget(self.browser, stretch=1)

        # ── Right: conversion panel ──────────────────────────────────────────
        right_container = QWidget()
        right_container.setStyleSheet(f"background: {LIGHT_BG};")
        right_layout = QVBoxLayout(right_container)
        right_layout.setContentsMargins(0, 0, 0, 0)

        top_bar = QFrame()
        top_bar.setFixedHeight(4)
        top_bar.setStyleSheet(f"background: {UF_ORANGE};")
        right_layout.addWidget(top_bar)

        self.right_panel = RightPanel()
        right_layout.addWidget(self.right_panel, stretch=1)

        # ── Assemble splitter ────────────────────────────────────────────────
        splitter.addWidget(browser_container)
        splitter.addWidget(right_container)
        # Give the browser about 60% of the width by default
        splitter.setSizes([840, 560])

        self.setCentralWidget(splitter)


def main():
    # Required on some platforms for WebEngine
    os.environ.setdefault("QTWEBENGINE_CHROMIUM_FLAGS", "--disable-gpu")

    app = QApplication(sys.argv)
    app.setApplicationName("UF Instruction Guide Converter")
    app.setStyle("Fusion")

    # Global font
    font = QFont("Calibri", 11)
    app.setFont(font)

    window = MainWindow()
    window.show()
    sys.exit(app.exec())


if __name__ == "__main__":
    main()
```

Would you like me to explain or break down the code?

---

**`build.bat`**

```bat
@echo off
echo Installing dependencies...
pip install -r requirements.txt

echo.
echo Building executable...
pyinstaller ^
  --onefile ^
  --windowed ^
  --name "UF_Guide_Converter" ^
  --add-data "converter.py;." ^
  main.py

echo.
echo Done. Find your .exe in the dist\ folder.
pause
```

---

A few things worth knowing about the build:

- **Persistent login** — the browser uses a named `QWebEngineProfile` so the user's session cookies survive app restarts. They won't have to log in every time.
- **PyInstaller + QtWebEngine** can produce a large `.exe` (typically 80–120 MB). That's normal — Chromium is bundled inside.
- On some machines you may need to add `--collect-all PyQt6` to the PyInstaller command if Qt plugins aren't found at runtime.
- The system prompt itself doesn't need to change at all — the `savedocx.js` script and button can stay in the HTML output, they just won't be used when the local app handles conversion instead. But if you'd like a trimmed version of the prompt that removes the JS save references, just say the word.

---

## 🧑 User

what about the template.docx that the new docx is supposed to be generated from?

---

## 🤖 Assistant

Great catch. Using a `template.docx` is actually the right approach here rather than manually registering styles — it guarantees the styles, fonts, and any Word-specific formatting are pixel-perfect matches to what the JS converter produces, since they'd both be sourcing from the same template.

A couple of questions before I revise the code:

1. **Do you already have a `template.docx`** that contains all the named styles (MsoNormal, BulletedList, Note, NormalImage, Clicks, etc.)? If so you can drop it in the project folder and I'll reference it directly.
2. If not, the cleanest way to create one is to **take any document the JS converter has already produced** and strip out its content, leaving just the styles. Do you have an existing converted `.docx` output I can base the template on, or should I write a one-time script that builds `template.docx` programmatically from scratch using the exact style definitions already documented in `savedocx.js`?

The second option means the template is fully self-contained in the project and anyone can regenerate it by running a script — no manual Word editing required. That's probably the most maintainable path. Want me to go that route?

---

## 🧑 User

I do have a template already

---

## 🤖 Assistant

Perfect — that's the cleanest solution then. Here's what I need to know:

1. **What is the filename?** I'll hardcode the reference so the app knows exactly where to look for it.
2. **Where should it live relative to the app?** I'd suggest putting it in the same folder as `main.py` and `converter.py`, so the structure becomes:

   ```
   docx_converter/
   ├── main.py
   ├── converter.py
   ├── template.docx
   ├── requirements.txt
   └── build.bat
   ```

   But if you have a different preference I can accommodate that.
3. **Does the template have all the named styles already in it** — MsoNormal, BulletedList, Note, NormalImage, Clicks, MsoIntenseEmphasis, etc.? If yes, `converter.py` can be significantly simplified since `_ensure_styles()` becomes unnecessary — we just open the template and let `python-docx` inherit everything from it.

Once I know the filename I'll rewrite `converter.py` to open the document with `Document("template.docx")` instead of `Document()`, remove the style registration logic, and update `build.bat` to bundle the template into the `.exe` via PyInstaller's `--add-data` flag so it's self-contained.

---

## 🧑 User

it is amed template.docx it has all the style names already in it. I also want to make sure that the h1 of the new document is also registered as the documents metadata title.

---

## 🤖 Assistant

Perfect. Here's the revised `converter.py`. The changes are:

- Opens from `template.docx` instead of a blank document
- Removes `_ensure_styles()` entirely
- Extracts the first `h1` text and sets it as the document's core properties title
- Handles the PyInstaller bundled path for `template.docx` so it works both in dev and as a `.exe`

---

**`converter.py`**

```python
import os
import sys
import re
from io import BytesIO

from bs4 import BeautifulSoup, NavigableString, Tag
from docx import Document
from docx.shared import Pt, Inches, RGBColor
from docx.enum.text import WD_ALIGN_PARAGRAPH
from docx.oxml.ns import qn
from docx.oxml import OxmlElement

UF_BLUE     = RGBColor(0x00, 0x21, 0xA5)
CLICKS_BLUE = RGBColor(0x17, 0x5C, 0x92)
BLACK       = RGBColor(0x00, 0x00, 0x00)


def _get_template_path() -> str:
    """
    Resolve the path to template.docx whether we are running from source
    or from a PyInstaller-bundled .exe (where _MEIPASS is the temp folder).
    """
    if getattr(sys, "frozen", False):
        base = sys._MEIPASS
    else:
        base = os.path.dirname(os.path.abspath(__file__))
    return os.path.join(base, "template.docx")


def _apply_note_border(paragraph):
    """Add a UF Blue left border to a Note paragraph via direct XML."""
    p    = paragraph._p
    pPr  = p.get_or_add_pPr()
    pBdr = OxmlElement("w:pBdr")
    left = OxmlElement("w:left")
    left.set(qn("w:val"),   "single")
    left.set(qn("w:sz"),    "12")
    left.set(qn("w:space"), "4")
    left.set(qn("w:color"), "0021A5")
    pBdr.append(left)
    pPr.append(pBdr)


def _heading_config(level: int) -> dict:
    configs = [
        {"size": 16, "bold": True,  "italic": False, "color": BLACK,
         "before": 18, "after": 4},
        {"size": 14, "bold": True,  "italic": False, "color": UF_BLUE,
         "before": 8,  "after": 4},
        {"size": 14, "bold": False, "italic": False, "color": UF_BLUE,
         "before": 8,  "after": 4},
        {"size": 14, "bold": False, "italic": True,  "color": UF_BLUE,
         "before": 4,  "after": 2},
        {"size": 14, "bold": False, "italic": False, "color": UF_BLUE,
         "before": 4,  "after": 2},
        {"size": 12, "bold": False, "italic": True,  "color": BLACK,
         "before": 2,  "after": 0},
    ]
    return configs[min(level - 1, 5)]


def _collect_inline_runs(node) -> list:
    """
    Recursively walk an element's children and return a list of run dicts:
    {text, bold, italic, color, char_style}
    """
    runs = []
    for child in node.children:
        if isinstance(child, NavigableString):
            text = str(child)
            if text:
                runs.append({
                    "text": text, "bold": False, "italic": False,
                    "color": BLACK, "char_style": None
                })
            continue
        if not isinstance(child, Tag):
            continue

        tag = child.name.lower() if child.name else ""
        cls = " ".join(child.get("class", [])).strip()

        if tag == "strong":
            for r in _collect_inline_runs(child):
                r["bold"] = True
                runs.append(r)
        elif tag == "em":
            for r in _collect_inline_runs(child):
                r["italic"] = True
                runs.append(r)
        elif tag == "span" and cls == "Clicks":
            runs.append({
                "text": child.get_text(), "bold": True,
                "italic": False, "color": CLICKS_BLUE,
                "char_style": "Clicks"
            })
        elif tag == "span" and cls == "MsoIntenseEmphasis":
            runs.append({
                "text": child.get_text(), "bold": True,
                "italic": True, "color": BLACK,
                "char_style": "MsoIntenseEmphasis"
            })
        elif tag == "span" and cls in (
            "MsoSubtleReference", "MsoIntenseReference", "MsoBookTitle"
        ):
            runs.append({
                "text": child.get_text(), "bold": True,
                "italic": cls == "MsoBookTitle",
                "color": BLACK, "char_style": cls
            })
        else:
            runs.extend(_collect_inline_runs(child))
    return runs


def _add_runs_to_paragraph(paragraph, run_dicts,
                            force_bold=False, force_italic=False,
                            force_color=None, font_size=None):
    """Write a list of run dicts onto an existing paragraph."""
    style_names = {s.name for s in paragraph.part.document.styles}
    for rd in run_dicts:
        run            = paragraph.add_run(rd["text"])
        run.bold       = force_bold   or rd["bold"]
        run.italic     = force_italic or rd["italic"]
        run.font.color.rgb = force_color or rd["color"]
        run.font.name  = "Calibri"
        if font_size:
            run.font.size = Pt(font_size)
        if rd["char_style"] and rd["char_style"] in style_names:
            run.style = paragraph.part.document.styles[rd["char_style"]]


def _process_node(doc: Document, node, h1_seen: list):
    """
    Convert a single top-level HTML node into one or more docx paragraphs.
    h1_seen is a one-element list used as a mutable flag so we can capture
    the first h1 text without a global variable.
    """
    if isinstance(node, NavigableString):
        return
    if not isinstance(node, Tag):
        return

    tag      = node.name.lower() if node.name else ""
    cls_list = node.get("class", [])
    cls      = cls_list[0] if cls_list else ""

    # ── Headings ─────────────────────────────────────────────────────────────
    heading_match = re.match(r"^h([1-6])$", tag)
    if heading_match:
        level = int(heading_match.group(1))
        cfg   = _heading_config(level)

        # Map h1–h6 to Word's built-in Heading style names
        style_name = f"Heading {level}"
        para = doc.add_paragraph(style=style_name)

        fmt = para.paragraph_format
        fmt.space_before = Pt(cfg["before"])
        fmt.space_after  = Pt(cfg["after"])

        run_dicts = _collect_inline_runs(node)
        _add_runs_to_paragraph(
            para, run_dicts,
            force_bold=cfg["bold"],
            force_italic=cfg["italic"],
            force_color=cfg["color"],
            font_size=cfg["size"]
        )

        # Capture the first h1 as the document metadata title
        if level == 1 and not h1_seen[0]:
            h1_seen[0] = node.get_text(strip=True)

        return

    # ── Paragraphs ───────────────────────────────────────────────────────────
    if tag == "p":

        if cls == "BulletedList":
            para = doc.add_paragraph(style="BulletedList")
            _add_runs_to_paragraph(para, _collect_inline_runs(node))
            return

        if cls == "Note":
            para = doc.add_paragraph(style="Note")
            _add_runs_to_paragraph(para, _collect_inline_runs(node))
            _apply_note_border(para)
            return

        if cls == "NormalImage":
            para = doc.add_paragraph(style="NormalImage")
            _add_runs_to_paragraph(
                para, _collect_inline_runs(node),
                force_italic=True,
                force_color=RGBColor(0x66, 0x66, 0x66)
            )
            return

        if cls in ("MsoQuote", "MsoIntenseQuote"):
            para = doc.add_paragraph(style=cls)
            _add_runs_to_paragraph(
                para, _collect_inline_runs(node),
                force_italic=True
            )
            if cls == "MsoIntenseQuote":
                para.paragraph_format.left_indent  = Inches(0.6)
                para.paragraph_format.right_indent = Inches(0.6)
            return

        # Default / MsoNormal
        para = doc.add_paragraph(style="MsoNormal")
        _add_runs_to_paragraph(para, _collect_inline_runs(node))
        return

    # ── Container elements — recurse into children ───────────────────────────
    if tag in ("div", "section", "article", "main", "header", "footer"):
        for child in node.children:
            _process_node(doc, child, h1_seen)
        return


def html_to_docx(html_string: str) -> bytes:
    """
    Parse the HTML string, walk the WordSection1 container, write each
    element into a copy of template.docx, set the h1 as the document
    metadata title, and return the result as bytes.
    """
    soup = BeautifulSoup(html_string, "lxml")

    # Prefer WordSection1; fall back to body
    container = (
        soup.find(class_="WordSection1")
        or soup.find("body")
        or soup
    )

    # Open a fresh copy of the template for every conversion
    template_path = _get_template_path()
    doc = Document(template_path)

    # Remove any placeholder paragraphs the template may contain
    # so we start with a clean body
    for p in list(doc.paragraphs):
        p._element.getparent().remove(p._element)

    # Also clear any placeholder tables if present
    for t in list(doc.tables):
        t._element.getparent().remove(t._element)

    # Mutable flag to capture first h1 text
    h1_seen = [None]

    for child in container.children:
        if isinstance(child, NavigableString):
            continue
        if not isinstance(child, Tag):
            continue
        # Skip the Save as Word button paragraph
        if child.find("button"):
            continue
        _process_node(doc, child, h1_seen)

    # ── Set document metadata title from the first h1 ────────────────────────
    if h1_seen[0]:
        doc.core_properties.title = h1_seen[0]

    buf = BytesIO()
    doc.save(buf)
    return buf.getvalue()
```

Would you like me to explain or break down the code?

---

And the updated `build.bat` to make sure `template.docx` gets bundled into the `.exe`:

**`build.bat`**

```bat
@echo off
echo Installing dependencies...
pip install -r requirements.txt

echo.
echo Building executable...
pyinstaller ^
  --onefile ^
  --windowed ^
  --name "UF_Guide_Converter" ^
  --add-data "template.docx;." ^
  main.py

echo.
echo Done. Find your .exe in the dist\ folder.
pause
```

The only meaningful changes from before are in `converter.py`:

- `_get_template_path()` resolves `template.docx` correctly both in dev and inside the bundled `.exe`
- `Document(template_path)` inherits all styles directly from your template instead of registering them manually
- The placeholder content is cleared from the template before writing, so each conversion starts clean
- `h1_seen` captures the first `h1` text and writes it to `doc.core_properties.title` before saving

`main.py` and `requirements.txt` are unchanged from before.

---

## 🧑 User

Ok now how do I build the app?

---

## 🤖 Assistant

Here's the step-by-step process:

---

### 1. Install Python

If you don't have Python installed, download it from **python.org**. Get the latest 3.11 or 3.12 release. During installation, **check the box that says "Add Python to PATH"** — this is easy to miss and will cause problems if skipped.

---

### 2. Set up the project folder

Create a folder somewhere on your machine, for example `C:\UF_Guide_Converter\`, and place these files inside it:

```
UF_Guide_Converter/
├── main.py
├── converter.py
├── template.docx
├── requirements.txt
└── build.bat
```

---

### 3. Install dependencies

Open a terminal in that folder. The easiest way is to type `cmd` directly into the Windows Explorer address bar while you're in the folder and hit Enter. Then run:

```
pip install -r requirements.txt
```

This will take a few minutes. PyQt6 and its WebEngine component are large downloads.

---

### 4. Test it before building

Before packaging, confirm it runs from source:

```
python main.py
```

The app should open with the browser on the left loading the UF model URL and the converter panel on the right. Fix any issues at this stage — it's much easier than debugging a compiled `.exe`.

---

### 5. Build the `.exe`

Once you're happy with how it runs, double-click `build.bat` or run it from the terminal:

```
build.bat
```

PyInstaller will work for a minute or two. When it finishes you'll find your `.exe` at:

```
UF_Guide_Converter/dist/UF_Guide_Converter.exe
```

---

### 6. Test the `.exe`

Double-click the `.exe` from the `dist` folder to confirm it works independently. If it opens correctly, that file is self-contained and can be copied to any Windows machine.

---

### A few things to watch for

- **PyQt6 WebEngine on first run** sometimes triggers a Windows Defender warning since it's an unsigned executable. You can click "More info → Run anyway" to proceed.
- **If the `.exe` crashes on launch**, run it from a terminal (`dist\UF_Guide_Converter.exe`) instead of double-clicking so you can see the error message.
- **If styles aren't resolving correctly** from `template.docx`, the most common cause is a style name mismatch. You can check the exact style names in your template by running this one-liner in the terminal from your project folder:

```
python -c "from docx import Document; [print(s.name) for s in Document('template.docx').styles]"
```

Compare the output against the style names used in `converter.py` and adjust if anything differs.

---

## 🧑 User

can we make the ui of the app look any nicer? more premium quality?

---

## 🤖 Assistant

Absolutely. Here's a fully redesigned `main.py` with a much more polished UI — cleaner typography, better spacing, a proper toolbar, subtle shadows, and a more considered use of the UF brand colours without being heavy-handed.

---

**`main.py`**

```python
import sys
import os
import re
from PyQt6.QtWidgets import (
    QApplication, QMainWindow, QWidget, QHBoxLayout,
    QVBoxLayout, QTextEdit, QPushButton, QLabel,
    QFileDialog, QSplitter, QFrame, QSizePolicy,
    QGraphicsDropShadowEffect
)
from PyQt6.QtWebEngineWidgets import QWebEngineView
from PyQt6.QtWebEngineCore import QWebEngineProfile, QWebEnginePage
from PyQt6.QtCore import QUrl, Qt, QMimeData, QSize, QPropertyAnimation, QEasingCurve
from PyQt6.QtGui import (
    QDragEnterEvent, QDropEvent, QFont, QColor,
    QPalette, QIcon, QPainter, QPixmap
)
from converter import html_to_docx

MODEL_URL = "https://chat.ai.it.ufl.edu/?model=tod-document-generator"

# ── Palette ───────────────────────────────────────────────────────────────────
UF_BLUE        = "#0021A5"
UF_BLUE_DARK   = "#001880"
UF_BLUE_LIGHT  = "#E8EDFB"
UF_ORANGE      = "#FA4616"
UF_ORANGE_DARK = "#D93A0F"
WHITE          = "#FFFFFF"
SURFACE        = "#F7F8FC"
SURFACE_ALT    = "#EDEEF5"
BORDER         = "#D0D3E8"
TEXT_PRIMARY   = "#1A1A2E"
TEXT_SECONDARY = "#555770"
TEXT_MUTED     = "#9194A8"
SUCCESS        = "#1B6B3A"
SUCCESS_BG     = "#E6F4EC"
ERROR          = "#9B1C1C"
ERROR_BG       = "#FEECEC"


# ── Reusable style snippets ───────────────────────────────────────────────────
def _btn_primary():
    return f"""
        QPushButton {{
            background: qlineargradient(x1:0, y1:0, x2:0, y2:1,
                stop:0 {UF_BLUE}, stop:1 {UF_BLUE_DARK});
            color: {WHITE};
            border: none;
            border-radius: 6px;
            padding: 9px 24px;
            font-size: 13px;
            font-weight: 600;
            font-family: 'Calibri';
            letter-spacing: 0.3px;
        }}
        QPushButton:hover {{
            background: qlineargradient(x1:0, y1:0, x2:0, y2:1,
                stop:0 #1A34B8, stop:1 {UF_BLUE});
        }}
        QPushButton:pressed {{
            background: {UF_BLUE_DARK};
            padding-top: 10px;
            padding-bottom: 8px;
        }}
        QPushButton:disabled {{
            background: #B0B4C8;
            color: #E0E2ED;
        }}
    """


def _btn_secondary():
    return f"""
        QPushButton {{
            background: {WHITE};
            color: {UF_BLUE};
            border: 1.5px solid {BORDER};
            border-radius: 6px;
            padding: 9px 20px;
            font-size: 13px;
            font-weight: 600;
            font-family: 'Calibri';
            letter-spacing: 0.3px;
        }}
        QPushButton:hover {{
            background: {UF_BLUE_LIGHT};
            border-color: {UF_BLUE};
        }}
        QPushButton:pressed {{
            background: {SURFACE_ALT};
        }}
    """


# ── Drop-enabled text editor ──────────────────────────────────────────────────
class DropTextEdit(QTextEdit):
    def __init__(self, parent=None):
        super().__init__(parent)
        self.setAcceptDrops(True)
        self.setPlaceholderText(
            "Paste HTML output from the model here,\n"
            "or drag and drop an .html file onto this area…"
        )

    def dragEnterEvent(self, event: QDragEnterEvent):
        if event.mimeData().hasUrls() or event.mimeData().hasText():
            event.acceptProposedAction()
        else:
            event.ignore()

    def dragMoveEvent(self, event):
        event.acceptProposedAction()

    def dropEvent(self, event: QDropEvent):
        mime: QMimeData = event.mimeData()
        if mime.hasUrls():
            for url in mime.urls():
                path = url.toLocalFile()
                if path.lower().endswith((".html", ".htm")):
                    try:
                        with open(path, "r", encoding="utf-8") as f:
                            self.setPlainText(f.read())
                        event.acceptProposedAction()
                        return
                    except Exception as e:
                        self.setPlainText(f"Error reading file:\n{e}")
                        return
        if mime.hasText():
            self.setPlainText(mime.text())
            event.acceptProposedAction()


# ── Divider line ──────────────────────────────────────────────────────────────
class HDivider(QFrame):
    def __init__(self, parent=None):
        super().__init__(parent)
        self.setFrameShape(QFrame.Shape.HLine)
        self.setFixedHeight(1)
        self.setStyleSheet(f"background: {BORDER}; border: none;")


# ── Status badge ──────────────────────────────────────────────────────────────
class StatusBadge(QLabel):
    def __init__(self, parent=None):
        super().__init__(parent)
        self.setWordWrap(True)
        self.hide()
        self.setStyleSheet("border-radius: 6px; padding: 8px 12px; font-size: 12px;")

    def set_success(self, message: str):
        self.setStyleSheet(
            f"border-radius: 6px; padding: 8px 12px; font-size: 12px;"
            f"background: {SUCCESS_BG}; color: {SUCCESS}; font-weight: 600;"
        )
        self.setText(f"✓  {message}")
        self.show()

    def set_error(self, message: str):
        self.setStyleSheet(
            f"border-radius: 6px; padding: 8px 12px; font-size: 12px;"
            f"background: {ERROR_BG}; color: {ERROR}; font-weight: 600;"
        )
        self.setText(f"✕  {message}")
        self.show()

    def set_info(self, message: str):
        self.setStyleSheet(
            f"border-radius: 6px; padding: 8px 12px; font-size: 12px;"
            f"background: {UF_BLUE_LIGHT}; color: {UF_BLUE}; font-weight: 600;"
        )
        self.setText(f"⟳  {message}")
        self.show()


# ── Browser panel (left) ──────────────────────────────────────────────────────
class BrowserPanel(QWidget):
    def __init__(self, parent=None):
        super().__init__(parent)
        self._build()

    def _build(self):
        layout = QVBoxLayout(self)
        layout.setContentsMargins(0, 0, 0, 0)
        layout.setSpacing(0)

        # ── Top chrome bar ───────────────────────────────────────────────────
        chrome = QWidget()
        chrome.setFixedHeight(48)
        chrome.setStyleSheet(
            f"background: {UF_BLUE};"
        )
        chrome_layout = QHBoxLayout(chrome)
        chrome_layout.setContentsMargins(16, 0, 16, 0)
        chrome_layout.setSpacing(10)

        # UF wordmark / label
        brand = QLabel("NaviGator AI  ·  Instruction Guide Generator")
        brand.setStyleSheet(
            f"color: {WHITE}; font-size: 13px; font-weight: 700;"
            f"font-family: 'Calibri'; letter-spacing: 0.4px;"
        )
        chrome_layout.addWidget(brand)
        chrome_layout.addStretch()

        # Reload button
        self.reload_btn = QPushButton("↺  Reload")
        self.reload_btn.setCursor(Qt.CursorShape.PointingHandCursor)
        self.reload_btn.setFixedHeight(30)
        self.reload_btn.setStyleSheet(
            f"""
            QPushButton {{
                background: rgba(255,255,255,0.15);
                color: {WHITE};
                border: 1px solid rgba(255,255,255,0.35);
                border-radius: 5px;
                padding: 0 14px;
                font-size: 12px;
                font-family: 'Calibri';
                font-weight: 600;
            }}
            QPushButton:hover {{
                background: rgba(255,255,255,0.25);
            }}
            QPushButton:pressed {{
                background: rgba(255,255,255,0.10);
            }}
            """
        )

        layout.addWidget(chrome)

        # ── Orange accent line ───────────────────────────────────────────────
        accent = QFrame()
        accent.setFixedHeight(3)
        accent.setStyleSheet(
            f"background: qlineargradient(x1:0, y1:0, x2:1, y2:0,"
            f"stop:0 {UF_ORANGE}, stop:1 {UF_ORANGE_DARK});"
        )
        layout.addWidget(accent)

        # ── Web view ─────────────────────────────────────────────────────────
        self.browser = QWebEngineView()
        profile = QWebEngineProfile("uf_navigator", self.browser)
        profile.setPersistentCookiesPolicy(
            QWebEngineProfile.PersistentCookiesPolicy.AllowPersistentCookies
        )
        page = QWebEnginePage(profile, self.browser)
        self.browser.setPage(page)
        self.browser.load(QUrl(MODEL_URL))

        # Wire reload button now that browser exists
        self.reload_btn.clicked.connect(self.browser.reload)
        chrome_layout.addWidget(self.reload_btn)

        layout.addWidget(self.browser, stretch=1)


# ── Converter panel (right) ───────────────────────────────────────────────────
class ConverterPanel(QWidget):
    def __init__(self, parent=None):
        super().__init__(parent)
        self.setStyleSheet(f"background: {SURFACE};")
        self._build()

    def _build(self):
        outer = QVBoxLayout(self)
        outer.setContentsMargins(0, 0, 0, 0)
        outer.setSpacing(0)

        # ── Top chrome bar (mirrors browser panel) ───────────────────────────
        chrome = QWidget()
        chrome.setFixedHeight(48)
        chrome.setStyleSheet(f"background: {TEXT_PRIMARY};")
        chrome_layout = QHBoxLayout(chrome)
        chrome_layout.setContentsMargins(20, 0, 20, 0)

        title_lbl = QLabel("HTML → Word Converter")
        title_lbl.setStyleSheet(
            f"color: {WHITE}; font-size: 13px; font-weight: 700;"
            f"font-family: 'Calibri'; letter-spacing: 0.4px;"
        )
        chrome_layout.addWidget(title_lbl)
        chrome_layout.addStretch()

        outer.addWidget(chrome)

        # ── Orange accent line ───────────────────────────────────────────────
        accent = QFrame()
        accent.setFixedHeight(3)
        accent.setStyleSheet(
            f"background: qlineargradient(x1:0, y1:0, x2:1, y2:0,"
            f"stop:0 {UF_ORANGE_DARK}, stop:1 {UF_ORANGE});"
        )
        outer.addWidget(accent)

        # ── Scrollable content area ──────────────────────────────────────────
        content = QWidget()
        content.setStyleSheet(f"background: {SURFACE};")
        layout = QVBoxLayout(content)
        layout.setContentsMargins(24, 24, 24, 20)
        layout.setSpacing(16)

        # Instruction text
        instructions = QLabel(
            "Paste the HTML output from the model below, or drag and drop "
            "an <span style='font-weight:600;'>.html</span> file directly "
            "onto the text area. Then click <span style='font-weight:600;'>"
            "Convert to Word</span> to save your document."
        )
        instructions.setWordWrap(True)
        instructions.setTextFormat(Qt.TextFormat.RichText)
        instructions.setStyleSheet(
            f"color: {TEXT_SECONDARY}; font-size: 12px; line-height: 1.5;"
        )
        layout.addWidget(instructions)

        layout.addWidget(HDivider())

        # ── Editor card ──────────────────────────────────────────────────────
        editor_card = QFrame()
        editor_card.setStyleSheet(
            f"""
            QFrame {{
                background: {WHITE};
                border: 1.5px solid {BORDER};
                border-radius: 8px;
            }}
            """
        )
        shadow = QGraphicsDropShadowEffect()
        shadow.setBlurRadius(18)
        shadow.setXOffset(0)
        shadow.setYOffset(2)
        shadow.setColor(QColor(0, 0, 0, 20))
        editor_card.setGraphicsEffect(shadow)

        card_layout = QVBoxLayout(editor_card)
        card_layout.setContentsMargins(0, 0, 0, 0)
        card_layout.setSpacing(0)

        # Card header
        card_header = QWidget()
        card_header.setFixedHeight(36)
        card_header.setStyleSheet(
            f"""
            background: {SURFACE_ALT};
            border-top-left-radius: 8px;
            border-top-right-radius: 8px;
            border-bottom: 1px solid {BORDER};
            """
        )
        card_header_layout = QHBoxLayout(card_header)
        card_header_layout.setContentsMargins(12, 0, 12, 0)

        # Three macOS-style traffic light dots — purely decorative
        for color in ("#FF5F57", "#FEBC2E", "#28C840"):
            dot = QLabel()
            dot.setFixedSize(11, 11)
            dot.setStyleSheet(
                f"background: {color}; border-radius: 5px; border: none;"
            )
            card_header_layout.addWidget(dot)

        card_header_layout.addSpacing(8)
        file_label = QLabel("HTML Source")
        file_label.setStyleSheet(
            f"color: {TEXT_MUTED}; font-size: 11px; font-family: 'Courier New';"
        )
        card_header_layout.addWidget(file_label)
        card_header_layout.addStretch()
        card_layout.addWidget(card_header)

        # The actual text editor
        self.text_edit = DropTextEdit()
        self.text_edit.setFont(QFont("Courier New", 10))
        self.text_edit.setStyleSheet(
            f"""
            QTextEdit {{
                background: {WHITE};
                border: none;
                border-bottom-left-radius: 8px;
                border-bottom-right-radius: 8px;
                padding: 12px;
                color: {TEXT_PRIMARY};
                selection-background-color: {UF_BLUE_LIGHT};
                selection-color: {UF_BLUE};
            }}
            QScrollBar:vertical {{
                border: none;
                background: {SURFACE};
                width: 8px;
                border-radius: 4px;
            }}
            QScrollBar::handle:vertical {{
                background: {BORDER};
                border-radius: 4px;
                min-height: 30px;
            }}
            QScrollBar::handle:vertical:hover {{
                background: {TEXT_MUTED};
            }}
            QScrollBar::add-line:vertical,
            QScrollBar::sub-line:vertical {{
                height: 0;
            }}
            """
        )
        card_layout.addWidget(self.text_edit)
        layout.addWidget(editor_card, stretch=1)

        # ── Action row ───────────────────────────────────────────────────────
        action_row = QHBoxLayout()
        action_row.setSpacing(10)

        self.clear_btn = QPushButton("Clear")
        self.clear_btn.setCursor(Qt.CursorShape.PointingHandCursor)
        self.clear_btn.setFixedHeight(38)
        self.clear_btn.setStyleSheet(_btn_secondary())
        self.clear_btn.clicked.connect(self._clear)

        self.convert_btn = QPushButton("  Convert to Word  ")
        self.convert_btn.setCursor(Qt.CursorShape.PointingHandCursor)
        self.convert_btn.setFixedHeight(38)
        self.convert_btn.setStyleSheet(_btn_primary())
        self.convert_btn.clicked.connect(self._convert)

        action_row.addWidget(self.clear_btn)
        action_row.addStretch()
        action_row.addWidget(self.convert_btn)
        layout.addLayout(action_row)

        # ── Status badge ─────────────────────────────────────────────────────
        self.status = StatusBadge()
        layout.addWidget(self.status)

        outer.addWidget(content, stretch=1)

        # ── Footer ───────────────────────────────────────────────────────────
        footer = QWidget()
        footer.setFixedHeight(32)
        footer.setStyleSheet(f"background: {SURFACE_ALT}; border-top: 1px solid {BORDER};")
        footer_layout = QHBoxLayout(footer)
        footer_layout.setContentsMargins(20, 0, 20, 0)

        footer_lbl = QLabel("University of Florida  ·  HR Training & Organizational Development")
        footer_lbl.setStyleSheet(
            f"color: {TEXT_MUTED}; font-size: 10px; font-family: 'Calibri';"
        )
        footer_layout.addWidget(footer_lbl)
        footer_layout.addStretch()

        version_lbl = QLabel("v1.0")
        version_lbl.setStyleSheet(
            f"color: {TEXT_MUTED}; font-size: 10px; font-family: 'Calibri';"
        )
        footer_layout.addWidget(version_lbl)
        outer.addWidget(footer)

    def _clear(self):
        self.text_edit.clear()
        self.status.hide()

    def _convert(self):
        html = self.text_edit.toPlainText().strip()
        if not html:
            self.status.set_error("Nothing to convert. Paste some HTML first.")
            return

        title_match = re.search(
            r"<title[^>]*>(.*?)</title>", html,
            re.IGNORECASE | re.DOTALL
        )
        default_name = "document"
        if title_match:
            default_name = (
                re.sub(r"\s+", "_", title_match.group(1).strip()) or "document"
            )

        save_path, _ = QFileDialog.getSaveFileName(
            self, "Save Word Document", f"{default_name}.docx",
            "Word Documents (*.docx)"
        )
        if not save_path:
            return

        self.convert_btn.setEnabled(False)
        self.status.set_info("Converting…")
        QApplication.processEvents()

        try:
            docx_bytes = html_to_docx(html)
            with open(save_path, "wb") as f:
                f.write(docx_bytes)
            self.status.set_success(
                f"Saved: {os.path.basename(save_path)}"
            )
        except Exception as e:
            self.status.set_error(f"Conversion failed: {e}")
        finally:
            self.convert_btn.setEnabled(True)


# ── Main window ───────────────────────────────────────────────────────────────
class MainWindow(QMainWindow):
    def __init__(self):
        super().__init__()
        self.setWindowTitle("UF Instruction Guide Converter")
        self.resize(1440, 900)
        self.setMinimumSize(900, 600)
        self._build()

    def _build(self):
        central = QWidget()
        central.setStyleSheet(f"background: {SURFACE};")
        root = QVBoxLayout(central)
        root.setContentsMargins(0, 0, 0, 0)
        root.setSpacing(0)

        # ── Splitter ─────────────────────────────────────────────────────────
        splitter = QSplitter(Qt.Orientation.Horizontal)
        splitter.setHandleWidth(5)
        splitter.setStyleSheet(
            f"""
            QSplitter::handle {{
                background: {BORDER};
            }}
            QSplitter::handle:hover {{
                background: {UF_BLUE};
            }}
            """
        )

        self.browser_panel    = BrowserPanel()
        self.converter_panel  = ConverterPanel()

        splitter.addWidget(self.browser_panel)
        splitter.addWidget(self.converter_panel)

        # 62 / 38 split by default
        splitter.setSizes([893, 547])
        splitter.setCollapsible(0, False)
        splitter.setCollapsible(1, False)

        root.addWidget(splitter)
        self.setCentralWidget(central)


# ── Entry point ───────────────────────────────────────────────────────────────
def main():
    os.environ.setdefault("QTWEBENGINE_CHROMIUM_FLAGS", "--disable-gpu")

    app = QApplication(sys.argv)
    app.setApplicationName("UF Instruction Guide Converter")
    app.setStyle("Fusion")

    # Set a clean Fusion palette so the OS theme doesn't bleed through
    palette = QPalette()
    palette.setColor(QPalette.ColorRole.Window,          QColor(SURFACE))
    palette.setColor(QPalette.ColorRole.WindowText,      QColor(TEXT_PRIMARY))
    palette.setColor(QPalette.ColorRole.Base,            QColor(WHITE))
    palette.setColor(QPalette.ColorRole.AlternateBase,   QColor(SURFACE_ALT))
    palette.setColor(QPalette.ColorRole.Text,            QColor(TEXT_PRIMARY))
    palette.setColor(QPalette.ColorRole.Button,          QColor(SURFACE))
    palette.setColor(QPalette.ColorRole.ButtonText,      QColor(TEXT_PRIMARY))
    palette.setColor(QPalette.ColorRole.Highlight,       QColor(UF_BLUE))
    palette.setColor(QPalette.ColorRole.HighlightedText, QColor(WHITE))
    app.setPalette(palette)

    font = QFont("Calibri", 11)
    app.setFont(font)

    window = MainWindow()
    window.show()
    sys.exit(app.exec())


if __name__ == "__main__":
    main()
```

Would you like me to explain or break down the code?

---

The key visual upgrades from the previous version:

- **Matched chrome bars** on both panels — UF Blue on the left, deep navy on the right — each with a gradient orange accent line underneath so the two sides feel like a unified app rather than two widgets side by side
- **Card-style editor** with a subtle drop shadow, rounded corners, and a macOS-inspired header strip with the traffic light dots to give it a premium editor feel
- **Gradient buttons** with pressed-state feedback and smooth hover transitions
- **Status badge** replaces the plain label — colour-coded green for success, red for error, blue for in-progress, with icon prefixes
- **Custom scrollbar** in the editor — thin, rounded, unobtrusive
- **Fusion palette** applied globally so the OS theme doesn't bleed through and make things look inconsistent on different Windows versions
- **Footer strip** with a UF attribution and version number
- **Splitter handle** turns UF Blue on hover so it's obvious but not distracting

`converter.py`, `requirements.txt`, and `build.bat` are all unchanged.

---

## 🧑 User

it is saying the conversion failed, no style msoNormal.

---

## 🤖 Assistant

That's a style name mismatch — `python-docx` is looking for `"MsoNormal"` but the style is stored in the template under a slightly different name. Let's check what it's actually called first.

Run this in your project folder:

```
python -c "from docx import Document; [print(repr(s.name)) for s in Document('template.docx').styles]"
```

That will print every style name exactly as it's stored. Look for anything that resembles `MsoNormal`, `Normal`, `Body Text` etc. and share the output here and I'll update `converter.py` with the exact names.

My guess is the template stores it as just `"Normal"` rather than `"MsoNormal"` — Word often normalizes that name when saving. If that's the case, the quick fix in `converter.py` is to change every fallback reference from `"MsoNormal"` to `"Normal"`:

```python
# In _process_node, the default paragraph catch-all at the bottom of the p block:
para = doc.add_paragraph(style="Normal")

# And in makeParagraph for any cls == "MsoNormal" check:
if cls in ("MsoNormal", ""):
    para = doc.add_paragraph(style="Normal")
```

But share the style list output first and I'll give you a precise corrected `converter.py` rather than a guess — there may be other name mismatches worth catching at the same time.

---

## 🧑 User

'Normal'
'Heading 1'
'Heading 2'
'Heading 3'
'Heading 4'
'Heading 5'
'Heading 6'
'Heading 7'
'Heading 8'
'Heading 9'
'Default Paragraph Font'
'Normal Table'
'No List'
'List Paragraph'
'Header'
'Header Char'
'Footer'
'Footer Char'
'Hyperlink'
'Document Map'
'Document Map Char'
'Balloon Text'
'Balloon Text Char'
'Heading 1 Char'
'TOC Heading'
'Heading 2 Char'
'Heading 3 Char'
'Heading 4 Char'
'Heading 5 Char'
'Heading 6 Char'
'Heading 7 Char'
'Heading 8 Char'
'Heading 9 Char'
'Caption'
'Title'
'Title Char'
'Subtitle'
'Subtitle Char'
'Strong'
'Emphasis'
'Quote'
'Quote Char'
'Intense Quote'
'Intense Quote Char'
'Subtle Emphasis'
'Intense Emphasis'
'Subtle Reference'
'Intense Reference'
'Book Title'
'toc 1'
'toc 2'
'Table Grid'
'annotation reference'
'annotation text'
'Comment Text Char'
'annotation subject'
'Comment Subject Char'
'Unresolved Mention'
'Grid Table 1 Light'
'Revision'
'List Number'
'Bulleted List'
'List Bullet'
'List Bullet Char'
'Bulleted List Char'
'Normal Image'
'Table'
'Clicks'
'FollowedHyperlink'
'toc 3'
'endnote reference'
'footnote reference'
'Hashtag'
'HTML Acronym'
'HTML Cite'
'HTML Code'
'HTML Definition'
'HTML Keyboard'
'HTML Sample'
'HTML Typewriter'
'HTML Variable'
'line number'
'page number'
'Placeholder Text'
'Smart Hyperlink'
'Smart Link'
'Note'
'Block Text'
'envelope address'
'envelope return'
'index 1'
'index heading'
'Medium Grid 2'
'Medium Grid 2 Accent 1'
'Medium Grid 2 Accent 2'
'Medium Grid 2 Accent 3'
'Medium Grid 2 Accent 4'
'Medium Grid 2 Accent 5'
'Medium Grid 2 Accent 6'
'Medium List 2'
'Medium List 2 Accent 1'
'Medium List 2 Accent 2'
'Medium List 2 Accent 3'
'Medium List 2 Accent 4'
'Medium List 2 Accent 5'
'Medium List 2 Accent 6'
'Message Header'
'Message Header Char'
'toa heading'
'HTML Preformatted'
'HTML Preformatted Char'
'macro'
'Macro Text Char'
'Plain Text'
'Plain Text Char'
'Normal (Web)'
'Body Text 3'
'Body Text 3 Char'
'Body Text Indent 3'
'Body Text Indent 3 Char'
'endnote text'
'Endnote Text Char'
'footnote text'
'Footnote Text Char'

---

## 🤖 Assistant

Perfect. All the important styles are there, just with slightly different names than what `converter.py` was expecting. Here's the complete mapping that needs to change:

| What converter.py used | Actual name in template |
|---|---|
| `MsoNormal` | `Normal` |
| `Note` | `Note` ✓ |
| `BulletedList` | `Bulleted List` |
| `NormalImage` | `Normal Image` |
| `MsoQuote` | `Quote` |
| `MsoIntenseQuote` | `Intense Quote` |
| `MsoIntenseEmphasis` (char) | `Intense Emphasis` |
| `MsoSubtleReference` (char) | `Subtle Reference` |
| `MsoIntenseReference` (char) | `Intense Reference` |
| `MsoBookTitle` (char) | `Book Title` |
| `Clicks` (char) | `Clicks` ✓ |

Here's the fully corrected `converter.py`:

```python
import os
import sys
import re
from io import BytesIO

from bs4 import BeautifulSoup, NavigableString, Tag
from docx import Document
from docx.shared import Pt, Inches, RGBColor
from docx.enum.text import WD_ALIGN_PARAGRAPH
from docx.oxml.ns import qn
from docx.oxml import OxmlElement

UF_BLUE     = RGBColor(0x00, 0x21, 0xA5)
CLICKS_BLUE = RGBColor(0x17, 0x5C, 0x92)
BLACK       = RGBColor(0x00, 0x00, 0x00)

# ── Canonical style name map ──────────────────────────────────────────────────
# Keys are the HTML class names used in the model output.
# Values are the exact style names as stored in template.docx.
PARA_STYLE_MAP = {
    "MsoNormal":        "Normal",
    "BulletedList":     "Bulleted List",
    "Note":             "Note",
    "NormalImage":      "Normal Image",
    "MsoQuote":         "Quote",
    "MsoIntenseQuote":  "Intense Quote",
}

CHAR_STYLE_MAP = {
    "Clicks":                "Clicks",
    "MsoIntenseEmphasis":    "Intense Emphasis",
    "MsoSubtleReference":    "Subtle Reference",
    "MsoIntenseReference":   "Intense Reference",
    "MsoBookTitle":          "Book Title",
}


def _get_template_path() -> str:
    """
    Resolve template.docx whether running from source or a
    PyInstaller-bundled .exe (sys._MEIPASS is the temp extraction folder).
    """
    if getattr(sys, "frozen", False):
        base = sys._MEIPASS
    else:
        base = os.path.dirname(os.path.abspath(__file__))
    return os.path.join(base, "template.docx")


def _apply_note_border(paragraph):
    """Attach a UF Blue left border to a Note paragraph via raw XML."""
    p    = paragraph._p
    pPr  = p.get_or_add_pPr()
    pBdr = OxmlElement("w:pBdr")
    left = OxmlElement("w:left")
    left.set(qn("w:val"),   "single")
    left.set(qn("w:sz"),    "12")
    left.set(qn("w:space"), "4")
    left.set(qn("w:color"), "0021A5")
    pBdr.append(left)
    pPr.append(pBdr)


def _heading_config(level: int) -> dict:
    configs = [
        {"size": 16, "bold": True,  "italic": False, "color": BLACK,
         "before": 18, "after": 4},
        {"size": 14, "bold": True,  "italic": False, "color": UF_BLUE,
         "before": 8,  "after": 4},
        {"size": 14, "bold": False, "italic": False, "color": UF_BLUE,
         "before": 8,  "after": 4},
        {"size": 14, "bold": False, "italic": True,  "color": UF_BLUE,
         "before": 4,  "after": 2},
        {"size": 14, "bold": False, "italic": False, "color": UF_BLUE,
         "before": 4,  "after": 2},
        {"size": 12, "bold": False, "italic": True,  "color": BLACK,
         "before": 2,  "after": 0},
    ]
    return configs[min(level - 1, 5)]


def _collect_inline_runs(node) -> list:
    """
    Recursively walk an element's children and return a list of run dicts:
    {text, bold, italic, color, char_style}
    char_style is the template.docx style name (from CHAR_STYLE_MAP), or None.
    """
    runs = []
    for child in node.children:
        if isinstance(child, NavigableString):
            text = str(child)
            if text:
                runs.append({
                    "text": text, "bold": False, "italic": False,
                    "color": BLACK, "char_style": None
                })
            continue
        if not isinstance(child, Tag):
            continue

        tag = child.name.lower() if child.name else ""
        cls = " ".join(child.get("class", [])).strip()

        if tag == "strong":
            for r in _collect_inline_runs(child):
                r["bold"] = True
                runs.append(r)

        elif tag == "em":
            for r in _collect_inline_runs(child):
                r["italic"] = True
                runs.append(r)

        elif tag == "span" and cls in CHAR_STYLE_MAP:
            # Map HTML class name → template style name
            template_style = CHAR_STYLE_MAP[cls]
            runs.append({
                "text":       child.get_text(),
                "bold":       cls in ("Clicks", "MsoIntenseEmphasis",
                                      "MsoSubtleReference",
                                      "MsoIntenseReference", "MsoBookTitle"),
                "italic":     cls in ("MsoIntenseEmphasis", "MsoBookTitle"),
                "color":      CLICKS_BLUE if cls == "Clicks" else BLACK,
                "char_style": template_style
            })

        else:
            runs.extend(_collect_inline_runs(child))

    return runs


def _add_runs_to_paragraph(paragraph, run_dicts,
                            force_bold=False, force_italic=False,
                            force_color=None, font_size=None):
    """Write a list of run dicts onto an existing paragraph."""
    style_names = {s.name for s in paragraph.part.document.styles}
    for rd in run_dicts:
        run             = paragraph.add_run(rd["text"])
        run.bold        = force_bold   or rd["bold"]
        run.italic      = force_italic or rd["italic"]
        run.font.color.rgb = force_color or rd["color"]
        run.font.name   = "Calibri"
        if font_size:
            run.font.size = Pt(font_size)
        if rd["char_style"] and rd["char_style"] in style_names:
            run.style = paragraph.part.document.styles[rd["char_style"]]


def _process_node(doc: Document, node, h1_seen: list):
    """
    Convert a single top-level HTML node into one or more docx paragraphs.
    h1_seen is a one-element mutable list used to capture the first h1 text.
    """
    if isinstance(node, NavigableString):
        return
    if not isinstance(node, Tag):
        return

    tag      = node.name.lower() if node.name else ""
    cls_list = node.get("class", [])
    cls      = cls_list[0] if cls_list else ""

    # ── Headings ─────────────────────────────────────────────────────────────
    heading_match = re.match(r"^h([1-6])$", tag)
    if heading_match:
        level      = int(heading_match.group(1))
        cfg        = _heading_config(level)
        style_name = f"Heading {level}"

        para = doc.add_paragraph(style=style_name)
        fmt  = para.paragraph_format
        fmt.space_before = Pt(cfg["before"])
        fmt.space_after  = Pt(cfg["after"])

        _add_runs_to_paragraph(
            para, _collect_inline_runs(node),
            force_bold=cfg["bold"],
            force_italic=cfg["italic"],
            force_color=cfg["color"],
            font_size=cfg["size"]
        )

        # Capture first h1 as document metadata title
        if level == 1 and not h1_seen[0]:
            h1_seen[0] = node.get_text(strip=True)
        return

    # ── Paragraphs ───────────────────────────────────────────────────────────
    if tag == "p":

        # Map the HTML class to the template style name,
        # falling back to Normal if the class isn't recognised
        template_style = PARA_STYLE_MAP.get(cls, "Normal")
        para = doc.add_paragraph(style=template_style)

        if cls == "Note":
            _add_runs_to_paragraph(para, _collect_inline_runs(node))
            _apply_note_border(para)
            return

        if cls == "NormalImage":
            _add_runs_to_paragraph(
                para, _collect_inline_runs(node),
                force_italic=True,
                force_color=RGBColor(0x66, 0x66, 0x66)
            )
            return

        if cls in ("MsoQuote", "MsoIntenseQuote"):
            _add_runs_to_paragraph(
                para, _collect_inline_runs(node),
                force_italic=True
            )
            if cls == "MsoIntenseQuote":
                para.paragraph_format.left_indent  = Inches(0.6)
                para.paragraph_format.right_indent = Inches(0.6)
            return

        # Normal, BulletedList, and any unrecognised class
        _add_runs_to_paragraph(para, _collect_inline_runs(node))
        return

    # ── Container elements — recurse into children ───────────────────────────
    if tag in ("div", "section", "article", "main", "header", "footer"):
        for child in node.children:
            _process_node(doc, child, h1_seen)
        return


def html_to_docx(html_string: str) -> bytes:
    """
    Parse the HTML string, walk the WordSection1 container, write each
    element into a fresh copy of template.docx, set the h1 text as the
    document metadata title, and return the result as bytes.
    """
    soup = BeautifulSoup(html_string, "lxml")

    container = (
        soup.find(class_="WordSection1")
        or soup.find("body")
        or soup
    )

    doc = Document(_get_template_path())

    # Clear any placeholder content from the template
    for p in list(doc.paragraphs):
        p._element.getparent().remove(p._element)
    for t in list(doc.tables):
        t._element.getparent().remove(t._element)

    h1_seen = [None]

    for child in container.children:
        if isinstance(child, NavigableString):
            continue
        if not isinstance(child, Tag):
            continue
        if child.find("button"):
            continue
        _process_node(doc, child, h1_seen)

    if h1_seen[0]:
        doc.core_properties.title = h1_seen[0]

    buf = BytesIO()
    doc.save(buf)
    return buf.getvalue()
```

Would you like me to explain or break down the code?

---

The key change is the `PARA_STYLE_MAP` and `CHAR_STYLE_MAP` dictionaries at the top. Rather than style names being scattered throughout the code, every HTML class → template style name mapping now lives in one place. If a name ever drifts again you only need to fix it in the map rather than hunting through the logic.

---

## 🧑 User

should i update the css from the source as well? would that be simpler?
  
```
 /* Font Definitions */
 
@font-face
    {font-family:Calibri;
    panose-1:2 15 5 2 2 2 4 3 2 4;
    mso-font-charset:0;
    mso-generic-font-family:swiss;
    mso-font-pitch:variable;
    mso-font-signature:-469750017 -1040178053 9 0 511 0;}
@font-face
    {font-family:"Calibri Light";
    panose-1:2 15 3 2 2 2 4 3 2 4;
    mso-font-charset:0;
    mso-generic-font-family:swiss;
    mso-font-pitch:variable;
    mso-font-signature:-469750017 -1040178053 9 0 511 0;}
@font-face
    {font-family:"Franklin Gothic";
    panose-1:0 0 0 0 0 0 0 0 0 0;
    mso-font-alt:Cambria;
    mso-font-charset:0;
    mso-generic-font-family:roman;
    mso-font-format:other;
    mso-font-pitch:auto;
    mso-font-signature:0 0 0 0 0 0;}
@font-face
    {font-family:Tahoma;
    panose-1:2 11 6 4 3 5 4 4 2 4;
    mso-font-charset:0;
    mso-generic-font-family:swiss;
    mso-font-pitch:variable;
    mso-font-signature:-520081665 -1073717157 41 0 66047 0;}
@font-face
    {font-family:"\@MS Gothic";
    panose-1:2 11 6 9 7 2 5 8 2 4;
    mso-font-charset:128;
    mso-generic-font-family:modern;
    mso-font-pitch:fixed;
    mso-font-signature:-536870145 1791491579 134217746 0 131231 0;}
@font-face
    {font-family:"\@MS Mincho";
    panose-1:2 2 6 9 4 2 5 8 3 4;
    mso-font-charset:128;
    mso-generic-font-family:modern;
    mso-font-pitch:fixed;
    mso-font-signature:-536870145 1791491579 134217746 0 131231 0;}
 /* Style Definitions */
 p.MsoNormal, li.MsoNormal, div.MsoNormal
    {mso-style-unhide:no;
    mso-style-qformat:yes;
    mso-style-parent:"";
    margin-top:0in;
    margin-right:0in;
    margin-bottom:8.0pt;
    margin-left:0in;
    line-height:107%;
    mso-pagination:widow-orphan;
    font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:Calibri;
    mso-fareast-theme-font:minor-latin;
    mso-bidi-font-family:Arial;
    mso-bidi-theme-font:minor-bidi;}
h1
    {mso-style-priority:9;
    mso-style-unhide:no;
    mso-style-qformat:yes;
    mso-style-link:"Heading 1 Char";
    mso-style-next:Normal;
    margin-top:.25in;
    margin-right:0in;
    margin-bottom:4.0pt;
    margin-left:0in;
    line-height:107%;
    mso-pagination:widow-orphan lines-together;
    page-break-after:avoid;
    mso-outline-level:1;
    font-size:16.0pt;
    mso-bidi-font-size:20.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:"MS Gothic";
    mso-fareast-theme-font:major-fareast;
    mso-bidi-font-family:"Times New Roman";
    mso-bidi-theme-font:major-bidi;
    mso-font-kerning:0pt;
    font-weight:bold;
    mso-bidi-font-weight:normal;}
h2
    {mso-style-priority:9;
    mso-style-qformat:yes;
    mso-style-link:"Heading 2 Char";
    mso-style-next:Normal;
    margin-top:8.0pt;
    margin-right:0in;
    margin-bottom:4.0pt;
    margin-left:0in;
    line-height:107%;
    mso-pagination:widow-orphan lines-together;
    page-break-after:avoid;
    mso-outline-level:2;
    font-size:14.0pt;
    mso-bidi-font-size:16.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:"MS Gothic";
    mso-fareast-theme-font:major-fareast;
    mso-bidi-font-family:"Times New Roman";
    mso-bidi-theme-font:major-bidi;
    color:#0021A5;
    font-weight:bold;
    mso-bidi-font-weight:normal;}
h3
    {mso-style-priority:9;
    mso-style-qformat:yes;
    mso-style-link:"Heading 3 Char";
    mso-style-next:Normal;
    margin-top:8.0pt;
    margin-right:0in;
    margin-bottom:4.0pt;
    margin-left:0in;
    line-height:107%;
    mso-pagination:widow-orphan lines-together;
    page-break-after:avoid;
    mso-outline-level:3;
    font-size:14.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:"Franklin Gothic";
    mso-bidi-font-family:"Franklin Gothic";
    color:#0021A5;
    font-weight:normal;}
h4
    {mso-style-priority:9;
    mso-style-qformat:yes;
    mso-style-link:"Heading 4 Char";
    mso-style-next:Normal;
    margin-top:4.0pt;
    margin-right:0in;
    margin-bottom:2.0pt;
    margin-left:0in;
    line-height:107%;
    mso-pagination:widow-orphan lines-together;
    page-break-after:avoid;
    mso-outline-level:4;
    font-size:14.0pt;
    mso-bidi-font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:"MS Gothic";
    mso-fareast-theme-font:major-fareast;
    mso-bidi-font-family:"Times New Roman";
    mso-bidi-theme-font:major-bidi;
    color:#0021A5;
    font-weight:normal;
    font-style:italic;}
h5
    {mso-style-priority:9;
    mso-style-link:"Heading 5 Char";
    mso-style-next:Normal;
    margin-top:4.0pt;
    margin-right:0in;
    margin-bottom:2.0pt;
    margin-left:0in;
    line-height:107%;
    mso-pagination:widow-orphan lines-together;
    page-break-after:avoid;
    mso-outline-level:5;
    font-size:14.0pt;
    mso-bidi-font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:"MS Gothic";
    mso-fareast-theme-font:major-fareast;
    mso-bidi-font-family:"Times New Roman";
    mso-bidi-theme-font:major-bidi;
    color:#0021A5;
    font-weight:normal;}
h6
    {mso-style-priority:9;
    mso-style-link:"Heading 6 Char";
    mso-style-next:Normal;
    margin-top:2.0pt;
    margin-right:0in;
    margin-bottom:0in;
    margin-left:0in;
    line-height:107%;
    mso-pagination:widow-orphan lines-together;
    page-break-after:avoid;
    mso-outline-level:6;
    font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:"MS Gothic";
    mso-fareast-theme-font:major-fareast;
    mso-bidi-font-family:"Times New Roman";
    mso-bidi-theme-font:major-bidi;
    font-weight:normal;
    font-style:italic;}
p.MsoHeading7, li.MsoHeading7, div.MsoHeading7
    {mso-style-priority:9;
    mso-style-link:"Heading 7 Char";
    mso-style-next:Normal;
    margin-top:2.0pt;
    margin-right:0in;
    margin-bottom:0in;
    margin-left:0in;
    line-height:107%;
    mso-pagination:widow-orphan lines-together;
    page-break-after:avoid;
    mso-outline-level:7;
    font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:"MS Gothic";
    mso-fareast-theme-font:major-fareast;
    mso-bidi-font-family:"Times New Roman";
    mso-bidi-theme-font:major-bidi;}
p.MsoHeading8, li.MsoHeading8, div.MsoHeading8
    {mso-style-priority:9;
    mso-style-link:"Heading 8 Char";
    mso-style-next:Normal;
    margin:0in;
    line-height:107%;
    mso-pagination:widow-orphan lines-together;
    page-break-after:avoid;
    mso-outline-level:8;
    font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:"MS Gothic";
    mso-fareast-theme-font:major-fareast;
    mso-bidi-font-family:"Times New Roman";
    mso-bidi-theme-font:major-bidi;
    font-style:italic;}
p.MsoHeading9, li.MsoHeading9, div.MsoHeading9
    {mso-style-priority:9;
    mso-style-link:"Heading 9 Char";
    mso-style-next:Normal;
    margin:0in;
    line-height:107%;
    mso-pagination:widow-orphan lines-together;
    page-break-after:avoid;
    mso-outline-level:9;
    font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:"MS Gothic";
    mso-fareast-theme-font:major-fareast;
    mso-bidi-font-family:"Times New Roman";
    mso-bidi-theme-font:major-bidi;
    color:#272727;
    mso-themecolor:text1;
    mso-themetint:216;}
p.MsoIndex1, li.MsoIndex1, div.MsoIndex1
    {mso-style-update:auto;
    mso-style-noshow:yes;
    mso-style-priority:99;
    mso-style-next:Normal;
    margin-top:0in;
    margin-right:0in;
    margin-bottom:0in;
    margin-left:12.0pt;
    text-indent:-12.0pt;
    line-height:normal;
    mso-pagination:widow-orphan;
    font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:Calibri;
    mso-fareast-theme-font:minor-latin;
    mso-bidi-font-family:Arial;
    mso-bidi-theme-font:minor-bidi;}
p.MsoToc1, li.MsoToc1, div.MsoToc1
    {mso-style-update:auto;
    mso-style-priority:39;
    mso-style-qformat:yes;
    mso-style-next:Normal;
    margin-top:0in;
    margin-right:0in;
    margin-bottom:5.0pt;
    margin-left:0in;
    line-height:107%;
    mso-pagination:widow-orphan;
    font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:Calibri;
    mso-fareast-theme-font:minor-latin;
    mso-bidi-font-family:Arial;
    mso-bidi-theme-font:minor-bidi;
    color:black;
    mso-themecolor:text1;}
p.MsoToc2, li.MsoToc2, div.MsoToc2
    {mso-style-update:auto;
    mso-style-priority:39;
    mso-style-qformat:yes;
    mso-style-next:Normal;
    margin-top:0in;
    margin-right:0in;
    margin-bottom:5.0pt;
    margin-left:12.0pt;
    line-height:107%;
    mso-pagination:widow-orphan;
    font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:Calibri;
    mso-fareast-theme-font:minor-latin;
    mso-bidi-font-family:Arial;
    mso-bidi-theme-font:minor-bidi;
    color:black;
    mso-themecolor:text1;}
p.MsoToc3, li.MsoToc3, div.MsoToc3
    {mso-style-update:auto;
    mso-style-priority:39;
    mso-style-qformat:yes;
    mso-style-next:Normal;
    margin-top:0in;
    margin-right:0in;
    margin-bottom:5.0pt;
    margin-left:24.0pt;
    line-height:107%;
    mso-pagination:widow-orphan;
    font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:Calibri;
    mso-fareast-theme-font:minor-latin;
    mso-bidi-font-family:Arial;
    mso-bidi-theme-font:minor-bidi;
    color:black;
    mso-themecolor:text1;}
p.MsoFootnoteText, li.MsoFootnoteText, div.MsoFootnoteText
    {mso-style-noshow:yes;
    mso-style-priority:99;
    mso-style-link:"Footnote Text Char";
    margin:0in;
    line-height:normal;
    mso-pagination:widow-orphan;
    font-size:12.0pt;
    mso-bidi-font-size:10.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:Calibri;
    mso-fareast-theme-font:minor-latin;
    mso-bidi-font-family:Arial;
    mso-bidi-theme-font:minor-bidi;}
p.MsoCommentText, li.MsoCommentText, div.MsoCommentText
    {mso-style-priority:99;
    mso-style-link:"Comment Text Char";
    margin-top:0in;
    margin-right:0in;
    margin-bottom:8.0pt;
    margin-left:0in;
    line-height:107%;
    mso-pagination:widow-orphan;
    font-size:12.0pt;
    mso-bidi-font-size:10.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:Calibri;
    mso-fareast-theme-font:minor-latin;
    mso-bidi-font-family:Arial;
    mso-bidi-theme-font:minor-bidi;}
p.MsoHeader, li.MsoHeader, div.MsoHeader
    {mso-style-priority:99;
    mso-style-link:"Header Char";
    margin:0in;
    line-height:107%;
    mso-pagination:widow-orphan;
    tab-stops:center 3.25in right 6.5in;
    font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:Calibri;
    mso-fareast-theme-font:minor-latin;
    mso-bidi-font-family:Arial;
    mso-bidi-theme-font:minor-bidi;}
p.MsoFooter, li.MsoFooter, div.MsoFooter
    {mso-style-priority:99;
    mso-style-link:"Footer Char";
    margin:0in;
    line-height:107%;
    mso-pagination:widow-orphan;
    tab-stops:center 3.25in right 6.5in;
    font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:Calibri;
    mso-fareast-theme-font:minor-latin;
    mso-bidi-font-family:Arial;
    mso-bidi-theme-font:minor-bidi;}
p.MsoIndexHeading, li.MsoIndexHeading, div.MsoIndexHeading
    {mso-style-noshow:yes;
    mso-style-priority:99;
    mso-style-next:"Index 1";
    margin-top:0in;
    margin-right:0in;
    margin-bottom:8.0pt;
    margin-left:0in;
    line-height:107%;
    mso-pagination:widow-orphan;
    font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:"MS Gothic";
    mso-fareast-theme-font:major-fareast;
    mso-bidi-font-family:"Times New Roman";
    mso-bidi-theme-font:major-bidi;
    font-weight:bold;}
p.MsoCaption, li.MsoCaption, div.MsoCaption
    {mso-style-noshow:yes;
    mso-style-priority:35;
    mso-style-qformat:yes;
    mso-style-next:Normal;
    margin-top:0in;
    margin-right:0in;
    margin-bottom:8.0pt;
    margin-left:0in;
    line-height:107%;
    mso-pagination:widow-orphan;
    font-size:12.0pt;
    mso-bidi-font-size:8.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:Calibri;
    mso-fareast-theme-font:minor-latin;
    mso-bidi-font-family:Arial;
    mso-bidi-theme-font:minor-bidi;
    text-transform:uppercase;
    font-weight:bold;}
p.MsoEnvelopeAddress, li.MsoEnvelopeAddress, div.MsoEnvelopeAddress
    {mso-style-noshow:yes;
    mso-style-priority:99;
    margin-top:0in;
    margin-right:0in;
    margin-bottom:0in;
    margin-left:2.0in;
    line-height:normal;
    mso-pagination:widow-orphan;
    mso-element:frame;
    mso-element-frame-width:5.5in;
    mso-element-frame-height:99.0pt;
    mso-element-frame-hspace:9.0pt;
    mso-element-wrap:auto;
    mso-element-anchor-horizontal:page;
    mso-element-left:center;
    mso-element-top:bottom;
    mso-height-rule:exactly;
    font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:"MS Gothic";
    mso-fareast-theme-font:major-fareast;
    mso-bidi-font-family:"Times New Roman";
    mso-bidi-theme-font:major-bidi;}
p.MsoEnvelopeReturn, li.MsoEnvelopeReturn, div.MsoEnvelopeReturn
    {mso-style-noshow:yes;
    mso-style-priority:99;
    margin:0in;
    line-height:normal;
    mso-pagination:widow-orphan;
    font-size:12.0pt;
    mso-bidi-font-size:10.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:"MS Gothic";
    mso-fareast-theme-font:major-fareast;
    mso-bidi-font-family:"Times New Roman";
    mso-bidi-theme-font:major-bidi;}
span.MsoFootnoteReference
    {mso-style-noshow:yes;
    mso-style-priority:99;
    vertical-align:super;}
span.MsoCommentReference
    {mso-style-noshow:yes;
    mso-style-priority:99;
    mso-ansi-font-size:12.0pt;
    mso-bidi-font-size:8.0pt;
    font-family:"Calibri",sans-serif;
    mso-ascii-font-family:Calibri;
    mso-hansi-font-family:Calibri;}
span.MsoEndnoteReference
    {mso-style-noshow:yes;
    mso-style-priority:99;
    vertical-align:super;}
p.MsoEndnoteText, li.MsoEndnoteText, div.MsoEndnoteText
    {mso-style-noshow:yes;
    mso-style-priority:99;
    mso-style-link:"Endnote Text Char";
    margin:0in;
    line-height:normal;
    mso-pagination:widow-orphan;
    font-size:12.0pt;
    mso-bidi-font-size:10.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:Calibri;
    mso-fareast-theme-font:minor-latin;
    mso-bidi-font-family:Arial;
    mso-bidi-theme-font:minor-bidi;}
p.MsoMacroText, li.MsoMacroText, div.MsoMacroText
    {mso-style-noshow:yes;
    mso-style-priority:99;
    mso-style-parent:"";
    mso-style-link:"Macro Text Char";
    margin:0in;
    line-height:107%;
    mso-pagination:widow-orphan;
    tab-stops:24.0pt 48.0pt 1.0in 96.0pt 120.0pt 2.0in 168.0pt 192.0pt 3.0in;
    font-size:12.0pt;
    mso-bidi-font-size:10.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:Calibri;
    mso-fareast-theme-font:minor-latin;
    mso-bidi-font-family:Arial;
    mso-bidi-theme-font:minor-bidi;}
p.MsoToaHeading, li.MsoToaHeading, div.MsoToaHeading
    {mso-style-noshow:yes;
    mso-style-priority:99;
    mso-style-next:Normal;
    margin-top:6.0pt;
    margin-right:0in;
    margin-bottom:8.0pt;
    margin-left:0in;
    line-height:107%;
    mso-pagination:widow-orphan;
    font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:"MS Gothic";
    mso-fareast-theme-font:major-fareast;
    mso-bidi-font-family:"Times New Roman";
    mso-bidi-theme-font:major-bidi;
    font-weight:bold;}
p.MsoListBullet, li.MsoListBullet, div.MsoListBullet
    {mso-style-noshow:yes;
    mso-style-priority:99;
    mso-style-link:"List Bullet Char";
    margin-top:0in;
    margin-right:0in;
    margin-bottom:8.0pt;
    margin-left:.25in;
    mso-add-space:auto;
    text-indent:-.25in;
    line-height:107%;
    mso-pagination:widow-orphan;
    mso-list:l0 level1 lfo2;
    tab-stops:list .25in;
    font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:Calibri;
    mso-fareast-theme-font:minor-latin;
    mso-bidi-font-family:Arial;
    mso-bidi-theme-font:minor-bidi;}
p.MsoListBulletCxSpFirst, li.MsoListBulletCxSpFirst, div.MsoListBulletCxSpFirst
    {mso-style-noshow:yes;
    mso-style-priority:99;
    mso-style-link:"List Bullet Char";
    mso-style-type:export-only;
    margin-top:0in;
    margin-right:0in;
    margin-bottom:0in;
    margin-left:.25in;
    mso-add-space:auto;
    text-indent:-.25in;
    line-height:107%;
    mso-pagination:widow-orphan;
    mso-list:l0 level1 lfo2;
    tab-stops:list .25in;
    font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:Calibri;
    mso-fareast-theme-font:minor-latin;
    mso-bidi-font-family:Arial;
    mso-bidi-theme-font:minor-bidi;}
p.MsoListBulletCxSpMiddle, li.MsoListBulletCxSpMiddle, div.MsoListBulletCxSpMiddle
    {mso-style-noshow:yes;
    mso-style-priority:99;
    mso-style-link:"List Bullet Char";
    mso-style-type:export-only;
    margin-top:0in;
    margin-right:0in;
    margin-bottom:0in;
    margin-left:.25in;
    mso-add-space:auto;
    text-indent:-.25in;
    line-height:107%;
    mso-pagination:widow-orphan;
    mso-list:l0 level1 lfo2;
    tab-stops:list .25in;
    font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:Calibri;
    mso-fareast-theme-font:minor-latin;
    mso-bidi-font-family:Arial;
    mso-bidi-theme-font:minor-bidi;}
p.MsoListBulletCxSpLast, li.MsoListBulletCxSpLast, div.MsoListBulletCxSpLast
    {mso-style-noshow:yes;
    mso-style-priority:99;
    mso-style-link:"List Bullet Char";
    mso-style-type:export-only;
    margin-top:0in;
    margin-right:0in;
    margin-bottom:8.0pt;
    margin-left:.25in;
    mso-add-space:auto;
    text-indent:-.25in;
    line-height:107%;
    mso-pagination:widow-orphan;
    mso-list:l0 level1 lfo2;
    tab-stops:list .25in;
    font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:Calibri;
    mso-fareast-theme-font:minor-latin;
    mso-bidi-font-family:Arial;
    mso-bidi-theme-font:minor-bidi;}
p.MsoListNumber, li.MsoListNumber, div.MsoListNumber
    {mso-style-noshow:yes;
    mso-style-priority:99;
    margin-top:0in;
    margin-right:0in;
    margin-bottom:8.0pt;
    margin-left:0in;
    mso-add-space:auto;
    line-height:107%;
    mso-pagination:widow-orphan;
    font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:Calibri;
    mso-fareast-theme-font:minor-latin;
    mso-bidi-font-family:Arial;
    mso-bidi-theme-font:minor-bidi;}
p.MsoListNumberCxSpFirst, li.MsoListNumberCxSpFirst, div.MsoListNumberCxSpFirst
    {mso-style-noshow:yes;
    mso-style-priority:99;
    mso-style-type:export-only;
    margin:0in;
    mso-add-space:auto;
    line-height:107%;
    mso-pagination:widow-orphan;
    font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:Calibri;
    mso-fareast-theme-font:minor-latin;
    mso-bidi-font-family:Arial;
    mso-bidi-theme-font:minor-bidi;}
p.MsoListNumberCxSpMiddle, li.MsoListNumberCxSpMiddle, div.MsoListNumberCxSpMiddle
    {mso-style-noshow:yes;
    mso-style-priority:99;
    mso-style-type:export-only;
    margin:0in;
    mso-add-space:auto;
    line-height:107%;
    mso-pagination:widow-orphan;
    font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:Calibri;
    mso-fareast-theme-font:minor-latin;
    mso-bidi-font-family:Arial;
    mso-bidi-theme-font:minor-bidi;}
p.MsoListNumberCxSpLast, li.MsoListNumberCxSpLast, div.MsoListNumberCxSpLast
    {mso-style-noshow:yes;
    mso-style-priority:99;
    mso-style-type:export-only;
    margin-top:0in;
    margin-right:0in;
    margin-bottom:8.0pt;
    margin-left:0in;
    mso-add-space:auto;
    line-height:107%;
    mso-pagination:widow-orphan;
    font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:Calibri;
    mso-fareast-theme-font:minor-latin;
    mso-bidi-font-family:Arial;
    mso-bidi-theme-font:minor-bidi;}
p.MsoTitle, li.MsoTitle, div.MsoTitle
    {mso-style-priority:10;
    mso-style-unhide:no;
    mso-style-qformat:yes;
    mso-style-link:"Title Char";
    mso-style-next:Normal;
    margin-top:0in;
    margin-right:0in;
    margin-bottom:4.0pt;
    margin-left:0in;
    mso-add-space:auto;
    line-height:107%;
    mso-pagination:widow-orphan;
    font-size:12.0pt;
    mso-bidi-font-size:28.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:"MS Gothic";
    mso-fareast-theme-font:major-fareast;
    mso-bidi-font-family:"Times New Roman";
    mso-bidi-theme-font:major-bidi;
    letter-spacing:-.5pt;
    mso-font-kerning:14.0pt;}
p.MsoTitleCxSpFirst, li.MsoTitleCxSpFirst, div.MsoTitleCxSpFirst
    {mso-style-priority:10;
    mso-style-unhide:no;
    mso-style-qformat:yes;
    mso-style-link:"Title Char";
    mso-style-next:Normal;
    mso-style-type:export-only;
    margin:0in;
    mso-add-space:auto;
    line-height:107%;
    mso-pagination:widow-orphan;
    font-size:12.0pt;
    mso-bidi-font-size:28.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:"MS Gothic";
    mso-fareast-theme-font:major-fareast;
    mso-bidi-font-family:"Times New Roman";
    mso-bidi-theme-font:major-bidi;
    letter-spacing:-.5pt;
    mso-font-kerning:14.0pt;}
p.MsoTitleCxSpMiddle, li.MsoTitleCxSpMiddle, div.MsoTitleCxSpMiddle
    {mso-style-priority:10;
    mso-style-unhide:no;
    mso-style-qformat:yes;
    mso-style-link:"Title Char";
    mso-style-next:Normal;
    mso-style-type:export-only;
    margin:0in;
    mso-add-space:auto;
    line-height:107%;
    mso-pagination:widow-orphan;
    font-size:12.0pt;
    mso-bidi-font-size:28.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:"MS Gothic";
    mso-fareast-theme-font:major-fareast;
    mso-bidi-font-family:"Times New Roman";
    mso-bidi-theme-font:major-bidi;
    letter-spacing:-.5pt;
    mso-font-kerning:14.0pt;}
p.MsoTitleCxSpLast, li.MsoTitleCxSpLast, div.MsoTitleCxSpLast
    {mso-style-priority:10;
    mso-style-unhide:no;
    mso-style-qformat:yes;
    mso-style-link:"Title Char";
    mso-style-next:Normal;
    mso-style-type:export-only;
    margin-top:0in;
    margin-right:0in;
    margin-bottom:4.0pt;
    margin-left:0in;
    mso-add-space:auto;
    line-height:107%;
    mso-pagination:widow-orphan;
    font-size:12.0pt;
    mso-bidi-font-size:28.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:"MS Gothic";
    mso-fareast-theme-font:major-fareast;
    mso-bidi-font-family:"Times New Roman";
    mso-bidi-theme-font:major-bidi;
    letter-spacing:-.5pt;
    mso-font-kerning:14.0pt;}
p.MsoMessageHeader, li.MsoMessageHeader, div.MsoMessageHeader
    {mso-style-noshow:yes;
    mso-style-priority:99;
    mso-style-link:"Message Header Char";
    margin-top:0in;
    margin-right:0in;
    margin-bottom:0in;
    margin-left:.75in;
    text-indent:-.75in;
    line-height:normal;
    mso-pagination:widow-orphan;
    background:#CCCCCC;
    mso-shading:windowtext;
    mso-pattern:gray-20 auto;
    border:none;
    mso-border-alt:solid windowtext .75pt;
    padding:0in;
    mso-padding-alt:1.0pt 1.0pt 1.0pt 1.0pt;
    font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:"MS Gothic";
    mso-fareast-theme-font:major-fareast;
    mso-bidi-font-family:"Times New Roman";
    mso-bidi-theme-font:major-bidi;}
p.MsoSubtitle, li.MsoSubtitle, div.MsoSubtitle
    {mso-style-priority:11;
    mso-style-unhide:no;
    mso-style-qformat:yes;
    mso-style-link:"Subtitle Char";
    mso-style-next:Normal;
    margin-top:0in;
    margin-right:0in;
    margin-bottom:8.0pt;
    margin-left:0in;
    line-height:107%;
    mso-pagination:widow-orphan;
    font-size:12.0pt;
    mso-bidi-font-size:14.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:"MS Gothic";
    mso-fareast-theme-font:major-fareast;
    mso-bidi-font-family:"Times New Roman";
    mso-bidi-theme-font:major-bidi;
    letter-spacing:.75pt;}
p.MsoBodyText3, li.MsoBodyText3, div.MsoBodyText3
    {mso-style-noshow:yes;
    mso-style-priority:99;
    mso-style-link:"Body Text 3 Char";
    margin-top:0in;
    margin-right:0in;
    margin-bottom:6.0pt;
    margin-left:0in;
    line-height:107%;
    mso-pagination:widow-orphan;
    font-size:12.0pt;
    mso-bidi-font-size:8.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:Calibri;
    mso-fareast-theme-font:minor-latin;
    mso-bidi-font-family:Arial;
    mso-bidi-theme-font:minor-bidi;}
p.MsoBodyTextIndent3, li.MsoBodyTextIndent3, div.MsoBodyTextIndent3
    {mso-style-noshow:yes;
    mso-style-priority:99;
    mso-style-link:"Body Text Indent 3 Char";
    margin-top:0in;
    margin-right:0in;
    margin-bottom:6.0pt;
    margin-left:.25in;
    line-height:107%;
    mso-pagination:widow-orphan;
    font-size:12.0pt;
    mso-bidi-font-size:8.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:Calibri;
    mso-fareast-theme-font:minor-latin;
    mso-bidi-font-family:Arial;
    mso-bidi-theme-font:minor-bidi;}
p.MsoBlockText, li.MsoBlockText, div.MsoBlockText
    {mso-style-noshow:yes;
    mso-style-priority:99;
    margin-top:0in;
    margin-right:.8in;
    margin-bottom:8.0pt;
    margin-left:.8in;
    line-height:107%;
    mso-pagination:widow-orphan;
    border:none;
    mso-border-alt:solid #4F81BD .25pt;
    mso-border-themecolor:accent1;
    padding:0in;
    mso-padding-alt:10.0pt 10.0pt 10.0pt 10.0pt;
    font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:"MS Mincho";
    mso-fareast-theme-font:minor-fareast;
    mso-bidi-font-family:Arial;
    mso-bidi-theme-font:minor-bidi;
    color:#4F81BD;
    mso-themecolor:accent1;
    font-style:italic;}
a:link, span.MsoHyperlink
    {mso-style-priority:99;
    mso-style-qformat:yes;
    mso-ansi-font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-ascii-font-family:Calibri;
    mso-hansi-font-family:Calibri;
    color:#0000EE;
    text-decoration:underline;
    text-underline:single;}
a:visited, span.MsoHyperlinkFollowed
    {mso-style-noshow:yes;
    mso-style-priority:99;
    color:purple;
    mso-themecolor:followedhyperlink;
    text-decoration:underline;
    text-underline:single;}
strong
    {mso-style-priority:22;
    mso-style-unhide:no;
    mso-style-qformat:yes;
    mso-ansi-font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-ascii-font-family:Calibri;
    mso-hansi-font-family:Calibri;
    color:black;
    mso-themecolor:text1;}
em
    {mso-style-priority:20;
    mso-style-unhide:no;
    mso-style-qformat:yes;
    mso-ansi-font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-ascii-font-family:Calibri;
    mso-hansi-font-family:Calibri;
    color:black;
    mso-themecolor:text1;}
p.MsoDocumentMap, li.MsoDocumentMap, div.MsoDocumentMap
    {mso-style-noshow:yes;
    mso-style-priority:99;
    mso-style-link:"Document Map Char";
    margin:0in;
    line-height:normal;
    mso-pagination:widow-orphan;
    font-size:12.0pt;
    mso-bidi-font-size:8.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:Calibri;
    mso-fareast-theme-font:minor-latin;
    mso-bidi-font-family:Tahoma;}
p.MsoPlainText, li.MsoPlainText, div.MsoPlainText
    {mso-style-noshow:yes;
    mso-style-priority:99;
    mso-style-link:"Plain Text Char";
    margin:0in;
    line-height:normal;
    mso-pagination:widow-orphan;
    font-size:12.0pt;
    mso-bidi-font-size:10.5pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:Calibri;
    mso-fareast-theme-font:minor-latin;
    mso-bidi-font-family:Arial;
    mso-bidi-theme-font:minor-bidi;}
p
    {mso-style-noshow:yes;
    mso-style-priority:99;
    margin-top:0in;
    margin-right:0in;
    margin-bottom:8.0pt;
    margin-left:0in;
    line-height:107%;
    mso-pagination:widow-orphan;
    font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:Calibri;
    mso-fareast-theme-font:minor-latin;
    mso-bidi-font-family:"Times New Roman";}
code
    {mso-style-noshow:yes;
    mso-style-priority:99;
    mso-ansi-font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-ascii-font-family:Calibri;
    mso-fareast-font-family:"Times New Roman";
    mso-hansi-font-family:Calibri;
    mso-bidi-font-family:"Times New Roman";}
kbd
    {mso-style-noshow:yes;
    mso-style-priority:99;
    mso-ansi-font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-ascii-font-family:Calibri;
    mso-fareast-font-family:"Times New Roman";
    mso-hansi-font-family:Calibri;
    mso-bidi-font-family:"Times New Roman";}
pre
    {mso-style-noshow:yes;
    mso-style-priority:99;
    mso-style-link:"HTML Preformatted Char";
    margin:0in;
    line-height:normal;
    mso-pagination:widow-orphan;
    tab-stops:.5in;
    font-size:12.0pt;
    mso-bidi-font-size:10.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:Calibri;
    mso-fareast-theme-font:minor-latin;
    mso-bidi-font-family:Arial;
    mso-bidi-theme-font:minor-bidi;}
samp
    {mso-style-noshow:yes;
    mso-style-priority:99;
    mso-ansi-font-size:12.0pt;
    mso-bidi-font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-ascii-font-family:Calibri;
    mso-fareast-font-family:"Times New Roman";
    mso-hansi-font-family:Calibri;
    mso-bidi-font-family:"Times New Roman";}
tt
    {mso-style-noshow:yes;
    mso-style-priority:99;
    mso-ansi-font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-ascii-font-family:Calibri;
    mso-fareast-font-family:"Times New Roman";
    mso-hansi-font-family:Calibri;
    mso-bidi-font-family:"Times New Roman";}
p.MsoCommentSubject, li.MsoCommentSubject, div.MsoCommentSubject
    {mso-style-noshow:yes;
    mso-style-priority:99;
    mso-style-parent:"Comment Text";
    mso-style-link:"Comment Subject Char";
    mso-style-next:"Comment Text";
    margin-top:0in;
    margin-right:0in;
    margin-bottom:8.0pt;
    margin-left:0in;
    line-height:107%;
    mso-pagination:widow-orphan;
    font-size:12.0pt;
    mso-bidi-font-size:10.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:Calibri;
    mso-fareast-theme-font:minor-latin;
    mso-bidi-font-family:Arial;
    mso-bidi-theme-font:minor-bidi;
    font-weight:bold;}
p.MsoAcetate, li.MsoAcetate, div.MsoAcetate
    {mso-style-noshow:yes;
    mso-style-priority:99;
    mso-style-link:"Balloon Text Char";
    margin:0in;
    line-height:normal;
    mso-pagination:widow-orphan;
    font-size:12.0pt;
    mso-bidi-font-size:8.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:Calibri;
    mso-fareast-theme-font:minor-latin;
    mso-bidi-font-family:Tahoma;}
span.MsoPlaceholderText
    {mso-style-noshow:yes;
    mso-style-priority:99;
    mso-style-unhide:no;
    color:#666666;}
p.MsoRMPane, li.MsoRMPane, div.MsoRMPane
    {mso-style-noshow:yes;
    mso-style-priority:99;
    mso-style-unhide:no;
    mso-style-parent:"";
    margin:0in;
    line-height:normal;
    mso-pagination:widow-orphan;
    font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:Calibri;
    mso-fareast-theme-font:minor-latin;
    mso-bidi-font-family:Arial;
    mso-bidi-theme-font:minor-bidi;
    mso-font-kerning:1.0pt;
    mso-ligatures:standardcontextual;}
p.MsoListParagraph, li.MsoListParagraph, div.MsoListParagraph
    {mso-style-update:auto;
    mso-style-priority:34;
    mso-style-unhide:no;
    mso-style-qformat:yes;
    mso-style-parent:"List Number";
    margin-top:0in;
    margin-right:0in;
    margin-bottom:6.0pt;
    margin-left:.5in;
    text-indent:-.25in;
    line-height:normal;
    mso-pagination:widow-orphan;
    mso-list:l1 level1 lfo22;
    tab-stops:list .5in;
    font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:Calibri;
    mso-fareast-theme-font:minor-latin;
    mso-bidi-font-family:Arial;
    mso-bidi-theme-font:minor-bidi;}
p.MsoQuote, li.MsoQuote, div.MsoQuote
    {mso-style-priority:29;
    mso-style-unhide:no;
    mso-style-qformat:yes;
    mso-style-link:"Quote Char";
    mso-style-next:Normal;
    margin-top:8.0pt;
    margin-right:0in;
    margin-bottom:8.0pt;
    margin-left:0in;
    text-align:center;
    line-height:107%;
    mso-pagination:widow-orphan;
    font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:Calibri;
    mso-fareast-theme-font:minor-latin;
    mso-bidi-font-family:Arial;
    mso-bidi-theme-font:minor-bidi;
    font-style:italic;}
p.MsoIntenseQuote, li.MsoIntenseQuote, div.MsoIntenseQuote
    {mso-style-priority:30;
    mso-style-unhide:no;
    mso-style-qformat:yes;
    mso-style-link:"Intense Quote Char";
    mso-style-next:Normal;
    margin-top:.25in;
    margin-right:.6in;
    margin-bottom:.25in;
    margin-left:.6in;
    text-align:center;
    line-height:107%;
    mso-pagination:widow-orphan;
    border:none;
    mso-border-top-alt:solid #365F91 .5pt;
    mso-border-top-themecolor:accent1;
    mso-border-top-themeshade:191;
    mso-border-bottom-alt:solid #365F91 .5pt;
    mso-border-bottom-themecolor:accent1;
    mso-border-bottom-themeshade:191;
    padding:0in;
    mso-padding-alt:10.0pt 0in 10.0pt 0in;
    font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:Calibri;
    mso-fareast-theme-font:minor-latin;
    mso-bidi-font-family:Arial;
    mso-bidi-theme-font:minor-bidi;
    font-style:italic;}
span.MsoSubtleEmphasis
    {mso-style-priority:19;
    mso-style-unhide:no;
    mso-style-qformat:yes;
    mso-ansi-font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-ascii-font-family:Calibri;
    mso-hansi-font-family:Calibri;
    color:black;
    mso-themecolor:text1;
    font-style:italic;}
span.MsoIntenseEmphasis
    {mso-style-priority:21;
    mso-style-unhide:no;
    mso-style-qformat:yes;
    mso-ansi-font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-ascii-font-family:Calibri;
    mso-hansi-font-family:Calibri;
    color:black;
    mso-themecolor:text1;
    font-weight:bold;
    mso-bidi-font-weight:normal;
    font-style:italic;}
span.MsoSubtleReference
    {mso-style-priority:31;
    mso-style-unhide:no;
    mso-style-qformat:yes;
    mso-ansi-font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-ascii-font-family:Calibri;
    mso-hansi-font-family:Calibri;
    font-variant:small-caps;
    color:black;
    mso-themecolor:text1;}
span.MsoIntenseReference
    {mso-style-priority:32;
    mso-style-unhide:no;
    mso-style-qformat:yes;
    mso-ansi-font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-ascii-font-family:Calibri;
    mso-hansi-font-family:Calibri;
    font-variant:small-caps;
    color:black;
    mso-themecolor:text1;
    letter-spacing:.25pt;
    font-weight:bold;}
span.MsoBookTitle
    {mso-style-priority:33;
    mso-style-unhide:no;
    mso-style-qformat:yes;
    mso-ansi-font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-ascii-font-family:Calibri;
    mso-hansi-font-family:Calibri;
    letter-spacing:.25pt;
    font-weight:bold;
    font-style:italic;}
p.MsoTocHeading, li.MsoTocHeading, div.MsoTocHeading
    {mso-style-update:auto;
    mso-style-priority:39;
    mso-style-qformat:yes;
    mso-style-parent:"Heading 1";
    mso-style-next:Normal;
    margin-top:12.0pt;
    margin-right:0in;
    margin-bottom:0in;
    margin-left:0in;
    line-height:107%;
    mso-pagination:widow-orphan lines-together;
    page-break-after:avoid;
    font-size:16.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:"MS Gothic";
    mso-fareast-theme-font:major-fareast;
    mso-bidi-font-family:"Times New Roman";
    mso-bidi-theme-font:major-bidi;
    color:black;
    mso-themecolor:text1;}
span.MsoSmartlink
    {mso-style-noshow:yes;
    mso-style-priority:99;
    color:blue;
    background:#F3F2F1;
    text-decoration:underline;
    text-underline:single;}
span.HeaderChar
    {mso-style-name:"Header Char";
    mso-style-priority:99;
    mso-style-unhide:no;
    mso-style-locked:yes;
    mso-style-link:Header;
    mso-ansi-font-size:12.0pt;
    mso-bidi-font-size:11.0pt;
    font-family:"Calibri",sans-serif;
    mso-ascii-font-family:Calibri;
    mso-fareast-font-family:Calibri;
    mso-fareast-theme-font:minor-latin;
    mso-hansi-font-family:Calibri;}
span.FooterChar
    {mso-style-name:"Footer Char";
    mso-style-priority:99;
    mso-style-unhide:no;
    mso-style-locked:yes;
    mso-style-link:Footer;
    mso-ansi-font-size:12.0pt;
    mso-bidi-font-size:11.0pt;
    font-family:"Calibri",sans-serif;
    mso-ascii-font-family:Calibri;
    mso-fareast-font-family:Calibri;
    mso-fareast-theme-font:minor-latin;
    mso-hansi-font-family:Calibri;}
span.DocumentMapChar
    {mso-style-name:"Document Map Char";
    mso-style-noshow:yes;
    mso-style-priority:99;
    mso-style-unhide:no;
    mso-style-locked:yes;
    mso-style-link:"Document Map";
    mso-bidi-font-size:8.0pt;
    font-family:"Tahoma",sans-serif;
    mso-bidi-font-family:Tahoma;}
span.BalloonTextChar
    {mso-style-name:"Balloon Text Char";
    mso-style-noshow:yes;
    mso-style-priority:99;
    mso-style-unhide:no;
    mso-style-locked:yes;
    mso-style-link:"Balloon Text";
    mso-bidi-font-size:8.0pt;
    font-family:"Tahoma",sans-serif;
    mso-bidi-font-family:Tahoma;}
span.Heading1Char
    {mso-style-name:"Heading 1 Char";
    mso-style-priority:9;
    mso-style-unhide:no;
    mso-style-locked:yes;
    mso-style-link:"Heading 1";
    mso-ansi-font-size:16.0pt;
    mso-bidi-font-size:20.0pt;
    font-family:"MS Gothic";
    mso-fareast-font-family:"MS Gothic";
    mso-fareast-theme-font:major-fareast;
    mso-bidi-font-family:"Times New Roman";
    mso-bidi-theme-font:major-bidi;
    font-weight:bold;
    mso-bidi-font-weight:normal;}
span.Heading2Char
    {mso-style-name:"Heading 2 Char";
    mso-style-priority:9;
    mso-style-unhide:no;
    mso-style-locked:yes;
    mso-style-link:"Heading 2";
    mso-ansi-font-size:14.0pt;
    mso-bidi-font-size:16.0pt;
    font-family:"Calibri",sans-serif;
    mso-ascii-font-family:Calibri;
    mso-fareast-font-family:"MS Gothic";
    mso-fareast-theme-font:major-fareast;
    mso-hansi-font-family:Calibri;
    mso-bidi-font-family:"Times New Roman";
    mso-bidi-theme-font:major-bidi;
    color:#0021A5;
    font-weight:bold;
    mso-bidi-font-weight:normal;}
span.Heading3Char
    {mso-style-name:"Heading 3 Char";
    mso-style-priority:9;
    mso-style-unhide:no;
    mso-style-locked:yes;
    mso-style-link:"Heading 3";
    mso-ansi-font-size:14.0pt;
    mso-bidi-font-size:14.0pt;
    font-family:"Calibri",sans-serif;
    mso-ascii-font-family:Calibri;
    mso-fareast-font-family:"Franklin Gothic";
    mso-hansi-font-family:Calibri;
    mso-bidi-font-family:"Franklin Gothic";
    color:#0021A5;}
span.Heading4Char
    {mso-style-name:"Heading 4 Char";
    mso-style-priority:9;
    mso-style-unhide:no;
    mso-style-locked:yes;
    mso-style-link:"Heading 4";
    mso-ansi-font-size:14.0pt;
    mso-bidi-font-size:11.0pt;
    font-family:"Calibri",sans-serif;
    mso-ascii-font-family:Calibri;
    mso-fareast-font-family:"MS Gothic";
    mso-fareast-theme-font:major-fareast;
    mso-hansi-font-family:Calibri;
    mso-bidi-font-family:"Times New Roman";
    mso-bidi-theme-font:major-bidi;
    color:#0021A5;
    font-style:italic;}
span.Heading5Char
    {mso-style-name:"Heading 5 Char";
    mso-style-priority:9;
    mso-style-unhide:no;
    mso-style-locked:yes;
    mso-style-link:"Heading 5";
    mso-ansi-font-size:14.0pt;
    mso-bidi-font-size:11.0pt;
    font-family:"Calibri",sans-serif;
    mso-ascii-font-family:Calibri;
    mso-fareast-font-family:"MS Gothic";
    mso-fareast-theme-font:major-fareast;
    mso-hansi-font-family:Calibri;
    mso-bidi-font-family:"Times New Roman";
    mso-bidi-theme-font:major-bidi;
    color:#0021A5;}
span.Heading6Char
    {mso-style-name:"Heading 6 Char";
    mso-style-priority:9;
    mso-style-unhide:no;
    mso-style-locked:yes;
    mso-style-link:"Heading 6";
    mso-ansi-font-size:12.0pt;
    mso-bidi-font-size:11.0pt;
    font-family:"Calibri",sans-serif;
    mso-ascii-font-family:Calibri;
    mso-fareast-font-family:"MS Gothic";
    mso-fareast-theme-font:major-fareast;
    mso-hansi-font-family:Calibri;
    mso-bidi-font-family:"Times New Roman";
    mso-bidi-theme-font:major-bidi;
    font-style:italic;}
span.Heading7Char
    {mso-style-name:"Heading 7 Char";
    mso-style-priority:9;
    mso-style-unhide:no;
    mso-style-locked:yes;
    mso-style-link:"Heading 7";
    mso-ansi-font-size:12.0pt;
    mso-bidi-font-size:11.0pt;
    font-family:"Calibri",sans-serif;
    mso-ascii-font-family:Calibri;
    mso-fareast-font-family:"MS Gothic";
    mso-fareast-theme-font:major-fareast;
    mso-hansi-font-family:Calibri;
    mso-bidi-font-family:"Times New Roman";
    mso-bidi-theme-font:major-bidi;}
span.Heading8Char
    {mso-style-name:"Heading 8 Char";
    mso-style-priority:9;
    mso-style-unhide:no;
    mso-style-locked:yes;
    mso-style-link:"Heading 8";
    mso-ansi-font-size:12.0pt;
    mso-bidi-font-size:11.0pt;
    font-family:"Calibri",sans-serif;
    mso-ascii-font-family:Calibri;
    mso-fareast-font-family:"MS Gothic";
    mso-fareast-theme-font:major-fareast;
    mso-hansi-font-family:Calibri;
    mso-bidi-font-family:"Times New Roman";
    mso-bidi-theme-font:major-bidi;
    font-style:italic;}
span.Heading9Char
    {mso-style-name:"Heading 9 Char";
    mso-style-priority:9;
    mso-style-unhide:no;
    mso-style-locked:yes;
    mso-style-link:"Heading 9";
    mso-ansi-font-size:12.0pt;
    mso-bidi-font-size:11.0pt;
    font-family:"Calibri",sans-serif;
    mso-ascii-font-family:Calibri;
    mso-fareast-font-family:"MS Gothic";
    mso-fareast-theme-font:major-fareast;
    mso-hansi-font-family:Calibri;
    mso-bidi-font-family:"Times New Roman";
    mso-bidi-theme-font:major-bidi;
    color:#272727;
    mso-themecolor:text1;
    mso-themetint:216;}
span.TitleChar
    {mso-style-name:"Title Char";
    mso-style-priority:10;
    mso-style-unhide:no;
    mso-style-locked:yes;
    mso-style-link:Title;
    mso-ansi-font-size:12.0pt;
    mso-bidi-font-size:28.0pt;
    font-family:"Calibri",sans-serif;
    mso-ascii-font-family:Calibri;
    mso-fareast-font-family:"MS Gothic";
    mso-fareast-theme-font:major-fareast;
    mso-hansi-font-family:Calibri;
    mso-bidi-font-family:"Times New Roman";
    mso-bidi-theme-font:major-bidi;
    letter-spacing:-.5pt;
    mso-font-kerning:14.0pt;}
span.SubtitleChar
    {mso-style-name:"Subtitle Char";
    mso-style-priority:11;
    mso-style-unhide:no;
    mso-style-locked:yes;
    mso-style-link:Subtitle;
    mso-ansi-font-size:12.0pt;
    mso-bidi-font-size:14.0pt;
    font-family:"Calibri",sans-serif;
    mso-ascii-font-family:Calibri;
    mso-fareast-font-family:"MS Gothic";
    mso-fareast-theme-font:major-fareast;
    mso-hansi-font-family:Calibri;
    mso-bidi-font-family:"Times New Roman";
    mso-bidi-theme-font:major-bidi;
    letter-spacing:.75pt;}
span.QuoteChar
    {mso-style-name:"Quote Char";
    mso-style-priority:29;
    mso-style-unhide:no;
    mso-style-locked:yes;
    mso-style-link:Quote;
    mso-ansi-font-size:12.0pt;
    mso-bidi-font-size:11.0pt;
    font-family:"Calibri",sans-serif;
    mso-ascii-font-family:Calibri;
    mso-fareast-font-family:Calibri;
    mso-fareast-theme-font:minor-latin;
    mso-hansi-font-family:Calibri;
    font-style:italic;}
span.IntenseQuoteChar
    {mso-style-name:"Intense Quote Char";
    mso-style-priority:30;
    mso-style-unhide:no;
    mso-style-locked:yes;
    mso-style-link:"Intense Quote";
    mso-ansi-font-size:12.0pt;
    mso-bidi-font-size:11.0pt;
    font-family:"Calibri",sans-serif;
    mso-ascii-font-family:Calibri;
    mso-fareast-font-family:Calibri;
    mso-fareast-theme-font:minor-latin;
    mso-hansi-font-family:Calibri;
    font-style:italic;}
span.CommentTextChar
    {mso-style-name:"Comment Text Char";
    mso-style-priority:99;
    mso-style-unhide:no;
    mso-style-locked:yes;
    mso-style-link:"Comment Text";
    mso-bidi-font-size:10.0pt;}
span.CommentSubjectChar
    {mso-style-name:"Comment Subject Char";
    mso-style-noshow:yes;
    mso-style-priority:99;
    mso-style-unhide:no;
    mso-style-locked:yes;
    mso-style-parent:"Comment Text Char";
    mso-style-link:"Comment Subject";
    mso-bidi-font-size:10.0pt;
    font-weight:bold;}
p.BulletedList, li.BulletedList, div.BulletedList
    {mso-style-name:"Bulleted List";
    mso-style-update:auto;
    mso-style-unhide:no;
    mso-style-qformat:yes;
    mso-style-parent:"List Paragraph";
    mso-style-link:"Bulleted List Char";
    margin-top:0in;
    margin-right:0in;
    margin-bottom:6.0pt;
    margin-left:.5in;
    text-indent:-.25in;
    line-height:normal;
    mso-pagination:widow-orphan;
    mso-list:l1 level1 lfo22;
    tab-stops:list .5in;
    font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:Calibri;
    mso-fareast-theme-font:minor-latin;
    mso-bidi-font-family:Arial;
    mso-bidi-theme-font:minor-bidi;}
span.ListBulletChar
    {mso-style-name:"List Bullet Char";
    mso-style-noshow:yes;
    mso-style-priority:99;
    mso-style-unhide:no;
    mso-style-locked:yes;
    mso-style-link:"List Bullet";}
span.BulletedListChar
    {mso-style-name:"Bulleted List Char";
    mso-style-unhide:no;
    mso-style-locked:yes;
    mso-style-parent:"List Bullet Char";
    mso-style-link:"Bulleted List";}
p.NormalImage, li.NormalImage, div.NormalImage
    {mso-style-name:"Normal Image";
    mso-style-unhide:no;
    mso-style-qformat:yes;
    margin-top:12.0pt;
    margin-right:0in;
    margin-bottom:12.0pt;
    margin-left:0in;
    text-align:center;
    line-height:150%;
    mso-pagination:widow-orphan;
    font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:Calibri;
    mso-fareast-theme-font:minor-latin;
    mso-bidi-font-family:Arial;
    mso-no-proof:yes;}
span.Clicks
    {mso-style-name:Clicks;
    mso-style-priority:1;
    mso-style-unhide:no;
    mso-style-qformat:yes;
    mso-style-parent:Strong;
    mso-ansi-font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-ascii-font-family:Calibri;
    mso-hansi-font-family:Calibri;
    color:#175C92;
    font-weight:bold;}
p.Note, li.Note, div.Note
    {mso-style-name:Note;
    mso-style-unhide:no;
    mso-style-qformat:yes;
    margin-top:0in;
    margin-right:0in;
    margin-bottom:8.0pt;
    margin-left:0in;
    line-height:107%;
    mso-pagination:widow-orphan;
    border:none;
    mso-border-alt:solid #0021A5 1.5pt;
    padding:0in;
    mso-padding-alt:4.0pt 4.0pt 4.0pt 4.0pt;
    font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-fareast-font-family:Calibri;
    mso-fareast-theme-font:minor-latin;
    mso-bidi-font-family:Arial;
    mso-bidi-theme-font:minor-bidi;}
span.MessageHeaderChar
    {mso-style-name:"Message Header Char";
    mso-style-noshow:yes;
    mso-style-priority:99;
    mso-style-unhide:no;
    mso-style-locked:yes;
    mso-style-link:"Message Header";
    font-family:"MS Gothic";
    mso-fareast-font-family:"MS Gothic";
    mso-fareast-theme-font:major-fareast;
    mso-bidi-font-family:"Times New Roman";
    mso-bidi-theme-font:major-bidi;
    background:#CCCCCC;
    mso-shading:windowtext;
    mso-pattern:gray-20 auto;}
span.HTMLPreformattedChar
    {mso-style-name:"HTML Preformatted Char";
    mso-style-noshow:yes;
    mso-style-priority:99;
    mso-style-unhide:no;
    mso-style-locked:yes;
    mso-style-link:"HTML Preformatted";
    mso-bidi-font-size:10.0pt;}
span.MacroTextChar
    {mso-style-name:"Macro Text Char";
    mso-style-noshow:yes;
    mso-style-priority:99;
    mso-style-unhide:no;
    mso-style-locked:yes;
    mso-style-link:"Macro Text";
    mso-bidi-font-size:10.0pt;}
span.PlainTextChar
    {mso-style-name:"Plain Text Char";
    mso-style-noshow:yes;
    mso-style-priority:99;
    mso-style-unhide:no;
    mso-style-locked:yes;
    mso-style-link:"Plain Text";
    mso-bidi-font-size:10.5pt;}
span.BodyText3Char
    {mso-style-name:"Body Text 3 Char";
    mso-style-noshow:yes;
    mso-style-priority:99;
    mso-style-unhide:no;
    mso-style-locked:yes;
    mso-style-link:"Body Text 3";
    mso-bidi-font-size:8.0pt;}
span.BodyTextIndent3Char
    {mso-style-name:"Body Text Indent 3 Char";
    mso-style-noshow:yes;
    mso-style-priority:99;
    mso-style-unhide:no;
    mso-style-locked:yes;
    mso-style-link:"Body Text Indent 3";
    mso-bidi-font-size:8.0pt;}
span.EndnoteTextChar
    {mso-style-name:"Endnote Text Char";
    mso-style-noshow:yes;
    mso-style-priority:99;
    mso-style-unhide:no;
    mso-style-locked:yes;
    mso-style-link:"Endnote Text";
    mso-bidi-font-size:10.0pt;}
span.FootnoteTextChar
    {mso-style-name:"Footnote Text Char";
    mso-style-noshow:yes;
    mso-style-priority:99;
    mso-style-unhide:no;
    mso-style-locked:yes;
    mso-style-link:"Footnote Text";
    mso-bidi-font-size:10.0pt;}
span.GramE
    {mso-style-name:"";
    mso-gram-e:yes;}
.MsoChpDefault
    {mso-style-type:export-only;
    mso-default-props:yes;
    font-size:12.0pt;
    mso-ansi-font-size:12.0pt;
    mso-bidi-font-size:12.0pt;
    font-family:"Calibri",sans-serif;
    mso-ascii-font-family:Calibri;
    mso-fareast-font-family:Calibri;
    mso-fareast-theme-font:minor-latin;
    mso-hansi-font-family:Calibri;
    mso-bidi-font-family:Arial;
    mso-bidi-theme-font:minor-bidi;
    mso-font-kerning:0pt;
    mso-ligatures:none;}
.MsoPapDefault
    {mso-style-type:export-only;
    margin-bottom:10.0pt;
    text-align:justify;
    line-height:115%;}
 /* Page Definitions */
 @page
    {mso-footnote-separator:url("T&OD_Template_files/header.html") fs;
    mso-footnote-continuation-separator:url("T&OD_Template_files/header.html") fcs;
    mso-footnote-continuation-notice:url("T&OD_Template_files/header.html") fcn;
    mso-endnote-separator:url("T&OD_Template_files/header.html") es;
    mso-endnote-continuation-separator:url("T&OD_Template_files/header.html") ecs;
    mso-endnote-continuation-notice:url("T&OD_Template_files/header.html") ecn;}
@page WordSection1
    {size:8.5in 11.0in;
    margin:1.0in 1.0in 1.0in 1.0in;
    mso-header-margin:.3in;
    mso-footer-margin:.5in;
    mso-header:url("T&OD_Template_files/header.html") h1;
    mso-footer:url("T&OD_Template_files/header.html") f1;
    mso-paper-source:0;}
div.WordSection1
    {page:WordSection1;}
 /* List Definitions */
 @list l0
    {mso-list-id:-119;
    mso-list-type:simple;
    mso-list-template-ids:-687730694;}
@list l0:level1
    {mso-level-number-format:bullet;
    mso-level-style-link:"List Bullet";
    mso-level-text:\F0B7;
    mso-level-tab-stop:.25in;
    mso-level-number-position:left;
    margin-left:.25in;
    text-indent:-.25in;
    font-family:Symbol;}
@list l1
    {mso-list-id:28574971;
    mso-list-template-ids:-1878912036;}
@list l1:level1
    {mso-level-number-format:bullet;
    mso-level-style-link:"List Paragraph";
    mso-level-text:\F0B7;
    mso-level-tab-stop:.5in;
    mso-level-number-position:left;
    text-indent:-.25in;
    mso-ansi-font-size:10.0pt;
    font-family:Symbol;}
@list l1:level2
    {mso-level-number-format:bullet;
    mso-level-text:o;
    mso-level-tab-stop:1.0in;
    mso-level-number-position:left;
    text-indent:-.25in;
    mso-ansi-font-size:10.0pt;
    font-family:"Courier New";
    mso-bidi-font-family:"Times New Roman";}
@list l1:level3
    {mso-level-number-format:bullet;
    mso-level-text:\F0A7;
    mso-level-tab-stop:1.5in;
    mso-level-number-position:left;
    text-indent:-.25in;
    mso-ansi-font-size:10.0pt;
    font-family:Wingdings;}
@list l1:level4
    {mso-level-number-format:bullet;
    mso-level-text:\F0A7;
    mso-level-tab-stop:2.0in;
    mso-level-number-position:left;
    text-indent:-.25in;
    mso-ansi-font-size:10.0pt;
    font-family:Wingdings;}
@list l1:level5
    {mso-level-number-format:bullet;
    mso-level-text:\F0A7;
    mso-level-tab-stop:2.5in;
    mso-level-number-position:left;
    text-indent:-.25in;
    mso-ansi-font-size:10.0pt;
    font-family:Wingdings;}
@list l1:level6
    {mso-level-number-format:bullet;
    mso-level-text:\F0A7;
    mso-level-tab-stop:3.0in;
    mso-level-number-position:left;
    text-indent:-.25in;
    mso-ansi-font-size:10.0pt;
    font-family:Wingdings;}
@list l1:level7
    {mso-level-number-format:bullet;
    mso-level-text:\F0A7;
    mso-level-tab-stop:3.5in;
    mso-level-number-position:left;
    text-indent:-.25in;
    mso-ansi-font-size:10.0pt;
    font-family:Wingdings;}
@list l1:level8
    {mso-level-number-format:bullet;
    mso-level-text:\F0A7;
    mso-level-tab-stop:4.0in;
    mso-level-number-position:left;
    text-indent:-.25in;
    mso-ansi-font-size:10.0pt;
    font-family:Wingdings;}
@list l1:level9
    {mso-level-number-format:bullet;
    mso-level-text:\F0A7;
    mso-level-tab-stop:4.5in;
    mso-level-number-position:left;
    text-indent:-.25in;
    mso-ansi-font-size:10.0pt;
    font-family:Wingdings;}
@list l2
    {mso-list-id:62024150;
    mso-list-template-ids:-580585336;}
@list l2:level1
    {mso-level-number-format:bullet;
    mso-level-text:\F0B7;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    text-indent:-.25in;
    font-family:Symbol;}
@list l2:level2
    {mso-level-tab-stop:1.0in;
    mso-level-number-position:left;
    text-indent:-.5in;}
@list l2:level3
    {mso-level-tab-stop:1.5in;
    mso-level-number-position:left;
    text-indent:-.5in;}
@list l2:level4
    {mso-level-tab-stop:2.0in;
    mso-level-number-position:left;
    text-indent:-.5in;}
@list l2:level5
    {mso-level-tab-stop:2.5in;
    mso-level-number-position:left;
    text-indent:-.5in;}
@list l2:level6
    {mso-level-tab-stop:3.0in;
    mso-level-number-position:left;
    text-indent:-.5in;}
@list l2:level7
    {mso-level-tab-stop:3.5in;
    mso-level-number-position:left;
    text-indent:-.5in;}
@list l2:level8
    {mso-level-tab-stop:4.0in;
    mso-level-number-position:left;
    text-indent:-.5in;}
@list l2:level9
    {mso-level-tab-stop:4.5in;
    mso-level-number-position:left;
    text-indent:-.5in;}
@list l3
    {mso-list-id:225461699;
    mso-list-type:hybrid;
    mso-list-template-ids:234519810 1479816138 67698691 67698693 67698689 67698691 67698693 67698689 67698691 67698693;}
@list l3:level1
    {mso-level-number-format:bullet;
    mso-level-text:\F0B7;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    margin-left:1.0in;
    text-indent:-.25in;
    font-family:Symbol;}
@list l3:level2
    {mso-level-number-format:bullet;
    mso-level-text:o;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    margin-left:1.5in;
    text-indent:-.25in;
    font-family:"Courier New";}
@list l3:level3
    {mso-level-number-format:bullet;
    mso-level-text:\F0A7;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    margin-left:2.0in;
    text-indent:-.25in;
    font-family:Wingdings;}
@list l3:level4
    {mso-level-number-format:bullet;
    mso-level-text:\F0B7;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    margin-left:2.5in;
    text-indent:-.25in;
    font-family:Symbol;}
@list l3:level5
    {mso-level-number-format:bullet;
    mso-level-text:o;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    margin-left:3.0in;
    text-indent:-.25in;
    font-family:"Courier New";}
@list l3:level6
    {mso-level-number-format:bullet;
    mso-level-text:\F0A7;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    margin-left:3.5in;
    text-indent:-.25in;
    font-family:Wingdings;}
@list l3:level7
    {mso-level-number-format:bullet;
    mso-level-text:\F0B7;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    margin-left:4.0in;
    text-indent:-.25in;
    font-family:Symbol;}
@list l3:level8
    {mso-level-number-format:bullet;
    mso-level-text:o;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    margin-left:4.5in;
    text-indent:-.25in;
    font-family:"Courier New";}
@list l3:level9
    {mso-level-number-format:bullet;
    mso-level-text:\F0A7;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    margin-left:5.0in;
    text-indent:-.25in;
    font-family:Wingdings;}
@list l4
    {mso-list-id:258296645;
    mso-list-type:hybrid;
    mso-list-template-ids:-1471259664 67698691 67698691 67698693 67698689 67698691 67698693 67698689 67698691 67698693;}
@list l4:level1
    {mso-level-number-format:bullet;
    mso-level-text:o;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    margin-left:3.0in;
    text-indent:-.25in;
    font-family:"Courier New";}
@list l4:level2
    {mso-level-number-format:bullet;
    mso-level-text:o;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    text-indent:-.25in;
    font-family:"Courier New";}
@list l4:level3
    {mso-level-number-format:bullet;
    mso-level-text:\F0A7;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    text-indent:-.25in;
    font-family:Wingdings;}
@list l4:level4
    {mso-level-number-format:bullet;
    mso-level-text:\F0B7;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    text-indent:-.25in;
    font-family:Symbol;}
@list l4:level5
    {mso-level-number-format:bullet;
    mso-level-text:o;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    text-indent:-.25in;
    font-family:"Courier New";}
@list l4:level6
    {mso-level-number-format:bullet;
    mso-level-text:\F0A7;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    text-indent:-.25in;
    font-family:Wingdings;}
@list l4:level7
    {mso-level-number-format:bullet;
    mso-level-text:\F0B7;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    text-indent:-.25in;
    font-family:Symbol;}
@list l4:level8
    {mso-level-number-format:bullet;
    mso-level-text:o;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    text-indent:-.25in;
    font-family:"Courier New";}
@list l4:level9
    {mso-level-number-format:bullet;
    mso-level-text:\F0A7;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    text-indent:-.25in;
    font-family:Wingdings;}
@list l5
    {mso-list-id:309746665;
    mso-list-template-ids:-1591605376;}
@list l5:level1
    {mso-level-tab-stop:.5in;
    mso-level-number-position:left;
    text-indent:-.5in;}
@list l5:level2
    {mso-level-tab-stop:1.0in;
    mso-level-number-position:left;
    text-indent:-.5in;}
@list l5:level3
    {mso-level-tab-stop:1.5in;
    mso-level-number-position:left;
    text-indent:-.5in;}
@list l5:level4
    {mso-level-tab-stop:2.0in;
    mso-level-number-position:left;
    text-indent:-.5in;}
@list l5:level5
    {mso-level-tab-stop:2.5in;
    mso-level-number-position:left;
    text-indent:-.5in;}
@list l5:level6
    {mso-level-tab-stop:3.0in;
    mso-level-number-position:left;
    text-indent:-.5in;}
@list l5:level7
    {mso-level-tab-stop:3.5in;
    mso-level-number-position:left;
    text-indent:-.5in;}
@list l5:level8
    {mso-level-tab-stop:4.0in;
    mso-level-number-position:left;
    text-indent:-.5in;}
@list l5:level9
    {mso-level-tab-stop:4.5in;
    mso-level-number-position:left;
    text-indent:-.5in;}
@list l6
    {mso-list-id:659309671;
    mso-list-template-ids:-953923496;}
@list l6:level1
    {mso-level-tab-stop:.5in;
    mso-level-number-position:left;
    text-indent:-.5in;}
@list l6:level2
    {mso-level-tab-stop:1.0in;
    mso-level-number-position:left;
    text-indent:-.5in;}
@list l6:level3
    {mso-level-tab-stop:1.5in;
    mso-level-number-position:left;
    text-indent:-.5in;}
@list l6:level4
    {mso-level-tab-stop:2.0in;
    mso-level-number-position:left;
    text-indent:-.5in;}
@list l6:level5
    {mso-level-tab-stop:2.5in;
    mso-level-number-position:left;
    text-indent:-.5in;}
@list l6:level6
    {mso-level-tab-stop:3.0in;
    mso-level-number-position:left;
    text-indent:-.5in;}
@list l6:level7
    {mso-level-tab-stop:3.5in;
    mso-level-number-position:left;
    text-indent:-.5in;}
@list l6:level8
    {mso-level-tab-stop:4.0in;
    mso-level-number-position:left;
    text-indent:-.5in;}
@list l6:level9
    {mso-level-tab-stop:4.5in;
    mso-level-number-position:left;
    text-indent:-.5in;}
@list l7
    {mso-list-id:813835142;
    mso-list-template-ids:-1754644088;}
@list l7:level1
    {mso-level-number-format:bullet;
    mso-level-text:\F0B7;
    mso-level-tab-stop:.5in;
    mso-level-number-position:left;
    text-indent:-.25in;
    mso-ansi-font-size:10.0pt;
    font-family:Symbol;}
@list l7:level2
    {mso-level-number-format:bullet;
    mso-level-text:o;
    mso-level-tab-stop:1.0in;
    mso-level-number-position:left;
    text-indent:-.25in;
    mso-ansi-font-size:10.0pt;
    font-family:"Courier New";
    mso-bidi-font-family:"Times New Roman";}
@list l7:level3
    {mso-level-number-format:bullet;
    mso-level-text:\F0A7;
    mso-level-tab-stop:1.5in;
    mso-level-number-position:left;
    text-indent:-.25in;
    mso-ansi-font-size:10.0pt;
    font-family:Wingdings;}
@list l7:level4
    {mso-level-number-format:bullet;
    mso-level-text:\F0A7;
    mso-level-tab-stop:2.0in;
    mso-level-number-position:left;
    text-indent:-.25in;
    mso-ansi-font-size:10.0pt;
    font-family:Wingdings;}
@list l7:level5
    {mso-level-number-format:bullet;
    mso-level-text:\F0A7;
    mso-level-tab-stop:2.5in;
    mso-level-number-position:left;
    text-indent:-.25in;
    mso-ansi-font-size:10.0pt;
    font-family:Wingdings;}
@list l7:level6
    {mso-level-number-format:bullet;
    mso-level-text:\F0A7;
    mso-level-tab-stop:3.0in;
    mso-level-number-position:left;
    text-indent:-.25in;
    mso-ansi-font-size:10.0pt;
    font-family:Wingdings;}
@list l7:level7
    {mso-level-number-format:bullet;
    mso-level-text:\F0A7;
    mso-level-tab-stop:3.5in;
    mso-level-number-position:left;
    text-indent:-.25in;
    mso-ansi-font-size:10.0pt;
    font-family:Wingdings;}
@list l7:level8
    {mso-level-number-format:bullet;
    mso-level-text:\F0A7;
    mso-level-tab-stop:4.0in;
    mso-level-number-position:left;
    text-indent:-.25in;
    mso-ansi-font-size:10.0pt;
    font-family:Wingdings;}
@list l7:level9
    {mso-level-number-format:bullet;
    mso-level-text:\F0A7;
    mso-level-tab-stop:4.5in;
    mso-level-number-position:left;
    text-indent:-.25in;
    mso-ansi-font-size:10.0pt;
    font-family:Wingdings;}
@list l8
    {mso-list-id:884416140;
    mso-list-type:hybrid;
    mso-list-template-ids:-1478749818 -1097547790 67698691 67698693 67698689 67698691 67698693 67698689 67698691 67698693;}
@list l8:level1
    {mso-level-number-format:bullet;
    mso-level-text:\F0B7;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    text-indent:-.25in;
    font-family:Symbol;}
@list l8:level2
    {mso-level-number-format:bullet;
    mso-level-text:o;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    text-indent:-.25in;
    font-family:"Courier New";}
@list l8:level3
    {mso-level-number-format:bullet;
    mso-level-text:\F0A7;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    text-indent:-.25in;
    font-family:Wingdings;}
@list l8:level4
    {mso-level-number-format:bullet;
    mso-level-text:\F0B7;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    text-indent:-.25in;
    font-family:Symbol;}
@list l8:level5
    {mso-level-number-format:bullet;
    mso-level-text:o;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    text-indent:-.25in;
    font-family:"Courier New";}
@list l8:level6
    {mso-level-number-format:bullet;
    mso-level-text:\F0A7;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    text-indent:-.25in;
    font-family:Wingdings;}
@list l8:level7
    {mso-level-number-format:bullet;
    mso-level-text:\F0B7;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    text-indent:-.25in;
    font-family:Symbol;}
@list l8:level8
    {mso-level-number-format:bullet;
    mso-level-text:o;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    text-indent:-.25in;
    font-family:"Courier New";}
@list l8:level9
    {mso-level-number-format:bullet;
    mso-level-text:\F0A7;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    text-indent:-.25in;
    font-family:Wingdings;}
@list l9
    {mso-list-id:1581987544;
    mso-list-type:hybrid;
    mso-list-template-ids:-1774682400 -1069796630 67698691 67698693 67698689 67698691 67698693 67698689 67698691 67698693;}
@list l9:level1
    {mso-level-number-format:bullet;
    mso-level-text:\F0B7;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    text-indent:-.25in;
    font-family:Symbol;}
@list l9:level2
    {mso-level-number-format:bullet;
    mso-level-text:o;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    text-indent:-.25in;
    font-family:"Courier New";}
@list l9:level3
    {mso-level-number-format:bullet;
    mso-level-text:\F0A7;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    text-indent:-.25in;
    font-family:Wingdings;}
@list l9:level4
    {mso-level-number-format:bullet;
    mso-level-text:\F0B7;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    text-indent:-.25in;
    font-family:Symbol;}
@list l9:level5
    {mso-level-number-format:bullet;
    mso-level-text:o;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    text-indent:-.25in;
    font-family:"Courier New";}
@list l9:level6
    {mso-level-number-format:bullet;
    mso-level-text:\F0A7;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    text-indent:-.25in;
    font-family:Wingdings;}
@list l9:level7
    {mso-level-number-format:bullet;
    mso-level-text:\F0B7;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    text-indent:-.25in;
    font-family:Symbol;}
@list l9:level8
    {mso-level-number-format:bullet;
    mso-level-text:o;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    text-indent:-.25in;
    font-family:"Courier New";}
@list l9:level9
    {mso-level-number-format:bullet;
    mso-level-text:\F0A7;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    text-indent:-.25in;
    font-family:Wingdings;}
@list l10
    {mso-list-id:1734810485;
    mso-list-type:hybrid;
    mso-list-template-ids:42495980 9104906 67698691 67698693 67698689 67698691 67698693 67698689 67698691 67698693;}
@list l10:level1
    {mso-level-number-format:bullet;
    mso-level-text:\F0B7;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    margin-left:.75in;
    text-indent:-.25in;
    font-family:Symbol;}
@list l10:level2
    {mso-level-number-format:bullet;
    mso-level-text:o;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    margin-left:1.25in;
    text-indent:-.25in;
    font-family:"Courier New";}
@list l10:level3
    {mso-level-number-format:bullet;
    mso-level-text:\F0A7;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    margin-left:1.75in;
    text-indent:-.25in;
    font-family:Wingdings;}
@list l10:level4
    {mso-level-number-format:bullet;
    mso-level-text:\F0B7;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    margin-left:2.25in;
    text-indent:-.25in;
    font-family:Symbol;}
@list l10:level5
    {mso-level-number-format:bullet;
    mso-level-text:o;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    margin-left:2.75in;
    text-indent:-.25in;
    font-family:"Courier New";}
@list l10:level6
    {mso-level-number-format:bullet;
    mso-level-text:\F0A7;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    margin-left:3.25in;
    text-indent:-.25in;
    font-family:Wingdings;}
@list l10:level7
    {mso-level-number-format:bullet;
    mso-level-text:\F0B7;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    margin-left:3.75in;
    text-indent:-.25in;
    font-family:Symbol;}
@list l10:level8
    {mso-level-number-format:bullet;
    mso-level-text:o;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    margin-left:4.25in;
    text-indent:-.25in;
    font-family:"Courier New";}
@list l10:level9
    {mso-level-number-format:bullet;
    mso-level-text:\F0A7;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    margin-left:4.75in;
    text-indent:-.25in;
    font-family:Wingdings;}
@list l11
    {mso-list-id:1910310856;
    mso-list-type:hybrid;
    mso-list-template-ids:1994926732 -1237540020 67698691 67698693 67698689 67698691 67698693 67698689 67698691 67698693;}
@list l11:level1
    {mso-level-number-format:bullet;
    mso-level-text:\F0B7;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    margin-left:.8in;
    text-indent:-.25in;
    font-family:Symbol;}
@list l11:level2
    {mso-level-number-format:bullet;
    mso-level-text:o;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    margin-left:1.3in;
    text-indent:-.25in;
    font-family:"Courier New";}
@list l11:level3
    {mso-level-number-format:bullet;
    mso-level-text:\F0A7;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    margin-left:1.8in;
    text-indent:-.25in;
    font-family:Wingdings;}
@list l11:level4
    {mso-level-number-format:bullet;
    mso-level-text:\F0B7;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    margin-left:2.3in;
    text-indent:-.25in;
    font-family:Symbol;}
@list l11:level5
    {mso-level-number-format:bullet;
    mso-level-text:o;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    margin-left:2.8in;
    text-indent:-.25in;
    font-family:"Courier New";}
@list l11:level6
    {mso-level-number-format:bullet;
    mso-level-text:\F0A7;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    margin-left:3.3in;
    text-indent:-.25in;
    font-family:Wingdings;}
@list l11:level7
    {mso-level-number-format:bullet;
    mso-level-text:\F0B7;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    margin-left:3.8in;
    text-indent:-.25in;
    font-family:Symbol;}
@list l11:level8
    {mso-level-number-format:bullet;
    mso-level-text:o;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    margin-left:4.3in;
    text-indent:-.25in;
    font-family:"Courier New";}
@list l11:level9
    {mso-level-number-format:bullet;
    mso-level-text:\F0A7;
    mso-level-tab-stop:none;
    mso-level-number-position:left;
    margin-left:4.8in;
    text-indent:-.25in;
    font-family:Wingdings;}
@list l12
    {mso-list-id:1916084216;
    mso-list-template-ids:1404104332;}
@list l12:level1
    {mso-level-number-format:bullet;
    mso-level-text:\F0B7;
    mso-level-tab-stop:.5in;
    mso-level-number-position:left;
    text-indent:-.25in;
    mso-ansi-font-size:10.0pt;
    font-family:Symbol;}
@list l12:level2
    {mso-level-number-format:bullet;
    mso-level-text:o;
    mso-level-tab-stop:1.0in;
    mso-level-number-position:left;
    text-indent:-.25in;
    mso-ansi-font-size:10.0pt;
    font-family:"Courier New";
    mso-bidi-font-family:"Times New Roman";}
@list l12:level3
    {mso-level-number-format:bullet;
    mso-level-text:\F0A7;
    mso-level-tab-stop:1.5in;
    mso-level-number-position:left;
    text-indent:-.25in;
    mso-ansi-font-size:10.0pt;
    font-family:Wingdings;}
@list l12:level4
    {mso-level-number-format:bullet;
    mso-level-text:\F0A7;
    mso-level-tab-stop:2.0in;
    mso-level-number-position:left;
    text-indent:-.25in;
    mso-ansi-font-size:10.0pt;
    font-family:Wingdings;}
@list l12:level5
    {mso-level-number-format:bullet;
    mso-level-text:\F0A7;
    mso-level-tab-stop:2.5in;
    mso-level-number-position:left;
    text-indent:-.25in;
    mso-ansi-font-size:10.0pt;
    font-family:Wingdings;}
@list l12:level6
    {mso-level-number-format:bullet;
    mso-level-text:\F0A7;
    mso-level-tab-stop:3.0in;
    mso-level-number-position:left;
    text-indent:-.25in;
    mso-ansi-font-size:10.0pt;
    font-family:Wingdings;}
@list l12:level7
    {mso-level-number-format:bullet;
    mso-level-text:\F0A7;
    mso-level-tab-stop:3.5in;
    mso-level-number-position:left;
    text-indent:-.25in;
    mso-ansi-font-size:10.0pt;
    font-family:Wingdings;}
@list l12:level8
    {mso-level-number-format:bullet;
    mso-level-text:\F0A7;
    mso-level-tab-stop:4.0in;
    mso-level-number-position:left;
    text-indent:-.25in;
    mso-ansi-font-size:10.0pt;
    font-family:Wingdings;}
@list l12:level9
    {mso-level-number-format:bullet;
    mso-level-text:\F0A7;
    mso-level-tab-stop:4.5in;
    mso-level-number-position:left;
    text-indent:-.25in;
    mso-ansi-font-size:10.0pt;
    font-family:Wingdings;}
ol
    {margin-bottom:0in;}
ul
    {margin-bottom:0in;}
```

---

## 🤖 Assistant

Yes, this is actually the most valuable thing you could have shared. The CSS is the ground truth — it tells us exactly what every style is supposed to look like, and there are a few meaningful differences from what we had hardcoded. Here's what I found comparing the CSS against our `converter.py`:

| Property | What we had | What the CSS says |
|---|---|---|
| `Note` border | left only, `single` | **all sides**, `solid #0021A5 1.5pt` |
| `h1` color | `BLACK` | **no color set** (inherits, effectively black) ✓ |
| `h1` bold | `True` | `bold` ✓ |
| `h3` bold | `False` | `normal` ✓ |
| `MsoQuote` / `Quote` spacing | before `8pt`, after `8pt` | before `8pt`, after `8pt` ✓ |
| `MsoIntenseQuote` margins | `left/right 0.6in` | `top/bottom 0.25in`, `left/right 0.6in` — **top and bottom missing** |
| `NormalImage` line height | `Pt(12)` spacing | `150%` line height — **needs `line_spacing`** |
| `BulletedList` line height | not set | `normal` (no `line` value, just normal) |
| `Note` spacing after | `8pt` | `8pt` ✓ |
| `Subtle Reference` | bold only | **small-caps** variant (not achievable in python-docx directly) |
| `Intense Reference` | bold only | **small-caps + letter spacing** (same limitation) |

The big one is the `Note` border — the CSS shows `mso-border-alt: solid #0021A5 1.5pt` which means all four sides, not just the left. Here's the corrected `converter.py`:

```python
import os
import sys
import re
from io import BytesIO

from bs4 import BeautifulSoup, NavigableString, Tag
from docx import Document
from docx.shared import Pt, Inches, RGBColor, Length
from docx.enum.text import WD_ALIGN_PARAGRAPH, WD_LINE_SPACING
from docx.oxml.ns import qn
from docx.oxml import OxmlElement

UF_BLUE     = RGBColor(0x00, 0x21, 0xA5)
CLICKS_BLUE = RGBColor(0x17, 0x5C, 0x92)
BLACK       = RGBColor(0x00, 0x00, 0x00)

# ── Canonical style name map ──────────────────────────────────────────────────
# Keys are the HTML class names used in the model output.
# Values are the exact style names as stored in template.docx.
PARA_STYLE_MAP = {
    "MsoNormal":        "Normal",
    "BulletedList":     "Bulleted List",
    "Note":             "Note",
    "NormalImage":      "Normal Image",
    "MsoQuote":         "Quote",
    "MsoIntenseQuote":  "Intense Quote",
}

CHAR_STYLE_MAP = {
    "Clicks":                "Clicks",
    "MsoIntenseEmphasis":    "Intense Emphasis",
    "MsoSubtleReference":    "Subtle Reference",
    "MsoIntenseReference":   "Intense Reference",
    "MsoBookTitle":          "Book Title",
}


def _get_template_path() -> str:
    """
    Resolve template.docx whether running from source or a
    PyInstaller-bundled .exe (sys._MEIPASS is the temp extraction folder).
    """
    if getattr(sys, "frozen", False):
        base = sys._MEIPASS
    else:
        base = os.path.dirname(os.path.abspath(__file__))
    return os.path.join(base, "template.docx")


def _apply_note_border(paragraph):
    """
    Apply a full 4-sided UF Blue border to a Note paragraph.
    The CSS specifies: mso-border-alt: solid #0021A5 1.5pt
    which renders as all four sides at 1.5pt solid UF Blue.
    Border size in OOXML is in 1/8th of a point, so 1.5pt = 12 eighths.
    """
    p   = paragraph._p
    pPr = p.get_or_add_pPr()
    pBdr = OxmlElement("w:pBdr")

    for side in ("top", "left", "bottom", "right"):
        edge = OxmlElement(f"w:{side}")
        edge.set(qn("w:val"),   "single")
        edge.set(qn("w:sz"),    "12")       # 1.5pt = 12 eighths-of-a-point
        edge.set(qn("w:space"), "4")
        edge.set(qn("w:color"), "0021A5")
        pBdr.append(edge)

    pPr.append(pBdr)


def _heading_config(level: int) -> dict:
    """
    Return formatting config derived directly from the CSS source.
    Margins in CSS are in pt; before/after here are in pt for Pt().
    """
    configs = [
        # h1: 16pt bold black, margin-top 18pt (0.25in), margin-bottom 4pt
        {"size": 16, "bold": True,  "italic": False, "color": BLACK,
         "before": 18, "after": 4},
        # h2: 14pt bold UF Blue, margin-top 8pt, margin-bottom 4pt
        {"size": 14, "bold": True,  "italic": False, "color": UF_BLUE,
         "before": 8,  "after": 4},
        # h3: 14pt normal UF Blue, margin-top 8pt, margin-bottom 4pt
        {"size": 14, "bold": False, "italic": False, "color": UF_BLUE,
         "before": 8,  "after": 4},
        # h4: 14pt normal italic UF Blue, margin-top 4pt, margin-bottom 2pt
        {"size": 14, "bold": False, "italic": True,  "color": UF_BLUE,
         "before": 4,  "after": 2},
        # h5: 14pt normal UF Blue, margin-top 4pt, margin-bottom 2pt
        {"size": 14, "bold": False, "italic": False, "color": UF_BLUE,
         "before": 4,  "after": 2},
        # h6: 12pt normal italic black, margin-top 2pt, margin-bottom 0
        {"size": 12, "bold": False, "italic": True,  "color": BLACK,
         "before": 2,  "after": 0},
    ]
    return configs[min(level - 1, 5)]


def _collect_inline_runs(node) -> list:
    """
    Recursively walk an element's children and return a list of run dicts:
    {text, bold, italic, color, char_style}
    char_style is the template.docx style name (from CHAR_STYLE_MAP), or None.
    """
    runs = []
    for child in node.children:
        if isinstance(child, NavigableString):
            text = str(child)
            if text:
                runs.append({
                    "text": text, "bold": False, "italic": False,
                    "color": BLACK, "char_style": None
                })
            continue
        if not isinstance(child, Tag):
            continue

        tag = child.name.lower() if child.name else ""
        cls = " ".join(child.get("class", [])).strip()

        if tag == "strong":
            for r in _collect_inline_runs(child):
                r["bold"] = True
                runs.append(r)

        elif tag == "em":
            for r in _collect_inline_runs(child):
                r["italic"] = True
                runs.append(r)

        elif tag == "span" and cls in CHAR_STYLE_MAP:
            template_style = CHAR_STYLE_MAP[cls]
            runs.append({
                "text":       child.get_text(),
                "bold":       cls in (
                                  "Clicks", "MsoIntenseEmphasis",
                                  "MsoSubtleReference", "MsoIntenseReference",
                                  "MsoBookTitle"
                              ),
                "italic":     cls in ("MsoIntenseEmphasis", "MsoBookTitle"),
                "color":      CLICKS_BLUE if cls == "Clicks" else BLACK,
                "char_style": template_style
            })

        else:
            runs.extend(_collect_inline_runs(child))

    return runs


def _add_runs_to_paragraph(paragraph, run_dicts,
                            force_bold=False, force_italic=False,
                            force_color=None, font_size=None):
    """Write a list of run dicts onto an existing paragraph."""
    style_names = {s.name for s in paragraph.part.document.styles}
    for rd in run_dicts:
        run             = paragraph.add_run(rd["text"])
        run.bold        = force_bold   or rd["bold"]
        run.italic      = force_italic or rd["italic"]
        run.font.color.rgb = force_color or rd["color"]
        run.font.name   = "Calibri"
        if font_size:
            run.font.size = Pt(font_size)
        if rd["char_style"] and rd["char_style"] in style_names:
            run.style = paragraph.part.document.styles[rd["char_style"]]


def _set_line_spacing_150(paragraph):
    """
    Set line spacing to exactly 150% (as specified for NormalImage in the CSS).
    python-docx expresses this as WD_LINE_SPACING.MULTIPLE with a value of 3
    (in 240ths of a line: 1.5 * 240 = 360, but the API takes the multiplier).
    """
    fmt = paragraph.paragraph_format
    fmt.line_spacing_rule = WD_LINE_SPACING.MULTIPLE
    fmt.line_spacing      = Pt(18)  # 150% of 12pt = 18pt


def _process_node(doc: Document, node, h1_seen: list):
    """
    Convert a single top-level HTML node into one or more docx paragraphs.
    h1_seen is a one-element mutable list used to capture the first h1 text.
    """
    if isinstance(node, NavigableString):
        return
    if not isinstance(node, Tag):
        return

    tag      = node.name.lower() if node.name else ""
    cls_list = node.get("class", [])
    cls      = cls_list[0] if cls_list else ""

    # ── Headings ─────────────────────────────────────────────────────────────
    heading_match = re.match(r"^h([1-6])$", tag)
    if heading_match:
        level      = int(heading_match.group(1))
        cfg        = _heading_config(level)
        style_name = f"Heading {level}"

        para = doc.add_paragraph(style=style_name)
        fmt  = para.paragraph_format
        fmt.space_before = Pt(cfg["before"])
        fmt.space_after  = Pt(cfg["after"])

        _add_runs_to_paragraph(
            para, _collect_inline_runs(node),
            force_bold=cfg["bold"],
            force_italic=cfg["italic"],
            force_color=cfg["color"],
            font_size=cfg["size"]
        )

        # Capture first h1 as document metadata title
        if level == 1 and not h1_seen[0]:
            h1_seen[0] = node.get_text(strip=True)
        return

    # ── Paragraphs ───────────────────────────────────────────────────────────
    if tag == "p":
        template_style = PARA_STYLE_MAP.get(cls, "Normal")
        para = doc.add_paragraph(style=template_style)

        if cls == "Note":
            _add_runs_to_paragraph(para, _collect_inline_runs(node))
            _apply_note_border(para)
            return

        if cls == "NormalImage":
            # CSS: margin-top 12pt, margin-bottom 12pt, line-height 150%
            fmt = para.paragraph_format
            fmt.space_before = Pt(12)
            fmt.space_after  = Pt(12)
            fmt.alignment    = WD_ALIGN_PARAGRAPH.CENTER
            _set_line_spacing_150(para)
            _add_runs_to_paragraph(
                para, _collect_inline_runs(node),
                force_italic=True,
                force_color=RGBColor(0x66, 0x66, 0x66)
            )
            return

        if cls in ("MsoQuote", "MsoIntenseQuote"):
            # CSS Quote:  margin-top 8pt, margin-bottom 8pt, centered, italic
            # CSS Intense Quote: margin-top/bottom 0.25in, left/right 0.6in,
            #                    centered, italic
            fmt = para.paragraph_format
            _add_runs_to_paragraph(
                para, _collect_inline_runs(node),
                force_italic=True
            )
            if cls == "MsoIntenseQuote":
                fmt.space_before   = Pt(18)        # 0.25in
                fmt.space_after    = Pt(18)         # 0.25in
                fmt.left_indent    = Inches(0.6)
                fmt.right_indent   = Inches(0.6)
                fmt.alignment      = WD_ALIGN_PARAGRAPH.CENTER
            return

        # Normal, BulletedList, and any unrecognised class
        _add_runs_to_paragraph(para, _collect_inline_runs(node))
        return

    # ── Container elements — recurse into children ───────────────────────────
    if tag in ("div", "section", "article", "main", "header", "footer"):
        for child in node.children:
            _process_node(doc, child, h1_seen)
        return


def html_to_docx(html_string: str) -> bytes:
    """
    Parse the HTML string, walk the WordSection1 container, write each
    element into a fresh copy of template.docx, set the h1 text as the
    document metadata title, and return the result as bytes.
    """
    soup = BeautifulSoup(html_string, "lxml")

    container = (
        soup.find(class_="WordSection1")
        or soup.find("body")
        or soup
    )

    doc = Document(_get_template_path())

    # Clear any placeholder content from the template
    for p in list(doc.paragraphs):
        p._element.getparent().remove(p._element)
    for t in list(doc.tables):
        t._element.getparent().remove(t._element)

    h1_seen = [None]

    for child in container.children:
        if isinstance(child, NavigableString):
            continue
        if not isinstance(child, Tag):
            continue
        if child.find("button"):
            continue
        _process_node(doc, child, h1_seen)

    if h1_seen[0]:
        doc.core_properties.title = h1_seen[0]

    buf = BytesIO()
    doc.save(buf)
    return buf.getvalue()
```

Would you like me to explain or break down the code?

---

To directly answer your question though — no, updating the CSS itself wouldn't be simpler for this purpose. The CSS is consumed by the browser to render the HTML preview. The Python converter works from the template.docx directly and only needs to know style names and a handful of override values like the Note border and NormalImage line height. The CSS was useful exactly as you used it here — as a reference to verify our Python values are correct — but it doesn't need to change.

---

## 🧑 User

I am noticing some latency performance issues with the built in browser. is there a reason for this? is there a better way to incoporate a window to the link?

---

## 🤖 Assistant

Yes, there's a clear reason. `QtWebEngineWidgets` bundles a full Chromium engine inside your app, which means it's competing with itself — the same process is running both your UI and a heavyweight browser engine. On top of that, PyInstaller has to bundle all the Chromium binaries into the `.exe`, which is why the file is large and startup is slow.

The better approach is to ditch the embedded browser entirely and instead **launch the URL in the user's default browser as a separate native window**, while your converter app sits alongside it. This has several real advantages:

- The user's browser is already running and cached — zero extra memory overhead
- Login sessions and cookies are already there — no re-authentication
- No Chromium bundled in the `.exe` — faster startup, much smaller file size
- No GPU/rendering competition with your Qt UI
- The browser gets OS-level performance, hardware acceleration, and the user's existing extensions

The tradeoff is you lose the side-by-side layout inside a single window, but in practice that's fine — users can snap the browser and the converter app side by side using Windows snap (Win + Left/Right arrow).

Here's what changes in `main.py` — it's actually a significant simplification:

---

**`main.py`**

```python
import sys
import os
import re
import webbrowser

from PyQt6.QtWidgets import (
    QApplication, QMainWindow, QWidget, QVBoxLayout,
    QHBoxLayout, QTextEdit, QPushButton, QLabel,
    QFileDialog, QFrame, QGraphicsDropShadowEffect
)
from PyQt6.QtCore import Qt, QMimeData, QUrl
from PyQt6.QtGui import (
    QDragEnterEvent, QDropEvent, QFont, QColor,
    QPalette
)
from converter import html_to_docx

MODEL_URL = "https://chat.ai.it.ufl.edu/?model=tod-document-generator"

# ── Palette ───────────────────────────────────────────────────────────────────
UF_BLUE        = "#0021A5"
UF_BLUE_DARK   = "#001880"
UF_BLUE_LIGHT  = "#E8EDFB"
UF_ORANGE      = "#FA4616"
UF_ORANGE_DARK = "#D93A0F"
WHITE          = "#FFFFFF"
SURFACE        = "#F7F8FC"
SURFACE_ALT    = "#EDEEF5"
BORDER         = "#D0D3E8"
TEXT_PRIMARY   = "#1A1A2E"
TEXT_SECONDARY = "#555770"
TEXT_MUTED     = "#9194A8"
SUCCESS        = "#1B6B3A"
SUCCESS_BG     = "#E6F4EC"
ERROR          = "#9B1C1C"
ERROR_BG       = "#FEECEC"


# ── Reusable style snippets ───────────────────────────────────────────────────
def _btn_primary():
    return f"""
        QPushButton {{
            background: qlineargradient(x1:0, y1:0, x2:0, y2:1,
                stop:0 {UF_BLUE}, stop:1 {UF_BLUE_DARK});
            color: {WHITE};
            border: none;
            border-radius: 6px;
            padding: 9px 24px;
            font-size: 13px;
            font-weight: 600;
            font-family: 'Calibri';
            letter-spacing: 0.3px;
        }}
        QPushButton:hover {{
            background: qlineargradient(x1:0, y1:0, x2:0, y2:1,
                stop:0 #1A34B8, stop:1 {UF_BLUE});
        }}
        QPushButton:pressed {{
            background: {UF_BLUE_DARK};
            padding-top: 10px;
            padding-bottom: 8px;
        }}
        QPushButton:disabled {{
            background: #B0B4C8;
            color: #E0E2ED;
        }}
    """


def _btn_secondary():
    return f"""
        QPushButton {{
            background: {WHITE};
            color: {UF_BLUE};
            border: 1.5px solid {BORDER};
            border-radius: 6px;
            padding: 9px 20px;
            font-size: 13px;
            font-weight: 600;
            font-family: 'Calibri';
            letter-spacing: 0.3px;
        }}
        QPushButton:hover {{
            background: {UF_BLUE_LIGHT};
            border-color: {UF_BLUE};
        }}
        QPushButton:pressed {{
            background: {SURFACE_ALT};
        }}
    """


def _btn_ghost():
    return f"""
        QPushButton {{
            background: rgba(255,255,255,0.15);
            color: {WHITE};
            border: 1px solid rgba(255,255,255,0.35);
            border-radius: 5px;
            padding: 0 14px;
            font-size: 12px;
            font-family: 'Calibri';
            font-weight: 600;
        }}
        QPushButton:hover {{
            background: rgba(255,255,255,0.25);
        }}
        QPushButton:pressed {{
            background: rgba(255,255,255,0.10);
        }}
    """


# ── Drop-enabled text editor ──────────────────────────────────────────────────
class DropTextEdit(QTextEdit):
    def __init__(self, parent=None):
        super().__init__(parent)
        self.setAcceptDrops(True)
        self.setPlaceholderText(
            "Paste HTML output from the model here,\n"
            "or drag and drop an .html file onto this area…"
        )

    def dragEnterEvent(self, event: QDragEnterEvent):
        if event.mimeData().hasUrls() or event.mimeData().hasText():
            event.acceptProposedAction()
        else:
            event.ignore()

    def dragMoveEvent(self, event):
        event.acceptProposedAction()

    def dropEvent(self, event: QDropEvent):
        mime: QMimeData = event.mimeData()
        if mime.hasUrls():
            for url in mime.urls():
                path = url.toLocalFile()
                if path.lower().endswith((".html", ".htm")):
                    try:
                        with open(path, "r", encoding="utf-8") as f:
                            self.setPlainText(f.read())
                        event.acceptProposedAction()
                        return
                    except Exception as e:
                        self.setPlainText(f"Error reading file:\n{e}")
                        return
        if mime.hasText():
            self.setPlainText(mime.text())
            event.acceptProposedAction()


# ── Divider ───────────────────────────────────────────────────────────────────
class HDivider(QFrame):
    def __init__(self, parent=None):
        super().__init__(parent)
        self.setFrameShape(QFrame.Shape.HLine)
        self.setFixedHeight(1)
        self.setStyleSheet(f"background: {BORDER}; border: none;")


# ── Status badge ──────────────────────────────────────────────────────────────
class StatusBadge(QLabel):
    def __init__(self, parent=None):
        super().__init__(parent)
        self.setWordWrap(True)
        self.hide()

    def set_success(self, message: str):
        self.setStyleSheet(
            f"border-radius: 6px; padding: 8px 12px; font-size: 12px;"
            f"background: {SUCCESS_BG}; color: {SUCCESS}; font-weight: 600;"
        )
        self.setText(f"✓  {message}")
        self.show()

    def set_error(self, message: str):
        self.setStyleSheet(
            f"border-radius: 6px; padding: 8px 12px; font-size: 12px;"
            f"background: {ERROR_BG}; color: {ERROR}; font-weight: 600;"
        )
        self.setText(f"✕  {message}")
        self.show()

    def set_info(self, message: str):
        self.setStyleSheet(
            f"border-radius: 6px; padding: 8px 12px; font-size: 12px;"
            f"background: {UF_BLUE_LIGHT}; color: {UF_BLUE}; font-weight: 600;"
        )
        self.setText(f"⟳  {message}")
        self.show()


# ── Main window ───────────────────────────────────────────────────────────────
class MainWindow(QMainWindow):
    def __init__(self):
        super().__init__()
        self.setWindowTitle("UF Instruction Guide Converter")
        self.resize(760, 900)
        self.setMinimumSize(500, 600)
        self._build()

    def _build(self):
        central = QWidget()
        central.setStyleSheet(f"background: {SURFACE};")
        root = QVBoxLayout(central)
        root.setContentsMargins(0, 0, 0, 0)
        root.setSpacing(0)

        # ── Top chrome bar ────────────────────────────────────────────────────
        chrome = QWidget()
        chrome.setFixedHeight(48)
        chrome.setStyleSheet(f"background: {UF_BLUE};")
        chrome_layout = QHBoxLayout(chrome)
        chrome_layout.setContentsMargins(20, 0, 20, 0)
        chrome_layout.setSpacing(12)

        brand = QLabel("UF Instruction Guide Converter")
        brand.setStyleSheet(
            f"color: {WHITE}; font-size: 13px; font-weight: 700;"
            f"font-family: 'Calibri'; letter-spacing: 0.4px;"
        )
        chrome_layout.addWidget(brand)
        chrome_layout.addStretch()

        # Open model button lives in the chrome bar
        open_btn = QPushButton("Open Model in Browser  ↗")
        open_btn.setCursor(Qt.CursorShape.PointingHandCursor)
        open_btn.setFixedHeight(30)
        open_btn.setStyleSheet(_btn_ghost())
        open_btn.clicked.connect(self._open_model)
        chrome_layout.addWidget(open_btn)

        root.addWidget(chrome)

        # ── Orange accent line ────────────────────────────────────────────────
        accent = QFrame()
        accent.setFixedHeight(3)
        accent.setStyleSheet(
            f"background: qlineargradient(x1:0, y1:0, x2:1, y2:0,"
            f"stop:0 {UF_ORANGE}, stop:1 {UF_ORANGE_DARK});"
        )
        root.addWidget(accent)

        # ── Content area ──────────────────────────────────────────────────────
        content = QWidget()
        content.setStyleSheet(f"background: {SURFACE};")
        layout = QVBoxLayout(content)
        layout.setContentsMargins(28, 24, 28, 20)
        layout.setSpacing(16)

        # Instructions
        instructions = QLabel(
            "Use the <span style='font-weight:600;'>Open Model in Browser</span> "
            "button to launch the NaviGator AI model, then paste the generated "
            "HTML below or drag and drop an "
            "<span style='font-weight:600;'>.html</span> file. "
            "Click <span style='font-weight:600;'>Convert to Word</span> "
            "to save your document."
        )
        instructions.setWordWrap(True)
        instructions.setTextFormat(Qt.TextFormat.RichText)
        instructions.setStyleSheet(
            f"color: {TEXT_SECONDARY}; font-size: 12px; line-height: 1.6;"
            f"background: transparent;"
        )
        layout.addWidget(instructions)

        layout.addWidget(HDivider())

        # ── Editor card ───────────────────────────────────────────────────────
        editor_card = QFrame()
        editor_card.setStyleSheet(
            f"""
            QFrame {{
                background: {WHITE};
                border: 1.5px solid {BORDER};
                border-radius: 8px;
            }}
            """
        )
        shadow = QGraphicsDropShadowEffect()
        shadow.setBlurRadius(18)
        shadow.setXOffset(0)
        shadow.setYOffset(2)
        shadow.setColor(QColor(0, 0, 0, 20))
        editor_card.setGraphicsEffect(shadow)

        card_layout = QVBoxLayout(editor_card)
        card_layout.setContentsMargins(0, 0, 0, 0)
        card_layout.setSpacing(0)

        # Card header strip
        card_header = QWidget()
        card_header.setFixedHeight(36)
        card_header.setStyleSheet(
            f"""
            background: {SURFACE_ALT};
            border-top-left-radius: 8px;
            border-top-right-radius: 8px;
            border-bottom: 1px solid {BORDER};
            """
        )
        card_header_layout = QHBoxLayout(card_header)
        card_header_layout.setContentsMargins(12, 0, 12, 0)

        for color in ("#FF5F57", "#FEBC2E", "#28C840"):
            dot = QLabel()
            dot.setFixedSize(11, 11)
            dot.setStyleSheet(
                f"background: {color}; border-radius: 5px; border: none;"
            )
            card_header_layout.addWidget(dot)

        card_header_layout.addSpacing(8)
        file_label = QLabel("HTML Source")
        file_label.setStyleSheet(
            f"color: {TEXT_MUTED}; font-size: 11px; font-family: 'Courier New';"
        )
        card_header_layout.addWidget(file_label)
        card_header_layout.addStretch()
        card_layout.addWidget(card_header)

        # Text editor
        self.text_edit = DropTextEdit()
        self.text_edit.setFont(QFont("Courier New", 10))
        self.text_edit.setStyleSheet(
            f"""
            QTextEdit {{
                background: {WHITE};
                border: none;
                border-bottom-left-radius: 8px;
                border-bottom-right-radius: 8px;
                padding: 12px;
                color: {TEXT_PRIMARY};
                selection-background-color: {UF_BLUE_LIGHT};
                selection-color: {UF_BLUE};
            }}
            QScrollBar:vertical {{
                border: none;
                background: {SURFACE};
                width: 8px;
                border-radius: 4px;
            }}
            QScrollBar::handle:vertical {{
                background: {BORDER};
                border-radius: 4px;
                min-height: 30px;
            }}
            QScrollBar::handle:vertical:hover {{
                background: {TEXT_MUTED};
            }}
            QScrollBar::add-line:vertical,
            QScrollBar::sub-line:vertical {{
                height: 0;
            }}
            """
        )
        card_layout.addWidget(self.text_edit)
        layout.addWidget(editor_card, stretch=1)

        # ── Action row ────────────────────────────────────────────────────────
        action_row = QHBoxLayout()
        action_row.setSpacing(10)

        self.clear_btn = QPushButton("Clear")
        self.clear_btn.setCursor(Qt.CursorShape.PointingHandCursor)
        self.clear_btn.setFixedHeight(38)
        self.clear_btn.setStyleSheet(_btn_secondary())
        self.clear_btn.clicked.connect(self._clear)

        self.convert_btn = QPushButton("  Convert to Word  ")
        self.convert_btn.setCursor(Qt.CursorShape.PointingHandCursor)
        self.convert_btn.setFixedHeight(38)
        self.convert_btn.setStyleSheet(_btn_primary())
        self.convert_btn.clicked.connect(self._convert)

        action_row.addWidget(self.clear_btn)
        action_row.addStretch()
        action_row.addWidget(self.convert_btn)
        layout.addLayout(action_row)

        # ── Status badge ──────────────────────────────────────────────────────
        self.status = StatusBadge()
        layout.addWidget(self.status)

        root.addWidget(content, stretch=1)

        # ── Footer ────────────────────────────────────────────────────────────
        footer = QWidget()
        footer.setFixedHeight(32)
        footer.setStyleSheet(
            f"background: {SURFACE_ALT}; border-top: 1px solid {BORDER};"
        )
        footer_layout = QHBoxLayout(footer)
        footer_layout.setContentsMargins(20, 0, 20, 0)

        footer_lbl = QLabel(
            "University of Florida  ·  HR Training & Organizational Development"
        )
        footer_lbl.setStyleSheet(
            f"color: {TEXT_MUTED}; font-size: 10px; font-family: 'Calibri';"
        )
        footer_layout.addWidget(footer_lbl)
        footer_layout.addStretch()

        version_lbl = QLabel("v1.0")
        version_lbl.setStyleSheet(
            f"color: {TEXT_MUTED}; font-size: 10px; font-family: 'Calibri';"
        )
        footer_layout.addWidget(version_lbl)
        root.addWidget(footer)

        self.setCentralWidget(central)

    def _open_model(self):
        """Open the model URL in the user's default browser."""
        webbrowser.open(MODEL_URL)

    def _clear(self):
        self.text_edit.clear()
        self.status.hide()

    def _convert(self):
        html = self.text_edit.toPlainText().strip()
        if not html:
            self.status.set_error("Nothing to convert. Paste some HTML first.")
            return

        title_match = re.search(
            r"<title[^>]*>(.*?)</title>", html,
            re.IGNORECASE | re.DOTALL
        )
        default_name = "document"
        if title_match:
            default_name = (
                re.sub(r"\s+", "_", title_match.group(1).strip())
                or "document"
            )

        save_path, _ = QFileDialog.getSaveFileName(
            self, "Save Word Document", f"{default_name}.docx",
            "Word Documents (*.docx)"
        )
        if not save_path:
            return

        self.convert_btn.setEnabled(False)
        self.status.set_info("Converting…")
        QApplication.processEvents()

        try:
            docx_bytes = html_to_docx(html)
            with open(save_path, "wb") as f:
                f.write(docx_bytes)
            self.status.set_success(f"Saved: {os.path.basename(save_path)}")
        except Exception as e:
            self.status.set_error(f"Conversion failed: {e}")
        finally:
            self.convert_btn.setEnabled(True)


# ── Entry point ───────────────────────────────────────────────────────────────
def main():
    app = QApplication(sys.argv)
    app.setApplicationName("UF Instruction Guide Converter")
    app.setStyle("Fusion")

    palette = QPalette()
    palette.setColor(QPalette.ColorRole.Window,          QColor(SURFACE))
    palette.setColor(QPalette.ColorRole.WindowText,      QColor(TEXT_PRIMARY))
    palette.setColor(QPalette.ColorRole.Base,            QColor(WHITE))
    palette.setColor(QPalette.ColorRole.AlternateBase,   QColor(SURFACE_ALT))
    palette.setColor(QPalette.ColorRole.Text,            QColor(TEXT_PRIMARY))
    palette.setColor(QPalette.ColorRole.Button,          QColor(SURFACE))
    palette.setColor(QPalette.ColorRole.ButtonText,      QColor(TEXT_PRIMARY))
    palette.setColor(QPalette.ColorRole.Highlight,       QColor(UF_BLUE))
    palette.setColor(QPalette.ColorRole.HighlightedText, QColor(WHITE))
    app.setPalette(palette)

    app.setFont(QFont("Calibri", 11))

    window = MainWindow()
    window.show()
    sys.exit(app.exec())


if __name__ == "__main__":
    main()
```

Would you like me to explain or break down the code?

---

You can also remove `PyQt6-WebEngine` from `requirements.txt` and the build since it's no longer needed, which will make both the install and the final `.exe` significantly lighter:

```
PyQt6
python-docx
beautifulsoup4
lxml
pyinstaller
```

And update `build.bat` accordingly — no longer needs `PyQt6-WebEngine` and the `.exe` will be notably smaller:

```bat
@echo off
echo Installing dependencies...
pip install -r requirements.txt

echo.
echo Building executable...
pyinstaller ^
  --onefile ^
  --windowed ^
  --name "UF_Guide_Converter" ^
  --add-data "template.docx;." ^
  main.py

echo.
echo Done. Find your .exe in the dist\ folder.
pause
```

---

## 🧑 User

I want the side by side layout, is there a way to make the users broser open in a window inside the app?

---

## 🤖 Assistant

Yes — the right tool for this is the **Windows API directly**. Instead of embedding a browser engine, you can launch the user's real browser as a separate process and then **reparent its window** into a panel inside your Qt app using the Windows `SetParent` call. This gives you the native browser at full performance inside your layout.

It does come with one honest caveat worth knowing upfront: browser windows weren't designed to be reparented, so occasionally on first launch there's a brief moment before the window is grabbed. It's minor and one retry handles it reliably.

This requires two new files alongside the others:

---

**Updated project structure:**

```
docx_converter/
├── main.py
├── converter.py
├── browser_host.py     ← new
├── template.docx
├── requirements.txt
└── build.bat
```

---

**`browser_host.py`**

```python
"""
Opens the model URL in the user's default browser, finds the resulting
window by title/process, and reparents it into a Qt widget container
using the Windows SetParent API.

Only the browser_host.py module touches win32 — main.py stays clean.
"""
import os
import re
import time
import subprocess
import webbrowser
import ctypes
import ctypes.wintypes

from PyQt6.QtWidgets import QWidget, QVBoxLayout, QLabel, QPushButton, QFrame
from PyQt6.QtCore import Qt, QTimer, QThread, pyqtSignal
from PyQt6.QtGui import QFont, QColor

# Windows API
user32   = ctypes.windll.user32
kernel32 = ctypes.windll.kernel32

GWL_STYLE       = -16
WS_CAPTION      = 0x00C00000
WS_THICKFRAME   = 0x00040000
WS_CHILD        = 0x40000000
WS_VISIBLE      = 0x10000000
SWP_FRAMECHANGED  = 0x0020
SWP_NOMOVE        = 0x0002
SWP_NOSIZE        = 0x0001
SWP_NOZORDER      = 0x0004
HWND_TOP          = 0

MODEL_URL = "https://chat.ai.it.ufl.edu/?model=tod-document-generator"

# Fragments that appear in browser tab titles for this URL
URL_TITLE_HINTS = [
    "navigat", "tod-document", "instruction guide",
    "chat.ai.it.ufl", "ufl.edu"
]

UF_BLUE       = "#0021A5"
UF_BLUE_DARK  = "#001880"
UF_ORANGE     = "#FA4616"
UF_ORANGE_DARK= "#D93A0F"
WHITE         = "#FFFFFF"
SURFACE_ALT   = "#EDEEF5"
BORDER        = "#D0D3E8"
TEXT_MUTED    = "#9194A8"
TEXT_PRIMARY  = "#1A1A2E"


def _get_window_pid(hwnd: int) -> int:
    pid = ctypes.wintypes.DWORD()
    user32.GetWindowThreadProcessId(hwnd, ctypes.byref(pid))
    return pid.value


def _enum_windows() -> list:
    """Return a list of (hwnd, title, pid) for all visible top-level windows."""
    results = []

    @ctypes.WINFUNCTYPE(ctypes.c_bool, ctypes.wintypes.HWND, ctypes.wintypes.LPARAM)
    def callback(hwnd, _):
        if not user32.IsWindowVisible(hwnd):
            return True
        length = user32.GetWindowTextLengthW(hwnd)
        if length == 0:
            return True
        buf = ctypes.create_unicode_buffer(length + 1)
        user32.GetWindowTextW(hwnd, buf, length + 1)
        results.append((hwnd, buf.value, _get_window_pid(hwnd)))
        return True

    user32.EnumWindows(callback, 0)
    return results


def _find_browser_hwnd(launched_pid: int = None,
                        timeout: float = 12.0) -> int | None:
    """
    Poll for a browser window that either:
      - belongs to the launched PID (most reliable), or
      - has a title containing one of the URL_TITLE_HINTS (fallback).
    Returns the hwnd or None if not found within timeout.
    """
    deadline = time.time() + timeout
    while time.time() < deadline:
        for hwnd, title, pid in _enum_windows():
            title_lower = title.lower()
            # Prefer matching by PID if we have one
            if launched_pid and pid == launched_pid:
                # Make sure it's an actual content window, not a subprocess helper
                if any(h in title_lower for h in URL_TITLE_HINTS) or len(title) > 4:
                    return hwnd
            # Fallback: title hint match
            if any(h in title_lower for h in URL_TITLE_HINTS):
                return hwnd
        time.sleep(0.3)
    return None


def _strip_chrome(hwnd: int):
    """Remove the window's title bar and resize border."""
    style = user32.GetWindowLongW(hwnd, GWL_STYLE)
    style &= ~(WS_CAPTION | WS_THICKFRAME)
    user32.SetWindowLongW(hwnd, GWL_STYLE, style)
    user32.SetWindowPos(
        hwnd, HWND_TOP, 0, 0, 0, 0,
        SWP_NOMOVE | SWP_NOSIZE | SWP_NOZORDER | SWP_FRAMECHANGED
    )


class BrowserFinderThread(QThread):
    """
    Background thread that launches the URL and waits for the browser
    window to appear, then signals back with the hwnd.
    """
    found    = pyqtSignal(int)   # emits hwnd
    failed   = pyqtSignal()

    def run(self):
        # Open the URL — webbrowser returns quickly; the window appears shortly after
        webbrowser.open(MODEL_URL)
        # Give the browser a moment to create its window
        time.sleep(1.5)
        hwnd = _find_browser_hwnd(timeout=12.0)
        if hwnd:
            self.found.emit(hwnd)
        else:
            self.failed.emit()


class BrowserHostWidget(QWidget):
    """
    A Qt widget that hosts a real browser window reparented into it.
    Shows a loading state while the browser is being found.
    """

    def __init__(self, parent=None):
        super().__init__(parent)
        self._hwnd        = None
        self._finder      = None
        self._resize_timer = QTimer(self)
        self._resize_timer.timeout.connect(self._sync_size)
        self._resize_timer.setInterval(100)
        self._build_placeholder()

    # ── UI ────────────────────────────────────────────────────────────────────

    def _build_placeholder(self):
        layout = QVBoxLayout(self)
        layout.setContentsMargins(0, 0, 0, 0)
        layout.setSpacing(0)

        self._placeholder = QWidget()
        self._placeholder.setStyleSheet(f"background: {SURFACE_ALT};")
        ph_layout = QVBoxLayout(self._placeholder)
        ph_layout.setAlignment(Qt.AlignmentFlag.AlignCenter)
        ph_layout.setSpacing(16)

        self._status_lbl = QLabel("Click  Open Model  to launch the browser.")
        self._status_lbl.setAlignment(Qt.AlignmentFlag.AlignCenter)
        self._status_lbl.setStyleSheet(
            f"color: {TEXT_MUTED}; font-size: 13px; background: transparent;"
        )
        ph_layout.addWidget(self._status_lbl)

        self._open_btn = QPushButton("  Open Model  ↗")
        self._open_btn.setCursor(Qt.CursorShape.PointingHandCursor)
        self._open_btn.setFixedHeight(38)
        self._open_btn.setFixedWidth(180)
        self._open_btn.setStyleSheet(
            f"""
            QPushButton {{
                background: qlineargradient(x1:0, y1:0, x2:0, y2:1,
                    stop:0 {UF_BLUE}, stop:1 {UF_BLUE_DARK});
                color: {WHITE};
                border: none;
                border-radius: 6px;
                font-size: 13px;
                font-weight: 600;
                font-family: 'Calibri';
            }}
            QPushButton:hover {{
                background: #1A34B8;
            }}
            QPushButton:disabled {{
                background: #B0B4C8;
                color: #E0E2ED;
            }}
            """
        )
        self._open_btn.clicked.connect(self.launch)
        ph_layout.addWidget(self._open_btn, alignment=Qt.AlignmentFlag.AlignCenter)

        layout.addWidget(self._placeholder)

    # ── Launch ────────────────────────────────────────────────────────────────

    def launch(self):
        self._open_btn.setEnabled(False)
        self._status_lbl.setText("Launching browser…")
        self._finder = BrowserFinderThread(self)
        self._finder.found.connect(self._on_browser_found)
        self._finder.failed.connect(self._on_browser_failed)
        self._finder.start()

    def _on_browser_found(self, hwnd: int):
        self._hwnd = hwnd
        self._embed(hwnd)

    def _on_browser_failed(self):
        self._status_lbl.setText(
            "Could not find the browser window.\n"
            "Try clicking Open Model again."
        )
        self._open_btn.setEnabled(True)

    # ── Embedding ─────────────────────────────────────────────────────────────

    def _embed(self, hwnd: int):
        """Reparent the browser window into this widget."""
        container_hwnd = int(self.winId())

        # Remove decorations from the browser window
        _strip_chrome(hwnd)

        # Reparent it into our container
        user32.SetParent(hwnd, container_hwnd)

        # Hide the placeholder
        self._placeholder.hide()

        # Force an immediate size sync then start the polling timer
        self._sync_size()
        self._resize_timer.start()

    def _sync_size(self):
        """Keep the browser window sized to fill this widget."""
        if not self._hwnd:
            return
        w = self.width()
        h = self.height()
        user32.MoveWindow(self._hwnd, 0, 0, w, h, True)

    # ── Qt overrides ──────────────────────────────────────────────────────────

    def resizeEvent(self, event):
        super().resizeEvent(event)
        if self._hwnd:
            self._sync_size()

    def closeEvent(self, event):
        self._resize_timer.stop()
        # Un-parent the browser before closing so it doesn't get destroyed
        if self._hwnd:
            user32.SetParent(self._hwnd, 0)
        super().closeEvent(event)
```

Would you like me to explain or break down the code?

---

Now update `main.py` to use `BrowserHostWidget` in the left panel instead of the old `BrowserPanel`:

**`main.py`** — only the import and left panel change, everything else stays identical:

```python
import sys
import os
import re

from PyQt6.QtWidgets import (
    QApplication, QMainWindow, QWidget, QHBoxLayout,
    QVBoxLayout, QTextEdit, QPushButton, QLabel,
    QFileDialog, QSplitter, QFrame, QSizePolicy,
    QGraphicsDropShadowEffect
)
from PyQt6.QtCore import QUrl, Qt, QMimeData
from PyQt6.QtGui import (
    QDragEnterEvent, QDropEvent, QFont, QColor, QPalette
)
from browser_host import BrowserHostWidget   # ← replaces QtWebEngine
from converter import html_to_docx

MODEL_URL = "https://chat.ai.it.ufl.edu/?model=tod-document-generator"

# ── Palette ───────────────────────────────────────────────────────────────────
UF_BLUE        = "#0021A5"
UF_BLUE_DARK   = "#001880"
UF_BLUE_LIGHT  = "#E8EDFB"
UF_ORANGE      = "#FA4616"
UF_ORANGE_DARK = "#D93A0F"
WHITE          = "#FFFFFF"
SURFACE        = "#F7F8FC"
SURFACE_ALT    = "#EDEEF5"
BORDER         = "#D0D3E8"
TEXT_PRIMARY   = "#1A1A2E"
TEXT_SECONDARY = "#555770"
TEXT_MUTED     = "#9194A8"
SUCCESS        = "#1B6B3A"
SUCCESS_BG     = "#E6F4EC"
ERROR          = "#9B1C1C"
ERROR_BG       = "#FEECEC"


def _btn_primary():
    return f"""
        QPushButton {{
            background: qlineargradient(x1:0, y1:0, x2:0, y2:1,
                stop:0 {UF_BLUE}, stop:1 {UF_BLUE_DARK});
            color: {WHITE};
            border: none;
            border-radius: 6px;
            padding: 9px 24px;
            font-size: 13px;
            font-weight: 600;
            font-family: 'Calibri';
            letter-spacing: 0.3px;
        }}
        QPushButton:hover {{
            background: qlineargradient(x1:0, y1:0, x2:0, y2:1,
                stop:0 #1A34B8, stop:1 {UF_BLUE});
        }}
        QPushButton:pressed {{
            background: {UF_BLUE_DARK};
            padding-top: 10px;
            padding-bottom: 8px;
        }}
        QPushButton:disabled {{
            background: #B0B4C8;
            color: #E0E2ED;
        }}
    """


def _btn_secondary():
    return f"""
        QPushButton {{
            background: {WHITE};
            color: {UF_BLUE};
            border: 1.5px solid {BORDER};
            border-radius: 6px;
            padding: 9px 20px;
            font-size: 13px;
            font-weight: 600;
            font-family: 'Calibri';
            letter-spacing: 0.3px;
        }}
        QPushButton:hover {{
            background: {UF_BLUE_LIGHT};
            border-color: {UF_BLUE};
        }}
        QPushButton:pressed {{
            background: {SURFACE_ALT};
        }}
    """


def _btn_ghost():
    return f"""
        QPushButton {{
            background: rgba(255,255,255,0.15);
            color: {WHITE};
            border: 1px solid rgba(255,255,255,0.35);
            border-radius: 5px;
            padding: 0 14px;
            font-size: 12px;
            font-family: 'Calibri';
            font-weight: 600;
        }}
        QPushButton:hover {{
            background: rgba(255,255,255,0.25);
        }}
        QPushButton:pressed {{
            background: rgba(255,255,255,0.10);
        }}
    """


class DropTextEdit(QTextEdit):
    def __init__(self, parent=None):
        super().__init__(parent)
        self.setAcceptDrops(True)
        self.setPlaceholderText(
            "Paste HTML output from the model here,\n"
            "or drag and drop an .html file onto this area…"
        )

    def dragEnterEvent(self, event: QDragEnterEvent):
        if event.mimeData().hasUrls() or event.mimeData().hasText():
            event.acceptProposedAction()
        else:
            event.ignore()

    def dragMoveEvent(self, event):
        event.acceptProposedAction()

    def dropEvent(self, event):
        mime = event.mimeData()
        if mime.hasUrls():
            for url in mime.urls():
                path = url.toLocalFile()
                if path.lower().endswith((".html", ".htm")):
                    try:
                        with open(path, "r", encoding="utf-8") as f:
                            self.setPlainText(f.read())
                        event.acceptProposedAction()
                        return
                    except Exception as e:
                        self.setPlainText(f"Error reading file:\n{e}")
                        return
        if mime.hasText():
            self.setPlainText(mime.text())
            event.acceptProposedAction()


class HDivider(QFrame):
    def __init__(self, parent=None):
        super().__init__(parent)
        self.setFrameShape(QFrame.Shape.HLine)
        self.setFixedHeight(1)
        self.setStyleSheet(f"background: {BORDER}; border: none;")


class StatusBadge(QLabel):
    def __init__(self, parent=None):
        super().__init__(parent)
        self.setWordWrap(True)
        self.hide()

    def set_success(self, message: str):
        self.setStyleSheet(
            f"border-radius:6px;padding:8px 12px;font-size:12px;"
            f"background:{SUCCESS_BG};color:{SUCCESS};font-weight:600;"
        )
        self.setText(f"✓  {message}")
        self.show()

    def set_error(self, message: str):
        self.setStyleSheet(
            f"border-radius:6px;padding:8px 12px;font-size:12px;"
            f"background:{ERROR_BG};color:{ERROR};font-weight:600;"
        )
        self.setText(f"✕  {message}")
        self.show()

    def set_info(self, message: str):
        self.setStyleSheet(
            f"border-radius:6px;padding:8px 12px;font-size:12px;"
            f"background:{UF_BLUE_LIGHT};color:{UF_BLUE};font-weight:600;"
        )
        self.setText(f"⟳  {message}")
        self.show()


# ── Left panel wrapper ────────────────────────────────────────────────────────
class BrowserPanel(QWidget):
    def __init__(self, parent=None):
        super().__init__(parent)
        layout = QVBoxLayout(self)
        layout.setContentsMargins(0, 0, 0, 0)
        layout.setSpacing(0)

        # Chrome bar
        chrome = QWidget()
        chrome.setFixedHeight(48)
        chrome.setStyleSheet(f"background: {UF_BLUE};")
        chrome_layout = QHBoxLayout(chrome)
        chrome_layout.setContentsMargins(16, 0, 16, 0)
        chrome_layout.setSpacing(10)

        brand = QLabel("NaviGator AI  ·  Instruction Guide Generator")
        brand.setStyleSheet(
            f"color:{WHITE};font-size:13px;font-weight:700;"
            f"font-family:'Calibri';letter-spacing:0.4px;"
        )
        chrome_layout.addWidget(brand)
        chrome_layout.addStretch()

        layout.addWidget(chrome)

        # Orange accent
        accent = QFrame()
        accent.setFixedHeight(3)
        accent.setStyleSheet(
            f"background:qlineargradient(x1:0,y1:0,x2:1,y2:0,"
            f"stop:0 {UF_ORANGE},stop:1 {UF_ORANGE_DARK});"
        )
        layout.addWidget(accent)

        # Browser host
        self.host = BrowserHostWidget()
        layout.addWidget(self.host, stretch=1)


# ── Right panel ───────────────────────────────────────────────────────────────
class ConverterPanel(QWidget):
    def __init__(self, parent=None):
        super().__init__(parent)
        self.setStyleSheet(f"background:{SURFACE};")
        self._build()

    def _build(self):
        outer = QVBoxLayout(self)
        outer.setContentsMargins(0, 0, 0, 0)
        outer.setSpacing(0)

        chrome = QWidget()
        chrome.setFixedHeight(48)
        chrome.setStyleSheet(f"background:{TEXT_PRIMARY};")
        chrome_layout = QHBoxLayout(chrome)
        chrome_layout.setContentsMargins(20, 0, 20, 0)

        title_lbl = QLabel("HTML → Word Converter")
        title_lbl.setStyleSheet(
            f"color:{WHITE};font-size:13px;font-weight:700;"
            f"font-family:'Calibri';letter-spacing:0.4px;"
        )
        chrome_layout.addWidget(title_lbl)
        chrome_layout.addStretch()
        outer.addWidget(chrome)

        accent = QFrame()
        accent.setFixedHeight(3)
        accent.setStyleSheet(
            f"background:qlineargradient(x1:0,y1:0,x2:1,y2:0,"
            f"stop:0 {UF_ORANGE_DARK},stop:1 {UF_ORANGE});"
        )
        outer.addWidget(accent)

        content = QWidget()
        content.setStyleSheet(f"background:{SURFACE};")
        layout = QVBoxLayout(content)
        layout.setContentsMargins(24, 24, 24, 20)
        layout.setSpacing(16)

        instructions = QLabel(
            "Paste the HTML output from the model below, or drag and drop "
            "an <span style='font-weight:600;'>.html</span> file directly "
            "onto the text area. Then click <span style='font-weight:600;'>"
            "Convert to Word</span> to save your document."
        )
        instructions.setWordWrap(True)
        instructions.setTextFormat(Qt.TextFormat.RichText)
        instructions.setStyleSheet(
            f"color:{TEXT_SECONDARY};font-size:12px;line-height:1.5;"
        )
        layout.addWidget(instructions)
        layout.addWidget(HDivider())

        editor_card = QFrame()
        editor_card.setStyleSheet(
            f"QFrame{{background:{WHITE};border:1.5px solid {BORDER};"
            f"border-radius:8px;}}"
        )
        shadow = QGraphicsDropShadowEffect()
        shadow.setBlurRadius(18)
        shadow.setXOffset(0)
        shadow.setYOffset(2)
        shadow.setColor(QColor(0, 0, 0, 20))
        editor_card.setGraphicsEffect(shadow)

        card_layout = QVBoxLayout(editor_card)
        card_layout.setContentsMargins(0, 0, 0, 0)
        card_layout.setSpacing(0)

        card_header = QWidget()
        card_header.setFixedHeight(36)
        card_header.setStyleSheet(
            f"background:{SURFACE_ALT};"
            f"border-top-left-radius:8px;border-top-right-radius:8px;"
            f"border-bottom:1px solid {BORDER};"
        )
        card_header_layout = QHBoxLayout(card_header)
        card_header_layout.setContentsMargins(12, 0, 12, 0)

        for color in ("#FF5F57", "#FEBC2E", "#28C840"):
            dot = QLabel()
            dot.setFixedSize(11, 11)
            dot.setStyleSheet(
                f"background:{color};border-radius:5px;border:none;"
            )
            card_header_layout.addWidget(dot)

        card_header_layout.addSpacing(8)
        file_label = QLabel("HTML Source")
        file_label.setStyleSheet(
            f"color:{TEXT_MUTED};font-size:11px;font-family:'Courier New';"
        )
        card_header_layout.addWidget(file_label)
        card_header_layout.addStretch()
        card_layout.addWidget(card_header)

        self.text_edit = DropTextEdit()
        self.text_edit.setFont(QFont("Courier New", 10))
        self.text_edit.setStyleSheet(
            f"""
            QTextEdit {{
                background:{WHITE};border:none;
                border-bottom-left-radius:8px;border-bottom-right-radius:8px;
                padding:12px;color:{TEXT_PRIMARY};
                selection-background-color:{UF_BLUE_LIGHT};
                selection-color:{UF_BLUE};
            }}
            QScrollBar:vertical {{
                border:none;background:{SURFACE};width:8px;border-radius:4px;
            }}
            QScrollBar::handle:vertical {{
                background:{BORDER};border-radius:4px;min-height:30px;
            }}
            QScrollBar::handle:vertical:hover {{background:{TEXT_MUTED};}}
            QScrollBar::add-line:vertical,
            QScrollBar::sub-line:vertical {{height:0;}}
            """
        )
        card_layout.addWidget(self.text_edit)
        layout.addWidget(editor_card, stretch=1)

        action_row = QHBoxLayout()
        action_row.setSpacing(10)

        self.clear_btn = QPushButton("Clear")
        self.clear_btn.setCursor(Qt.CursorShape.PointingHandCursor)
        self.clear_btn.setFixedHeight(38)
        self.clear_btn.setStyleSheet(_btn_secondary())
        self.clear_btn.clicked.connect(self._clear)

        self.convert_btn = QPushButton("  Convert to Word  ")
        self.convert_btn.setCursor(Qt.CursorShape.PointingHandCursor)
        self.convert_btn.setFixedHeight(38)
        self.convert_btn.setStyleSheet(_btn_primary())
        self.convert_btn.clicked.connect(self._convert)

        action_row.addWidget(self.clear_btn)
        action_row.addStretch()
        action_row.addWidget(self.convert_btn)
        layout.addLayout(action_row)

        self.status = StatusBadge()
        layout.addWidget(self.status)
        outer.addWidget(content, stretch=1)

        footer = QWidget()
        footer.setFixedHeight(32)
        footer.setStyleSheet(
            f"background:{SURFACE_ALT};border-top:1px solid {BORDER};"
        )
        footer_layout = QHBoxLayout(footer)
        footer_layout.setContentsMargins(20, 0, 20, 0)

        footer_lbl = QLabel(
            "University of Florida  ·  HR Training & Organizational Development"
        )
        footer_lbl.setStyleSheet(
            f"color:{TEXT_MUTED};font-size:10px;font-family:'Calibri';"
        )
        footer_layout.addWidget(footer_lbl)
        footer_layout.addStretch()
        footer_layout.addWidget(
            QLabel("v1.0", styleSheet=f"color:{TEXT_MUTED};font-size:10px;")
        )
        outer.addWidget(footer)

    def _clear(self):
        self.text_edit.clear()
        self.status.hide()

    def _convert(self):
        html = self.text_edit.toPlainText().strip()
        if not html:
            self.status.set_error("Nothing to convert. Paste some HTML first.")
            return

        import re
        title_match = re.search(
            r"<title[^>]*>(.*?)</title>", html,
            re.IGNORECASE | re.DOTALL
        )
        default_name = "document"
        if title_match:
            default_name = (
                re.sub(r"\s+", "_", title_match.group(1).strip()) or "document"
            )

        save_path, _ = QFileDialog.getSaveFileName(
            self, "Save Word Document", f"{default_name}.docx",
            "Word Documents (*.docx)"
        )
        if not save_path:
            return

        self.convert_btn.setEnabled(False)
        self.status.set_info("Converting…")
        QApplication.processEvents()

        try:
            docx_bytes = html_to_docx(html)
            with open(save_path, "wb") as f:
                f.write(docx_bytes)
            self.status.set_success(f"Saved: {os.path.basename(save_path)}")
        except Exception as e:
            self.status.set_error(f"Conversion failed: {e}")
        finally:
            self.convert_btn.setEnabled(True)


# ── Main window ───────────────────────────────────────────────────────────────
class MainWindow(QMainWindow):
    def __init__(self):
        super().__init__()
        self.setWindowTitle("UF Instruction Guide Converter")
        self.resize(1440, 900)
        self.setMinimumSize(900, 600)
        self._build()

    def _build(self):
        central = QWidget()
        central.setStyleSheet(f"background:{SURFACE};")
        root = QVBoxLayout(central)
        root.setContentsMargins(0, 0, 0, 0)
        root.setSpacing(0)

        splitter = QSplitter(Qt.Orientation.Horizontal)
        splitter.setHandleWidth(5)
        splitter.setStyleSheet(
            f"QSplitter::handle{{background:{BORDER};}}"
            f"QSplitter::handle:hover{{background:{UF_BLUE};}}"
        )

        self.browser_panel   = BrowserPanel()
        self.converter_panel = ConverterPanel()

        splitter.addWidget(self.browser_panel)
        splitter.addWidget(self.converter_panel)
        splitter.setSizes([893, 547])
        splitter.setCollapsible(0, False)
        splitter.setCollapsible(1, False)

        root.addWidget(splitter)
        self.setCentralWidget(central)


# ── Entry point ───────────────────────────────────────────────────────────────
def main():
    app = QApplication(sys.argv)
    app.setApplicationName("UF Instruction Guide Converter")
    app.setStyle("Fusion")

    palette = QPalette()
    palette.setColor(QPalette.ColorRole.Window,          QColor(SURFACE))
    palette.setColor(QPalette.ColorRole.WindowText,      QColor(TEXT_PRIMARY))
    palette.setColor(QPalette.ColorRole.Base,            QColor(WHITE))
    palette.setColor(QPalette.ColorRole.AlternateBase,   QColor(SURFACE_ALT))
    palette.setColor(QPalette.ColorRole.Text,            QColor(TEXT_PRIMARY))
    palette.setColor(QPalette.ColorRole.Button,          QColor(SURFACE))
    palette.setColor(QPalette.ColorRole.ButtonText,      QColor(TEXT_PRIMARY))
    palette.setColor(QPalette.ColorRole.Highlight,       QColor(UF_BLUE))
    palette.setColor(QPalette.ColorRole.HighlightedText, QColor(WHITE))
    app.setPalette(palette)
    app.setFont(QFont("Calibri", 11))

    window = MainWindow()
    window.show()
    sys.exit(app.exec())


if __name__ == "__main__":
    main()
```

Would you like me to explain or break down the code?

---

`requirements.txt` stays the same lean version — no WebEngine needed:

```
PyQt6
python-docx
beautifulsoup4
lxml
pyinstaller
```

And add `browser_host.py` to the PyInstaller bundle:

**`build.bat`**

```bat
@echo off
echo Installing dependencies...
pip install -r requirements.txt

echo.
echo Building executable...
pyinstaller ^
  --onefile ^
  --windowed ^
  --name "UF_Guide_Converter" ^
  --add-data "template.docx;." ^
  --add-data "browser_host.py;." ^
  main.py

echo.
echo Done. Find your .exe in the dist\ folder.
pause
```

---

## 🧑 User

ok that is better but is there a way to make it so a new browser window opens and automatically navigates to that url and snaps into the window?

---
