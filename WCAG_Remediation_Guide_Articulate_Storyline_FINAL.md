# WCAG Remediation Guide for Updating Articulate Storyline Courses FINAL VERSION

*University of Florida — Training & Organizational Development*

> **Internal use only.** This is an internal and informal guide specific to the T&OD instructional design team. It is not to be made available to the University at large.

---

## Remediation Steps

1. **Disable or delete narration triggers and related controls.** Remove legacy narration, audio triggers, audio buttons, and any instructions to listen to narration. Follow this order for each affected slide:
   1. Delete the extra layer created for the audio button (do not delete other layers on the slide)
   2. Remove the audio button on the base slide and the audio volume button (off slide)
   3. Delete any unassigned slide triggers
   4. Delete slide notes

2. **Use a sans-serif font for body text at a minimum of 12pt** and ensure text remains readable.

3. **Check text color contrast**, especially where text appears over images. Improve readability and adjust the visual treatment as needed so contrast is sufficient.

4. **Add alt text to all non-decorative images.** Decorative images should be hidden from accessibility tools. All AI-generated alt text must be manually reviewed for accuracy and instructional context.

5. **Add proper manual focus order after all other edits are complete.** Place slide titles first, instructions before related controls, body text in logical reading order, and interactive controls in a logical sequence. Ensure hidden or duplicate objects do not receive focus. Review focus order separately for each layer.
   - For overlaid text boxes and shapes, consider grouping them together, labeling the group's alternative text, and using the group in the focus order. Delete the individual text boxes and shapes from the focus order once grouped.
   - For quiz questions and knowledge checks, focus order should follow: question → multiple choice options → submit button → incorrect options → correct options.
   - For quiz result slides, focus order should follow: quiz results → success message → failure message → quiz results → success quiz % → failure quiz % → quiz results passing score → quiz results your points → success quiz points → failure quiz points → quiz results passing points → Submit/Next button.

6. **Label buttons and icon controls with meaningful accessible names** such as "Close," "Exit," or "Return to slide" — not generic names like "Button 3" or "Shape 9."

7. **Correct hyperlinks** so visible link text uses descriptive titles rather than full web addresses. If direct PDF links are used, replace them with a webpage version or parent page whenever possible, and update surrounding wording to match the new destination.

8. **Check and replace broken links.** Verify that every hyperlink goes to the correct, active destination. Replace direct PDF links with updated web guides or parent webpages when possible.

9. **Add closed captions to videos and any essential audio that remains.** Use synchronized captions, ideally with a transcript, and enable the Captions button in Player Properties. If media plays automatically, revise it so learners can control playback when possible.

10. **Remove drag-and-drop interactions** and replace them with more accessible alternatives or structured text.

11. **Give each slide a unique, descriptive title** rather than using only a number. Apply Heading 1 to the slide title, and apply appropriate heading and paragraph styles to other text as needed.

12. **Make sure tables use proper table structure**, including a defined header row and captions.

13. **Remove screen recording videos or add audio descriptions** throughout.

14. **Motion and Animation (WCAG 2.3.3):** Reduce or disable non-essential animations to support users who are sensitive to motion.

15. **Consistent Navigation (WCAG 3.2.3):** Keep navigation controls (e.g., Next, Back, Menu) in consistent locations across slides to ensure a predictable experience.

16. **Flashing Content (WCAG 2.3.2):** Review courses for any flashing or rapidly animated content exceeding three flashes per second, as this can pose risks for users with photosensitive conditions.

17. **Audio Control (WCAG 1.4.2):** Ensure any audio that plays automatically includes accessible controls (e.g., pause/stop and volume adjustment).

18. **Keyboard Accessibility:** Confirm that all interactions are fully operable via keyboard, including logical Tab/Shift+Tab navigation and proper activation of controls using Enter/Space.

19. **Enable accessibility settings in the player.** Use the Modern Player, set the correct course language in Text Labels, and turn on Accessibility Controls so learners can use accessible text and navigation preferences.

20. **Run the Accessibility Checker** and complete all recommended corrections. Review AI-generated accessibility items manually before finalizing.

21. **Publish and re-upload the course in myTraining** using [Replace Content](https://uflorida.sharepoint.com/:b:/r/teams/HR_TrainingOrganizationalDevelopment/Shared%20Documents/myTraining%20System/myTraining_Partner_Program/Toolkit_Instruction_Guides/28Aug2024_myTraining_ReplaceContent_Guide.pdf?csf=1&web=1&e=NFhJcB).

22. **Update the OLT Numbers spreadsheet**, column L, to "ADA2.0 Complete."
