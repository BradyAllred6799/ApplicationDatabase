# Workday E2E GitLab Validation Checklist

**University of Florida — Training & Organizational Development**
*Information Technology | Program Management Office — 4/16/2026*

---

## Table of Contents

- [Section 0: Accessing the Project](#section-0-accessing-the-project)
- [Section 1: Objective Selection](#section-1-objective-selection)
- [Section 2: Create a New Scenario and Child Tasks](#section-2-create-a-new-scenario-and-child-tasks)
- [Section 3: Execution (Finding Work)](#section-3-execution-finding-work)
- [Section 4: Task Outcome](#section-4-task-outcome)
- [Section 5: Task Passed Successfully, and a Handoff is Required](#section-5-task-passed-successfully-and-a-handoff-is-required)
- [Section 6: Task and Scenario Testing is Complete](#section-6-task-and-scenario-testing-is-complete)
- [Section 7: Defect Logging](#section-7-defect-logging)
- [Section 8: Accessing Reports](#section-8-accessing-reports)

---

## Section 0: Accessing the Project

We are shifting from Unit Testing (Sprints 1–3) to End-to-End Collaborative Testing. Your actions in GitLab now trigger dependencies for other departments.

Follow the *Actions* to perform the task. Use the *Validation* checklist to confirm completion.

### Actions

- Navigate to the [End to End Testing](https://gitlab.it.ufl.edu/es/empowering-uf/end-to-end-testing) project in GitLab and sign in.
- Navigate to Plan > Issue Boards.

### Validation

- [ ] Successfully logged in via UF SSO.
- [ ] The "End to End Testing" project landing page is visible.

---

## Section 1: Objective Selection

Select your current goal to determine where to start:

- I need to create a **NEW Test Scenario**. → Go to Section 2
- I have tasks and need to **work on them**. → Go to Section 3
- I need to **view the Status Reports**. → Go to Section 8

---

## Section 2: Create a New Scenario and Child Tasks

> **Note:** GitLab does not have required fields. Follow these steps exactly.

### Create a New Scenario

- Make sure you are in the **Scenarios** board.
- Click the Plus (+) icon in the "Open" column.
- Give the Scenario a title that describes the overall testing.
- Click **Create Issue**.
- Select the **Edit** button at the top right corner of the Scenario Pop-Up.
- Click "Choose a template" below "Description" and select your Functional Template.
- Click **Apply Template**.
- Fill in all the indicative data related to your scenario in the description.
- Click **Save Changes**.
- Click **Edit** next to Labels.
- Type "Relative Size" into the search bar and select a Relative Size (Small, Medium, Large) according to the urgency of the scenario.
- Once the appropriate labels are checked, click **Apply**.
- Click **Edit** next to Milestone.
- Select the Current Phase (E2E 1a, 1b, 2, etc.).

#### Validation

- [ ] Scenario created using the correct Functional Template.
- [ ] The scenario has at least one assignee.
- [ ] Relative Size Label (S, M, or L) is applied.
- [ ] The correct Milestone is assigned.

---

### Link Dependencies

- If a scenario or task cannot start until another is finished, link it. In the Scenario or task you are working on, scroll to **Linked Items** and click **Add**.
- Check the **"blocks"** option if this scenario must be completed before another can start, or **"is blocked by"** if another must be completed before this one can start.
- Click the search bar below "the following items" and type the name of the related scenario or task.
- Click **Add**.

#### Validation

- [ ] Dependencies (Blocked by/Blocks) are linked to the scenario if applicable.

---

### Create a Child Task

- In the Parent Scenario, navigate to **Child Items** and click the **Add** dropdown.
- Select **New Task**.
- Give the Task a concise title that describes its purpose.
- Click **Create Task**, and repeat for however many tasks you need. Ensure the order is correct — the first task to be completed should be at the top of the list, and the last at the bottom.
- Click on the name of the new task to open it (side-by-side view or new window depending on current view).
- Click **Edit** in the top right corner of the task.
- The Default template is applied automatically. Fill out the table within the description field according to this specific task.
- Click **Save Changes**.
- Click **Edit** next to Assignees in the right-hand menu. Select the appropriate assignee(s) based on who needs to complete this step, then click **Apply**.
- Click **Edit** next to Labels in the right-hand menu to update the Primary Functional Area and Workstream.
  - Type "Primary" and select the appropriate Primary Functional Area from the dropdown.
  - Do the same for "Workstream."
- Click **Edit** next to Milestone in the right-hand menu to update the Milestone.
- Navigate back to the Parent Scenario by clicking the Scenario name in the Parent section of the right-hand menu.

#### Validation

- [ ] Child Tasks have been created for the scenario.
- [ ] The correct template has been applied to the description and is filled in.
- [ ] The task has at least one assignee.
- [ ] The task has the correct Primary Functional Area label applied.
- [ ] The task has the correct Workstream label applied.
- [ ] The task has been linked to the correct milestone.
- [ ] Dependencies (Blocked by/Blocks) are linked to the task if applicable.

---

## Section 3: Execution (Finding Work)

### Actions

- Navigate to Plan > Issue Boards.
- Make sure you are in the **Scenarios** board.
- Select the filter bar at the top of the board.
- Click **Assignee** > **"= is"** > your name. This filter ensures you only see scenarios assigned to you.
- Click the magnifying glass icon to apply the filter.
- Select a scenario from the Open or In Progress columns. Prioritize by Relative Size label: **Large first, then Medium, then Small**.
- Click the scenario number above the title to open it in full-screen view.
- If the scenario is not already in progress, add the In Progress status label. Click **Edit** next to Labels.

> **⚠ ATTENTION:** The statuses of Scenarios and Defects are treated differently from tasks. **Scenarios and Defects** change status via the **Labels** tool. **Tasks** change status via the **status tool**. Make sure you are using the correct tool in the correct instance.

- Type "Scenario Status" in the box and select the **Scenario Status::In Progress** label.
- Click **Apply**.
- Select the task assigned to you under "Child Items." This opens the task in the side panel with the parent scenario on the left — keep this view to reference indicative data from the parent.
- **Verify Order:** Ensure all previous tasks in the list are marked "Passed" before starting your task (e.g., Task 1 must be done before starting Task 2).
- Change the status of the task to **In Progress** via the status tool.

> **⚠ ATTENTION:** Scenarios and Defects change status via the **Labels** tool. Tasks change status via the **status tool**.

- Use the Indicative Data table on the left (Parent) side to perform your test.
- Log the results of your test in the comments, including screenshots of the process.

### Validation

- [ ] Filtered the Scenarios board by Assignee (= Your Name).
- [ ] Selected a scenario based on priority (Relative Size: Large → Medium → Small).
- [ ] The status of the Scenario is set to "In Progress" via the Labels tool.
- [ ] Verified that previous tasks in the Child Items list are marked "Done" before starting.
- [ ] The status of the task is set to "In Progress" via the status tool.
- [ ] Test results logged in the comments, including screenshots.

---

## Section 4: Task Outcome

Depending on the results of your test, select the applicable path:

- **Task Passed Successfully, and a Handoff is Required** (sending to another department) → Go to Section 5
- **Task and Scenario Testing is Complete** (success) → Go to Section 6
- **Task Failed** (defect/blocker) → Go to Section 7

---

## Section 5: Task Passed Successfully, and a Handoff is Required

> **⚠ Critical:** Changing "Assignee" does **NOT** send a notification. You must comment.

### Actions

- Change the status of the task to **Passed** via the Status tool.
- Click the **X** at the top right to close the task pane and return to the parent scenario.
- Change the owner of the scenario to the assignee of the next task. Scroll to Child Items to view the next task.
- Hover over the assignee icon of the next task to view their username.
- Scroll to comments and type **@username** to tag the new owner. Include a note that your task passed and you are assigning it to them.
- Post the comment.
- Remove yourself as the assignee to the scenario and change it to the assignee of the next task.

### Validation

- [ ] Your task status is set to Passed via the status tool.
- [ ] The new owner of the scenario is the owner of the next task in the list.
- [ ] New owner is explicitly tagged (@name) in the comments.

---

## Section 6: Task and Scenario Testing is Complete

### Actions

- Change the status of the task to **Passed** via the Status tool.
- Click the **X** at the top right to close the task pane and return to the parent scenario.
- Make sure there are no other tasks to be completed in the scenario, and all tasks passed.
- Paste any required proof/screenshots into the comment box of the scenario, with a note confirming the test passed.
- Change the status dropdown of the scenario from Open to **Closed** via the Status tool.

> **⚠ ATTENTION:** This is the **only time** you should use the status tool in a Scenario.

### Validation

- [ ] Your task status is set to Passed.
- [ ] All other tasks in the scenario are set to Passed.
- [ ] Confirmation comment (with evidence if required) is posted.
- [ ] Parent Scenario is marked Closed.

---

## Section 7: Defect Logging

### Actions

- Change the status of the task to **Failed** via the Status tool.

> **Note:** Only use "Blocked" if you are unable to start the test due to an integration or system error.

- Copy the current **Task ID** (e.g., #123) located at the top of the task panel.
- Click the three dots (⋮) and select **New related item**.
- Change the type to **"Issue."**
- Enter a title for the Defect briefly describing the problem.
- Change the Template to **Defect**.
- Type a description of the defect. Use screenshots for proof of the problem.
- Locate the text `/blocks #[Task Number]` in the template and replace `[Task Number]` with your Task ID (e.g., `/blocks #123`).
- Click **Edit** next to Labels.
- Type "Workstream" into the box and select the appropriate workstream for this defect.
- Before closing the Labels editor, apply a **Defect Focus Area** label. Type "Defect Focus" and select the appropriate label.
- Before closing the Label Editor, apply a **Priority** label. Type "Priority" into the box.
  - The template default is set to Low. Change if needed based on the following guidelines:
    - **High:** Defect blocks task completion.
    - **Medium:** Workaround is available.
    - **Low:** Cosmetic issues only.
- Click **Apply**.
- Remove the **"Defect Focus Area: None"** label.
- Click **Create Issue**.
- Close the new issue pop-up.
- Navigate to Issue Boards.
- Change the board from "Scenario" to **"Defects."**
- Scroll in the Open column to ensure the new defect is present.
- Open the defect and ensure the linked items section shows it is blocking the appropriate task.

### Validation

- [ ] Task status changed to Failed.
- [ ] New Defect Issue created using the Defect Template.
- [ ] Defect is correctly linked as "blocks" to the original Task ID.
- [ ] Workstream and Defect Focus Area labels are applied.
- [ ] Priority Label (High, Medium, or Low) accurately reflects the impact on testing.
- [ ] Defect is visible on the Defects Board in the "Open" column.

---

## Section 8: Accessing Reports

### Actions

- Request the security role **UF_N_Powering** to access.
- Visit the [PowerBI Dashboard](https://app.powerbi.com/groups/me/apps/d18e2eb6-53b9-466b-8fd1-4c59e9efd727/reports/8b9592d1-da5e-483c-af37-1169a976355c/a1282359c21481ec8d28?ctid=0d4da0f8-4a31-4d76-ace6-0a62331e1b84&portalSessionId=fd3a4013-5c16-44db-a9b4-59fe64cdbc0b&experience=power-bi) to track Scenarios, Tasks, and Defects.

### Validation

- [ ] You have security role UF_N_Powering.
- [ ] You can see and track reports in the PowerBI Dashboard.
