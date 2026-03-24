# Product Build Record — Church Expense Coordination App
> Instance of the Corporate Intelligence Framework — Product
> [Church Name] United Methodist Church

---

## Document Control

| Field | Value |
|---|---|
| **Initiative Name** | Church Expense Coordination App |
| **Record Type** | Growth Initiative |
| **Validation Stage** | Prototype |
| **Status** | Scoping |
| **Author** | Treasurer |
| **Created** | 2026-03-14 |
| **Last Updated** | 2026-03-14 |
| **Target Release** | [TBD] |
| **Actual Release** | |
| **Linked Business Case** | Church-Business-Case.md |
| **Prior Build Record(s)** | First in sequence |
| **Linked Strategy Goal** | SG-020 — Lightweight expense coordination tool |

> **Significant Change Log**

| Date | What Changed | What It Was Before | Why It Changed | Connected Artifacts Affected |
|---|---|---|---|---|
| 2026-03-14 | Initial creation | No prior version | Framework instantiation — Prototype stage | Church-Business-Case.md |

---

## 1. Problem Statement

### 1.1 Context

The church tracks expenses through a shared Google Sheet — an improvement over prior practice that provides visibility but no workflow. Two users interact with expense data: the Office Administrator who enters expenses and the Treasurer who reviews and reconciles them. Both users access the same flat spreadsheet with no role differentiation, no review signal, and no structured entry guidance.

The church's accounting system of record is QuickBooks Desktop Pro. The Google Sheet is a coordination layer, not a replacement for QuickBooks. This application extends that coordination layer with a browser-based interface, basic identity and access management, and structured expense entry — while continuing to use the existing Google Sheet as its data source.

### 1.2 Problem Definition

**The problem is:** The Treasurer and Office Administrator have no structured workflow for expense entry, review, and status tracking — coordination happens informally with no persistent record, and misclassifications are discovered at month-end rather than at entry.

**We know this is a problem because:** The current shared spreadsheet provides a single flat view with no role differentiation, no entry guidance, no status tracking, and no coordination signal between users.

**If we don't solve this:** Misclassifications continue to accumulate until month-end reconciliation, restricted fund entries remain at risk of error, and the Treasurer cannot review expenses remotely without direct QuickBooks access.

### 1.3 Opportunity

A lightweight browser-based application — built specifically around the church's chart of accounts and two-person workflow — can provide structured entry, basic IAM, and expense status tracking at no ongoing cost. The prototype validates whether this approach improves the coordination workflow before committing to a production build.

**Prototype learning goal:** Does a browser-based interface with guided entry and role-based login improve the accuracy and coordination of expense tracking for the Treasurer and Office Administrator?

---

## 2. Goals and Success Metrics

### 2.1 Business Goals

- Validate that a browser-based interface with Google Sheets as a data source is technically viable for this use case
- Confirm that the expense entry flow is intuitive enough for the Office Administrator without accounting knowledge
- Establish a foundation for role-based access that can be extended in future iterations

### 2.2 User Goals

- **Office Administrator**: Enter an expense quickly, select the correct expense type from a curated list, and know that the entry is complete and visible to the Treasurer
- **Treasurer**: See all entered expenses, search by vendor/description/amount, and understand the status of each expense without opening QuickBooks

### 2.3 Success Metrics (KPIs)

| Metric | Baseline | Target | Measurement Method |
|---|---|---|---|
| Expense entry time | [Current avg. time to enter in spreadsheet] | Equal or faster | Observation during prototype test |
| Expense type selection accuracy | [Current misclassification rate — TBD] | Reduction vs. baseline | Treasurer review of prototype entries vs. QuickBooks |
| Administrator confidence in entry | Unknown | Administrator reports feeling guided, not guessing | Post-test conversation |

### 2.4 Non-Goals — Prototype Stage

The following are explicitly out of scope for this prototype and flagged for future iterations:

- **Treasurer review / approve / return workflow** — deferred to next iteration; high value but adds complexity beyond prototype scope
- **Budget-vs-actual reporting** — stays in QuickBooks for now
- **Finance Committee read-only view** — stays in QuickBooks for now
- **Predictive expense type suggestion** — deferred; AI-assisted classification is a future iteration
- **Mobile app** — browser only for prototype
- **Offline capability** — requires Google Sheets connectivity

---

## 3. Users and Personas

> Reference Church-Roles-and-Personas.md for full persona detail.

### 3.1 Primary User

**Persona**: Office Administrator
**Key Need**: Enter expenses quickly with guided account selection — no accounting expertise required
**Pain Point**: No feedback loop on whether entries are correct; unclear which expense type to use for ambiguous items

### 3.2 Other Relevant Roles

| Role Type | Persona | Relevance to This Initiative |
|---|---|---|
| User | Treasurer | Reviews entered expenses, searches by vendor/description/amount, monitors payment status |
| Internal Affected Party | Finance Committee | Not users of the prototype — reporting stays in QuickBooks; access design should anticipate future read-only view |

### 3.3 Out of Scope

- Finance Committee members — not users in this prototype
- Ministry staff and Committee Chairs — submit expenses through the Office Administrator; do not interact with the app directly
- Pastor — not a user in this prototype

---

## 4. Cost Estimate

### 4.1 Estimate Stage
ROM (Rough Order of Magnitude) — Prototype stage

### 4.2 Estimate Provenance
Treasurer estimate based on AI-assisted development approach

### 4.3 ROM Estimate

| Element | Estimate | Notes |
|---|---|---|
| Google OAuth setup and IAM | 2–4 hours | Google Cloud Console configuration + React auth flow |
| Google Sheets API integration | 2–4 hours | Read expense types tab; read/write expense entries tab |
| Expense entry form | 3–5 hours | Form fields, validation, submission to Sheets |
| Expense search and status view | 2–4 hours | Query Sheets data, display results with status |
| UI / layout | 2–3 hours | Basic responsive layout — not production-grade |
| Testing and iteration | 2–4 hours | Structured test with Office Administrator |
| **Total ROM** | **13–24 hours** | Wide range reflects unknowns in Sheets API integration |

### 4.4 Ongoing Cost

| Element | Cost | Notes |
|---|---|---|
| Hosting (local prototype) | $0 | Runs on Treasurer's machine during prototype phase |
| Hosting (remote — Vercel free tier) | $0 | Free tier sufficient for two-user prototype; enables remote access |
| Google Sheets API | $0 | Free within Google Workspace / personal Google account limits |
| Google OAuth | $0 | Free for this usage level |

---

## 5. Functional Requirements

### 5.1 Authentication and IAM

| ID | Requirement | Priority | Notes |
|---|---|---|---|
| REQ-001 | User must authenticate via Google OAuth before accessing any app function | P0 | Leverages existing Google accounts — no separate credential management |
| REQ-002 | System must recognize two roles: Treasurer and Office Administrator | P0 | Role assigned by email address match against a defined list — no self-registration |
| REQ-003 | Unauthorized Google accounts must be denied access with a clear message | P0 | Only the two defined users can log in |
| REQ-004 | Role differentiation must be in place architecturally even if functionality is identical in this prototype | P0 | Foundation for future role-based feature separation |
| REQ-005 | User must be able to log out | P1 | |

### 5.2 Expense Entry

| ID | Requirement | Priority | Notes |
|---|---|---|---|
| REQ-010 | User must be able to enter a new expense with: Description, Amount, Vendor / Reimbursement Target | P0 | All three fields required |
| REQ-011 | User must be able to select an Expense Type from a curated list | P0 | List sourced from existing Google Sheet expense types tab — not free-text |
| REQ-012 | User must be able to indicate payment method: Church Credit Card or Direct Remittance | P0 | Determines whether payment is immediate or waits for credit card statement |
| REQ-013 | User must be able to indicate receipt status: Received Electronically (yes / no) | P0 | Flags whether documentation is in hand |
| REQ-014 | Entered expense must be written to the Google Sheet immediately on submission | P0 | Google Sheet remains the data store |
| REQ-015 | Submitted expense must default to status: Pending | P0 | |
| REQ-016 | Entry form must validate required fields before submission — no silent incomplete entries | P0 | |
| REQ-017 | Entry form must confirm successful submission to the user | P0 | Clear success state — user knows the entry landed |

### 5.3 Expense Search and Status

| ID | Requirement | Priority | Notes |
|---|---|---|---|
| REQ-020 | User must be able to search previously entered expenses by Vendor / Reimbursement Target | P0 | Partial match acceptable |
| REQ-021 | User must be able to search previously entered expenses by Description | P0 | Partial match acceptable |
| REQ-022 | User must be able to search previously entered expenses by Amount | P1 | Exact match or range TBD |
| REQ-023 | Search results must display: Description, Amount, Vendor, Expense Type, Payment Method, Receipt Status, and current Status | P0 | |
| REQ-024 | Status must display as: Pending or Paid (with date paid when applicable) | P0 | Status and paid date read from Google Sheet |
| REQ-025 | Search with no results must display a clear empty state — not an error | P0 | |

---

## 6. User Stories

### Story 1: Office Administrator enters a new expense

**As an** Office Administrator,
**I want to** enter a new expense with the relevant details and select the correct expense type from a list,
**so that** the Treasurer can see it immediately and I know my entry is complete and correctly classified.

**Acceptance Criteria:**
- [ ] AC-001: Given I am logged in, when I navigate to New Expense, then I see a form with Description, Amount, Vendor/Reimbursement Target, Expense Type selector, Payment Method selector, and Receipt Status toggle
- [ ] AC-002: Given I complete all required fields and submit, then the expense appears in the Google Sheet within 5 seconds
- [ ] AC-003: Given I submit successfully, then I see a confirmation message and the form resets for the next entry
- [ ] AC-004: Given I attempt to submit with a required field empty, then I see an inline validation message and submission is blocked

**Priority:** P0

---

### Story 2: Treasurer searches for a specific expense

**As a** Treasurer,
**I want to** search for a previously entered expense by vendor name, description, or amount,
**so that** I can quickly find a specific entry and see its current status without scrolling through the full sheet.

**Acceptance Criteria:**
- [ ] AC-005: Given I enter a vendor name (partial or full) in the search field, then I see all matching expenses with their full details and status
- [ ] AC-006: Given I enter a description term in the search field, then I see all matching expenses
- [ ] AC-007: Given my search returns no results, then I see a clear message — not an error or blank screen
- [ ] AC-008: Given an expense has been paid, then the status shows "Paid" with the date paid

**Priority:** P0

---

### Story 3: User logs in with Google OAuth

**As a** Treasurer or Office Administrator,
**I want to** log in with my existing Google account,
**so that** I don't need a separate username and password and my access is controlled by the Treasurer.

**Acceptance Criteria:**
- [ ] AC-009: Given I navigate to the app, then I see a "Sign in with Google" prompt
- [ ] AC-010: Given I sign in with an authorized Google account, then I am granted access and see my role displayed
- [ ] AC-011: Given I sign in with an unauthorized Google account, then I am denied access with a clear message
- [ ] AC-012: Given I am logged in, then I can log out and am returned to the sign-in screen

**Priority:** P0

---

## 7. Non-Functional Requirements

### 7.1 Performance
- [ ] Expense submission must complete within 5 seconds under normal conditions
- [ ] Search results must return within 3 seconds for a sheet with up to 500 expense entries

### 7.2 Security and Compliance
- [ ] Authentication must use Google OAuth — no passwords stored in the application
- [ ] Google Sheet must not be publicly accessible — access controlled at the Google Drive level
- [ ] Only authorized email addresses may access the application — role list maintained by Treasurer

### 7.3 Accessibility
- [ ] Form fields must have visible labels
- [ ] Required field errors must be clearly indicated

### 7.4 Reliability
- [ ] If Google Sheets API is unavailable, the app must display a clear error rather than silently failing or losing data

---

## 8. Dependencies and Constraints

### 8.1 Dependencies

| Dependency | Type | Owner | Status | Risk if Delayed |
|---|---|---|---|---|
| Google Sheet — expense types tab | Internal data | Treasurer | Ready | Blocks expense type selector |
| Google Sheet — expense entries tab | Internal data | Treasurer | Needs confirmation of column structure | Blocks write and search functions |
| Google Cloud Console project | Technical | Treasurer | Not yet created | Blocks OAuth and Sheets API setup |
| QuickBooks chart of accounts cleanup | Organizational | Treasurer | In progress | App expense type list should reflect stable accounts — launch after cleanup is substantially complete |

### 8.2 Constraints

- **Cost**: No paid services — all components must operate on free tiers
- **Users**: Two users only for prototype — Treasurer and Office Administrator
- **Data store**: Google Sheet is the data store for prototype — no separate database
- **Accounting system**: QuickBooks Desktop Pro remains the system of record — this app does not replace it
- **Timeline**: Prototype should be testable before the next Finance Committee meeting if possible

---

## 9. Open Questions

| # | Question | Owner | Due Date | Resolution |
|---|---|---|---|---|
| 1 | What is the column structure of the existing Google Sheet expense entries tab? Does it need a new tab for app-entered expenses, or will entries go into the existing sheet? | Treasurer | | |
| 2 | What Google account will be used for the Google Cloud Console project — personal or a church-owned Google account? | Treasurer | | |
| 3 | Should the app show all expenses entered by either user, or only expenses entered by the logged-in user? | Treasurer | | |
| 4 | Who sets the "Paid" status and date — the Treasurer manually in the sheet, or will the app have a mark-as-paid function? | Treasurer | | |
| 5 | What is the expense approval threshold — below which Treasurer alone approves vs. Finance Committee involvement? This affects future iteration scope but should be understood now | Finance Committee | | |
| 6 | Should Committee Chairs eventually have read-only access to their specific budget lines? Affects IAM architecture decisions made in prototype | Treasurer / Finance Committee | | |

---

## 10. Test and Validation

### 10.1 Validation Strategy

**Primary question this prototype answers:** Is a browser-based interface with Google Sheets as a data source a viable and usable foundation for the church expense coordination workflow?

**Validation method:** Structured hands-on test with the Office Administrator using realistic expense scenarios.

**Success definition:** The Administrator can complete all core entry tasks without assistance, expresses confidence in the expense type selection, and prefers the interface to the current spreadsheet for new expense entry.

**What would change our minds:** If the Administrator finds the interface more cumbersome than the spreadsheet, or if Google Sheets API latency makes the experience noticeably slow, we would reconsider the tech stack before building further.

### 10.2 Concept Validation

Before building, confirm with the Office Administrator:
- [ ] Walk through the proposed entry flow verbally — does it match how she currently thinks about entering an expense?
- [ ] Review the expense type list — are the categories clear and complete for her most common entries?
- [ ] Confirm the payment method distinction (credit card vs. direct remittance) is meaningful to her current process

### 10.3 Pilot Validation

Structured test with Office Administrator — 3–5 realistic expense entry scenarios:

| Scenario | Type | Success Criteria |
|---|---|---|
| Enter a utility payment (credit card) with receipt | Routine entry | Completes without assistance; correct expense type selected |
| Enter a reimbursement to a staff member (direct remittance) | Reimbursement entry | Correctly identifies payment method; completes without confusion |
| Enter an expense for a ministry program budget line | Class-sensitive entry | Selects correct expense type; Treasurer can identify the right QuickBooks class from the entry |
| Search for a previously entered vendor | Search | Returns correct results within expected time |
| Attempt to submit with a missing required field | Validation | Sees clear error; understands what to fix |

### 10.4 Validation Sign-Off

| Role | Name | Approval | Date |
|---|---|---|---|
| Treasurer | | | |
| Office Administrator | | | |

---

## 11. Agent Handoff Instructions

### 11.1 Objective

Build a browser-based React application that uses Google OAuth for authentication, Google Sheets as the data source, and provides two core functions: structured expense entry and expense search with status display.

### 11.2 Inputs

- [ ] This Product Build Record (requirements and acceptance criteria)
- [ ] Google Sheet ID and tab names (to be provided by Treasurer before build begins)
- [ ] Authorized user email addresses for role assignment (Treasurer and Office Administrator)
- [ ] Google Cloud Console project credentials (OAuth client ID and Sheets API key)

### 11.3 Explicit Constraints

- **Do not** create a database — Google Sheets is the data store for this prototype
- **Do not** implement the Treasurer review/approve/return workflow — explicitly deferred
- **Do not** implement budget-vs-actual reporting — out of scope
- **Do not** use any paid services or APIs — free tier only
- **Do not** store credentials in the codebase — use environment variables
- **Do not** make the Google Sheet publicly accessible

### 11.4 Ambiguity Protocol

1. Check Open Questions (Section 9) first
2. For Google Sheets column structure questions — wait for Treasurer input before assuming
3. For UI layout decisions not specified — choose the simplest option that satisfies the acceptance criteria
4. Flag any assumption made in a code comment marked `// ASSUMPTION:`
5. Log new questions discovered during build in Section 9

### 11.5 Definition of Done

- [ ] All P0 requirements in Section 5 are implemented
- [ ] All P0 acceptance criteria in Section 6 are passing
- [ ] Google OAuth login works with authorized email list
- [ ] Expense entry writes to Google Sheet correctly
- [ ] Expense search returns results from Google Sheet
- [ ] No credentials stored in code — environment variables used
- [ ] App runs locally with `npm start` or equivalent
- [ ] Vercel deployment instructions documented for remote access

---

## 12. Execution Log

| Date | Entry | Author |
|---|---|---|
| 2026-03-14 | Product Build Record created — Prototype stage | Treasurer |

---

## 13. Actuals and Retrospective

> To be completed after prototype build and validation test.

### 13.1 Cost Actuals

| Element | Estimated | Actual | Variance |
|---|---|---|---|
| Total build hours | 13–24 hours | | |

### 13.2 Variance Analysis
[To be completed]

### 13.3 Benefit Realization

For a Prototype, benefit realization is measured against learning goals:
- [ ] Did we answer the primary prototype question? (viable tech stack + usable interface)
- [ ] What did the Administrator validation test reveal?
- [ ] What changes to the approach are indicated before the next build record?

### 13.4 Reference Class Record

| Field | Value |
|---|---|
| **Actual duration** | [TBD] |
| **Complexity factors** | Google OAuth setup, Sheets API integration, two-user IAM |
| **What took longer than expected** | [TBD] |
| **What was faster than expected** | [TBD] |

### 13.5 Retrospective Notes
[To be completed after validation test]
