# NutriFlow – MVP Software Test Plan

This document describes the overall testing strategy as well as detailed test cases for the **NutriFlow** MVP. The test cases are derived from the MVP feature list and data models in the project design document (e.g., CRUD for foods/meals/meal plans/recipes, intake logging, pantry/cart management, etc.). 

---

## Part I. Overall Test Plan Description

NutriFlow’s MVP is a multi-entity system with non-trivial relationships (e.g., **Meals** reference Foods/Ingredients, **Meal Plans** schedule Meals, **Carts** are derived from planned Meals and Pantry contents, and **Households** govern shared access control). Our primary strategy is **repeatable, requirements-driven blackbox functional testing** at the API/UI boundary to validate that core user workflows (CRUD operations, logging intake, pantry/cart synchronization, collaboration) behave correctly without relying on our knowledge of internal implementation details.

In parallel, we use **whitebox unit testing** for high-risk internal logic that is easy to regress: nutrition aggregation (sum of macros across foods/ingredients/meals), permission and role enforcement, cart generation and mismatch detection rules, and search filtering logic. We include **abnormal** and **boundary** cases for invalid inputs and constraint violations (e.g., negative quantities, invalid units, missing references, unauthorized actions), ensuring the system fails safely with clear validation errors and without corrupting state.

Performance testing in the MVP is limited and applied selectively to **search** and **nutrition aggregation**, since these operations scale with user data size. Because we have not established concrete performance criteria at this phase, these tests will be designated as functional for now, and focus on correctness and reliability. More performance testing will be necessary as the project progresses.

---

## Part II. Test Case Descriptions

> **Notation:** Test cases use TC-XX identifiers. For assignment items 6–9, one primary term is chosen per test, with some containing a secondary designation if it is a multi-stage test (some tests contain additional steps to avoid too much redundancy in the test suite).

### TC-01: User Registration
- **Purpose:** Verify successful account creation and uniqueness constraint on email.
- **Description:** Create a user with a valid, unused email; then attempt registration again with the same email.
- **Inputs:** first_name, last_name, email (unique → duplicate), valid password.
- **Expected Output:** First registration succeeds; second registration is rejected with a “duplicate email” validation error; no duplicate user record exists in DB.
- **Case Type:** Normal/Boundary
- **Test Type:** Blackbox
- **Test Focus:** Functional
- **Test Level:** Integration

---

### TC-02: Login
- **Purpose:** Verify authentication accepts valid credentials and rejects invalid passwords.
- **Description:** Log in with correct email/password; then retry with incorrect password.
- **Inputs:** email; password (correct → incorrect).
- **Expected Output:** First login returns session/token; second returns authentication error; account remains unchanged.
- **Case Type:** Normal/Boundary
- **Test Type:** Blackbox
- **Test Focus:** Functional
- **Test Level:** Integration

---

### TC-03: Food CRUD – Create, Read, Update, Delete
- **Purpose:** Validate CRUD for user-defined foods.
- **Description:** Create a food with nutrition facts; retrieve it; update name/macros; delete it; confirm it is gone.
- **Inputs:** Food name, nutrition facts, category/subcategory, visibility.
- **Expected Output:** Food persists, updates persist, and deletion removes it from listings and direct fetch.
- **Case Type:** Normal
- **Test Type:** Blackbox
- **Test Focus:** Functional
- **Test Level:** Integration

---

### TC-04: Meal CRUD – Create, Read, Update, Delete with Foods and Ingredients
- **Purpose:** Validate full CRUD functionality for user-defined meals composed of foods and/or ingredients.
- **Description:** Create a meal composed of multiple foods and/or ingredients with quantities; retrieve the meal and verify its composition; update the meal’s name and quantities; delete the meal; confirm it is no longer retrievable.
- **Inputs:** 
  - Meal name  
  - foods_map {food_id → quantity} and/or ingredients_map {ingredient_id → quantity}  
  - visibility  
- **Expected Output:** Meal persists with correct references and quantities; updates are saved correctly; deletion removes the meal from all listings and direct fetch.
- **Case Type:** Normal
- **Test Type:** Blackbox
- **Test Focus:** Functional
- **Test Level:** Integration

---

### TC-05: Recipe CRUD – Create, Read, Update, Delete with Foods/Ingredients, Instructions, and Servings
- **Purpose:** Validate full CRUD functionality for user-defined recipes composed of foods and/or ingredients with preparation instructions and serving metadata.
- **Description:** Create a recipe composed of multiple foods and/or ingredients with quantities, an ordered list of instructions, and a specified number of servings; retrieve the recipe and verify its composition and instruction order; update the recipe’s name, ingredient/food quantities, or servings; delete the recipe; confirm it is no longer retrievable.
- **Inputs:** 
  - Recipe name  
  - foods_map {food_id → quantity} and/or ingredients_map {ingredient_id → quantity}  
  - instructions[] (ordered list of steps)  
  - servings  
  - visibility  
- **Expected Output:** Recipe persists with correct references, quantities, instruction order, and serving count; updates are saved correctly; deletion removes the recipe from all listings and direct fetch.
- **Case Type:** Normal
- **Test Type:** Blackbox
- **Test Focus:** Functional
- **Test Level:** Integration

---

### TC-06: Meal Plan CRUD – Create and Schedule Meals
- **Purpose:** Validate meal plan creation and scheduling of meals.
- **Description:** Create a meal plan; add meal_plan_entry items with valid meal_id and datetime; retrieve schedule.
- **Inputs:** meal_plan.name; schedule entries (meal_id, when, locked).
- **Expected Output:** Meal plan persists; schedule entries persist; ordering and timestamps preserved.
- **Case Type:** Normal
- **Test Type:** Blackbox
- **Test Focus:** Functional
- **Test Level:** Integration

---

### TC-07 Input Validation - Food, Meal, Recipe, Mealplan
- **Purpose:** Ensure invalid numerical inputs and references to other objects are rejected.
- **Description:** Attempt to create/update a food, meal, recipe, and mealplan with negative values, missing required fields, or references to non-existent objects
- **Inputs:** calories < 0, omitted required macro fields, quantity_of_food < 0, invalid meal_id, etc.
- **Expected Output:** Validation errors; no records created/updated; system state unchanged.
- **Case Type:** Boundary
- **Test Type:** Blackbox
- **Test Focus:** Functional
- **Test Level:** Unit

---

### TC-08: Intake Log – Log Meal to Specific Date
- **Purpose:** Verify daily nutrition tracking via intake log.
- **Description:** Create an intake log entry for a date and add a meal (both predefined and list of foods/ingredients).
- **Inputs:** date; meal reference; optional quantity metadata.
- **Expected Output:** Intake log contains the entry; associated meal references are correct.
- **Case Type:** Normal
- **Test Type:** Blackbox
- **Test Focus:** Functional
- **Test Level:** Integration

---

### TC-09: Intake Log Validation – Invalid Date and Empty Entry
- **Purpose:** Ensure intake log rejects malformed/empty entries.
- **Description:** Attempt to create an intake log with invalid date format; attempt to add an intake item with neither foods_map nor ingredients_map nor meal.
- **Inputs:** invalid date; empty intake_log_item.
- **Expected Output:** Validation errors; log not created/updated.
- **Case Type:** Abnormal
- **Test Type:** Blackbox
- **Test Focus:** Functional
- **Test Level:** Integration

---

### TC-10: Nutrition Aggregation – Correct Totals Across Meal
- **Purpose:** Validate macro calculations for a meal built from foods with known nutrition.
- **Description:** Use foods with deterministic macros; create a meal; compute totals.
- **Inputs:** foods with known calories/protein/carb/fat; quantities.
- **Expected Output:** Aggregated totals match expected sums (within rounding rules if applicable).
- **Case Type:** Normal
- **Test Type:** Whitebox
- **Test Focus:** Functional
- **Test Level:** Unit

---

### TC-11: Household – Create Household and Add Member
- **Purpose:** Validate MVP collaboration: a user can create a household and add members.
- **Description:** Create household; invite/add another existing user; verify membership.
- **Inputs:** household name; invited user identifier.
- **Expected Output:** household created; membership record created; member appears in household members list.
- **Case Type:** Normal
- **Test Type:** Blackbox
- **Test Focus:** Functional
- **Test Level:** Integration

---

### TC-12: Household Roles/Permissions – Restrict Pantry/Cart Modification
- **Purpose:** Ensure permission flags (can_modify_cart / can_modify_pantry) are enforced.
- **Description:** Configure member with can_modify_pantry=false; attempt pantry update. Configure member with can_modify_cart=false; attempt cart update.
- **Inputs:** membership permission flags; pantry/cart modification requests.
- **Expected Output:** Unauthorized modifications rejected with permission error; authorized actions succeed.
- **Case Type:** Abnormal
- **Test Type:** Whitebox
- **Test Focus:** Functional
- **Test Level:** Unit

---

### TC-13: Pantry CRUD – Add/Remove Pantry Items
- **Purpose:** Validate household pantry CRUD for MVP.
- **Description:** Add pantry item (food_id or ingredient_id or store_item_id); update servings_left; remove item.
- **Inputs:** pantry_item fields (one-of IDs), servings_left, storage_medium.
- **Expected Output:** Pantry item created/updated/deleted; pantry list reflects changes.
- **Case Type:** Normal
- **Test Type:** Blackbox
- **Test Focus:** Functional
- **Test Level:** Integration

---

### TC-14: Pantry Expiration Warnings – Expired and Near-Expiry
- **Purpose:** Verify expiry warnings/recommendations for pantry items.
- **Description:** Create items with expiration_date in the past, today, and near-future; request pantry warnings.
- **Inputs:** expiration_date ∈ {past, today, +N days}.
- **Expected Output:** Past-dated items flagged as expired; today/near-future flagged as expiring soon per rules; no false positives for far-future dates.
- **Case Type:** Boundary
- **Test Type:** Blackbox
- **Test Focus:** Functional
- **Test Level:** Integration

---

### TC-15: Cart – Auto-Populate from Meal Plan with Pantry Factoring
- **Purpose:** Validate MVP cart auto-population based on planned meals and pantry contents.
- **Description:** With a meal plan active and pantry containing some needed items, generate cart for date range.
- **Inputs:** active meal plan range; pantry items; planned meals with required ingredients/foods.
- **Expected Output:** Cart includes only missing required items (not already satisfied by pantry, per rules); quantities are correct.
- **Case Type:** Normal
- **Test Type:** Whitebox
- **Test Focus:** Functional
- **Test Level:** Integration

---

### TC-16: Cart – Manual Add/Remove and Mismatch Warning
- **Purpose:** Validate manual cart edits and mismatch detection warning.
- **Description:** Manually remove a required planned item; manually add unrelated item; validate mismatch warning; restore required item and verify warning clears.
- **Inputs:** cart modifications; planned meal requirements.
- **Expected Output:** Warning triggered when cart diverges from planned meals; warning cleared when cart matches requirements.
- **Case Type:** Abnormal
- **Test Type:** Blackbox
- **Test Focus:** Functional
- **Test Level:** Integration

---

### TC-17: Search – Full-Text Search with Filters (Ingredient/Food/Recipe)
- **Purpose:** Validate MVP exploration: searchable entities with filters.
- **Description:** Seed known foods/ingredients/recipes; search by keyword; apply filters; verify returned set.
- **Inputs:** query string; filters (entity type, category, etc.).
- **Expected Output:** Results contain all and only matching items; filters reduce results correctly; empty search yields sensible default (per spec).
- **Case Type:** Normal
- **Test Type:** Blackbox
- **Test Focus:** Functional
- **Test Level:** Integration

---

### TC-18: Search – No Results and Special Characters
- **Purpose:** Ensure search handles edge input safely.
- **Description:** Search for a string that should return zero results; search with special characters and very long query.
- **Inputs:** query="zzzz-not-found"; query with punctuation/emoji; long query string.
- **Expected Output:** Empty result set with no error; special/long queries do not crash and return either empty or valid matches.
- **Case Type:** Abnormal
- **Test Type:** Blackbox
- **Test Focus:** Functional
- **Test Level:** Integration

---

### TC-19: Receipt Import – OCR Pipeline State Transitions
- **Purpose:** Validate MVP receipt scanning flow for pantry update assistance.
- **Description:** Upload receipt images; verify status transitions through uploaded→parsed→applied; verify error handling.
- **Inputs:** receipt image(s): (a) clear receipt, (b) unreadable/blank image.
- **Expected Output:** Clear receipt produces parsed lines and can be applied; unreadable image transitions to error with diagnostic; no pantry corruption.
- **Case Type:** Abnormal
- **Test Type:** Blackbox
- **Test Focus:** Functional
- **Test Level:** Integration

---

## Part III. Test Case Matrix

| Test Case ID | Normal / Abnormal / Boundary | Blackbox / Whitebox | Functional / Performance | Unit / Integration |
|--------------|------------------------------|----------------------|--------------------------|--------------------|
| TC-01 | Normal / Boundary | Blackbox | Functional | Integration |
| TC-02 | Normal / Boundary | Blackbox | Functional | Integration |
| TC-03 | Normal | Blackbox | Functional | Integration |
| TC-04 | Normal | Blackbox | Functional | Integration |
| TC-05 | Normal | Blackbox | Functional | Integration |
| TC-06 | Normal | Blackbox | Functional | Integration |
| TC-07 | Boundary | Blackbox | Functional | Unit |
| TC-08 | Normal | Blackbox | Functional | Integration |
| TC-09 | Abnormal | Blackbox | Functional | Integration |
| TC-10 | Normal | Whitebox | Functional | Unit |
| TC-11 | Normal | Blackbox | Functional | Integration |
| TC-12 | Abnormal | Whitebox | Functional | Unit |
| TC-13 | Normal | Blackbox | Functional | Integration |
| TC-14 | Boundary | Blackbox | Functional | Integration |
| TC-15 | Normal | Whitebox | Functional | Integration |
| TC-16 | Abnormal | Blackbox | Functional | Integration |
| TC-17 | Normal | Blackbox | Functional | Integration |
| TC-18 | Abnormal | Blackbox | Functional | Integration |
| TC-19 | Abnormal | Blackbox | Functional | Integration |
