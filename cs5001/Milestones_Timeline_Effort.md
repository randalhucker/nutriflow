# NutriFlow - Milestones, Timeline, and Effort Matrix (Assignment #6)

**Team Members:** Randy Hucker, Sam Graler  
**Project Title:** NutriFlow  
**Goal Statement:** Help households plan meals, track nutrition, and purchase ingredients at the best value while minimizing waste.  
**Planning Window:** Start **2025-09-09** → Final submission **2025-12-08**.

This document reflects the updated Tasklist (18 items) and the modules/subsystems from the approved design (MP, PM, CE, IX, SR, CL, RE, NT, EI). Milestones are mapped to these subsystems and appear in the timeline table.

---

## Milestones List

- **M1 - Project Kickoff & Architecture Baseline (Sep 12, 2025):** Confirm canonical domain types (Quantity, Money, NutritionFacts), agree on initial data entities, and sketch service/API boundaries. Deliverables: shared glossary, entity list, and high-level API map.
- **M2 - Data Models & Migrations Ready (Sep 23, 2025):** SQLAlchemy models and Alembic migrations ready for core entities (USER, HOUSEHOLD/Memberships, PANTRYITEM, CART/CARTITEM, STORE/STOREITEM/PriceHistory, INTAKELOG/Items, ACTIONLOG). Seed fixtures available.
- **M3 - API Design & QA Plan Approved (Sep 23, 2025):** REST/OpenAPI endpoints (MP, PM, CE, IX, SR, CL) reviewed; MVP acceptance criteria and QA plans approved.
- **M4 - Integrations Alpha (Oct 8, 2025):** OCR/Barcode ingestion creates PANTRYITEM updates; mock store adapters feed STOREITEM + PriceHistory; CE can read external data for comparisons.
- **M5 - Cart Engine Compute + Smart Cart UI Beta (Oct 26, 2025):** CE computes “Needed Items” (Plan − Pantry), evaluates substitutions; Smart Cart UI shows diff, store switcher, price cards, and recipe cost breakdown.
- **M6 - Analytics Rollups + UI Implementations (Nov 3, 2025):** IX rollups across ingredient→recipe→meal→plan→intake cached; MP/IX/RE and PM/CE/SR UI implementations hit functional parity for MVP.
- **M7 - Testing Suite in Place (Nov 10, 2025):** Contract tests and E2E tests for critical paths are automated and green in CI.
- **M8 - Feature Complete & Security Review (Dec 1, 2025):** MVP features closed; documentation and runbook up to date; privacy/retention/security checks complete.
- **M9 - Final MVP Demo & Submission (Dec 8, 2025):** End-to-end demonstration and course submission (includes names of all team members).

> Milestones trace to the D1/D2 modules: MP, PM, CE, IX, SR, CL, RE, NT, and EI.

---

## Table 1. Timeline (Tasks and Milestones)

_All dates are planned and reflect dependencies and module sequencing across the Sept 9–Dec 8 window._

|  ID |   Type    | Task/Milestone                                                                    | Owner (Primary) | Start      | End / Planned Date | Dependencies | Deliverable / Notes                                             |
| --: | :-------: | :-------------------------------------------------------------------------------- | :-------------- | :--------- | :----------------- | :----------- | :-------------------------------------------------------------- |
|   1 |   Task    | Specify SQLAlchemy models & migrations (core entities)                            | Randy           | 2025-09-09 | 2025-09-23         | -            | Models & Alembic migrations; seed fixtures                      |
|   2 |   Task    | Specify canonical data models (Quantity, Money, NutritionFacts) & normalize joins | Randy           | 2025-09-09 | 2025-09-16         | -            | D2-aligned types and Recipe/Meal joins                          |
|   3 |   Task    | Implement CL authorization/roles & visibility rules                               | Randy           | 2025-09-20 | 2025-09-27         | 1            | Policy middleware + tests; FOOD/RECIPE/MEAL/MEALPLAN visibility |
|   4 |   Task    | Implement store/e-commerce adapters & price history ingestion                     | Randy           | 2025-09-23 | 2025-10-07         | 1            | Mock providers + ingestion pipeline                             |
|   5 |   Task    | Implement OCR/Barcode receipt ingestion → PANTRYITEM updates                      | Randy           | 2025-09-24 | 2025-10-08         | 1            | OCR pipeline; line matching with confidence; pantry writes      |
|   6 |   Task    | Design UI for PM, CE, SR                                                          | Randy           | 2025-09-20 | 2025-09-30         | 1,2          | Wireframes and interaction specs                                |
|   7 |   Task    | Implement UI for PM, CE, SR                                                       | Randy           | 2025-10-12 | 2025-10-26         | 4,5,6        | React views integrated with CE/PM/SR endpoints                  |
|   8 |   Task    | Research AI/ML touchpoints (chatbot, recipe gen, similarity)                      | Randy           | 2025-10-15 | 2025-10-22         | 1–7          | Findings doc + feasibility notes                                |
|   9 |   Task    | Implement lightweight AI/ML touchpoints                                           | Randy           | 2025-10-22 | 2025-11-05         | 8            | Minimal viable models wired into UX                             |
|  10 |   Task    | Specify MVP acceptance criteria & QA test plans                                   | Sam             | 2025-09-15 | 2025-09-22         | 1,2          | Written criteria; test plan checklist                           |
|  11 |   Task    | Design REST/OpenAPI endpoints (MP, PM, CE, IX, SR, CL)                            | Sam             | 2025-09-10 | 2025-09-20         | 1,2          | OpenAPI spec with error models                                  |
|  12 |   Task    | Develop API contract tests & E2E tests (seeded fixtures)                          | Sam             | 2025-10-20 | 2025-11-10         | 1,3,11       | CI jobs for contract & E2E                                      |
|  13 |   Task    | Develop Smart Cart UI (diff, switcher, price cards, cost breakdown)               | Sam             | 2025-10-10 | 2025-10-24         | 4            | Smart Cart screens aligned to CE                                |
|  14 |   Task    | Build CE computation (Needed Items, substitutions, price/serving)                 | Sam             | 2025-10-01 | 2025-10-15         | 1,11         | CE service with unit tests                                      |
|  15 |   Task    | Optimize IX rollups & caching (day/week) + progress hooks                         | Sam             | 2025-10-05 | 2025-10-19         | 1            | Aggregators + cache strategy                                    |
|  16 |   Task    | Design UI for MP, IX, RE                                                          | Sam             | 2025-09-20 | 2025-09-30         | 1,2          | Wireframes & content model                                      |
|  17 |   Task    | Implement UI for MP, IX, RE                                                       | Sam             | 2025-10-20 | 2025-11-03         | 14,15,16     | React views; rollup visualizations                              |
|  18 |   Task    | Establish automated testing & project documentation                               | Sam             | 2025-11-10 | 2025-11-24         | 10,12        | CI coverage; contributor docs/runbook                           |
|  M1 | Milestone | Project Kickoff & Architecture Baseline                                           | -               | -          | **2025-09-12**     | 1–2 (drafts) | Glossary + entity/API sketch                                    |
|  M2 | Milestone | Data Models & Migrations Ready                                                    | -               | -          | **2025-09-23**     | 1–2          | Core DB ready; seeds done                                       |
|  M3 | Milestone | API Design & QA Plan Approved                                                     | -               | -          | **2025-09-22**     | 10–11        | OpenAPI + QA plan approved                                      |
|  M4 | Milestone | Integrations Alpha                                                                | -               | -          | **2025-10-08**     | 4–5          | OCR/Barcode + store adapters                                    |
|  M5 | Milestone | CE Compute + Smart Cart UI Beta                                                   | -               | -          | **2025-10-26**     | 7,13,14      | CE + UI join; demoable                                          |
|  M6 | Milestone | Analytics Rollups + UI Implementations                                            | -               | -          | **2025-11-03**     | 7,15,17      | IX ready; MP/IX/RE + PM/CE/SR UIs                               |
|  M7 | Milestone | Testing Suite in Place                                                            | -               | -          | **2025-11-10**     | 12           | Contract + E2E in CI                                            |
|  M8 | Milestone | Feature Complete & Security Review                                                | -               | -          | **2025-12-01**     | 9,18         | Feature freeze + runbook/security                               |
|  M9 | Milestone | Final MVP Demo & Submission                                                       | -               | -          | **2025-12-08**     | M1–M8        | End-to-end demo + submission                                    |

---

## Table 2. Effort Matrix (Percent of Effort per Task)

_Primary owner receives the larger share. Percentages per task sum to 100%._

|  ID | Task (short)                     | Randy (%) | Sam (%) | Primary |
| --: | :------------------------------- | --------: | ------: | :------ |
|   1 | Models & migrations              |        80 |      20 | Randy   |
|   2 | Canonical data & joins           |        80 |      20 | Randy   |
|   3 | CL auth/roles & visibility       |        80 |      20 | Randy   |
|   4 | Store adapters & price ingestion |        75 |      25 | Randy   |
|   5 | OCR/Barcode → Pantry updates     |        75 |      25 | Randy   |
|   6 | UI design PM/CE/SR               |        60 |      40 | Randy   |
|   7 | Implement UI PM/CE/SR            |        60 |      40 | Randy   |
|   8 | Research AI/ML touchpoints       |        70 |      30 | Randy   |
|   9 | Implement AI/ML touchpoints      |        70 |      30 | Randy   |
|  10 | MVP criteria & QA plans          |        30 |      70 | Sam     |
|  11 | REST/OpenAPI endpoints           |        30 |      70 | Sam     |
|  12 | Contract + E2E tests             |        35 |      65 | Sam     |
|  13 | Smart Cart UI                    |        35 |      65 | Sam     |
|  14 | CE computation                   |        30 |      70 | Sam     |
|  15 | IX rollups & caching             |        30 |      70 | Sam     |
|  16 | UI design MP/IX/RE               |        40 |      60 | Sam     |
|  17 | Implement UI MP/IX/RE            |        35 |      65 | Sam     |
|  18 | Automation & documentation       |        30 |      70 | Sam     |

**Totals (normalized across all tasks):** Randy ≈ 50%; Sam ≈ 50%.

> The division of labor aligns with roles: Randy leads backend/data layer, integrations, and initial UI for PM/CE/SR; Sam leads API design, CE compute, IX rollups, Smart Cart UI, testing, and documentation.
