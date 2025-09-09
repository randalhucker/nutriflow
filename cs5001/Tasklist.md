# Tasklist - NutriFlow (Assignment #5)

> Scope aligns with Design Diagrams (D0–D2): Meal Planning (MP), Pantry Manager (PM), Cart Engine & Price Compare (CE), Intake Log & Analytics (IX), Search & Exploration (SR), Collaboration & Permissions (CL), Recommendation Engine (RE), Notifications (NT), and External Integrations (Store APIs, OCR/Barcode).

## Team

- **Randy** - Backend & Data Layer, Frontend, Service Integration
- **Sam** - Data Integrations, Product QA, Frontend

## Tasks (14)

1. **Specify** canonical domain types (Quantity, Money, NutritionFacts) and normalize join tables for Recipe/Meal entities consistent with D2, **[Owner: Randy]**.
2. **Design** REST/OpenAPI endpoints for MP, PM, CE, IX, SR, and CL with clear resource lifecycles and error models, **[Owner: Randy]**.
3. **Develop** SQLAlchemy models and database migrations for USER, HOUSEHOLD & Memberships, PANTRYITEM, CART/CARTITEM, STORE/STOREITEM & PriceHistory, INTAKELOG & Items, and ACTIONLOG, **[Owner: Randy]**.
4. **Implement** authorization and role checks for CL (admin/member/viewer) including granular pantry/cart edit toggles and visibility on FOOD/RECIPE/MEAL/MEALPLAN, **[Owner: Randy]**.
5. **Build** the CE computation that derives “Needed Items” (Plan − Pantry), evaluates substitutions, and normalizes price‑per‑serving, **[Owner: Randy]**.
6. **Optimize** IX roll‑ups (ingredient→recipe→meal→plan→intake) with caching for day/week summaries and expose progress bars to the UI, **[Owner: Randy]**.
7. **Integrate** service stubs for store checkout/autoload flows to support future e‑commerce handoff while gating behind feature flags, **[Owner: Randy]**.

---

8. **Integrate** store/e‑commerce adapters (e.g., Kroger/Walmart/Instacart mocks) and implement the price history ingestion pipeline into STORE/STOREITEM, **[Owner: Sam]**.
9. **Implement** OCR/Barcode receipt ingestion using external services, parse line items, match to STOREITEM with confidence scoring, and emit PANTRYITEM updates, **[Owner: Sam]**.
10. **Develop** Smart Cart UI (plan‑vs‑pantry diff, store switcher, price cards, recipe cost breakdown) aligned to CE outputs and error states, **[Owner: Sam]**.
11. **Build** SR UI with global command bar (⌘K), filters, nutrition sliders, cuisine chips, and “similar items” carousels backed by search endpoints, **[Owner: Sam]**.
12. **Specify** MVP acceptance criteria and author QA test plans covering Plan creation, Pantry update from receipt, Cart generation, and Intake logging, **[Owner: Sam]**.
13. **Develop** automated API contract tests and end‑to‑end UI tests with seeded fixtures and synthetic store/recipe data for critical paths, **[Owner: Sam]**.
14. **Validate** security, privacy, and data retention policies (PII, household sharing, action logs) and document outcomes in the project runbook, **[Owner: Sam]**.
