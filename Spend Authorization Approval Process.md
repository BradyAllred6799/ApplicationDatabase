# Spend Authorization Approval Process Overview

This guide explains the full approval workflow for Spend Authorizations at the University of Florida. It covers the roles involved in the approval process, what each role is responsible for, and the actions available at each stage. Understanding this process helps ensure that travel requests are reviewed efficiently, accurately, and in compliance with UF policy.

[NOTE] A Spend Authorization must be fully approved before any travel is booked, travel-related purchases are made, or the traveler departs on official university business.

## How the Approval Workflow Works

When a Spend Authorization is submitted in Workday, the system automatically determines the approval route based on the funding sources, worktags, and roles assigned. The workflow is not chosen manually — Workday builds the routing path dynamically.

The two most common routing paths are:

- **Employee submitted for themselves** — Routes directly to the Manager for review.
- **EDES submitted on behalf of an employee** — The worker (employee traveler) must approve first, then the request routes to the Manager.

[NOTE] If the same person holds more than one role in the approval workflow, Workday automatically skips duplicate approval steps for that individual. No one can approve their own transaction.

## Approval Routing Scenarios

The table below summarizes how routing differs based on submission type and travel category.

- **Domestic – Self-Submitted:** Manager → Cost Center Coordinator → Financial Approver(s)
- **Domestic – EDES-Submitted:** Worker → Manager → Cost Center Coordinator → Financial Approver(s)
- **International – EDES-Submitted:** Worker → International Travel Attestation → Manager → RISC Office → Cost Center Coordinator → Financial Approver(s)
- **Split Funding:** Financial Approvers for each funding source may be routed concurrently at the same time.
- **Special Circumstances:** Additional approvers such as UAA Spend Compliance, Student Financial Aid, Grant Manager, Gift Manager, or C&G Accountant may be added as needed.

## Approver Roles and Responsibilities

### Worker (Employee Traveler)

The Worker is the first approver when a Spend Authorization has been submitted by an EDES on their behalf.

**Responsibilities:**

- Review the Spend Authorization to confirm all trip details are accurate, including dates, destinations, business purpose, and estimated costs.
- Approve the request to confirm the information is correct before it routes forward.
- For international travel submitted by an EDES, complete the **International Travel Attestation** immediately after approving.

**Available Actions:**

- Approve
- Send Back (with instructions for the EDES to correct)

[NOTE] If the employee submitted the Spend Authorization for themselves, this worker approval step is skipped and the request routes directly to the Manager.

---

### International Travel Attestation

For international travel created by an EDES on behalf of a worker, the worker must complete an attestation after their approval and before the request continues in the workflow.

**The attestation requires the worker to:**

- Confirm the Spend Authorization accurately represents their intended travel plans as they relate to UF business.
- Acknowledge the policies and directives associated with international travel.
- Certify that they will register with UFIC's International Travel and Insurance Registry.

[WARNING] This attestation step is mandatory for international travel submitted by an EDES. The request will not route to the Manager until it is completed.

---

### Manager

The Manager reviews the Spend Authorization for business need, documentation completeness, and policy compliance.

**Responsibilities:**

- Confirm the traveler name and company are correct.
- Verify travel start and end dates are accurate and reasonable.
- Review the Business Purpose and Justification fields to ensure the five Ws (Who, What, Where, When, Why) are clearly addressed and the trip supports UF's mission.
- Review each line item for correct destinations, reasonable estimated amounts, and appropriate funding worktags.
- Verify that any cash advance request includes a Cash Advance Justification and that the circumstances genuinely require one.
- Review all attachments such as conference agendas, cost comparisons, or third-party confirmations.

**Available Actions:**

- [Clicks:Approve] — Confirms the request is complete, accurate, and policy-compliant. Routes to the Cost Center Coordinator (or RISC Office for international travel).
- [Clicks:Send Back] — Returns the request to the submitter with instructions for corrections.
- [Clicks:Approve and Add Approver] — Approves the request and routes it to an additional reviewer before continuing the workflow.
- [Clicks:Cancel] — Exits the task without taking action; the request remains in the inbox.

[WARNING] The Manager cannot edit a Spend Authorization directly. If corrections are needed, the request must be sent back to the submitter. Selecting [Clicks:Approve and Add Approver] constitutes an approval — only use this option when you are confident the request is approvable in its current form.

[NOTE] Any additional approver added by a Manager must hold the **Manager** security role in Workday.

[IMAGE] The bottom of the Spend Authorization approval page showing the Approve, Send Back, Approve and Add Approver, and Cancel action buttons.

---

### RISC Office (International Travel Only)

For international Spend Authorizations, after Manager approval, the request routes to the RISC Office before continuing to the Cost Center Coordinator.

**Responsibilities:**

- Review the request for compliance with university and sponsor rules related to international travel.
- Confirm the traveler is going to a safe and approved location.

**Available Actions:**

- Approve
- Send Back (with instructions)
- Add an additional approver

[NOTE] The RISC Office cannot edit a Spend Authorization. Like the Manager, they may only approve, send back, or add an approver.

---

### Cost Center Coordinator

The Cost Center Coordinator is a uniquely powerful role in the approval workflow. They are the **only approver** who can edit a submitted Spend Authorization.

**Responsibilities:**

- Review the request after Manager (and RISC Office, if applicable) approval.
- Correct any errors or add missing information — such as updating worktags — before the request moves to financial approval.
- Ensure all financial and compliance requirements are met.

**Available Actions:**

- Approve
- Edit the Spend Authorization directly (exclusive to this role)
- Send Back (with instructions)

[TIP] Because the Cost Center Coordinator is the only role that can make edits during the workflow, communicating known issues to them early can help avoid unnecessary Send Back steps and keep the process moving efficiently.

[IMAGE] The Spend Authorization detail view as seen by the Cost Center Coordinator, with editable fields visible.

---

### Financial Approver

After Cost Center Coordinator approval, the request routes to the appropriate Financial Approver based on the funding sources and worktags entered on each line.

Depending on how the trip is funded, the Financial Approver may be one of the following:

- **Cost Center Manager** — Reviews departmentally funded requests.
- **Grant Manager** — Reviews requests funded by a grant worktag.
- **Gift Manager** — Reviews requests funded by a gift worktag.
- **Project Manager** — Reviews requests funded by a project worktag.

**Responsibilities:**

- Review the funding details of the Spend Authorization based on the worktags assigned to each line.
- Confirm that the funding sources are appropriate for the travel described.

**Available Actions:**

- Approve
- Send Back (with instructions)

[NOTE] Financial Approvers cannot edit the Spend Authorization. If corrections to funding or worktags are needed, the request must be sent back. When a trip uses split funding across multiple sources, Workday may route the request to multiple Financial Approvers concurrently.

---

### Additional and Specialized Approvers

Some Spend Authorizations require routing to one or more specialized approvers depending on the nature of the trip or the funding involved. These approvals are triggered automatically by Workday based on the circumstances of the request.

Examples of specialized approvers include:

- **UAA Spend Compliance Approver**
- **Student Financial Aid**
- **Contracts & Grants (C&G) Accountant** — Required when a cash advance is requested on 201 or 209 funds.
- **Construction Project Accountant**
- **Expense Partner**

## Key Rules for All Approvers

- **No one may approve their own transaction.** Workday enforces this automatically.
- **Only the Cost Center Coordinator can edit a Spend Authorization** during the approval workflow. All other roles must send it back if corrections are needed.
- **Workday skips duplicate approval steps** automatically when the same person holds more than one role in the workflow.
- **If a Spend Authorization is changed and resubmitted**, it routes through the full approval workflow again from the beginning.
- **Travel cannot be booked and purchases cannot be made** until the Spend Authorization has been fully approved by all required roles.
- **All approvers are accountable** for the requests they approve. Thorough review before approving ensures UF funds are used responsibly.
