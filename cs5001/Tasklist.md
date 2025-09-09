# Tasklist - NutriFlow (Assignment #5)

## Terminology

Here we establish a list of acronyms to promote brevity in the descriptions of the following tasks:
- **D0-D2**: three design diagrams created to satisfy assignment 4 (stored under `design_diagrams`)
- Features:
  - **MP**: Meal Planning
  - **PM**: Pantry Manager
  - **CE**: Cart Engine & Price Compare
  - **IX**: Intake Log & Analytics
  - **SR**: Search & Exploration
  - **CL**: Collaboration & Permissions 
  - **RE**: Recommendation Engine
  - **NT**: Notifications
  - **EI**: External Integrations (Store APIs, OCR/Barcode)

## Team

- **Randy** - Backend & Data Layer, External Service Integration, Frontend, AI/ML Integration
- **Sam** - Product QA, Backend API, Cart / Pantry Algorithms, Frontend, AI/ML Integration

## Tasks (14)

1. **Specify** SQLAlchemy models and database migrations for USER, HOUSEHOLD & Memberships, PANTRYITEM, CART/CARTITEM, STORE/STOREITEM & PriceHistory, INTAKELOG & Items, and ACTIONLOG, **[Owner: Randy]**.
2. **Specify** canonical data models (Quantity, Money, NutritionFacts) and normalize join tables for Recipe/Meal entities consistent with D2, **[Owner: Randy]**.
3. **Implement** authorization and role checks for CL (admin/member/viewer) including granular pantry/cart edit toggles and visibility on FOOD/RECIPE/MEAL/MEALPLAN, **[Owner: Randy]**.
4. **Implement** store/e‑commerce adapters (e.g., Kroger/Walmart/Instacart mocks) and implement the price history ingestion pipeline into STORE/STOREITEM, **[Owner: Randy]**.
5. **Implement** OCR/Barcode receipt ingestion using external services, parse line items, match to STOREITEM with confidence scoring, and emit PANTRYITEM updates, **[Owner: Randy]**.
6. **Design** UI for PM, CE, SR, **[Owner: Randy]**.
7. **Implement** UI for PM, CE, SR, **[Owner: Randy]**.
8. **Research** Additional places to add AI/ML integration, such as a site chat bot or custom recipe creation, **[Owner: Randy]**.
9. **Implement** Additional AI/ML touch points using lightweight models to produce quality output as quickly as possible, **[Owner: Randy]**.

---

10. **Specify** MVP acceptance criteria and author QA test plans covering Plan creation, Pantry update from receipt, Cart generation, and Intake logging, **[Owner: Sam]**.
11. **Design** REST/OpenAPI endpoints for MP, PM, CE, IX, SR, and CL with clear resource lifecycles and error models, **[Owner: Sam]**.
12. **Develop** automated API contract tests and end‑to‑end UI tests with seeded fixtures and synthetic store/recipe data for critical paths, **[Owner: Sam]**.
13. **Develop** Smart Cart UI (plan‑vs‑pantry diff, store switcher, price cards, recipe cost breakdown) aligned to CE outputs and error states, **[Owner: Sam]**.
14. **Build** the CE computation that derives “Needed Items” (Plan − Pantry), evaluates substitutions, and normalizes price‑per‑serving, **[Owner: Sam]**.
15. **Optimize** IX roll‑ups (ingredient→recipe→meal→plan→intake) with caching for day/week summaries and expose progress bars to the UI, **[Owner: Sam]**.
16. **Design** UI for MP, IX, RE, **[Owner: Sam]**.
17. **Implement** UI for MP, IX, RE, **[Owner: Sam]**.
18. **Establish** automated testing according to QA plans and add project documentation, **[Owner: Sam]**.