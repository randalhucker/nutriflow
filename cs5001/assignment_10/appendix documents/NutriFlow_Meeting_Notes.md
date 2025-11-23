# NutriFlow — Meeting Notes (Sept 2 – Nov 20, 2025)

The NutriFlow team met most Tuesdays and Thursdays during the semester from 3:30 to ~5:30 pm. Below are the meeting notes taken to track progress.

## Week of Sept 1, 2025

### **Tue, Sept 2, 2025 — Project Kickoff**
**Topics**
- Reviewed capstone expectations and team contract, ensuring understanding of deliverables and communication expectations.  
- Completed Assignment 3 (team portion), aligning on shared goals and division of labor.
- Discussed initial priorities, including how to balance early administrative workload with the need to begin design work.  

**Decisions**
- Team will begin with data model design since it will underpin UI planning, backend architecture, and API development.

**Action Items**
- Complete individual portions of Assignment 3.
- Begin listing entities based on early feature discussions, even if not finalized.

### **Thu, Sept 4, 2025 — Brainstorming**
**Topics**
- Walked through rarly ER model for USER, HOUSEHOLD, MEMBERSHIPS, PANTRYITEM, CART, STORE, STOREITEM, INTAKELOG.
- Discussed gaps between the early ER model and the actual user experience we envisioned.
- Realized the need to reverse the approach: define core features → derive data model from real workflows.

**Decisions**
- Household owns Pantry/Carts (important for collaboration and shared grocery planning).
- Re-align focus on features rather than data models so the schema accurately reflects user needs.

**Action Items**
- Brainstorm full feature set including stretch goals.
- Categorize features into MVP vs post-MVP.

---

## Week of Sept 8, 2025

### **Tue, Sept 9, 2025 — Feature Brainstorming**
**Topics**
- Discussed a wide range of feature ideas (meal planning, grocery automation, AI suggestions, dietary settings, barcode/OCR, macro tracking, etc.)
- Documented features into a formal design document for clarity.  
- Finalized and submitted Assignment 3 (team + individual portions).

**Decisions**
- MVP features: meal planning, cart management (procurement), pantry management, household collaboration, exploration/search, and AI/ML recommendations.
- Users may join only one household in MVP to simplify permissions logic and reduce edge cases.

**Action Items**
- Sam: Draft user stories based on feature list.
- Randy: Draft design diagrams showing system interactions and subsystem boundaries.

### **Thu, Sept 11, 2025 — Assignment Work**
**Topics**
- Reviewed user stories and design diagrams
- Finalized and submitted Assignment 4 (user stories and design diagrams)
- Work through Assignments 5 and 6 (task list, milestones, and effort matrix)
- Draft Assignment 7
- Resumed work on the data model design
- Talked through what technologies we would like to make use of

**Decisions**
- Use React Native so we can develop both for web and mobile
- Prioritize completing assignments to allow us more time to design and develop later in the semester

**Action Items**
- Sam: Complete and submit Assignment 7 (5 and 6 were completed during the meeting)
- Randy: Investigate platforms and tools to help develop with React Native.

---

## Week of Sept 15, 2025

### **Tue, Sept 16, 2025 — Data Model Design**
**Topics**
- Returned to deeper data model work now that assignments are out of the way.
- Sketched canonical data types and relations (Quantity, Money, NutritionFacts, Recipe, Meal, PantryItem).
- Discussed how to handle user-generated vs system-defined foods/ingredients.

**Decisions**
- Data model must allow for flexible nutrition mapping and multiple input forms (e.g., weight, volume, units).

**Action Items**
- N/A

### **Thu, Sept 18, 2025 — Data Model Design**
**Topics**
- Continued refining complex entities (MealPlan, IntakeLog, StoreItem).
- Discussed handling substitutions and price history for the Cart Engine.
- Evaluated how Household preferences will override User preferences in shared contexts.

**Decisions**
- Use JSONB for flexible mappings (ingredients_map, foods_map) in MVP.
- Begin building constraints and validation rules for ingredients.

**Action Items**
- N/A

---

## Week of Sept 22, 2025

### **Tue, Sept 23, 2025 — Data Model Design**
**Topics**
- Reviewed canonical models and refined types based on emerging edge cases.
- Differentiated Meal vs Recipe vs Food more clearly.
- Discussed lifecycle for MealPlan entries and how scheduling should work.

**Decisions**
- Keep JSONB maps for MVP to simplify early backend dev.
- Prioritize correctly capturing nutrition facts and serving sizes to prepare for nutrition insight rollups later.

**Action Items**
- Randy: Finalize models for migration planning.
- Sam: Begin drafting REST API surface matching latest schema.

### **Thu, Sept 25, 2025 — Data Model Design**
**Topics**
- Reviewed privacy & regulatory constraints (GDPR/CCPA, storing grocery credentials, sensitive food data).
- Discussed safe credential handling for grocery stores/third-party integrations.

**Decisions**
- No persistent credential storage for store integrations in MVP.
- Add permissions/role fields to household membership design.

**Action Items**
- N/A

---

## Week of Sept 29, 2025

### **Thu, Oct 2, 2025 — Data Model Design**
**Topics**
- Finalized data models after several rounds of iteration.
- Distinguished entities requiring tables (User, Household, StoreItem, PantryItem, Meal, Recipe) from application-only types (Quantity, Money, NutritionFacts).

**Decisions**
- Core relational tables identified; supporting types will live as structured JSON within entities when appropriate.

**Action Items**
- N/A

---

## Week of Oct 6, 2025

### **Tue, Oct 7, 2025 — Expo Experimentation**
**Topics**
- Installed and tested Expo.
- Successfully deployed a Hello World app to both web and mobile preview.
- Discussed project folder structure for shared components.

**Decisions**
- Expo chosen as primary cross-platform framework.

**Action Items**
- N/A

### **Thu, Oct 9, 2025 — Expo Experimentation**
**Topics**
- Continued working with Expo; 
- Discussed how OCR → receipt_line processing will work.

**Decisions**
- Maintain structured status lifecycle for receipts (`uploaded → parsed → applied → error`), including when their data is discarded after a certain time

**Action Items**
- N/A

---

## Week of Oct 13, 2025

### **Tue, Oct 14, 2025 — Landing Page Prototyping**
**Topics**
- Designed early landing page mockups and early screens for Pantry/Cart/Search flows.
- Looked at design conventions from other nutrition apps for inspiration.

**Decisions**
- Pantry should surface key warnings (expiration, low-stock) using lightweight visual cues.

**Action Items**
- Randy: Continue polishing initial UI implementation.
- Sam: Work on and complete slideshow for Assignment 8 before next meeting.

### **Thu, Oct 16, 2025 — Record for Assignment 8**
**Topics**
- Reviewed slide deck for Assignment 8.
- Discussed speaking order, transitions, and narrative flow.
- Recorded multiple takes for video presentation.

**Decisions**
- N/A

**Action Items**
- Randy: Edit video to meet time limits.
- Both: Submit Assignment 8.

---

## Week of Oct 20, 2025

### **Tue, Oct 21, 2025 — Component Library Search**
**Topics**
- Discussed ongoing dev pain points (inconsistent styling, reinventing UI components, layout issues across platforms).
- Reviewed multiple React Native component libraries.
- Chose gluestack for simplicity, consistency, theming, and active support.

**Decisions**
- Move forward with a unified component library to speed UI work and ensure consistent UX.

**Action Items**
- N/A

### **Thu, Oct 23, 2025 — Refactor Current Pages**
**Topics**
- Began migrating existing screens to gluestack-based components.
- Updated navigation to use standardized button, dropdown, and card components.

**Decisions**
- N/A

**Action Items**
- Both: Complete Assignment 9 (peer reviews).

---

## Week of Oct 27, 2025

### **Tue, Oct 28, 2025 — Sign-in and Auth Flow**
**Topics**
- Designed complete sign-in / sign-up flow for both mobile and web.
- Discussed login patterns.

**Decisions**
- Web will show landing page; mobile will route new users to sign-in or registration.
- Shared auth logic via a common API service.

**Action Items**
- N/A

---

## Week of Nov 3, 2025

### **Tue, Nov 4, 2025 — Dependency Debugging**
**Topics**
- Noticed inconsistent styling between mobile and web builds due to mismatched dependency versions.
- Compared environment configs.
- Identified issues with default CSS resets on web version of Expo.

**Decisions**
- Follow "development pain points" doc in team drive as a reference.
- Enforce pinned dependency versions for UI packages.

**Action Items**
- N/A

---

## Week of Nov 10, 2025

We were unable to conduct meetings this week due to our other academic coursework, so we resolved to spend time catching up on assignments and resuming meetings next week.

---

## Week of Nov 17, 2025

### **Tue, Nov 18, 2025 — Assignment Revision**
**Topics**
- Revise completed Assignments for inclusion in the final design report (Assignment 10)

**Decisions**
- Not all assignments needed to be changed, but we did have some things to add outside of any existing assignment (design document for data models and feature list, mocks, budget)

**Action Items**
- Sam: Work on correcting formatting the repository and ensure everything necessary is included

### **Thu, Nov 20, 2025 — Assignment Work**
**Topics**
- Finalize Assignment 10

**Decisions**
- N/A

**Action Items**
- Sam: Submit Assignment 10 and notify project advisor 
