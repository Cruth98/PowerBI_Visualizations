# Power BI Semantic Models & Enterprise Reporting

Production-grade Power BI reports built for finance, audit, and operations 
stakeholders in an enterprise restaurant environment. Each report is backed 
by a structured semantic model with dimensional design, SQL-sourced data, 
and self-service functionality enabling non-technical users to explore data 
independently.

These are not prototype dashboards — they were actively used by accounting 
teams, treasury, and senior finance leadership.

---

## Technical Foundation

**Modeling Approach**
- Star schema dimensional modeling (fact + dimension tables)
- SQL-backed semantic layers with structured relationships
- DAX measures for KPI calculation, aging analysis, and variance logic
- Slicers, cross-filtering, and drill-through for self-service navigation

**Tools & Concepts**
- Power BI Desktop & Power BI Service
- SQL (data sourcing and transformation)
- DAX (measures, calculated columns, conditional logic)
- Dimensional modeling (FindingsFact, BaswareFact, StoreListDim, COA)
- Data reconciliation and audit-focused KPI design
- Self-service report design with embedded user guidance

---

## Reports

### 1. Unrecorded Liability Audit Dashboard

Built to support audit teams in identifying, quantifying, and resolving 
unrecorded liability findings across the enterprise. This is the most 
technically complex report in this collection.

**Semantic Model**
The underlying model follows a star schema with four tables:
- `FindingsFact` — core audit findings grain with accrual type, 
  journal metadata, and over/under amounts
- `BaswareFact` — invoice-level data including creation lag, 
  payment source, and supplier detail
- `StoreListDim` — store hierarchy dimension (MKP, MP, Regional 
  Partner, Staff Accountant, State)
- `COA` — chart of accounts dimension (Main Account Name and Number)

Relationships are structured with proper one-to-many cardinality 
between dimension and fact tables, enabling consistent cross-filtering 
across all report pages.

**Report Pages**
- **Summary Analysis** — findings instances by timing (current vs. 
  post-dated), result type, and research process; trend view across 
  5-week audit cycle
- **Accrual Analysis** — 918 findings instances broken down by 
  research process and Basware accrual timing; identifies accrual 
  gaps and invoice availability issues
- **Vendor Analysis** — 528 vendor count with average BW creation 
  lag and invoice creation lag by vendor; surfaces chronic late 
  submitters
- **Service Date Analysis** — average service date lag and vendor 
  send lag analysis; identifies timing breakdowns between service 
  delivery and invoice submission
- **Store & Main Account Analysis** — findings by cost center group, 
  main account, market partner, and managing partner

**Business Impact**
This dashboard directly supported identification of $2M+ in previously 
unrecorded liabilities by giving audit teams structured visibility into 
findings patterns across vendors, stores, and account types.

**Artifacts**
- `Audit_PBI_Report.pdf` — sanitized export showing all report pages 
  and dimensional model view

---

### 2. Fixed Asset & Depreciation Projections

Built for finance and operations stakeholders to monitor asset cost, 
net book value, additions, roll-offs, and depreciation timing across 
store locations.

**Key Features**
- Asset type breakdown (BLDG/LHI, Equipment, Furniture, Signage) 
  by store and region
- Historical additions view across 10-year horizon
- Roll-off tracking with end depreciation dates by asset
- Depreciation expense projection by asset type with forward-looking 
  period estimates
- Regional Construction Manager and Opened Year filters for 
  capital planning support

**Artifacts**
- `Depreciation_Projections_PBI.pdf` — sanitized export; 
  financial values redacted

---

### 3. Outstanding Gift Card Balances & Aging

Built for treasury and accounting to monitor outstanding gift card 
balances, inactive orders, payment reconciliation, and aging across 
market partners and store locations.

**Key Features**
- Multi-account view (Accrued Charitable Events, CoBrand Gift Card 
  Receivable, Direct Bills) with period and year filtering
- Data update timeline embedded directly in report for stakeholder 
  transparency — removes dependency on accounting team for 
  data freshness questions
- Aged CoBrand order tracking with days-aged flagging
- Payment reconciliation view identifying payments received without 
  matching CoBrand order numbers (449 total misrings identified)
- Self-service design with embedded FAQ and Getting Started guide

**Design Note**
The embedded instruction page and FAQ reflect a deliberate self-service 
design philosophy: stakeholders should be able to answer their own 
questions without escalating to the accounting team. This pattern 
reduces support burden and increases report adoption.

**Artifacts**
- `Outstanding_Balances_PBI.pdf` — redacted export; 
  store names and financial balances visible, personal data removed

---

## Notes
- All reports were production-deployed in an enterprise Power BI 
  Service environment
- Underlying data has been excluded from this repository; 
  PDFs are sanitized exports only
- Financial amounts redacted where applicable
