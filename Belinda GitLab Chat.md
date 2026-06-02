# Belinda GitLab Teams Chat

**Hanson, Belinda** — *1/21/2026, 12:54 PM*

**Section 3:** Not all tasks are preassigned. People also navigate to boards and choose work. If just looking for assigned tasks, the personal GitLab home page located in the upper left hand corner will navigate you to your page with all assigned work in one place — this was added in our recent upgrade.

If only opening tasks, the indicative data for the scenario is located in the scenario itself and you may be working task 5 in a scenario without 1–4 being completed.

*Example:* *(image)* — If I click on the first one in the list it would not be the next issue in the scenario.

*(image)* — This is the child task opened by clicking. If I click the demo example parent scenario, you see that demo task 2 is next and demo task 1 is currently in progress still.

*(image)* — If I now click a child task from this page it opens in a side by side view.

*(image)*

**Hanson, Belinda** — *1/21/2026, 12:55 PM*

It was a bit long so did not want to scroll the chat too far.

**Allred, Brady** — *1/21/2026, 12:55 PM*

Perfect, this is excellent! Thank you so much Belinda!

**Hanson, Belinda** — *1/21/2026, 12:56 PM*

np

**Hanson, Belinda** — *1/21/2026, 1:26 PM*

In Section 2:

1. Open the new issue, click **Edit** next to **Labels**, and select a **Size** (S, M, L). These are the labels in the production instance if you need the names. *(image)*
2. Click **Edit** next to **Milestone** and select the current phase (e.g., ETE 1). This is currently **E2E 1** in prod (currently).

**Hanson, Belinda** — *1/22/2026, 7:57 PM*

Ok, I went ahead and cleaned up the page. I will work on the boards and status/labels some tomorrow. I did leave the actual URL the same so as not to break anyone's URL navigation, and I went ahead and archived the other E2E test builds we did not go with. GitLab is a fairly flexible tool — there were 5 different builds I came up with and we went with #2 of those that just made more sense from a user experience.

**Hanson, Belinda** — *1/22/2026, 7:58 PM*

🔗 [https://test.gitlab.it.ufl.edu/adi/empowering-uf-test/e2e-test-2](https://test.gitlab.it.ufl.edu/adi/empowering-uf-test/e2e-test-2) — So this landing page looks like the production view currently.

**Allred, Brady** — *1/22/2026, 7:59 PM*

Perfect, thank you for doing that! I know you have a lot on your plate.

**Hanson, Belinda** — *1/22/2026, 8:04 PM*

I have no meetings tomorrow like I said, so I will try and have test match current prod in the morning. Feel free to reach out tomorrow — I will meet my counterpart Monday and hope we can get the remaining info needed for the build setup and definitions for relative size, etc. Let me know any gaps or specifics you need for the training and I can work on getting that to you as well. And while I am thinking about it, I granted you access at the group so the links to the guides I wrote up should work too in the project's wiki page.

**Allred, Brady** — *1/22/2026, 8:05 PM*

Thank you! That's very helpful! I had an all-day meeting for tomorrow cancel so I will have time to get a lot done with the training stuff as well.

**Hanson, Belinda** — *1/22/2026, 8:06 PM*

Fantastic, sounds like Friday will be a win-win for productivity!

**Hanson, Belinda** — *1/23/2026, 3:43 PM*

Ok, I updated a label on the defect template and tweaked the status labels and boards. There are 2 examples of each board — one using status (the default) and a backup using labels, just in case someone changes their mind on something — but I noted them with "(labels)" in the name. I am sure I will need to modify my wiki guides and flows for the use of status instead of labels, but waiting till everything is fleshed out. I will update the status labels in prod now, but test is the most updated as it works better for your training. That with what Manny updated you with earlier should help.

**Allred, Brady** — *1/23/2026, 3:46 PM*

Thank you, that is great! I really appreciate the help — makes the training much better to have it as close as possible to the real deal.

**Hanson, Belinda** — *1/23/2026, 3:47 PM*

Happy to help.

**Hanson, Belinda** — *1/26/2026, 5:35 PM*

Ginny requested a checklist this morning. I know you were working on one as well. I typed this up very fast — are we discussing the checklist Brady made? Or something like this:

**Working/Creating a Scenario**

**Create Scenario:**

- Choose the correct Functional Area template.
- Update the default labels included in the template:
  - Type: Scenario label
  - Primary Functional Area label
  - Workstream label
  - Relative Size label
- Add Milestone

**Working a Scenario:**

- Mark the Scenario Status **In Progress**
- Create child issues (default task template provided)
- Update Default Template:
  - Verify you are assigned
  - Verify Type: Task label is present
  - Verify Primary Functional Area for task
  - Update task status to **In Progress** from **Not Started**
- **Status options:** Not Started · In Progress · Fail · Ready for Re-Test · Pass · Blocked · Closed · Deferred to Post Go-Live · No Longer Needed · Duplicate
- When done, change status to **Closed**
- Reassign as needed for next task
- When all tasks are complete, change Scenario to **Closed**
- Leave comments to document work or changes in task or scenario
- Verify all information above is correct before closing

**Verifying All Fields Are Completed (after updating your Primary Functional Area template):**

| HCM Payroll | Finance Res |
|||
| Name | Name |
| Worker Type | Company |
| Worker Sub Type | Cost Center |
| EMPLID | Fund |
| Position Number | Program |
| Job Profile | Gift |
| Pay Group | Grant |
| Unions | Designated |
| Exempt/Non-Exempt | Project |
| Salary/Hourly | Activity |
| AWP | Initiative |
| Assignee | Budget Year |
| DPP | Spend Category |
| Flexible Work Arrangement | |
| Supervisory Organization | |
| Manager | |
| Additional Testing Scenario Data | |
| FTE/Working Hours | |
| Benefits | |
| Work Address | |
| Home Address | |
| Additional Testing Scenario Data | |

**Update the default labels:**

- Type: Scenario label
- Primary Functional Area label
- Workstream label
- Relative Size label
- Add Milestone

**Working a Scenario:**

- Mark the Scenario Status **In Progress**
- Create child issues (default task template provided)
- Update Default Template Fields — Task: Transaction No. · Integration # · Report #
- Verify you are assigned
- Verify Type: Task label is present
- Verify Primary Functional Area for task
- Update task status to **In Progress** from **Not Started**
- **Status options:** Not Started · In Progress · Fail · Ready for Re-Test · Pass · Blocked · Closed · Deferred to Post Go-Live · No Longer Needed · Duplicate
- When done, change status to **Closed**
- Reassign as needed for next task
- When all tasks are complete, change Scenario to **Closed**
- Leave comments to document work or changes in task or scenario
- Always verify the required data to ensure accurate reporting:
  - To Do → Close
  - Scenario Status / Task Status
  - Type: Scenario/Task
  - Primary Function label
  - Workstream Label
  - Relative Size Label
  - Milestone
  - Assignee
  - Comments

**Hanson, Belinda** — *1/26/2026, 5:35 PM*

This is just conjecture currently based on the existing reports. This checklist was simply a brain dump created this morning per her request — we can modify and expand on it after this if needed.

**Allred, Brady** — *1/26/2026, 5:36 PM*

This is great! Thank you!

**Hanson, Belinda** — *1/26/2026, 5:37 PM*

np ty

**Hanson, Belinda** — *1/26/2026, 6:45 PM*

For the link to the checklist requested by Ginny — did you want to link to the draft above or incorporate it into what you showed previously?

**Allred, Brady** — *1/26/2026, 6:47 PM*

We can link to the checklist document. I will go in and add it, planning to cross-reference yours to make sure it is accurate.

**Hanson, Belinda** — *1/26/2026, 6:47 PM*

Sounds awesome.

**Allred, Brady** — *1/26/2026, 7:26 PM*

Are they expected to update the iteration of a task? It mentions it in the PowerPoint but I don't see it in your checklist.

**Hanson, Belinda** — *1/26/2026, 7:28 PM*

Iterations are like sprints in Agile. At this time it has not been mentioned that there will be weekly or biweekly iterations — my understanding is just milestones.

**Hanson, Belinda** — *1/26/2026, 7:29 PM*

I did catch one thing to match the documentation — in the boards I used "to do" but in the documentation I used "not started," so I fixed it in both test and prod to match "not started."

**Allred, Brady** — *1/26/2026, 7:29 PM*

Perfect! Thank you!

**Hanson, Belinda** — *1/26/2026, 7:29 PM*

So all good now, np.

**Hanson, Belinda** — *1/26/2026, 7:30 PM*

The statuses are a new feature and Ashwin is going to use status in his reports, so I had backup label versions of the boards — I am deleting them.

**Hanson, Belinda** — *1/26/2026, 7:30 PM*

Less confusing too.

**Hanson, Belinda** — *1/26/2026, 7:32 PM*

Ok, both test and prod now have just Scenarios and Defect boards.

**Allred, Brady** — *1/26/2026, 7:34 PM*

Thanks for all this — it does make a difference for the training materials when it is all as close as possible, so I appreciate your time on it.

**Hanson, Belinda** — *1/26/2026, 7:34 PM*

Just in case you happened to see "Scenarios" and "Scenarios (Labels)."

**Hanson, Belinda** — *1/26/2026, 7:35 PM*

np, happy to help — the more confident the team is in the workflow, the better E2E will progress.

**Allred, Brady** — *1/26/2026, 7:58 PM*

On the scenarios board, is there a way to filter to show scenarios that have child tasks assigned to me? Or that have child tasks associated with my functional area or workstream but don't have an assignee? I'm trying to find the best way to help them find tasks that are pertinent to them.

**Hanson, Belinda** — *1/26/2026, 8:01 PM*

Child tasks do not appear on board view. You can go to **Plan > Issues** and filter by:

- Assignee is: *(choose name)*
- Type is: Task

🔗 [https://test.gitlab.it.ufl.edu/adi/empowering-uf-test/e2e-test-2/-/issues](https://test.gitlab.it.ufl.edu/adi/empowering-uf-test/e2e-test-2/-/issues)

**Hanson, Belinda** — *1/26/2026, 8:06 PM*

Example from the scenario board. *(image)*

**Hanson, Belinda** — *1/26/2026, 8:09 PM*

The dropdown only displays by issue and incident from the board view.

**Allred, Brady** — *1/26/2026, 8:10 PM*

Sounds good. I will direct them to the issues rather than the boards, then, and tell them how to find what they need from there.

**Hanson, Belinda** — *1/26/2026, 8:11 PM*

In a perfect world you would be able to see and sort those items from the board — but sounds good.

**Allred, Brady** — *1/26/2026, 8:17 PM*

The only hiccup I see is if they are assigned a task, or need to work on a task, but don't know the scenario it belongs to. I am not sure how likely that case is to come up, but it was just a thought — I could picture a cross-functional scenario having tasks from different functional areas, so then the user sits down and looks at the issues board but would have to see if a given scenario, or rather the tasks within the scenario, applies to them or not, so they would have to open them individually and look at the tasks. Is that right or am I missing something?

**Hanson, Belinda** — *1/26/2026, 8:22 PM*

Ok, they can find tasks they are assigned via their personal home page and the issue log. When they click the task, the associated parent issue appears above the title. *(image)*

**Hanson, Belinda** — *1/26/2026, 8:23 PM*

They could also use the assignee field of the scenario to assign all people working the tasks as they go.

**Hanson, Belinda** — *1/26/2026, 8:23 PM*

GitLab is flexible — there are so many ways to do something, it tends to boil down to preference and ease of use.

**Hanson, Belinda** — *1/26/2026, 8:24 PM*

Those are the first solutions that came to mind.

**Allred, Brady** — *1/26/2026, 8:25 PM*

Sounds good. Thanks for looking into it. Yes, I think most of them will experiment and find their own ways of doing things — the checklist part will be much more important than the instructions part by the end of it.

**Hanson, Belinda** — *1/26/2026, 8:28 PM*

Yes, agreed — but in theory, assigning the next person (if not yourself) to the scenario and task would allow for easier sorting from the board view.

**Hanson, Belinda** — *1/26/2026, 8:28 PM*

Another step, but in theory...

**Allred, Brady** — *1/26/2026, 8:29 PM*

So you are saying they change the assignee of the scenario and the task every time they complete a task, as a part of the handoff to the next person? That way it would show up on the issues board if they filter by assignee for themselves?

**Hanson, Belinda** — *1/26/2026, 8:31 PM*

In theory that would work, and technically they would not need to remove the scenario assignee — they could add users as a log of all assignees. It just depends on how they want to do it and what is easier for the functional teams working the scenarios.

**Hanson, Belinda** — *1/26/2026, 8:32 PM*

We want it to be as user-friendly and simple as possible, while at the same time being functional.

**Hanson, Belinda** — *1/26/2026, 8:37 PM*

But the scenario level has an assignee field — if the teams would like to use board view to search for issues requiring their attention they could use that field to do so. I hate to have them need to update another thing, but: say Scenario Demo has 5 child tasks and task 1 could be me, task 2 could be me, task 3 could be Manny — when I am done I could assign the task and scenario to him, and he would be able to locate it from the board. If steps 4 and 5 are assigned to you, he would assign it to you, etc.

**Hanson, Belinda** — *1/26/2026, 8:38 PM*

Scenario "Demo" and Child Tasks (5) — just used for the written example above.

**Allred, Brady** — *1/26/2026, 8:40 PM*

Yeah, I am wondering if that would make the most sense. I think that if you want them to be utilizing the scenarios board to move the process along, it would probably have to be something like that. Otherwise, I would imagine they will just get used to going to their home dashboard and working from there.

**Hanson, Belinda** — *1/26/2026, 8:42 PM*

Agreed — E2E is a lot different than user stories and testing, so teams will need to learn the task functions that were not utilized in user stories and testing, where we just used issues and linking as needed.

**Hanson, Belinda** — *1/26/2026, 8:46 PM*

We want it to be easy and functional for the team members who are not GitLab experts. We learn more every day and discover new things that make our process better than it was yesterday.

**Hanson, Belinda** — *1/26/2026, 8:53 PM*

Technically, assigning at the scenario level too would resolve the board search — and it's something they were doing in user stories and testing to assign to someone else. The tasks would keep track of who did what task with their individual assignee fields.

**Hanson, Belinda** — *1/26/2026, 8:53 PM*

Probably the simplest solution.

**Allred, Brady** — *1/26/2026, 8:59 PM*

Yeah, I think that is probably the route to go. With that, I could see either having the scenario start with all the people assigned to it who will have to take part in a child task, but I think it would also make sense to change the assignee of the scenario to match whoever is next in the list of tasks — so there would only be one person assigned the scenario at a time. Then the last person who gets assigned the scenario can move it to "Closed."

**Hanson, Belinda** — *1/26/2026, 8:59 PM*

**Pro:** Also easy to pick up new work from the board — assign the issue to yourself and add your name to the first task, etc.

**Hanson, Belinda** — *1/26/2026, 9:00 PM*

Yes, that sounds good — the task would keep track of who did what with their individual assignees, and the scenario would be assigned to the next user.

**Allred, Brady** — *1/26/2026, 9:02 PM*

Sounds good, we will go with that then. We will make it a part of the handoff to change the assignee on the scenario each time.

I did just think though — what if they don't know who should get the scenario next?

**Hanson, Belinda** — *1/26/2026, 9:03 PM*

I think we have a good workable solution that's easy for the end user too — that we need to enquire about, like do they assign it to a lead and have them reassign it if they don't know, etc., with a comment added.

**Hanson, Belinda** — *1/26/2026, 9:04 PM*

Let me know your thoughts. I will be back online at 7am — sound good?

**Allred, Brady** — *1/26/2026, 9:04 PM*

Sounds good, thanks for all your help today!

**Hanson, Belinda** — *1/26/2026, 9:04 PM*

np, thank you.

**Hanson, Belinda** — *1/27/2026, 1:33 PM*

**Questions the user may have:**

- **How do I know who to pass the baton to?** Based on workstream and functional area.
- **If a defect needs my attention, will I be able to see it on the scenario board?** It will be in the defect board as an issue linked to the task in the scenario.
- **How do I know which status I should set my task or scenario to?**
  - When starting a scenario, the task is marked **In Progress**.
  - If the test/step fails, it would be **Fail** and a defect would be created.
  - When the defect blocking the task is resolved, it would move to **Ready to Retest**.
  - If there is a blocker, it would be moved to **Blocked**.
  - If the task is not going to be performed during the project, it would be moved to **Deferred to Post Go-Live**.
  - If you encounter a duplicated item, it would be marked **Duplicate**.
  - When all steps are completed, mark as **Closed**.
  - If there are statuses we would like to move to the scenario level from tasks, we can do that as well.
- **At what point does a scenario or task move from Not Started to In Progress?** When the first analyst selects it and begins work.
- **When creating a defect, what type is it?** (Task, incident, or issue?) It is an **issue** and will appear on the defect board once created.
- **Does a defect block the task or the scenario or both?** It would block the task that it was created from.
- **As a part of the handoff, do I also need to change the workstream or primary function labels of the scenario?** For the task, if not already provided at creation.

**Hanson, Belinda** — *1/29/2026, 1:52 PM*

Due to where the GitLab status is created, the project could run a risk of other teams modifying them. This would disrupt testing and change issue status during testing. I will communicate with teams to not adjust the task type status, which may be of less need in their teams.

**Allred, Brady** — *1/29/2026, 1:53 PM*

Sounds good. Is there a place we should include something about that in the training checklist or presentation?

**Hanson, Belinda** — *1/29/2026, 2:00 PM*

The status will likely come in when you are making your recordings. I did not notice the checklist displaying the board specifics, but we will likely want to document the workflow itself so the team knows what to expect. Most normal work without defects will happen within a scenario via tasks and their status. The scenario board has minimal status for the End-to-End phase: **Not Started** (covered in your documents), **In Progress** — and the only 2 additional fields are **No Longer Needed** (where the scenario itself is no longer needed) and Ankit suggested a **Blocked/On Hold** status in case the scenario cannot progress due to an integration or some development contained within the tasks. I know Ginny would like the training sent to the leads today to begin their review. I will try to have test complete by today's meeting and we can discuss it more in the meeting later today — sound good? Ginny mentioned Ankit will be unable to attend today's meeting.

**Hanson, Belinda** — *1/29/2026, 2:10 PM*

The boards are done to reflect the email. The links to the boards are updated. The workflow shown here has changed and is currently being updated to reflect the current build and display the labels themselves, as we have done for other phases. I will let you know once it is updated. *(image)*

**Allred, Brady** — *1/29/2026, 2:13 PM*

Sounds good, thank you!

**Hanson, Belinda** — *1/29/2026, 2:48 PM*

Ok, I added you to the email with my counterpart who will officially be joining the project on Monday. Ankit is the Deloitte testing and cutover lead.

**Hanson, Belinda** — *1/29/2026, 7:49 PM*

Does this sound accurate to you?

> Good afternoon,
>
> As we prepare for the next project phase, we are working with the Training team to develop materials for the End-to-End Testing phase. This document will be presented to the teams as we introduce the upcoming testing activities. During your review, please add any suggestions or comments using the comment feature. Kindly refrain from making direct edits to the document slides. We ask that all comments and feedback be submitted by **February 5, 2026**.
>
> Thank you!

**Allred, Brady** — *1/29/2026, 7:49 PM*

That looks great to me! Thanks for getting it out!

**Hanson, Belinda** — *1/29/2026, 7:50 PM*

Or was it the 6th?

**Hanson, Belinda** — *1/29/2026, 7:51 PM*

And that is the correct link to the document I believe — just verifying before I click send.

**Allred, Brady** — *1/29/2026, 7:52 PM*

I am pretty sure she said the 5th. And yes, this is the right link.

**Hanson, Belinda** — *1/29/2026, 7:52 PM*

Awesome, sending now.

**Hanson, Belinda** — *1/29/2026, 7:54 PM*

When sending, not all recipients will have access to the document.

**Hanson, Belinda** — *1/29/2026, 7:54 PM*

Can I give you the audience to verify access to the document?

**Allred, Brady** — *1/29/2026, 7:56 PM*

I can make a link that lets anyone at UF access it. I thought that one would, but maybe I can just make it so anyone at UF can access it in general somehow.

**Hanson, Belinda** — *1/29/2026, 7:56 PM*

Recipients:

- Jeffers, Nicole Garvey — <ngarvey@ufl.edu>
- Ciccarelli, Meagan — <meciccarelli@deloitte.com>
- Wuertz, Amber D — <amccurry@ufl.edu>
- Ling, Laura B — <lbling@ufl.edu>
- Malley, Andrew — <anmalley@deloitte.com>
- Gopinath, Ashwin — <ashwingopinath@ufl.edu>
- ankitkumar48 — <ankitkumar48@deloitte.com>
- Ahuja, Ginny — <ginny.ahuja@ufl.edu>
- Cadwallader, Gwynn — <gcadwallader@ufl.edu>
- Allred, Brady — <brady.allred@ufl.edu>
- Delara, Manny — <mdelara@ufl.edu>

If it's just Ankit, it may be due to access until he is fully onboarded.

**Allred, Brady** — *1/29/2026, 7:57 PM*

That is probably why — I think the highest permission I can give is "anyone at UF can edit," but if he isn't UF-affiliated yet then I don't think it would work.

**Allred, Brady** — *1/29/2026, 7:59 PM*

I gave them access specifically — it didn't say that it didn't work.

**Hanson, Belinda** — *1/29/2026, 8:00 PM*

*(image)*

**Allred, Brady** — *1/29/2026, 8:01 PM*

They should be notified I gave them access, even if that link doesn't work.

**Hanson, Belinda** — *1/29/2026, 8:02 PM*

Ok, I can also add a disclaimer: "If you are having difficulty using the document link, please let us know."

**Allred, Brady** — *1/29/2026, 8:03 PM*

Yeah, that would probably be fine. Worst case we can give them a local copy and they can just send us their comments.

**Hanson, Belinda** — *1/29/2026, 8:03 PM*

Yeah, sounds good.

**Hanson, Belinda** — *1/29/2026, 8:05 PM*

Ok, sent — fingers crossed lol.

**Allred, Brady** — *1/29/2026, 8:05 PM*

Haha, no worries. We probably won't hear about any problems till tomorrow or Monday.

**Hanson, Belinda** — *1/29/2026, 8:05 PM*

No error on the last try so we may be fine.

**Hanson, Belinda** — *1/29/2026, 8:06 PM*

Oh exactly.

**Hanson, Belinda** — *1/30/2026, 6:03 PM*

📄 [E2E slide deck uf version2.pptx](#) — these are both working for me?

**Allred, Brady** — *1/30/2026, 6:07 PM*

Try now.

**Allred, Brady** — *1/30/2026, 6:07 PM*

Sorry, it deleted from my desktop but not the Teams location.

**Hanson, Belinda** — *1/30/2026, 6:08 PM*

Ok cool, now I can't.

**Allred, Brady** — *1/30/2026, 6:08 PM*

Thanks for checking! Would have missed that.

**Hanson, Belinda** — *1/30/2026, 6:08 PM*

np, just wanted to verify before sending the update. 🙂

**Hanson, Belinda** — *2/17/2026, 3:00 PM*

I don't think it affects your recordings, but I did go in and update test with the name changes — like "Fix" to "Ready to Retest" and added "Not Started" to the boards. Very minor visual changes. We did them in prod and the slide deck notes, and I just applied them to test to match. Let me know if there is anything I missed. I also added a link to reporting to make it easier to locate — could be temporary so it's only in the test readme — but should not alter anything.

**Allred, Brady** — *2/17/2026, 3:02 PM*

Perfect, thank you so much! I don't think it will impact the recordings much — they don't go into many statuses.

**Hanson, Belinda** — *2/17/2026, 3:03 PM*

Exactly.

**Hanson, Belinda** — *2/17/2026, 3:03 PM*

I keep misplacing the link to the reports, and the scenario ones were erroring since yesterday — so it's all fixed. I reached out to Ashwin this morning.

**Hanson, Belinda** — *2/17/2026, 3:04 PM*

So I added it to the readme in test. I may apply a disclaimer if they want it in prod, noting that if it doesn't load you are missing a role.

**Hanson, Belinda** — *2/17/2026, 3:04 PM*

If they want it there.

**Allred, Brady** — *2/17/2026, 3:05 PM*

That would be good — would probably mean less questions for your team later.

**Hanson, Belinda** — *2/17/2026, 3:11 PM*

Indeed.

**Allred, Brady** — *2/17/2026, 7:06 PM*

Hey Belinda, I get a 404 error with that link — is that due to permission restrictions for my GitLab account?

🔗 [https://gitlab.it.ufl.edu/es/empowering-uf/end-to-end-testing](https://gitlab.it.ufl.edu/es/empowering-uf/end-to-end-testing)

**Hanson, Belinda** — *2/17/2026, 7:06 PM*

Yes, you have access to test, not prod.

**Allred, Brady** — *2/17/2026, 7:07 PM*

Perfect, just wanted to make sure. Thank you!

**Hanson, Belinda** — *2/17/2026, 7:07 PM*

np
