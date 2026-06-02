# End-to-End Workflow

*Teams working in the End to End Testing project will follow this basic workflow.*

---

## Slide 1 — End-to-End Workflow

Teams working in the End to End Testing project will follow this basic workflow.

---

## Slide 2 — Context: Why This Phase is Different

*(Visual slide — no additional text content)*

---

## Slide 3 — The 'Golden Rule' of The Testing Process

*(Visual slide — no additional text content)*

---

## Slide 4 — Key Terminology

Use this translation guide:

| GitLab Term | Testing Term | Description |
|---|---|---|
| **Issue** | Test Scenario | The container for the whole test |
| **Child Tasks** | Test Steps | The ordered list of actions to complete the scenario |
| **Defects** | Bugs/Failures | Logged at the task or scenario level when a test fails |
| **Board** | Dashboard | Visual status of work |
| **Milestone** | Testing Phase | e.g., E2E 1, PCT |
| **Linked Items** | Dependencies | Connects defects or blocking items to the scenario |

---

## Slide 5 — Test Scenario Examples

> Test scenario descriptions should include assumptions about the scenario. Tasks outline high-level actions — not each step of a Workday business transaction.

### Example 1 — FIN/RES: Purchase a microscope for a faculty member's new lab

**Indicative Data fields:** Name, Company, Cost Center, Fund, Program, Gift, Grant, Designated, Project, Activity, Assignee, Initiative, Budget Year, Spend Category, Additional Testing Scenario Data

**Tasks:**

1. Create purchase requisition
2. Run task: Connect to Supplier Website and Punchout to Jaggaer
3. In Jaggaer, "return the cart" after shopping
4. Submit Purchase Requisition
5. Create and Issue PO
6. Upon Approval of Requisition, PO is auto-sourced
7. Department Receives Microscope
8. INT XXX — Jaggaer pushes invoice into Workday
9. Supplier Invoice Approval
10. …

### Example 2 — HCM/PAY: Hire an out-of-state non-academic staff salaried campus employee

**Indicative Data fields:** Name, Worker Type, Worker Sub-Type, EMPLID, Position Number, Job Profile, Pay Group, Unions, Exempt/Non-Exempt, Salary/Hourly, AWP, DPP, Flexible Work Arrangement, Supervisory Organization, Manager

**Tasks:**

1. Create job requisition
2. Post Job
3. Candidate Applies
4. Review and Interview
5. Offer
6. INT XXX – Background Check
7. Ready to Hire
8. Hire
9. …

**Legend:** Integration | Recruiting | Core HR | Procurement | Supplier Accounts

*Speaker: Meagan / Ekanth*

---

## Slide 6 — How It Connects

**Hierarchy:** Test Scenario → Child Tasks → Defect

*(Visual diagram slide)*

---

## Slide 7 — Controls & Quick Tips: What if…?

*(Visual slide — no additional text content)*

---

## Slide 8 — Navigation and Information

*(Visual slide — no additional text content)*

---

## Slide 9 — All Scenarios will need to be created in GitLab

*(Visual slide — no additional text content)*

---

## Slide 10 — Scenario Workflow

*(Visual diagram slide)*

---

## Slide 11 — Create a New Scenario

Start by navigating to your board and clicking the "+" at the top of the first column.

---

## Slide 12 — Recording Walkthrough: Create a Scenario

*(Walkthrough recording slide)*

---

## Slide 13 — Scenario Statuses

| Status | Description |
|---|---|
| **Open** | Default status |
| **Scenario Status \| In Progress** | The test run has been started or is underway but not yet complete |
| **Scenario Status \| Blocked/On Hold** | A test cannot be executed as an underlying business process or integration is in error |
| **Scenario Status \| No Longer Needed** | No longer relevant and will not be completed |
| **Closed** | Closed status |

---

## Slide 14 — Create Child Tasks

Now that you have created a scenario, the next step is creating the tasks needed.

---

## Slide 15 — Recording Walkthrough: Create a Child Task

*(Walkthrough recording slide)*

---

## Slide 16 — Child Task Statuses

| Status | Description |
|---|---|
| **Not Started** | The task has been identified and logged but not yet reviewed or assigned |
| **In Progress** | The task has been started or is underway but not yet complete |
| **Failed** | The actual task results did not match the expected results. A defect will need to be created |
| **Ready for Re-test** | The defect tied to the task that initially failed has been addressed; the task is now ready to be retested |
| **Blocked** | The task cannot be executed as an underlying business process or integration is in error |
| **Skipped** | The task has been skipped to the next test cycle/phase. Please leave comments describing the reason |
| **Passed** | Task was completed successfully and executed with expected results |
| **No Longer Needed** | No longer relevant and will not be completed |
| **Duplicate** | Duplicate task |
| **Closed** | Task is completed |

---

## Slide 17 — Find and Execute A Task

*(Visual slide — no additional text content)*

---

## Slide 18 — Recording Walkthrough: Find and Execute a Task

*(Walkthrough recording slide)*

---

## Slide 19 — Create a New Defect

> **Navigation notes:** Clicking the defect under linked items will navigate the user to the defect in full screen. Clicking the parent work item will open it in a side-by-side view. If the defect was created from a child task, clicking the link at the top will navigate back to the Scenario in a full screen view when you are done.

---

## Slide 20 — Recording Walkthrough: Create a Defect

*(Walkthrough recording slide)*

---

## Slide 21 — Defect Statuses

| Status | Description |
|---|---|
| **Open** | Default status |
| **Defect Status \| Not Started** | The defect has been identified and logged but not yet reviewed or assigned |
| **Defect Status \| In Progress** | The defect is currently being worked on by the assigned developer or team member |
| **Defect Status \| Under Fix** | The defect requires a fix and the fix is being implemented |
| **Defect Status \| Fixed** | The defect has been fixed and the task related to the defect is now ready to be retested |
| **Defect Status \| Reopened** | The defect was closed (as Fixed) and the same defect has been detected and requires further action |
| **Defect Status \| Stalled** | The defect resolution is on hold pending some other action (e.g., an integration is needed prior to working on the defect) |
| **Defect Status \| Not a Defect** | The defect is invalid |
| **Defect Status \| Change Request** | The defect does not match any business/design requirement and is considered a change request |
| **Closed** | The defect has been fixed and the test scenario related to the defect is now ready to be retested |

---

## Slide 22 — Reporting & Verification Phase

This dashboard tracks the health of the E2E Project.

- **To Access:** You must request the security role **UF_N_EMPOWERING**.
- Once approved, you can access interactive Power BI reports to track your Scenarios, Tasks, and Defects.

---

## Slide 23 — Detailed Reports

| Report | Details |
|---|---|
| **Scenario Tracking** | Number of Scenarios by Status; option to filter by Author, Milestone, and Labels; direct navigation through GitLab URLs |
| **Defect Status Tracking** | Number of Defects by Status; option to filter by Author, Milestone, and Labels; details related to linked tasks; direct navigation through GitLab URLs |
| **Task Tracking** | Number of Tasks by Status; option to filter by Author, Milestone, and Labels; details related to Parent Scenarios; direct navigation through GitLab URLs |
| **Hierarchical Data** | View of hierarchical relationship between a Scenario, Task, and Defect via a Tree or Matrix; ability to drill-through at each type and view detailed information |

**More to Come:**

- \# and % daily scenario/task/defect that have passed
- \# and % daily scenario/task/defect that have failed
- \# and % cumulative scenario/task/defect that have passed
- \# and % cumulative scenario/task/defect that have failed

---

## Slide 24 — Q&A

**Next Step:** Download the Checklist and log in.
