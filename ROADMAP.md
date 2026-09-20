# Granite Signal Analytics — Three-Point Project Roadmap

## Roadmap objective

Complete and pilot the inventory management and quality-assurance platform in **3 expected months**, while learning the skills needed to design, build, test, deploy, and operate it. The roadmap assumes one primary learner-builder with focused weekly effort and limited stakeholder support.

The project will deliver a usable pilot for three manufacturing clients, not a fully mature enterprise platform. Advanced machine learning, mobile scanning, and supplier self-service are deferred until after the pilot.

## Estimation method

Each workstream uses three-point estimates:

- **Best case (B):** Work proceeds smoothly with few blockers.
- **Expected case (E):** Most likely duration, including normal learning and rework.
- **Worst case (W):** Duration if unfamiliar technology, integration problems, or defects create delays.
- **Expected estimate:** `(B + 4E + W) / 6` using a PERT-style weighted estimate.

Durations are shown in **person-weeks**. Workstreams may overlap, so the sum of estimates is greater than the calendar roadmap duration.

## Three-point estimates by workstream

| ID | Workstream | Skills learned or strengthened | Best | Expected | Worst | PERT expected | Primary outcome |
|---|---|---|---:|---:|---:|---:|---|
| W1 | Discovery and delivery setup | Product discovery, stakeholder interviews, Git/GitHub workflow, Agile planning | 1 wk | 2 wks | 3 wks | 2.0 wks | Approved scope, personas, baseline metrics, and delivery plan |
| W2 | Architecture and data model | System design, relational modeling, API design, data governance | 1 wk | 2 wks | 4 wks | 2.2 wks | Architecture decision record and validated schema |
| W3 | Development environment and foundations | Programming language/framework, testing, CI, configuration, secure development | 1 wk | 2 wks | 3 wks | 2.0 wks | Running application skeleton with automated checks |
| W4 | Inventory and transaction management | CRUD/API development, business rules, database transactions, validation | 2 wks | 3 wks | 5 wks | 3.2 wks | Inventory, receiving, transfers, adjustments, and transaction history |
| W5 | Purchasing, suppliers, and integrations | CSV processing, API integration, error handling, data quality | 1 wk | 3 wks | 5 wks | 3.0 wks | Purchase-order reconciliation and import pipeline |
| W6 | Quality assurance and traceability | Workflow design, lot/batch traceability, quality controls, audit logging | 1 wk | 2 wks | 4 wks | 2.2 wks | Inspection, quarantine, release, rejection, and audit workflows |
| W7 | Forecasting and anomaly detection | Statistics, forecasting, feature preparation, model evaluation | 2 wks | 3 wks | 6 wks | 3.3 wks | Baseline forecast and explainable anomaly flags |
| W8 | Dashboards, alerts, and reporting | Data visualization, UX, role-based workflows, reporting | 1 wk | 2 wks | 4 wks | 2.2 wks | Operational dashboards, alerts, and exports |
| W9 | Security, performance, reliability, and accessibility | Authentication, authorization, threat modeling, performance testing, WCAG | 1 wk | 2 wks | 4 wks | 2.2 wks | Security and nonfunctional acceptance evidence |
| W10 | Testing, deployment, and pilot readiness | Test strategy, CI/CD, cloud deployment, backups, monitoring, documentation | 2 wks | 3 wks | 5 wks | 3.2 wks | Deployed pilot release and operating runbook |
| W11 | Pilot, measurement, and stabilization | UAT, training, incident response, product analytics, iteration | 1 wk | 2 wks | 4 wks | 2.2 wks | Three-client pilot, outcome report, and prioritized next release |

## Calendar roadmap: expected completion in 3 months

### Month 1 — Discover, design, and establish the foundation

**Weeks 1–2: Discovery and planning**

- Confirm personas, workflows, scope, assumptions, and success metrics.
- Capture the 30-day baseline for accuracy, stockouts, excess inventory, and reporting effort.
- Create the product backlog, repository conventions, development environment, and learning plan.
- Learn or refresh Git, issue tracking, Agile estimation, requirements analysis, and stakeholder interviewing.

**Weeks 2–3: Architecture and data foundation**

- Define system boundaries, architecture, security model, and integration approach.
- Design inventory, transaction, supplier, purchase-order, quality, forecast, alert, and audit entities.
- Build the application skeleton, database migration strategy, local development setup, and CI checks.
- Learn relational modeling, API design, automated testing, and data governance.

**Weeks 3–4: Inventory core**

- Implement inventory records, locations, quantities, reorder points, lot/batch data, receipts, issues, transfers, adjustments, and history.
- Add validation, permissions, and initial audit events.
- Demonstrate the end-to-end inventory workflow with representative data.

**Month 1 exit criteria:** Core inventory workflows pass acceptance tests; baseline metrics are documented; architecture and data model are approved.

### Month 2 — Build integrations, quality workflows, and analytics

**Weeks 5–6: Purchasing and data integration**

- Implement purchase orders, receiving reconciliation, supplier metrics, CSV import, and row-level error reporting.
- Create test fixtures and data-quality checks for duplicate, missing, invalid, and inconsistent records.
- Learn file processing, API integration, observability, and integration testing.

**Weeks 6–7: Quality assurance and traceability**

- Implement inspection results, approved/quarantined/rejected/released states, and lot traceability.
- Prevent quarantined and rejected inventory from production allocation.
- Implement searchable audit history and cycle-count reconciliation.

**Weeks 7–8: Forecasting, anomaly detection, and alerts**

- Create a baseline demand forecast with documented assumptions and error measurement.
- Implement stockout, reorder, overstock, obsolete-inventory, and anomaly alerts.
- Build review, classification, and resolution flows for analytics alerts.
- Learn exploratory data analysis, forecasting evaluation, feature engineering, and explainability.

**Month 2 exit criteria:** Purchase, receiving, QA, traceability, cycle-count, forecast, and alert workflows operate on realistic test data; critical risks have mitigation plans.

### Month 3 — Make it usable, secure, deployable, and measurable

**Weeks 9–10: Dashboards and user experience**

- Build role-based dashboards for inventory accuracy, stockouts, aging inventory, quality incidents, supplier performance, alerts, and replenishment.
- Add CSV/PDF exports, clear error messages, keyboard navigation, and responsive layouts.
- Conduct usability testing with representative warehouse, purchasing, QA, and operations users.

**Weeks 10–11: Nonfunctional hardening**

- Implement authentication, role-based authorization, encryption in transit, session timeout, backup, restore, monitoring, and incident alerts.
- Run performance, security, accessibility, reliability, and recovery tests against SMART requirements.
- Resolve critical and high-severity defects before release.

**Weeks 11–12: Deployment, UAT, pilot, and measurement**

- Deploy the release, seed pilot data, train users, and execute UAT.
- Run the pilot with three manufacturing clients and provide support.
- Measure outcomes after live operation, compare with baseline, document lessons learned, and prioritize the next release.

**Month 3 exit criteria:** Pilot is deployed; critical requirements pass; users are trained; runbooks and rollback procedures exist; initial outcome measurements are available.

## Milestones and decision gates

| Milestone | Target | Evidence required | Decision |
|---|---|---|---|
| M1: Scope and baseline approved | End of week 2 | Personas, workflows, backlog, baseline plan | Proceed to build |
| M2: Core inventory demonstrated | End of week 4 | Working inventory and transaction flows, tests | Continue integrations |
| M3: Operational workflows complete | End of week 8 | Purchasing, QA, traceability, analytics demo | Approve hardening |
| M4: Release candidate ready | End of week 11 | UAT candidate, security/performance/accessibility results | Go/no-go pilot |
| M5: Pilot complete | End of week 12 | Deployment, training, support log, initial KPI report | Decide next release |

## Delivery risks and contingency actions

- **Integration data is inconsistent:** Start with CSV adapters and a canonical schema; reserve worst-case time in weeks 5–6 for cleansing and mapping.
- **Machine-learning data is insufficient:** Ship explainable rules and a baseline forecast first; treat advanced models as post-pilot work.
- **Learning curve threatens the three-month target:** Prioritize Must-have requirements, use proven frameworks, and schedule focused learning alongside each workstream.
- **Security or deployment defects delay launch:** Begin threat modeling and deployment automation in month 1 rather than postponing them to the end.
- **Pilot users resist adoption:** Involve users during discovery, test workflows early, and provide role-specific training and quick-reference guides.

## Scope rule

The expected three-month plan is achievable only if the pilot remains focused on the Must-have requirements in `REQUIREMENTS.md`. Advanced machine learning, mobile scanning, automated purchasing recommendations, and supplier self-service should be separate post-pilot epics.
