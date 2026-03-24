# Business Case: Church Expense Coordination App
> Instance of the Corporate Intelligence Framework — Product
> [Church Name] United Methodist Church

---

## Document Control

| Field | Value |
|---|---|
| **Initiative Name** | Church Expense Coordination App |
| **Author** | Treasurer |
| **Sponsor** | Finance Committee |
| **Date** | 2026-03-14 |
| **Status** | Draft |
| **Decision Needed By** | [TBD] |
| **Related Build Record(s)** | [To be created — Prototype stage] |

> **Significant Change Log**

| Date | What Changed | What It Was Before | Why It Changed | Connected Artifacts Affected |
|---|---|---|---|---|
| 2026-03-14 | Initial creation | No prior version | Framework instantiation | Strategy-and-Intent, Roles-and-Personas |
| 2026-03-14 | Proposed initiative scope narrowed — Finance Committee reporting and budget-vs-actual removed | Proposed initiative included Finance Committee read-only view, budget-vs-actual reporting, and export/report generation | Scope decision: these capabilities stay in QuickBooks for the foreseeable future; app scope limited to expense entry, search, and status for Treasurer and Office Administrator | Roles-and-Personas, Internal-Stakeholders |

---

## 1. The One-Paragraph Summary

The church currently tracks expenses through a shared spreadsheet — a significant improvement over prior practice, but one that provides visibility without workflow. Expenses are entered but not reviewed in a structured way, misclassifications are discovered at month-end, and there is no coordination signal between the Treasurer and Office Administrator. This Business Case proposes building a lightweight, custom expense coordination tool tailored to the church's specific chart of accounts and two-person workflow. The tool is free to operate, requires no paid software, and is scoped specifically to the church's needs — something no general-purpose business expense tool provides at this scale. The recommendation is to build a Prototype, validate the workflow with the Treasurer and Office Administrator, and proceed to a simple production application if the prototype confirms the approach.

---

## 2. Problem or Opportunity

### 2.1 The Problem

The church's expense tracking and coordination between the Treasurer and Office Administrator has two distinct gaps:

**Gap 1 — No review workflow.** Expenses entered by the Office Administrator are not reviewed by the Treasurer until month-end QuickBooks reconciliation. Misclassifications — wrong account, wrong class, missing restricted fund designation — accumulate between entry and discovery. Corrections at month-end are time-consuming and create reconciliation complexity.

**Gap 2 — No coordination signal.** There is no shared indicator of what has been reviewed, what is pending, or what needs attention. The Treasurer and Administrator coordinate informally — by email, phone, or in-person conversation — with no persistent record of what was discussed or decided.

**Why this matters:**
- Misclassifications in restricted fund accounts (memorial fund, committee budgets) create compliance risk — donor-designated funds must be used per donor intent
- Month-end corrections erode confidence in the interim numbers the Finance Committee sees
- The Treasurer cannot review entries remotely without direct QuickBooks access
- The Administrator has no feedback loop — no way to know if an entry was correct until the Treasurer mentions it

### 2.2 The Opportunity

The church's use case is small and specific enough that a purpose-built tool — designed around the actual chart of accounts, the actual two-person workflow, and the actual reporting needs of the Finance Committee — will outperform any general-purpose tool. The opportunity is to build something that fits the church's situation exactly, at no ongoing cost, and that makes the Treasurer's oversight and the Administrator's entry both faster and more accurate.

---

## 3. Proposed Initiative

Build a lightweight web-based expense coordination application with the following core capabilities:

**For the Office Administrator:**
- Guided expense entry — account and class selection presented in plain language mapped to the QuickBooks chart of accounts
- Receipt status indicator (received electronically yes/no)
- Payment method selection (church credit card or direct remittance)
- Status indicator — shows whether an entry is Pending or Paid

**For the Treasurer:**
- Remote visibility of all entered expenses and their status
- Expense search by vendor, description, or amount
- Status tracking — Pending or Paid with date

**What is explicitly deferred to future iterations:**
- Treasurer review / approve / return workflow — high value, out of scope for prototype
- Budget-vs-actual reporting — stays in QuickBooks for the foreseeable future
- Finance Committee read-only view — stays in QuickBooks for the foreseeable future
- Predictive expense type suggestion — future iteration

**What it is not:**
- A replacement for QuickBooks — the church's accounting system of record remains QuickBooks Desktop Pro
- A reporting tool — financial reporting to the Finance Committee and congregation stays in QuickBooks
- A full accounting system — it is a coordination and entry layer that feeds into QuickBooks
- A paid service — hosted and operated at no ongoing cost

---

## 4. Alternatives Considered

| Alternative | Description | Why Ruled Out |
|---|---|---|
| **Continue with shared spreadsheet** | Current state — shared Google Sheet or Excel for expense tracking | Provides visibility but no workflow — no review signal, no coordination, no guided entry. Misclassifications continue to be discovered at month-end. |
| **Shared QuickBooks access** | Give the Administrator direct QuickBooks Desktop Pro entry rights | QuickBooks Desktop Pro is single-user by design — concurrent access is not supported without upgrade. Requires the Administrator to navigate full accounting software, which is beyond the scope of their role. High error risk without guided entry. |
| **Commercial expense tool (Expensify, Concur, etc.)** | General-purpose business expense management software | Designed for business reimbursement workflows, not church fund accounting. Cannot be configured around a specific chart of accounts and class structure. Monthly subscription cost is unjustified for a two-person workflow at this scale. |
| **QuickBooks Online upgrade** | Move from Desktop Pro to QBO with multi-user access | Ongoing subscription cost. Migration effort. QBO still does not provide the guided, church-specific entry experience the Administrator needs. Solves the access problem but not the workflow or guidance problems. |

---

## 5. Expected Benefits

| Benefit | Type | Estimate | Basis |
|---|---|---|---|
| Reduced month-end correction time | Cost reduction — Treasurer time | [Est. X hours/month saved] | Currently spends [Y hours] on retroactive corrections |
| Earlier detection of misclassifications | Risk reduction | Qualitative | Errors caught at entry vs. at month-end close |
| Reduced coordination overhead | Cost reduction — both users | [Est. X hours/month saved] | Currently requires separate email/phone coordination for unclear entries |
| Improved QuickBooks data quality | Quality improvement | Qualitative | Guided entry reduces misclassifications before they reach QuickBooks — cleaner source data improves all downstream reporting |
| Restricted fund compliance confidence | Risk reduction | Qualitative | Memorial and designated fund entries reviewed before close reduces compliance risk |

> Benefit estimates to be refined based on Treasurer's assessment of current time spent on corrections and coordination.

---

## 6. Estimated Cost and Effort

### 6.1 Build Cost

| Element | Estimate | Notes |
|---|---|---|
| **Prototype build** | [Est. X hours] | Treasurer + AI-assisted development; no external contractor |
| **Chart of accounts configuration** | [Est. X hours] | Mapping QuickBooks accounts and classes to app entry options |
| **Testing with Office Administrator** | [Est. X hours] | Structured workflow test before any production use |
| **Total Prototype effort** | [Est. X hours] | |

### 6.2 Ongoing Cost

| Element | Cost | Notes |
|---|---|---|
| **Hosting** | $0 — [TBD hosting approach] | Target: free tier hosting (GitHub Pages, Vercel, or similar) |
| **Maintenance** | Treasurer time — as needed | Account list updates when QuickBooks changes |
| **Software licenses** | $0 | No paid dependencies |

### 6.3 Key Dependency

The app's chart of accounts must mirror QuickBooks exactly at go-live. The QuickBooks cleanup must be substantially complete before the app is configured. If accounts change in QuickBooks after go-live, the app must be updated in parallel — this is the primary ongoing maintenance obligation.

---

## 7. Risks

| Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|
| QuickBooks cleanup not complete at app go-live | Medium | High — account mismatch creates reconciliation errors | Treat cleanup completion as a go-live prerequisite; do not launch app with provisional accounts |
| Office Administrator does not adopt the new tool | Low-Medium | High — tool only works if both users use it | Involve Administrator in prototype testing; design entry flow around her current process, not against it |
| App account list drifts from QuickBooks over time | Medium | Medium — gradual reconciliation errors | Document account sync as a Key Operational Process; update app whenever QuickBooks changes |
| Prototype reveals the workflow assumption is wrong | Low | Low — this is why we prototype | Prototype is explicitly designed to surface this; findings feed directly into production design |

---

## 8. Recommendation and Decision Request

**Recommendation:** Approve a Prototype build.

The shared spreadsheet has demonstrated that both users will adopt a shared tool when it fits their workflow. The prototype extends that foundation with a review workflow and guided entry — two specific gaps the spreadsheet cannot address. The cost is Treasurer time only. The risk is low — a prototype that doesn't work is a learning, not a loss.

**Decision requested:** Finance Committee awareness and informal approval to proceed with a Prototype. No budget commitment required — build cost is Treasurer time. Formal approval of a production application to follow if the Prototype validates the approach.

**Proposed next step:** Build Prototype → Test with Office Administrator → Review findings with Finance Committee → Decision on production build.

---

## 9. Open Questions

| # | Question | Owner | Due Date | Resolution |
|---|---|---|---|---|
| 1 | What is the expense approval threshold — below which the Treasurer alone approves vs. Finance Committee involvement? | Finance Committee | | |
| 2 | Should Committee Chairs have read-only access to their specific budget lines, or only the Treasurer and Finance Committee see all accounts? | Treasurer / Finance Committee | | |
| 3 | What hosting approach is preferred — local only, church network, or cloud-hosted? | Treasurer | | |
| 4 | Is the Office Administrator aware of and supportive of this initiative? | Treasurer | | |
| 5 | What is the target go-live date for the Prototype test? | Treasurer | | |
