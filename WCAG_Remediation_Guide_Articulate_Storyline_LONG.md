# WCAG Remediation Guide for Updating Articulate Storyline Courses LONG VERSION

*University of Florida — Training & Organizational Development | Human Resources — 3/25/2026*

---

## Introduction

This guide is intended for teams updating legacy Articulate Storyline courses that do not meet — or only partially meet — WCAG 2.2 AA. It is written specifically for the remediation of existing courses, not for building new ones from scratch.

The goal is to systematically remove accessibility barriers, modernize outdated course behavior, and improve consistency so the final published course is much closer to WCAG 2.2 AA.

---

## Accelerate Remediation with AI-Assisted Accessibility Tools

Articulate's recent AI Assistant updates have integrated automated tools directly into the Accessibility Checker. When used strategically, these tools significantly cut down the manual labor of remediating legacy courses. However, AI outputs must always be treated as a first draft, not a final solution.

**Integrated AI features to use:**

- **Bulk AI Alt Text Generation:** Use the Accessibility Checker to automatically generate alt text for all visual assets at once. This establishes a fast baseline — but you must manually verify and edit each description to ensure it serves the instructional goal of the slide.
- **The "Awaiting Review" Workflow:** The Accessibility Checker displays a distinctive icon next to AI-generated alt text awaiting review. Process these in batches. AI cannot understand the instructional context of an image, so human review is essential before finalizing.
- **Automated Closed Captions:** Use the AI Assistant to auto-generate synchronized captions for uncaptioned video or essential audio. Always spot-check for accuracy, especially with technical acronyms and complex terminology.

---

## Start with Triage

Before fixing anything, determine whether the course is a good remediation candidate.

**A course is usually a reasonable remediation candidate if:**

- The content is still current
- The structure is still usable
- The interaction model is not overly complex
- Most issues can be solved through cleanup, relabeling, simplifying interactions, removing outdated assets, and testing

**A course may need partial or full rebuild if:**

- It relies heavily on drag-and-drop
- It depends on custom narration for core instruction
- It uses hover-only or hotspot-heavy interactions throughout
- It has many fragile custom triggers
- Important content exists only in images or narrated media
- The course is full of outdated links, PDFs, and broken resources
- The layout is so cluttered that a usable focus order will still be hard to achieve even after cleanup

---

## Audit the Existing Course Before Changing Anything

Perform a structured audit before editing anything.

**Identify:**

- Outdated or broken hyperlinks
- Direct PDF links
- Slide narration and audio assets
- Audio buttons and audio triggers
- Hover-only interactions
- Drag-and-drop and hotspots
- Missing or vague slide titles
- Unlabeled buttons and icons
- Low-contrast text or controls
- Inaccessible quiz formats
- Broken or inconsistent navigation
- Layers that may confuse users
- Timelines or variables tied to legacy media
- Decorative clutter and duplicate objects
- Missing visible text where narration currently carries the content

**Also document the course at a high level:**

- Number of scenes/modules
- Approximate number of slides
- Number of layers/lightboxes
- Interaction types used
- Media types used
- External resources used
- Any known completion logic or LMS behavior

> Do not begin accessibility cleanup until you understand what is in the file.

---

## Update Course-Level Player and Master Settings First

Fix the structural foundation before touching individual slides. Legacy courses often use outdated player wrappers and hardcoded master slides that fail WCAG standards immediately.

**For the course player:**

- Switch to the **Modern Player** (the Classic Player does not meet current accessibility standards)
- Go to **Player > Text Labels** and ensure the Course Language is set correctly for screen readers (e.g., English (US))
- Go to **Player > Controls** and check the **"Accessibility controls"** box so learners can toggle accessible text and adjust navigation preferences

**For the slide architecture:**

- Open **View > Slide Master** and **View > Feedback Master**
- Right-click global, repeating elements on the master slide (e.g., logos, decorative footers), open the Accessibility tab, and uncheck **"Object is visible to accessibility tools"** if they are redundant
- Mark background images on the masters as decorative
- Verify that no invisible or off-screen master elements are inadvertently pulling into the default focus order
- Ensure global titles use Heading 1 or Heading 2 styles
- Verify that default feedback banners have sufficient contrast and a logical reading order

> Fixing the masters now prevents having to manually fix the same background elements on every individual slide later.

---

## Use the Right Remediation Order

For legacy course remediation, the order of operations matters. Focus order should come near the end — not the beginning — since objects often change during cleanup.

### First: Validate Content and Resources

Confirm the course is still current and worth remediating.

### Second: Update Links and Remove PDF Dependency

Correct destinations, replace direct PDF links, and update wording.

### Third: Remove Legacy Narration and Narration Controls

Delete audio files, audio triggers, audio buttons, and narration instructions.

### Fourth: Restore Any Content That Was Only Present in Narration

Add it back as visible accessible text.

### Fifth: Simplify or Replace Inaccessible Interactions

Replace drag-and-drop, hover-only content, hotspot-heavy layouts, and fragile custom controls.

### Sixth: Clean Up Functionality and Trigger Logic

Remove orphaned references, repair timeline behavior, and confirm navigation and completion logic still work.

### Seventh: Fix Visible Accessibility Issues

Repair contrast, labels, instructions, target size, predictable navigation, and other usability issues.

### Eighth: Set Final Focus Order and Reading Order

Only after the slide is stable should you finalize focus order for the base slide and all layers.

### Ninth: Perform Final Accessibility and Functional Testing

Test in the published environment using keyboard, screen reader, and real link behavior.

> This sequence prevents repeated rework.

---

## Fix Hyperlinks and Remove Direct PDF Dependency Early

For every hyperlink:

- Verify it goes to the correct place
- Confirm the destination is active
- Check whether it points directly to a PDF
- If an updated instruction guide exists as a webpage, link to that webpage instead
- If no updated web guide exists, link to the parent webpage where the PDF lives
- If neither exists, flag the item for content-owner review

### Also Update Visible Wording

If the destination changes from a direct PDF to a webpage, update the surrounding text. Do not leave behind wording that falsely implies the user is opening a PDF.

Use wording like:

- "View the updated instruction guide"
- "Open the instruction guide webpage"
- "Visit the forms and instructions page"

> This part of remediation should happen early because link changes may alter on-screen text, objects, and layout.

---

## Remove Legacy Narration and Narration Controls

T&OD standard is to remove custom integrated narration and rely on accessible on-screen text, proper labels and structure, and learner-controlled screen readers and assistive technology.

**For each slide and each layer, remove:**

- Audio tracks
- Autoplay narration
- Triggers that play, pause, stop, resume, or replay narration
- Narration control buttons
- Speaker icons used only for narration
- Instructions telling the learner to listen to narration

### Before Deleting Audio

Check whether the narration contains unique information. If it does, add that information back into the slide as visible accessible text before deleting.

### After Deleting Audio

Repair logic that depended on it. Older Storyline courses often tie narration to:

- Timeline progression
- Layer behavior
- Object state changes
- Variable updates
- Completion logic

Deleting the audio is only the first step — you must also remove or rebuild anything that relied on it.

> This work should happen before focus order because it may add or remove objects from the slide.

---

## Convert Narration-Only and Image-Only Information into Visible Accessible Text

Once audio is removed, check whether the slide still communicates the full instructional message.

**Common legacy issues:**

- Explanation exists only in narration
- Instructions exist only inside a screenshot
- Process detail exists only in an image callout
- Learners are expected to infer meaning from a visual sequence

**Fix these by:**

- Adding real on-screen text
- Summarizing visuals in text
- Giving clear written instructions
- Making sure a learner can understand the slide without hearing narration

> If content is only visible in an image, convert it into accessible text where possible rather than relying on alt text alone.

---

## Address Remaining Media, Motion, and Timing

If media or motion must stay in the course, ensure:

- All video or essential audio has synchronized **Closed Captions** (.vtt files) and ideally a static transcript
- The **Captions button** is enabled in Player Properties so learners can toggle captions on and off
- Any looping animation or background video lasting longer than 5 seconds has a clear way to pause, stop, or hide it
- Countdown timers on quizzes are removed, or the learner is given a way to extend the time limit before it expires

---

## Simplify Old Interactions

Legacy Storyline files often include interaction types that are difficult to remediate well. Replace rather than rescue when possible:

| Replace | With |
|---|---|
| Drag-and-drop | Select-and-submit |
| Hotspots | Labeled buttons |
| Hover reveals | Click-to-reveal |
| Tiny click targets | Larger buttons |
| Custom branching widgets | Standard buttons |
| Narration-driven sequences | Structured text plus clear controls |
| Single-character key shortcuts | Modifier-key shortcuts (e.g., Ctrl+N) or standard button navigation |

> This step should happen before focus order cleanup, because replacing interactions usually changes the objects that need to be focused.

---

## Clean Up Triggers, Variables, and Functional Dependencies

After links and audio cleanup, test and repair:

- Timeline triggers
- State-change triggers
- Object states (convert custom-named states to Storyline's built-in states: Hover, Visited, Selected)
- Layer-open and layer-close behavior
- Layer properties (check **"Prevent the user from clicking on the base layer"** for popups so focus is properly trapped)
- Variable-based completion logic
- Navigation rules
- Feedback triggers
- Any object that previously depended on media completion

> Legacy courses often contain orphaned logic that does not fail obviously until later testing. Remove broken dependencies now so the slide structure is stable before you set focus order.

---

## Fix Labels, Visible Instructions, and Object Naming

For each meaningful object:

- Give it a clear accessible name
- Make button labels describe the action
- Rename icon controls meaningfully
- Update text instructions to match the current interaction
- Remove references to deleted narration or old files

**Examples of useful names:**

- "Next"
- "Open policy webpage"
- "Close feedback"
- "Scenario choice: Escalate the issue"
- "Image: Employee using safety goggles"

**Examples of poor names:**

- "Shape 9"
- "Button 3"
- "Speaker icon"
- "Blue square"

> Do this before final focus order so objects are already correctly named when you arrange them.

---

## Fix Contrast, Readability, and Other Visible Accessibility Issues

Review and improve:

- Text contrast
- Button contrast
- Focus contrast potential
- Readability of text over images
- Visibility of links
- Visibility of selected states
- Clarity of instructions
- Target size of buttons and links
- Text rendering (set text boxes to **"Do not autofit"** to support custom text-spacing styles without truncating)
- Semantic structure for data tables (check **"Header Row"** in Table Tools)
- Semantic structure for lists (use native bullet/number formatting instead of drawn shapes)
- Color is not the only indicator of meaning (e.g., do not just turn text red for "incorrect" — add an icon or the word "Incorrect")
- Instructions do not rely on spatial or sensory cues (e.g., change "Click the button on the right" to "Select the Next button")

**Legacy design patterns to watch for:**

- Pale text
- Subtle button styling
- Weak selected-state indication
- Text layered over photos
- Tiny icons used as controls
- Green/red text only to show quiz results
- Directional language ("see the chart below") instead of explicit names

> Accessibility should take priority over preserving old visual styling.

---

## Repair Navigation and Target Usability

Check:

- Next, previous, submit, and close controls are present where needed
- Duplicate or competing navigation controls are removed
- Labels are consistent across slides
- Controls are large enough to use
- Click/tap areas are not tiny
- Progression is not dependent on removed narration or inaccessible interactions
- Scrolling panels can receive keyboard focus and be scrolled using the up/down arrow keys

> If a learner must satisfy a condition to move forward, confirm that the condition can be met accessibly.

---

## Repair Quizzes, Forms, and Dynamic Behavior

Review:

- Quiz instructions
- Selected states
- Feedback behavior
- Text-entry fields
- Required field indicators
- Error messages
- Layers and popups
- Variable-driven feedback

Make sure:

- Quiz types are still worth keeping
- Inaccessible question formats are replaced if needed
- Feedback is clear
- Errors are explicit in text and provide a specific suggestion for how to fix the issue
- Focus is managed so that when an error layer or "Invalid Answer" popup appears, the screen reader's focus immediately moves to the error text (not trapped on the submit button)
- Layers have a usable close control
- Selected/expanded/completed states are understandable

> Do this before focus order because these changes often alter the interactive object list.

---

## Set Focus Order and Final Reading Order Last

Focus order should come very late in remediation — after content, links, audio, interactions, navigation, and logic have been stabilized.

**For each slide:**

- Confirm the slide title is meaningful
- Confirm slide names in storyview match the title
- Apply appropriate heading and paragraph styles (Heading 1 for the slide title)
- Place the title first in focus order
- Place instructions before related controls
- Place body text in reading order
- Place interactive controls in a logical sequence
- Remove decorative or unnecessary objects from focus where possible
- Ensure duplicate or hidden objects do not receive focus

**For each layer:**

- Review focus order separately
- Ensure focus lands on meaningful layer content when opened
- Apply appropriate heading and paragraph styles
- Make the close control easy to reach
- Prevent background clutter from confusing the reading experience
- Group related elements together (e.g., an image and its visible text caption) so the screen reader announces them as one cohesive concept rather than fragmented stops

> Because this happens last, you are much less likely to redo the work after other slide changes.

---

## Verify Keyboard Accessibility After Focus Order is Final

Confirm a user can:

- Reach every interactive object
- Understand where focus is
- Activate controls
- Open and close layers
- Answer questions
- Submit responses
- Use links
- Move through the course without a mouse
- Avoid keyboard traps

> If an interaction still fails keyboard use at this stage, replace it rather than trying to force a last-minute workaround.

---

## Make Sure Focus is Clearly Visible

After final focus order is set, confirm that focus is visually obvious on:

- Buttons
- Links
- Answer choices
- Text-entry fields
- Layer controls
- Player controls (if applicable)

Check that focus:

- Is not hidden by custom styling
- Contrasts against the background
- Remains visible at magnification
- Does not disappear on layers or feedback screens

> WCAG 2.2 places increased emphasis on visible focus — do not treat this as optional.

---

## Review Images, Alt Text, and Decorative Content

Once the slide is structurally stable, do a final review:

- Meaningful images have appropriate alt text
- Decorative images are hidden from assistive technology
- Image-only text has been converted into real text where needed
- Screenshots are not the sole source of essential information
- Icons that are controls have meaningful labels

---

## Review Layers, States, and Screen Reader Flow

After focus order is stable, do a final pass on dynamic behavior:

- Selected states are understandable
- Expanded/collapsed states are understandable
- Visited/completed states are understandable
- Layer entry and exit make sense
- Screen reader flow is not cluttered
- Background objects do not create confusion when overlays appear

---

## Test the Published Course

Once remediation is complete, publish the course and test the real output. Test for:

- Correct hyperlink destinations
- Correct replacement of PDF links
- No leftover narration controls
- No references to removed audio
- Correct keyboard access
- Correct focus order
- Visible focus
- Correct layer behavior
- Correct quiz behavior
- Correct screen reader experience
- Correct completion and navigation

> Do not rely on Storyline preview mode alone.

---

## Use Regression Testing

Legacy courses often break in subtle ways after cleanup.

**After major updates, test:** navigation, variables, triggers, layers, feedback, completion, external links, and object states.

**Regression testing should happen:**

- After link cleanup
- After audio deletion
- After interaction replacement
- After final focus order
- After publishing

---

## Common Problems in Legacy Remediation

Expect these issues in legacy remediation work:

- Direct PDF links across many slides
- Outdated resources
- Speaker buttons left behind after audio deletion
- Unique content lost when narration is removed
- Duplicate or hidden objects cluttering the slide
- Interactions built around hover or hotspots
- Broken triggers tied to deleted audio
- Layers with confusing focus behavior
- Inconsistent navigation from years of editing
- Weak contrast from old templates
- Generic slide titles
- Unlabeled icons and buttons
- Visual-only feedback
- Too-early focus-order cleanup that has to be redone later
- Text without the proper heading or paragraph style applied

> That last issue is exactly why this revised workflow moves focus order to the end.

---

## Practical Remediation Workflow for Each Slide

### Step 1: Confirm Content is Current

Do not remediate obsolete content.

### Step 2: Review and Update Hyperlinks

Verify destinations, remove direct PDF links, replace with web guide or parent page.

### Step 3: Remove Legacy Narration

Delete audio, audio triggers, audio buttons, and references to narration.

### Step 4: Restore Any Lost Instructional Content

Add visible accessible text for anything that existed only in narration.

### Step 5: Simplify Inaccessible Interactions

Replace drag-and-drop, hotspots, hover-only reveals, and fragile custom controls.

### Step 6: Repair Triggers and Logic

Fix timeline behavior, variable logic, and progression rules.

### Step 7: Fix Labels, Text Styles, Instructions, Contrast, and Control Usability

Make the slide visually and functionally stable.

### Step 8: Set Final Focus Order

Only now arrange the focus order for the slide and its layers.

### Step 9: Test Keyboard and Screen Reader Behavior

Confirm the slide works in the repaired state.

---

## Slide-by-Slide Remediation Checklist

### Global Settings

- [ ] Modern Player is enabled with Accessibility Controls active
- [ ] Course Language is set correctly in Text Labels
- [ ] Slide and Feedback Masters are structurally clean
- [ ] Captions button is enabled in Player Properties for media-heavy courses
- [ ] Accessible Text rendering is enabled globally
- [ ] Redundant global elements on Master Slides (e.g., logos) are hidden from accessibility tools

### Content and Links

- [ ] Content is still current
- [ ] All hyperlinks were checked
- [ ] Broken links were corrected
- [ ] Direct PDF links were removed where possible
- [ ] PDF links were replaced with updated web guides or parent pages
- [ ] Link text matches destination

### Audio Cleanup

- [ ] Legacy narration was removed
- [ ] Autoplay audio was removed
- [ ] Audio triggers were removed
- [ ] Audio buttons/icons were removed
- [ ] Narration instructions were removed
- [ ] Narration-only content was converted to visible text
- [ ] No trigger still depends on deleted audio

### Interaction and Functionality

- [ ] Inaccessible interactions were replaced or simplified
- [ ] Navigation works
- [ ] Layers behave correctly
- [ ] Variables and triggers still work
- [ ] Buttons and controls are usable
- [ ] Instructions match the current interaction
- [ ] Time limits are removed or adjustable
- [ ] Animations/media can be paused or stopped
- [ ] Scrolling panels are keyboard operable
- [ ] Popups and modals have "Prevent user from clicking base layer" checked
- [ ] Interactive objects use built-in states instead of custom states
- [ ] Single-character keyboard shortcuts have been removed or modified
- [ ] Error messages provide explicit suggestions for correcting the input
- [ ] Screen reader focus is purposefully directed to the text of error layers and popups upon opening

### Visual Accessibility

- [ ] Contrast is sufficient
- [ ] Links are visible
- [ ] Control targets are large enough
- [ ] Visual states are understandable
- [ ] Visible text covers essential content
- [ ] Images and objects have sufficient alt text or are marked as decorative
- [ ] All AI-generated alt text and closed captions have been manually reviewed for accuracy and instructional context
- [ ] Color is not used as the sole method of conveying meaning
- [ ] Instructions do not rely on spatial directions (e.g., "click right")
- [ ] Text boxes are set to "Do not autofit" to support spacing overrides
- [ ] Data tables use defined Header Rows
- [ ] Lists use native paragraph formatting instead of custom shapes

### Final Structure

- [ ] Slide has a meaningful title
- [ ] Slide names in storyview match the title
- [ ] Text has the appropriate heading or paragraph styles applied
- [ ] Controls have meaningful labels
- [ ] Decorative objects do not clutter the accessibility experience
- [ ] Final focus order is logical
- [ ] Layer focus order is logical
- [ ] Focus is clearly visible
- [ ] Related text and visual elements are grouped for a cohesive reading experience

### Final Testing

- [ ] Keyboard pass succeeds
- [ ] Screen reader spot check passes
- [ ] Published output works as expected

---

## Know When to Stop Patching and Rebuild Instead

Consider rebuilding a slide or activity if:

- The interaction pattern is fundamentally inaccessible
- The slide depends heavily on deleted narration
- The layout is too cluttered to produce a clean reading order
- Trigger logic is too tangled to repair confidently
- The visual design cannot support contrast and focus well
- Remediation is taking longer than rebuilding would

> A partial rebuild is often better than endless patching.

---

## What Success Looks Like

A remediated older course does not need to preserve every original design choice. Success means the course is:

- Current in its content
- Stable in its links
- Free of direct PDF dependency where possible
- Free of legacy custom narration
- Understandable through visible accessible text
- Keyboard operable
- Clear in its labels and instructions
- Manageable with screen readers
- Tested in the published environment
- Logically ordered after all other changes are complete

> In remediation, the reading and focus order should reflect the final repaired slide — not an earlier version of it.

---

## Final Recommendation

When remediating older Storyline courses, think like a restorer, not just a fixer. Remove obsolete dependencies first, simplify the interaction model, stabilize the slide, and only then finalize focus order and accessibility structure.

That sequencing will save time and produce a cleaner result.
