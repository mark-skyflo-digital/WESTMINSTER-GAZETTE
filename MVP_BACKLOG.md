# Westminster Gazette MVP Backlog (First Pass)

This backlog is now created in Beads. Use IDs below for assignment and tracking.

## Release Gate (Must Not Be Skipped)
- `WestminsterGazette-2no.1` Story: Build `Westminster_MVP_FullCRUD` permission set
- Gate rule: MVP is not deployable until this story is complete and assigned to admin users for build/UAT.

## Epic and Story List

## 1) `WestminsterGazette-4ox` EPIC: Foundation, Org Baseline, and PSS Inventory
- `WestminsterGazette-4ox.1` Connect orgs and confirm source-driven deployment path
- `WestminsterGazette-4ox.2` Inventory native PSS and standard object API names
- `WestminsterGazette-4ox.3` Establish branch/worktree strategy for parallel agents

## 2) `WestminsterGazette-p36` EPIC: Gazetteer and Back Office Data Model
- `WestminsterGazette-p36.1` Implement Gazetteer property/address model with UPRN
- `WestminsterGazette-p36.2` Implement Planning case model
- `WestminsterGazette-p36.3` Implement Building Control case model
- `WestminsterGazette-p36.4` Implement Licensing case model
- `WestminsterGazette-p36.5` Validate model against tender requirement matrix

## 3) `WestminsterGazette-2no` EPIC: Security and Access Control
- `WestminsterGazette-2no.1` Build `Westminster_MVP_FullCRUD` permission set
- `WestminsterGazette-2no.2` Build role-based least-privilege permission sets
- `WestminsterGazette-2no.3` Assign admin profile/tab visibility and baseline sharing

## 4) `WestminsterGazette-y5c` EPIC: App UX, Tabs, and Record Experience
- `WestminsterGazette-y5c.1` Build Westminster Gazette Lightning App and navigation
- `WestminsterGazette-y5c.2` Build page layouts with related lists and file uploads
- `WestminsterGazette-y5c.3` Build responder/ops focused mobile app page

## 5) `WestminsterGazette-prs` EPIC: Workflow Automation and SLA Execution
- `WestminsterGazette-prs.1` Intake and triage automation
- `WestminsterGazette-prs.2` SLA and escalation automation
- `WestminsterGazette-prs.3` Closure and audit automation

## 6) `WestminsterGazette-w55` EPIC: Integration and Data Onboarding
- `WestminsterGazette-w55.1` Seed import templates for key objects
- `WestminsterGazette-w55.2` Integration stubs for external systems

## 7) `WestminsterGazette-qi6` EPIC: Reporting, UAT, and Release Readiness
- `WestminsterGazette-qi6.1` KPI and SLA dashboard pack
- `WestminsterGazette-qi6.2` End-to-end UAT script and sample data
- `WestminsterGazette-qi6.3` Deployment runbook and cutover checklist

## Recommended MVP Execution Order
1. Foundation: `4ox.1`, `4ox.2`, `4ox.3`
2. Core model: `p36.1`, `p36.2`, `p36.3`, `p36.4`, then `p36.5`
3. Security baseline (parallel start after `4ox.2`): `2no.1`, `2no.3`
4. UX shell: `y5c.1`, `y5c.2`, then `y5c.3`
5. Automation: `prs.1`, `prs.2`, `prs.3`
6. Data onboarding and integrations: `w55.1`, `w55.2`
7. Reporting and release: `qi6.1`, `qi6.2`, `qi6.3`
8. Final hardening: `2no.2` least-privilege permission sets before production cutover

## CRUD Permission Set Scope Notes (`2no.1`)
- Include object CRUD for:
  - All in-scope native PSS/standard objects discovered in `4ox.2`
  - All custom objects delivered by `p36.*`, `prs.*`, and integration objects
- Include FLS Read/Edit for all in-scope custom fields
- Explicitly verify app/tab visibility works for System Administrator and deployment users
- Keep this permission set for build/UAT; runtime users use least-privilege sets (`2no.2`)
