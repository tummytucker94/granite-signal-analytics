# Software Design Specification (SDS)

## 1. Document Control

| Field | Value |
|---|---|
| Project | Granite Signal Analytics Inventory Management and Quality Assurance Platform |
| Version | 1.0 |
| Status | Draft for review |
| Repository | `tummytucker94/granite-signal-analytics` |
| Design inputs | `REQUIREMENTS.md`, `ROADMAP.md`, `docs/1_Planning/SysRS.md`, `docs/1_Planning/SRS.md` |

## 2. Purpose and Design Goals

This Software Design Specification translates the system and software requirements into an implementable pilot architecture. The design prioritizes reliable inventory transactions, quality traceability, explainable analytics, strong auditability, and a modular foundation for future integrations.

## 3. Architectural Style

Use a modular layered architecture:

```text
Presentation Layer
  dashboards | forms | alerts | reports
          |
Application Layer
  inventory | procurement | quality | analytics | reporting services
          |
Domain Layer
  inventory rules | supplier rules | quality rules | forecast rules
          |
Data Layer
  relational records | transactions | audit events | forecast data
          |
Integration Layer
  CSV imports | external APIs | CSV/PDF exports
```

The application layer coordinates use cases. The domain layer owns business rules. The data layer handles persistence and transactions. Integration adapters isolate external formats from internal models.

## 4. Component Design

### 4.1 Inventory Service

Responsibilities:

- Manage item, location, balance, and lot records.
- Validate quantities and inventory status.
- Process receipts, issues, transfers, returns, adjustments, and counts.
- Write an immutable transaction history.

### 4.2 Procurement Service

Responsibilities:

- Manage purchase orders and suppliers.
- Reconcile ordered, received, and rejected quantities.
- Calculate supplier lead time, fill rate, delivery, and defect metrics.

### 4.3 Quality Service

Responsibilities:

- Record inspections and inspection results.
- Manage approved, quarantined, rejected, and released statuses.
- Prevent nonconforming inventory from allocation.
- Provide lot and batch traceability.

### 4.4 Analytics Service

Responsibilities:

- Prepare historical usage data.
- Produce a baseline 12-week forecast.
- Calculate projected inventory position.
- Detect stockout, overstock, aging, obsolete, and anomalous conditions.
- Store model inputs, outputs, assumptions, and evaluation metrics.

### 4.5 Reporting Service

Responsibilities:

- Aggregate KPI data.
- Render dashboards.
- Export CSV and PDF reports.
- Apply role-based visibility to reports.

### 4.6 Identity and Audit Service

Responsibilities:

- Authenticate users.
- Enforce role-based authorization.
- Record security-sensitive and business-critical events.
- Support audit search, retention, and review.

## 5. Data Model

| Entity | Key fields | Relationships |
|---|---|---|
| Item | item_id, SKU, description, unit, status | Has balances, lots, and transactions |
| Location | location_id, warehouse, zone, active | Holds inventory balances |
| InventoryBalance | item_id, location_id, available, reserved, reorder point, safety stock | Belongs to item and location |
| InventoryLot | lot_id, item_id, supplier, received date, expiry, quantity, quality status | Has inspections and movements |
| InventoryTransaction | transaction_id, type, quantity, source, destination, user, timestamp | Changes balances and links to source document |
| Supplier | supplier_id, name, lead time, delivery rate, defect rate | Has purchase orders and receipts |
| PurchaseOrder | PO number, supplier, dates, status, quantities | Contains purchase-order lines and receipts |
| QualityInspection | inspection_id, lot, inspector, result, notes, timestamp | Changes quality disposition |
| Forecast | item, period, predicted quantity, method, error metric, generated date | Supports alerts and planning |
| Alert | alert_id, item, type, severity, message, status, timestamps | Assigned to users for review |
| AuditEvent | event_id, entity, action, actor, before, after, timestamp | Provides traceability |

## 6. Transaction and Consistency Rules

1. Inventory-changing operations must execute atomically.
2. A transfer must decrement the source and increment the destination in one transaction.
3. Available quantity must never become negative unless an explicitly approved business rule allows it.
4. Rejected and quarantined inventory cannot be allocated to production.
5. Every accepted inventory change must create a transaction and audit event.
6. Invalid imports must be rejected at row level and must not silently change balances.
7. Duplicate source-document identifiers must be detected before a transaction is applied.

## 7. Key Workflow Designs

### 7.1 Receiving

1. Validate supplier, purchase order, item, quantity, lot, and date.
2. Compare received quantity with ordered quantity.
3. Create or update the inventory lot.
4. Increase the inventory balance.
5. Create the transaction and audit event.
6. Generate a discrepancy alert when tolerance is exceeded.

### 7.2 Quality Disposition

1. QA user selects a lot and records inspection results.
2. The service validates user permission and inspection data.
3. The lot status changes to approved, quarantined, rejected, or released.
4. Allocation rules immediately reflect the new status.
5. The system records the before and after values and notifies affected users.

### 7.3 Stockout Alert

1. Load current balances, open purchase orders, forecast demand, and lead times.
2. Calculate projected available inventory by item and period.
3. Compare the projection with reorder point and safety stock.
4. Create or update an alert with severity and recommended review action.
5. Notify the inventory planner and purchasing manager.

### 7.4 Anomaly Review

1. Analytics service identifies a potential anomaly.
2. The alert includes the affected item, evidence, detection rule/model, and timestamp.
3. An authorized user marks the alert valid, false positive, or resolved.
4. The review outcome is stored for reporting and future model improvement.

## 8. Interface Design

### Operational screens

- Inventory search and detail
- Receive inventory
- Transfer inventory
- Adjust inventory
- Cycle count
- Purchase order and receiving reconciliation
- Quality inspection and disposition
- Alert review

### Management views

- Inventory accuracy dashboard
- Stockout and replenishment dashboard
- Aging and excess inventory report
- Supplier performance scorecard
- Quality incident dashboard
- Forecast and anomaly review

### Import and export

- CSV template with required columns, data types, and validation rules
- Row-level import error report
- CSV and PDF report exports
- Versioned integration/API contracts

## 9. Security Design

- Use least-privilege role-based authorization.
- Protect authentication credentials through a supported identity mechanism.
- Encrypt data in transit.
- Apply session expiration and reauthentication for sensitive actions.
- Log permission changes, quality dispositions, inventory adjustments, and administrative changes.
- Do not expose supplier or operational data to unauthorized roles.

## 10. Reliability, Monitoring, and Recovery

Monitor:

- availability and response time,
- failed transactions,
- import failures,
- alert-processing failures,
- database and storage health,
- backup completion and restore tests.

Create daily backups, retain them for at least 30 days, and test restoration before pilot launch. Critical failures should notify the support owner within 15 minutes.

## 11. Testing Design

- Unit tests for quantity calculations, thresholds, quality status rules, and forecast helpers.
- Integration tests for receiving, transfers, imports, purchase reconciliation, and quality workflows.
- End-to-end tests for planner, warehouse, purchasing, and QA use cases.
- Security tests for role boundaries and unauthorized operations.
- Performance tests against 100 concurrent users and pilot data volume.
- Accessibility tests for keyboard use, labels, focus, contrast, and errors.
- Data-quality tests for duplicates, missing fields, invalid quantities, and source-system conflicts.

## 12. Implementation Priorities

### Pilot release

- Inventory master data and transactions
- Purchase orders and receiving reconciliation
- Quality hold and release
- Audit trail and role-based access
- Basic forecasts, alerts, dashboards, and reports
- Imports, backups, monitoring, and deployment

### Post-pilot

- Advanced machine-learning models
- Mobile scanning
- Automated purchasing recommendations
- Supplier self-service
- Additional ERP and warehouse integrations

## 13. Traceability

| Design area | Requirements covered |
|---|---|
| Inventory service | FR-01, FR-02, FR-13 |
| Procurement service | FR-03, FR-04, FR-14 |
| Quality service | FR-05, FR-12 |
| Analytics service | FR-06, FR-07, FR-08, FR-09 |
| Reporting service | FR-10 |
| Identity and audit | FR-11, FR-12, NFR-03, NFR-04, NFR-05 |
| Operations and recovery | NFR-01, NFR-02, NFR-06, NFR-11 |

## 14. Design Acceptance

The SDS is accepted when the proposed architecture, data model, workflows, security controls, testing strategy, and pilot priorities are reviewed against `SysRS.md`, `SRS.md`, `REQUIREMENTS.md`, and `ROADMAP.md`.
