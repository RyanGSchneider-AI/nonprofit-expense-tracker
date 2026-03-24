# Strategy and Intent — [Church Name]
> Instance of the Corporate Intelligence Framework — Organizational Intelligence
> Living organizational goals and the reasoning behind them for [Church Name] UMC.
> Scoped to the near-term financial coordination effort — not a full church strategic plan.

---

## Document Control

| Field | Value |
|---|---|
| **Organization** | [Church Name] — United Methodist Church |
| **Maintainer** | Treasurer |
| **Status** | Active |
| **Last Updated** | 2026-03-14 |

> **Connected artifacts:**
> - **Funding-and-Business-Model** — organizational drivers and horizon there are consistent with the goals here
> - **Internal-Stakeholders** — goals here have identifiable owners in the org structure there
> - **Business-Case** — the expense coordination app initiative is the primary connected initiative to the current focus goal below
> - **Roles-and-Personas** — capability needs implied by goals here map to the user types defined there

> **Significant Change Log**

| Date | What Changed | What It Was Before | Why It Changed | Connected Artifacts Affected |
|---|---|---|---|---|
| 2026-03-14 | Initial creation | No prior version | Framework instantiation scoped to financial coordination effort | Business-Case, Funding-and-Business-Model |

---

## 1. How to Use This Document

This document is scoped to the near-term financial coordination effort — it is not a full church strategic plan. Goals here reflect the Treasurer's operational mandate and the Finance Committee's current priorities. Broader congregational strategy (membership growth, capital campaigns, ministry direction) is outside the scope of this instantiation.

---

## 2. Organizational Mission and Vision

**Mission**: To make disciples of Jesus Christ for the transformation of the world — the mission of the United Methodist Church, locally expressed through worship, community, outreach, and pastoral care.

**Vision**: A financially stable, transparently governed congregation that sustains its ministry programs, maintains its facilities, and serves its community with integrity.

**Core Values** (as they relate to financial stewardship):
- Transparency — the congregation deserves accurate, readable financial reporting
- Stewardship — every dollar given is a trust to be managed carefully
- Accessibility — financial processes should not require accounting expertise to participate in

---

## 3. Strategic Goals

### 3.1 Long-Term Goals

---

**Goal ID**: SG-001
**Goal**: Maintain a financially stable church with adequate operating reserves and well-maintained facilities
**Owner**: Finance Committee / Treasurer
**Last Updated**: 2026-03-14

**Why This Goal**:
The church operates on voluntary giving with seasonal variation and no commercial revenue. Without operating reserves, a short giving period creates immediate operational risk. Facilities are aging and deferred maintenance compounds over time. Stability requires both a financial cushion and a proactive approach to building stewardship.

**Key Results / Success Indicators**:
- Operating reserves at [target months] of operating expenses
- No deficit spending in any fiscal year
- Deferred maintenance backlog identified and prioritized by Trustees annually

**Connected Initiatives**:
- Annual budget process
- Trustee facilities assessment

**Notes**: Reserve target to be established by Finance Committee.

---

### 3.2 Near-Term Goals

---

**Goal ID**: SG-010
**Goal**: Establish accurate, reliable financial reporting that the Finance Committee and congregation can trust
**Owner**: Treasurer
**Last Updated**: 2026-03-14

**Why This Goal**:
The current Treasurer inherited a chart of accounts with misclassifications, inconsistent account usage, and reporting that did not clearly reflect the church's financial position. Correcting this is a prerequisite for any meaningful financial decision-making — budgeting, reserve planning, capital expenditure evaluation. Trust in the numbers must be established before the numbers can be used.

**Key Results / Success Indicators**:
- QuickBooks chart of accounts cleanup complete — all accounts correctly typed, named, and classified
- Class tracking in place for all restricted funds and committee budgets
- Monthly Finance Committee report produced from accurate data with no manual adjustments required
- Congregation-facing annual report clearly separates unrestricted operating funds from restricted and endowment funds

**Connected Initiatives**:
- QuickBooks chart of accounts cleanup (in progress)
- Church expense coordination app — Business-Case-Church-Expense-App.md

**Notes**: The cleanup and the app are sequentially dependent — the app's chart of accounts must match QuickBooks exactly or it creates a reconciliation problem rather than solving one.

---

### 3.3 Current Focus

---

**Goal ID**: SG-020
**Goal**: Create a lightweight expense coordination tool that allows the Treasurer, Office Administrator, and Committee Chairs to stay coordinated on church expenses without requiring accounting expertise or paid software
**Owner**: Treasurer
**Due**: [Target date TBD]
**Last Updated**: 2026-03-14

**Why This Goal**:
The current shared spreadsheet provides visibility but no workflow. Expenses are entered but not reviewed in a structured way. Misclassifications are discovered at month-end rather than at entry. There is no clear signal to the Administrator that an entry has been reviewed, or to the Treasurer that something needs attention. A lightweight custom tool built around the church's specific chart of accounts and workflow can solve this without the cost or complexity of a general-purpose business expense tool.

**Success Conditions**:
- Treasurer can review and approve expense entries remotely without accessing QuickBooks directly
- Office Administrator can enter expenses with guided account selection — no accounting expertise required
- Misclassifications are caught at entry, not at month-end
- Finance Committee can view a clean budget-vs-actual summary without requesting it from the Treasurer

**Connected Initiatives**:
- Business-Case-Church-Expense-App.md

**Notes**: This is a Prototype-stage initiative. The goal is to validate the workflow before building a production-grade application.

---

## 4. Strategic Assumptions and Risks

### 4.1 Strategic Assumptions

---

**Assumption ID**: SA-001
**Assumption**: The Office Administrator is willing and able to adopt a new expense entry tool if it is simpler than the current spreadsheet process
**Category**: Organizational
**Basis**: The spreadsheet is already in use — the Administrator has demonstrated willingness to use a shared tool. Simplification should reduce resistance.
**Confidence**: Medium
**How We'd Know If It's Wrong**: Administrator reverts to paper or email-based expense submission after the tool is introduced
**Last Reviewed**: 2026-03-14

---

**Assumption ID**: SA-002
**Assumption**: The QuickBooks chart of accounts cleanup will be substantially complete before the app goes live
**Category**: Organizational
**Basis**: Cleanup is actively in progress. App and cleanup are treated as sequential — app account list mirrors QuickBooks.
**Confidence**: Medium
**How We'd Know If It's Wrong**: Cleanup stalls and app is needed before accounts are stable — would require managing two account structures simultaneously
**Last Reviewed**: 2026-03-14

---

### 4.2 Strategic Risks

---

**Risk ID**: SR-001
**Risk**: App account structure diverges from QuickBooks over time as accounts are added or changed in one system but not the other
**Category**: Operational
**Likelihood**: Medium
**Impact if realized**: Reconciliation errors accumulate; month-end corrections required; erodes trust in the tool
**Connected Assumption**: SA-002
**Early Warning Signals**: Treasurer notices account options in app don't match QuickBooks during reconciliation
**Response**: Establish a simple update process — any QuickBooks account change triggers an app update; document as a Key Operational Process
**Last Reviewed**: 2026-03-14

---

## 5. Goal History

| Goal ID | Goal | Outcome | Date Closed | Notes |
|---|---|---|---|---|
| — | — | — | — | No closed goals yet |

---

## 6. Open Questions

| # | Question | Owner | Due Date | Resolution |
|---|---|---|---|---|
| 1 | What is the Finance Committee's target operating reserve level? | Finance Committee | | |
| 2 | What is the target go-live date for the expense coordination app? | Treasurer | | |
| 3 | Should the app eventually replace the shared spreadsheet entirely, or run alongside it during a transition period? | Treasurer / Office Administrator | | |
