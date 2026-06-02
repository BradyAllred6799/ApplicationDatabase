# Finding and Changing a Spend Authorization

This guide explains how to locate an existing Spend Authorization in Workday and make changes to it when updates are needed before or after approval. Use this guide any time trip details change and the Spend Authorization needs to be corrected or updated.

[NOTE] A Spend Authorization can only be changed if an Expense Report has not yet been submitted against it. Once an Expense Report is submitted, the Spend Authorization is locked and cannot be edited. [1]

## Before You Begin

- Confirm that no Expense Report has been submitted against the Spend Authorization you need to change.
- Have the relevant trip details on hand, such as updated travel dates, destinations, or funding information.
- Be aware that resubmitting a changed Spend Authorization will restart the full approval workflow from the beginning. [1]

## Finding a Spend Authorization

There are two ways to locate an existing Spend Authorization in Workday: the Find Spend Authorizations report and the Expenses Hub. Both methods bring you to the same information.

### Method 1: Using the Find Spend Authorizations Report

Use this method for in-depth searches or when you need to filter by specific criteria such as traveler name, document number, or date range.

1. Type **Find Spend Authorizations** into the [Clicks:Search Bar] at the top of the Workday home page.
2. Select the [Clicks:Find Spend Authorizations] report from the search results.
3. In the filter box, enter one or more of the following criteria to narrow your search:
   - Company
   - Spend Authorization Status
   - For (the employee traveler)
   - Payee Type
   - Document Number
   - Created by Worker
   - Spend Start or End Date
   - Created On or Before / On or After
   - Approved On or Before / On or After
4. Click [Clicks:OK] to run the report.
5. Review the results. Each row displays the Spend Authorization Number, Description, traveler name, Payee Type, Company, travel dates, created date, approval status and date, total and remaining balance, currency, and links to related expenses.

[IMAGE] The Find Spend Authorizations filter screen in Workday with example search criteria entered, such as company and traveler name.

[TIP] If you cannot find the request you are looking for, try broadening your search criteria — for example, removing date filters or searching by traveler name only.

### Method 2: Using the Expenses Hub

Use this method for quick day-to-day access and status checks on recently submitted Spend Authorizations.

1. Select [Clicks:Menu] in the top left corner of the Workday home page.
2. Select [Clicks:Expenses Hub] from the menu.
3. In the left side panel, select [Clicks:Spend Authorizations].
4. Review the list of submitted Spend Authorizations and their current statuses.
5. Select any Spend Authorization from the list to view its details.

[IMAGE] The Expenses Hub in Workday showing the Spend Authorizations panel with a list of submitted requests and their statuses.

[NOTE] Only submitted Spend Authorizations appear in the Expenses Hub. Drafts saved for later will not appear in this view. [1]

## Changing a Spend Authorization

Once you have located the Spend Authorization that needs to be updated, follow the steps below to make changes and resubmit it for approval.

1. Locate the Spend Authorization using either method described above.
2. Select the [Clicks:Actions] dropdown next to the Spend Authorization you need to edit.
3. Select [Clicks:Change Spend Authorization] from the dropdown menu.

[IMAGE] The Spend Authorization report list in Workday with the Actions dropdown open and the Change Spend Authorization option highlighted.

4. On the Change Spend Authorization page, update the fields that require correction. You can edit most fields, including:
   - Travel start and end dates
   - Destinations and origination points
   - Estimated amounts
   - Worktags and funding details
   - Supporting documentation and attachments
   - Memo and justification details
5. Document the reason for your changes in the [Clicks:Memo] or [Clicks:Justification] field so approvers understand what was updated and why.
6. Review all fields carefully to confirm all information is accurate before resubmitting.
7. Select [Clicks:Submit] to resubmit the Spend Authorization for approval.

[IMAGE] The Change Spend Authorization page in Workday with updated fields visible, such as revised travel dates or corrected worktags.

[WARNING] When you resubmit a changed Spend Authorization, Workday will display an alert indicating that the previously approved request is now routing through the approval process again. Read this alert carefully before confirming. The full approval workflow restarts from the beginning. [1]

## After Resubmitting

Once the updated Spend Authorization is resubmitted, it re-enters the standard approval workflow:

- **Domestic travel** — Routes to the Manager, then the Cost Center Coordinator, then the Financial Approver(s).
- **International travel** — Routes to the Manager, then the RISC Office, then the Cost Center Coordinator, then the Financial Approver(s).
- **Split funding** — May route to multiple Financial Approvers concurrently based on the funding sources entered.

[TIP] Communicate proactively with approvers to let them know a revised Spend Authorization is coming their way. This helps avoid confusion and keeps the approval process moving efficiently. [1]

## Key Rules to Remember

- A Spend Authorization **cannot be changed** after an Expense Report has been submitted against it.
- **Only the Cost Center Coordinator** can edit a Spend Authorization during the approval workflow. If you are not a Cost Center Coordinator and need a correction made mid-workflow, ask an approver to send the request back to you.
- Resubmitting a changed Spend Authorization **restarts the full approval workflow** — the request does not resume where it left off.
- Always double-check all entries before resubmitting to avoid unnecessary additional rounds of review.
- Travel **cannot be booked or purchases made** until the updated Spend Authorization has completed the full approval process again.
