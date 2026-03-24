# Roles and Personas — Church Expense Coordination App
> Instance of the Corporate Intelligence Framework — Market and Customer
> User and stakeholder archetypes for the church expense coordination application.
> Covers the people who use, are affected by, or influence the application —
> not every role in the organization. See Internal-Stakeholders for the full org map.

---

## Document Control

| Field | Value |
|---|---|
| **Organization** | [Church Name] — United Methodist Church |
| **Maintainer** | Treasurer |
| **Status** | Active |
| **Last Updated** | 2026-03-14 |

> **Connected artifacts:**
> - **Internal-Stakeholders** — all roles here exist in the org structure there; application access levels defined there
> - **Product-Build-Record** — Section 3 (Users and Personas) references the primary user and other relevant roles from this document
> - **Strategy-and-Intent** — the coordination goal this application serves is defined there

> **Significant Change Log**

| Date | What Changed | What It Was Before | Why It Changed | Connected Artifacts Affected |
|---|---|---|---|---|
| 2026-03-14 | Initial creation | No prior version | Framework instantiation for church expense coordination project | Product-Build-Record |
| 2026-03-14 | Finance Committee and Pastor removed as application users — reporting stays in QuickBooks for foreseeable future | Finance Committee Member and Pastor listed as secondary read-only users of the application | Scope decision: budget-vs-actual reporting and Finance Committee read-only view deferred; QuickBooks remains the reporting system of record | Internal-Stakeholders, Business-Case |

---

## 1. How to Use This Document

This application has two primary users with meaningfully different needs and very different relationships to accounting. The Treasurer has deep financial context and owns accuracy. The Office Administrator has operational context and owns speed and volume. The application must serve both without requiring either to work outside their natural domain.

The Finance Committee and Pastor are not application users in this prototype or near-term plan — financial reporting stays in QuickBooks. The application access design should anticipate future read-only access for these roles without implementing it now.

---

## 2. User Personas

### 2.1 The Treasurer (Full Persona)

---

**Persona Name**: "The Treasurer"
**Use Case**: Church expense coordination, financial reporting, QuickBooks reconciliation
**Role**: Treasurer — part-time volunteer with accounting/financial background
**Last Validated**: 2026-03-14
**Research Basis**: Direct — this persona is the artifact author

#### Who They Are
A part-time volunteer with financial expertise, responsible for the accuracy of the church's books, the integrity of the chart of accounts, and the quality of financial reporting to the Finance Committee and congregation. Currently leading a QuickBooks Desktop Pro chart of accounts cleanup — consolidating accounts, resolving misclassifications, and establishing class tracking for fund and committee separation. Reports to the Finance Committee.

#### Jobs to Be Done
- Ensure all expenses are classified correctly against the right account and class before month-end close
- Review and approve expense entries made by the Office Administrator without having to be physically present
- Generate accurate, readable financial reports for the Finance Committee and congregation
- Catch and correct misclassifications before they compound
- Maintain a clear record of what was spent, by whom, against which budget line

#### Pain Points
- No reliable way to review Administrator-entered expenses in real time — currently dependent on periodic QuickBooks exports or in-person review
- Misclassifications discovered at month-end require retroactive corrections that create reconciliation complexity
- Coordination happens informally — email, phone, verbal — with no shared record of what has been reviewed and approved
- Restricted fund and memorial fund transactions require extra care that is easy to miss in a busy month

#### Adoption Drivers
- Immediate visibility into expenses as they are entered — no lag
- Ability to flag or correct a misclassification before it hits QuickBooks
- A clear audit trail of what was reviewed and approved

#### Adoption Risks
- If the application adds steps without reducing errors or review time, it will be abandoned in favor of the existing informal process
- If the chart of accounts in the application doesn't match QuickBooks exactly, it creates a reconciliation problem rather than solving one

#### Success Looks Like
Month-end close requires no retroactive corrections. The Treasurer can see all entered expenses and their status from anywhere without needing to be in the office or open QuickBooks directly. Finance Committee reporting continues through QuickBooks.

---

### 2.2 The Office Administrator (Full Persona)

---

**Persona Name**: "The Office Administrator"
**Use Case**: Day-to-day expense entry, vendor payment coordination, receipt management
**Role**: Office Administrator — full-time staff
**Last Validated**: 2026-03-14
**Research Basis**: Inferred from role and current process — validate with Administrator directly

#### Who They Are
A full-time staff member who manages the day-to-day administrative operations of the church — including processing expenses, coordinating vendor payments, managing receipts, and supporting ministry staff with administrative needs. Not an accountant, but operationally familiar with the church's regular expense categories. Currently enters or coordinates most routine expenses and payments.

#### Jobs to Be Done
- Enter expenses quickly and accurately without needing to know the full chart of accounts structure
- Attach or reference receipts so the Treasurer has what they need for review
- Know whether an expense has been reviewed and approved without having to ask
- Flag unusual or uncertain expenses for Treasurer guidance before they're finalized
- Not get blocked by accounting complexity — needs clear, guided choices

#### Pain Points
- Chart of accounts has historically been inconsistent — unclear which account to use for similar expenses
- No feedback loop on whether entries were correct — learns about misclassifications only when the Treasurer mentions it
- Coordination with Treasurer is informal — no shared view of what's pending, what's been reviewed, what needs attention
- Restricted and memorial fund transactions require special handling that isn't always clearly communicated

#### Adoption Drivers
- Simple, guided expense entry — account choices presented in plain language, not accounting codes
- Clear confirmation that an entry has been reviewed — removes uncertainty
- Ability to flag something for Treasurer review with a note, rather than guessing

#### Adoption Risks
- Any interface that requires accounting knowledge beyond their current level will create errors and frustration
- If the application is slower than the current process for routine entries, it will be bypassed
- If the Treasurer doesn't respond to flagged items promptly, the feedback loop breaks down

#### Success Looks Like
The Administrator enters expenses confidently, knowing the account choices are correct. Unusual items get flagged to the Treasurer without requiring a separate conversation. No misclassifications reach month-end.

---

## 3. Gatekeeper Personas

### 3.1 The Finance Committee (Lightweight)

---

**Persona Name**: "The Finance Committee"
**Function**: Financial oversight and governance
**Last Validated**: 2026-03-14

**Who They Are**: Volunteer committee members with varying levels of financial background, responsible for oversight of the church's finances. Review Treasurer reports monthly. Do not enter transactions. Their concern is whether the reports are accurate, readable, and show the church is operating within budget.

**Their Specific Concerns**:
- Are reports clear enough for members without accounting backgrounds to understand?
- Is the church on budget by category?
- Are restricted funds being handled appropriately?

**What Resolves Their Concern**: A clean, readable monthly report — budget vs. actual by category, restricted fund balances clearly separated, no unexplained variances.

**Blocking Behaviors**: If the application's coordination workflow creates more work for the Treasurer without meaningfully reducing errors or coordination overhead, the Finance Committee will question the value of the change. Note: the Finance Committee does not interact with the application directly — reporting stays in QuickBooks.

---

## 4. Internal Affected Party Personas

### 4.1 Ministry Staff and Committee Chairs (Lightweight)

---

**Persona Name**: "The Ministry Budget Owner"
**Function**: Youth, Children/Family, Music, Outreach, UMM, UWiF, and similar
**Last Validated**: 2026-03-14

**Who They Are**: Part-time staff or volunteer committee chairs who spend against a specific ministry budget line. They submit receipts or expense requests to the Office Administrator. They do not use the application directly but their spending flows through it.

**How They Are Affected**: If the account and class structure in the application correctly maps to their ministry budget, their expenses land in the right place. If it doesn't, their budget reporting is wrong.

**What They Need**: Clear guidance from the Office Administrator on how to submit expenses (what receipts are needed, what information to provide). They should not need to know the chart of accounts themselves.

**Change Management Implications**: When the application goes live, the Office Administrator needs a simple intake process for ministry expense submissions — a form, a standard email format, or a shared folder for receipts — so that incoming expenses are structured enough to enter quickly and accurately.

---

## 5. Open Questions

| # | Question | Owner | Due Date | Resolution |
|---|---|---|---|---|
| 1 | Does the Office Administrator currently enter expenses directly into QuickBooks, or into a separate system/spreadsheet? | Treasurer | | |
| 2 | What does the Administrator currently do when they're unsure which account to use — guess, ask the Treasurer, or leave it blank? | Treasurer / Administrator | | |
| 3 | How does the Administrator currently receive expense requests from ministry staff — email, paper, verbal? | Treasurer / Administrator | | |
| 4 | When should Finance Committee read-only access be added to the application — after the prototype validates the core workflow, or as part of the first production build? | Treasurer / Finance Committee | | |
| 5 | Should the Pastor have access to the application, or is a monthly summary report sufficient? | Pastor / Treasurer | | |
