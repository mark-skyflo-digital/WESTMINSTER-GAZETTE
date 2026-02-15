# Westminster Gazette MVP PRD

## 1. Objective
Deliver a Salesforce Public Sector Solutions (PSS) MVP for Westminster that supports:
- Gazetteer-centric property/address management (UPRN as the operational key)
- Back-office case handling for Planning, Building Control, and Licensing
- Service levels, KPI reporting, and auditable workflow execution

## 2. MVP Outcomes
- Single operational app for officers and managers
- End-to-end case lifecycle from intake to closure
- Native PSS data model leveraged first, with custom model only where required
- Role-based access with full CRUD/FLS package for MVP build and admin operations
- Dashboard visibility for SLA and service-credit metrics

## 3. In Scope
- Salesforce org setup and source-driven delivery model
- Object model for Gazetteer + three service domains (Planning/Building Control/Licensing)
- Case intake, triage, assignment, SLA tracking, and closure flows
- Lightning app, tabs, layouts, related lists, file upload enablement
- Permission model (including a full CRUD permission set covering relevant PSS + custom objects)
- Seed data and UAT script for end-to-end demonstration

## 4. Out of Scope (MVP)
- Full legacy migration and historical data backfill
- Production-grade external integration hardening (MVP uses controlled interfaces/stubs)
- Advanced AI automation beyond deterministic flow-based orchestration

## 5. Personas
- Customer Services Agent (create/intake/update requests)
- Case Officer (process planning/building/licensing cases)
- Team Manager (monitor SLA/KPI and workload)
- System Administrator (configure, govern access, release)
- Integration User (system-to-system data exchange)

## 6. Core Processes
1. Intake
- Request received via internal channel or import
- Record linked to person/account and property (UPRN)

2. Triage
- Routing to Planning, Building Control, or Licensing queue
- Priority and due dates set from SLA policy

3. Case Handling
- Officer updates milestones, inspections, documents, decisions
- Related records and files captured as evidence

4. Decision and Closure
- Outcome recorded and communicated
- SLA and KPI snapshots updated

5. Oversight and Reporting
- Dashboard view of open backlog, SLA compliance, breaches, and throughput

## 7. Data Model Principles
- Use native PSS objects where capability already exists
- Add custom objects only for Westminster-specific data and process gaps
- Standardize key references: Contact/Account, Property/UPRN, Case type, Status, SLA milestone

## 8. Security and Access Requirements
- Create permission set `Westminster_MVP_FullCRUD` with:
  - Object CRUD (Create/Read/Edit/Delete) on all in-scope custom objects
  - Object CRUD on in-scope native PSS/standard objects used by workflows
  - Field-level Read/Edit on all in-scope custom fields
- Assign to System Administrator during MVP build and UAT
- Preserve least-privilege role-based permission sets for runtime users

## 9. Non-Functional Requirements
- Full auditability (field history/record tracking where needed)
- Repeatable deployments via source control
- Metadata validation and test execution gates before merge
- Performance baseline for list views/reports on MVP data volumes

## 10. Acceptance Criteria
- AC1: End-to-end intake-to-closure works for each service domain (Planning/Building/Licensing)
- AC2: UPRN-linked property record is mandatory and reportable
- AC3: SLA due dates and breach flags are automatically maintained
- AC4: Files can be attached and viewed in all key case record pages
- AC5: `Westminster_MVP_FullCRUD` grants full build/admin access for all in-scope objects/fields
- AC6: Dashboard shows agreed KPI set from tender service level requirements
- AC7: UAT script passes with seeded sample data

## 11. Delivery Phasing
- Phase 1: Foundation + Data Model
- Phase 2: App UX + Security + Automation
- Phase 3: Reporting + UAT + Release Hardening
