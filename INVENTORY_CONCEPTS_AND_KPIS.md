# Inventory Management Concepts and Industry KPIs

## 1. Top 20 Inventory Management Concepts and Terms

| # | Concept or term | Definition | Why it matters to Granite Signal Analytics |
|---:|---|---|---|
| 1 | SKU | Stock Keeping Unit; a unique identifier for a product or material. | Provides the basic unit for tracking inventory, demand, and quality data. |
| 2 | Inventory on hand | Quantity physically available at a location. | Establishes current supply and supports accurate stock reporting. |
| 3 | Available inventory | On-hand inventory that is not reserved, blocked, or quarantined. | Prevents planners from treating unusable material as available supply. |
| 4 | Safety stock | Extra inventory held to protect against demand or supply uncertainty. | Helps reduce stockouts while balancing carrying cost. |
| 5 | Reorder point | Inventory level that triggers replenishment action. | Supports timely alerts before a shortage occurs. |
| 6 | Economic Order Quantity (EOQ) | Order size intended to balance ordering and holding costs. | Provides a traditional replenishment reference for purchasing decisions. |
| 7 | Lead time | Time between placing an order and receiving usable inventory. | Drives projected stockout dates and supplier evaluation. |
| 8 | Demand forecasting | Estimation of future item demand using historical and contextual data. | Enables the platform to project inventory needs and replenishment risk. |
| 9 | Stockout | Situation in which required inventory is unavailable. | Directly affects production continuity and is a key business outcome. |
| 10 | Overstock | Inventory quantity that exceeds expected operational need. | Ties up cash, increases storage cost, and can create obsolescence. |
| 11 | Obsolete inventory | Inventory no longer expected to be used or sold. | Identifies avoidable carrying cost and disposal or disposition opportunities. |
| 12 | Carrying cost | Total cost of holding inventory, including storage, insurance, capital, and risk. | Helps quantify the financial impact of excess inventory. |
| 13 | Cycle counting | Repeated counting of selected inventory rather than one annual count. | Provides ongoing accuracy measurement and faster variance investigation. |
| 14 | Inventory accuracy | Agreement between system quantity and physically verified quantity. | Core KPI; the pilot target is at least 95%. |
| 15 | Lot or batch traceability | Ability to follow material from receipt through movement, inspection, and consumption. | Supports quality investigations, recalls, and audit readiness. |
| 16 | Quarantine | Temporary restriction that prevents inventory from being used until reviewed. | Protects production from potentially nonconforming material. |
| 17 | ABC analysis | Classification of items by relative value or importance, commonly A, B, and C. | Helps prioritize counting, controls, and management attention. |
| 18 | FIFO / FEFO | FIFO uses oldest receipt first; FEFO uses earliest expiry first. | Reduces aging, expiry, and waste where applicable. |
| 19 | Shrinkage | Inventory loss caused by damage, theft, miscounts, process errors, or unexplained variance. | Anomaly detection and audit trails can help identify root causes. |
| 20 | Inventory turnover | Number of times inventory is used or sold during a period. | Indicates how efficiently inventory is being used and replenished. |

## 2. Top 5 Industry-Standard Inventory KPIs

| # | KPI | Formula | Recommended target or interpretation | Project relevance |
|---:|---|---|---|---|
| 1 | Inventory accuracy | `(Correct inventory records / Records counted) × 100` | Target at least 95% for the pilot. | Measures whether system quantities match physical counts. |
| 2 | Stockout rate | `(Stockout events / Total item-location demand opportunities) × 100` | Reduce stockout incidents by at least 30% from baseline. | Measures whether replenishment and forecasting prevent shortages. |
| 3 | Inventory turnover | `Cost of goods used or sold / Average inventory value` | Higher is generally better, but compare by item category and service level. | Shows whether inventory is moving efficiently without harming availability. |
| 4 | Days Inventory Outstanding (DIO) | `Average inventory value / Cost of goods used or sold × Days in period` | Decrease excessive days while maintaining required service levels. | Quantifies how long capital remains tied up in inventory. |
| 5 | Carrying cost percentage | `Annual inventory carrying cost / Average inventory value × 100` | Track trend and reduce avoidable carrying cost from excess or obsolete stock. | Connects inventory decisions to storage, capital, insurance, and obsolescence costs. |

## 3. KPI Measurement Guidance

- Establish a 30-day baseline before pilot deployment.
- Define the numerator, denominator, time period, and data source for every KPI.
- Segment KPIs by SKU, location, warehouse, supplier, and item category where useful.
- Compare pilot results with the baseline after 90 days of live operation.
- Document exclusions, such as planned shutdowns or approved quality quarantines, so results remain interpretable.
- Review KPI trends with operational users rather than treating a single measurement as conclusive.
