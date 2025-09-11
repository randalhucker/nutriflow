# NutriFlow - Milestones, Timeline, and Effort Matrix (Assignment #6)

**Team Members:** Randy Hucker; Sam Graler  
**Project Title:** NutriFlow  
**Start Date:** 2025-09-09 • **Due Date:** 2026-03-27  
**Goal Statement:** Help households plan meals, track nutrition, and purchase ingredients at the best value while minimizing waste.

---

## Milestones List (with explanations)

- **M1 - Project Kickoff & Architecture Baseline (2025-09-15):** Agree on canonical data types (Quantity, Money, NutritionFacts), initial ER model, and high-level API surface; align on D2 entities.
- **M2 - Core Data Layer & Auth Complete (2025-10-20):** Models + migrations ready; Collaboration/Permissions (CL) roles in place; seeds available for dev/test.
- **M3 - External Integrations Alpha (2025-11-14):** Store adapters and OCR/Barcode pipeline ingest data into STOREITEM/PriceHistory and PANTRYITEM; basic price compare flows.
- **M4 - Cart Engine + Smart Cart UI Beta (2025-12-12):** CE computes Needed Items (Plan − Pantry), substitutions; Smart Cart UI shows diffs, store switcher, cost breakdown.
- **M5 - Search/Planning/Intake UI Cohesion (2026-01-20):** MP, IX, SR, RE UIs implemented and integrated with endpoints; macro rollups visible with progress hooks.
- **M6 - AI/ML Touchpoints POC (2026-02-10):** Lightweight AI features (recipe assist, similarity, chatbot) deployed behind flags; measured for latency/quality.
- **M7 - QA Coverage, Security & Docs (2026-03-10):** Acceptance criteria met; API contract + E2E tests passing; security/privacy reviewed; runbook and user help drafted.
- **M8 - MVP Release Candidate & Final Submission (2026-03-27):** Demo-ready build with end-to-end flow; submission package prepared and delivered.

> Milestones map to subsystems in D1/D2: MP (Meal Planning), PM (Pantry), CE (Cart Engine & Price Compare), IX (Intake Log), SR (Search), CL (Collaboration), RE (Recs), NT (Notifications), EI (External Integrations).

---

## Table 1. Timeline (Tasks and Milestones)

_All dates are planned; sequencing reflects dependencies across modules._

|  ID |   Type    | Task/Milestone                                                                                                           | Owner (Primary) | Start      | End / Planned Date | Dependencies | Deliverable / Notes                                                                                                                  |
| --: | :-------: | :----------------------------------------------------------------------------------------------------------------------- | :-------------- | :--------- | :----------------- | :----------- | :----------------------------------------------------------------------------------------------------------------------------------- |
|   1 |   Task    | Specify SQLAlchemy models and migrations (USER/HOUSEHOLD/Memberships/PANTRYITEM/CART/STORE/LOG)                          | Randy           | 2025-09-09 | 2025-10-06         | -            | -                                                                                                                                    |
|   2 |   Task    | Specify canonical data models (Quantity/Money/NutritionFacts) and normalize joins for Recipe/Meal                        | Randy           | 2025-09-09 | 2025-09-20         | -            | -                                                                                                                                    |
|   3 |   Task    | Implement CL authorization and role checks (admin/member/viewer) with granular pantry/cart toggles and entity visibility | Randy           | 2025-10-01 | 2025-10-20         | 1            | -                                                                                                                                    |
|   4 |   Task    | Implement store/e-commerce adapters and price history ingestion into STORE/STOREITEM                                     | Randy           | 2025-10-06 | 2025-11-07         | 1            | -                                                                                                                                    |
|   5 |   Task    | Implement OCR/Barcode receipt ingestion; parse, match to STOREITEM with confidence; emit PANTRYITEM updates              | Randy           | 2025-10-10 | 2025-11-14         | 1            | -                                                                                                                                    |
|   6 |   Task    | Design UI for PM, CE, SR                                                                                                 | Randy           | 2025-10-15 | 2025-11-05         | 1,2          | -                                                                                                                                    |
|   7 |   Task    | Implement UI for PM, CE, SR                                                                                              | Randy           | 2025-11-06 | 2025-12-10         | 6,4,5        | -                                                                                                                                    |
|   8 |   Task    | Research additional AI/ML touch points (chatbot, custom recipes, similarity search)                                      | Randy           | 2025-12-01 | 2026-01-10         | 4,5          | -                                                                                                                                    |
|   9 |   Task    | Implement additional AI/ML touch points with lightweight models (fast outputs)                                           | Randy           | 2026-01-11 | 2026-02-10         | 8            | -                                                                                                                                    |
|  10 |   Task    | Specify MVP acceptance criteria and QA test plans (Plan, Pantry-from-receipt, Cart, Intake)                              | Sam             | 2025-09-15 | 2025-09-26         | 1,2          | -                                                                                                                                    |
|  11 |   Task    | Design REST/OpenAPI endpoints for MP, PM, CE, IX, SR, CL with lifecycles and error models                                | Sam             | 2025-09-12 | 2025-10-01         | 1,2          | -                                                                                                                                    |
|  12 |   Task    | Develop automated API contract tests and E2E UI tests with seeded fixtures                                               | Sam             | 2025-10-20 | 2025-11-20         | 11           | -                                                                                                                                    |
|  13 |   Task    | Develop Smart Cart UI (plan-vs-pantry diff, store switcher, price cards, recipe cost breakdown)                          | Sam             | 2025-11-10 | 2025-12-12         | 7,4,14       | -                                                                                                                                    |
|  14 |   Task    | Build CE computation (Needed Items, substitutions, price-per-serving)                                                    | Sam             | 2025-10-25 | 2025-11-30         | 3            | -                                                                                                                                    |
|  15 |   Task    | Optimize IX rollups (ingredient→recipe→meal→plan→intake) and caching; expose UI progress                                 | Sam             | 2025-12-15 | 2026-01-15         | 1            | -                                                                                                                                    |
|  16 |   Task    | Design UI for MP, IX, RE                                                                                                 | Sam             | 2025-11-01 | 2025-11-20         | 11           | -                                                                                                                                    |
|  17 |   Task    | Implement UI for MP, IX, RE                                                                                              | Sam             | 2025-11-21 | 2026-01-20         | 16,15        | -                                                                                                                                    |
|  18 |   Task    | Establish automated testing per QA plans and add project documentation                                                   | Sam             | 2026-02-01 | 2026-03-10         | 10,12        | -                                                                                                                                    |
|  M1 | Milestone | Project Kickoff & Architecture Baseline                                                                                  | -               | -          | **2025-09-15**     | see tasks    | Agree on canonical data types (Quantity, Money, NutritionFacts), initial ER model, and high-level API surface; align on D2 entities. |
|  M2 | Milestone | Core Data Layer & Auth Complete                                                                                          | -               | -          | **2025-10-20**     | see tasks    | Models + migrations ready; Collaboration/Permissions (CL) roles in place; seeds available for dev/test.                              |
|  M3 | Milestone | External Integrations Alpha                                                                                              | -               | -          | **2025-11-14**     | see tasks    | Store adapters and OCR/Barcode pipeline ingest data into STOREITEM/PriceHistory and PANTRYITEM; basic price compare flows.           |
|  M4 | Milestone | Cart Engine + Smart Cart UI Beta                                                                                         | -               | -          | **2025-12-12**     | see tasks    | CE computes Needed Items (Plan − Pantry), substitutions; Smart Cart UI shows diffs, store switcher, cost breakdown.                  |
|  M5 | Milestone | Search/Planning/Intake UI Cohesion                                                                                       | -               | -          | **2026-01-20**     | see tasks    | MP, IX, SR, RE UIs implemented and integrated with endpoints; macro rollups visible with progress hooks.                             |
|  M6 | Milestone | AI/ML Touchpoints POC                                                                                                    | -               | -          | **2026-02-10**     | see tasks    | Lightweight AI features (recipe assist, similarity, chatbot) deployed behind flags; measured for latency/quality.                    |
|  M7 | Milestone | QA Coverage, Security & Docs                                                                                             | -               | -          | **2026-03-10**     | see tasks    | Acceptance criteria met; API contract + E2E tests passing; security/privacy reviewed; runbook and user help drafted.                 |
|  M8 | Milestone | MVP Release Candidate & Final Submission                                                                                 | -               | -          | **2026-03-27**     | see tasks    | Demo-ready build with end-to-end flow; submission package prepared and delivered.                                                    |

---

## Table 2. Effort Matrix (Percent of Effort per Task)

_Primary owner receives the larger share. Percentages per task sum to 100%._

|  ID | Task (short)                                                                                                | Randy (%) | Sam (%) | Primary |
| --: | :---------------------------------------------------------------------------------------------------------- | --------: | ------: | :------ |
|   1 | Specify SQLA models and migrations                                                                          |        80 |      20 | Randy   |
|   2 | Specify canonical data models                                                                               |        80 |      20 | Randy   |
|   3 | Implement CL auth and role checks                                                                           |        75 |      25 | Randy   |
|   4 | Implement store/e-commerce adapters and price history ingestion into STORE/STOREITEM                        |        70 |      30 | Randy   |
|   5 | Implement OCR/Barcode receipt ingestion; parse, match to STOREITEM with confidence; emit PANTRYITEM updates |        70 |      30 | Randy   |
|   6 | Design UI for PM, CE, SR                                                                                    |        60 |      40 | Randy   |
|   7 | Implement UI for PM, CE, SR                                                                                 |        60 |      40 | Randy   |
|   8 | Research additional AI/ML touch points                                                                      |        60 |      40 | Randy   |
|   9 | Implement additional AI/ML touch points with lightweight models                                             |        65 |      35 | Randy   |
|  10 | Specify MVP acceptance criteria and QA test plans                                                           |        20 |      80 | Sam     |
|  11 | Design REST/OpenAPI endpoints for MP, PM, CE, IX, SR, CL with lifecycles and error models                   |        30 |      70 | Sam     |
|  12 | Develop automated API contract tests and E2E UI tests with seeded fixtures                                  |        25 |      75 | Sam     |
|  13 | Develop Smart Cart UI                                                                                       |        35 |      65 | Sam     |
|  14 | Build CE computation                                                                                        |        30 |      70 | Sam     |
|  15 | Optimize IX rollups                                                                                         |        30 |      70 | Sam     |
|  16 | Design UI for MP, IX, RE                                                                                    |        25 |      75 | Sam     |
|  17 | Implement UI for MP, IX, RE                                                                                 |        25 |      75 | Sam     |
|  18 | Establish automated testing per QA plans and add project documentation                                      |        25 |      75 | Sam     |

**Totals (sum of task-level percentages):** Randy = 865 • Sam = 935

> Distribution matches roles: Randy leads backend/data layer and integrations; Sam leads CE/algorithms, QA, and UI for MP/IX/SR/RE/Cart.
