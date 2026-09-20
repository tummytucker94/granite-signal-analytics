# GitHub Project Setup Guide

This guide explains how to organize the Granite Signal Analytics work in GitHub Issues and GitHub Projects. It includes two options:

1. Use GitHub Copilot to create and organize the work.
2. Create the work manually through the GitHub web interface.

Repository: [tummytucker94/granite-signal-analytics](https://github.com/tummytucker94/granite-signal-analytics)

## Recommended work hierarchy

Use the following structure to divide the project:

- **Epics:** Large product areas that group related work.
- **User stories:** User-focused outcomes that can be completed independently.
- **Tasks:** Technical activities required to complete a story.
- **Sagas:** Optional cross-epic workflows that span multiple features, such as procurement or pilot validation.

### Epics

1. Product discovery and foundation
2. Core inventory management
3. Supplier and purchase-order workflows
4. Quality assurance and traceability
5. Forecasting, alerts, and anomaly detection
6. Dashboarding, reporting, and user experience
7. Security, reliability, and deployment
8. Pilot launch and measurement

### Suggested sagas

- Discovery and setup
- Inventory operations
- Procurement and receiving
- Quality assurance controls
- Analytics and exception management
- Operational visibility
- Hardening and release readiness
- Pilot validation and stabilization

## Step-by-step: Set up the project with GitHub Copilot

Copilot's exact interface and capabilities can vary by GitHub plan and environment. Review every generated issue before accepting it, especially estimates, dependencies, security requirements, and business targets.

### Option A: Use Copilot in the repository

1. Open the repository on GitHub:
   `https://github.com/tummytucker94/granite-signal-analytics`
2. Open the **Issues** tab and select the option to create a new issue or use the available Copilot-assisted issue workflow.
3. Give Copilot the project context. You can paste a prompt similar to the following:

   > In this repository, create a backlog for the Granite Signal Analytics inventory management and quality-assurance platform. Use the requirements in `REQUIREMENTS.md` and the three-month plan in `ROADMAP.md`. Create eight epic-level issues: Product discovery and foundation; Core inventory management; Supplier and purchase-order workflows; Quality assurance and traceability; Forecasting, alerts, and anomaly detection; Dashboarding, reporting, and user experience; Security, reliability, and deployment; Pilot launch and measurement. Under each epic, create user-story issues using the format "As a [role], I want [capability], so that [outcome]." Include acceptance criteria, dependencies, priority, and the roadmap month or week. Do not invent requirements that conflict with the repository documents.

4. Ask Copilot to create or refine one epic at a time rather than generating the entire backlog without review.
5. For each generated issue, verify:
   - The title clearly identifies the epic or user story.
   - The description includes a user story or objective.
   - Acceptance criteria are testable.
   - The issue links to the appropriate requirement in `REQUIREMENTS.md`.
   - The issue links to the appropriate roadmap section in `ROADMAP.md`.
   - The priority and dependency information are reasonable.
6. Ask Copilot to identify missing dependencies and duplicate stories.
7. Ask Copilot to break large stories into implementation tasks only when the story cannot be completed in one focused iteration.
8. Add approved issues to the project board and assign priorities manually if Copilot cannot do so in your GitHub plan.

### Useful Copilot prompts

#### Create an epic

> Create an epic issue titled `Epic: Core inventory management`. Use `REQUIREMENTS.md` and `ROADMAP.md` as the source of truth. Include objective, business value, scope, non-goals, linked SMART requirements, dependencies, expected month, and a checklist of user stories. Do not create implementation details that are not supported by the repository documents.

#### Create user stories for an epic

> For the core inventory management epic, create user stories for inventory records, stock receipts, stock transfers, inventory adjustments, transaction history, and cycle counts. Use the format `As a [role], I want [capability], so that [outcome]`. Give every story testable acceptance criteria, priority, estimated size, and dependencies.

#### Review a backlog

> Review the current Granite Signal Analytics issues for duplicate work, missing acceptance criteria, unclear ownership, missing dependencies, and scope that is too large for a three-month pilot. Recommend changes without changing the SMART targets in `REQUIREMENTS.md`.

#### Generate implementation tasks

> For the selected user story, create a concise checklist of implementation, test, documentation, and deployment tasks. Keep the tasks within the story scope and identify any blocking dependency.

## Step-by-step: Set up the project manually

### 1. Create a GitHub Project

1. Open the repository.
2. Select the **Projects** tab.
3. Select **New project**.
4. Choose a board, table, or roadmap layout. A table is useful for planning; a board is useful for daily execution.
5. Name the project `Granite Signal Analytics — Inventory Platform`.
6. Add these fields:
   - **Status:** Backlog, Ready, In progress, In review, Blocked, Done
   - **Priority:** High, Medium, Low
   - **Work type:** Epic, Story, Task, Saga
   - **Roadmap month:** Month 1, Month 2, Month 3, Post-pilot
   - **Estimate:** Best case, Expected, Worst case, or a numeric size
   - **Area:** Discovery, Inventory, Procurement, QA, Analytics, Reporting, Platform, Pilot
7. Create project views such as:
   - **Backlog:** all unfinished work grouped by epic
   - **Current sprint:** Ready and In progress items
   - **Roadmap:** grouped by roadmap month
   - **Blocked work:** items with Status = Blocked
   - **Pilot readiness:** Month 3 and release-related items

### 2. Create epic issues

Create one issue for each epic listed below. Use the `Epic` work type and add the matching area and month.

1. `Epic: Product discovery and foundation` — Month 1 — High
2. `Epic: Core inventory management` — Month 1 — High
3. `Epic: Supplier and purchase-order workflows` — Month 2 — High
4. `Epic: Quality assurance and traceability` — Month 2 — High
5. `Epic: Forecasting, alerts, and anomaly detection` — Month 2 — High
6. `Epic: Dashboarding, reporting, and user experience` — Month 3 — High
7. `Epic: Security, reliability, and deployment` — Month 3 — High
8. `Epic: Pilot launch and measurement` — Month 3 — High

Use this description template for each epic:

```markdown
## Objective

[Describe the outcome this epic delivers.]

## Business value

[Explain how it supports the SMART business outcomes.]

## Scope

- [Included capability]
- [Included capability]

## Non-goals

- [Explicitly deferred capability]

## Source documents

- [REQUIREMENTS.md](../blob/main/REQUIREMENTS.md)
- [ROADMAP.md](../blob/main/ROADMAP.md)

## User stories

- [ ] #issue-number — [Story title]
- [ ] #issue-number — [Story title]

## Dependencies

- [Blocking issue or dependency]
```

### 3. Create user-story issues

Create the following initial stories and associate each with its epic. Use labels such as `story`, `high-priority`, and the relevant area label.

#### Product discovery and foundation

- Define business scope, personas, workflows, and success metrics.
- Capture the 30-day baseline for inventory accuracy, stockouts, excess inventory, and reporting effort.
- Define the system architecture and data model.
- Set up the development environment, repository workflow, and continuous integration checks.

#### Core inventory management

- Manage inventory records by SKU, location, quantity, reorder point, and lot or batch.
- Record receipts, issues, transfers, returns, and adjustments.
- View inventory movement history and audit events.
- Schedule and reconcile cycle counts.

#### Supplier and purchase-order workflows

- Manage suppliers and purchase orders.
- Reconcile ordered, received, and rejected quantities.
- Import spreadsheet data with row-level validation errors.
- Measure supplier lead time, fill rate, delivery performance, and defect trends.

#### Quality assurance and traceability

- Record inspection results for inventory lots or batches.
- Quarantine and release inventory based on quality status.
- Prevent rejected or quarantined material from production allocation.
- Trace each lot or batch from receipt through current location or consumption.

#### Forecasting, alerts, and anomaly detection

- Generate a 12-week baseline demand forecast.
- Notify users of reorder and stockout risk.
- Identify overstocked, aging, and obsolete inventory.
- Detect and resolve abnormal inventory patterns.

#### Dashboarding, reporting, and user experience

- Build inventory accuracy, stockout, aging, quality, supplier, and alert dashboards.
- Export standard reports to CSV or PDF.
- Provide role-based views for warehouse, purchasing, QA, and management users.
- Validate usability and accessibility.

#### Security, reliability, and deployment

- Implement authentication and role-based authorization.
- Add audit logging, encryption in transit, and session timeout.
- Configure backups, restore procedures, monitoring, and incident alerts.
- Run performance, security, reliability, and accessibility testing.
- Deploy a release candidate and document rollback procedures.

#### Pilot launch and measurement

- Prepare pilot data for three manufacturing clients.
- Conduct user acceptance testing and resolve critical defects.
- Train pilot users and provide quick-reference documentation.
- Measure results against the baseline after 90 days of live operation.
- Document lessons learned and prioritize the post-pilot release.

### 4. Add acceptance criteria to each story

Use Given/When/Then criteria where possible. For example:

```markdown
## Acceptance criteria

- Given an authorized warehouse user, when a receipt is submitted, then the inventory balance increases by the accepted quantity.
- Given a receipt with a quantity mismatch, when it is saved, then the system flags the discrepancy and records it in the audit trail.
- Given invalid required data, when the user submits the form, then the system prevents the transaction and displays a clear error.
```

Link each story to the relevant SMART requirement. For example, the stockout-alert story should reference **FR-06**, and the security story should reference **NFR-04**.

### 5. Add labels

Create and apply labels such as:

- `epic`
- `story`
- `task`
- `saga`
- `discovery`
- `inventory`
- `procurement`
- `quality-assurance`
- `analytics`
- `reporting`
- `security`
- `deployment`
- `pilot`
- `high-priority`
- `blocked`
- `post-pilot`

### 6. Link and order the work

1. Add stories to their parent epic in the epic checklist.
2. Add blocking relationships where supported, or record dependencies in the issue body.
3. Put discovery and architecture before implementation.
4. Put core inventory work before analytics that depends on transaction data.
5. Put security, deployment, and recovery work before pilot launch.
6. Keep advanced machine learning and mobile scanning in a `post-pilot` group.

## Suggested three-month iteration plan

### Month 1

- Discovery, scope, personas, and baseline.
- Architecture and data model.
- Development foundation and CI.
- Core inventory records and transaction workflows.

### Month 2

- Purchase orders, suppliers, receiving, and data imports.
- Quality inspections, quarantine, release, and traceability.
- Cycle counts and audit workflows.
- Baseline forecasts and operational alerts.

### Month 3

- Dashboards and reports.
- Security, performance, accessibility, backups, and monitoring.
- Deployment, UAT, training, and pilot support.
- Initial KPI comparison and post-pilot backlog.

## Definition of Ready

A story is ready for implementation when:

- The user, capability, and outcome are clear.
- Acceptance criteria are testable.
- The requirement and roadmap references are identified.
- Dependencies are known.
- The story is small enough for one focused iteration.
- Required data, permissions, and design decisions are available.

## Definition of Done

A story is done when:

- The implementation is complete and reviewed.
- Automated and relevant manual tests pass.
- Acceptance criteria are demonstrated.
- Documentation is updated where needed.
- Security, accessibility, and data-quality impacts are addressed.
- The issue is linked to the project and moved to Done.

## Important planning note

A three-month expected completion is realistic only for a focused pilot. Keep the Must-have requirements in `REQUIREMENTS.md` as the release target. Treat advanced machine-learning models, mobile scanning, automated purchasing recommendations, and supplier self-service as post-pilot work unless the schedule has contingency.
