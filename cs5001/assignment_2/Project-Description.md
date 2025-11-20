# NutriFlow Project Description

### Team Members

- **Randy Hucker**
  - Major: Computer Science
  - Email: [randalhucker@gmail.com](mailto:randalhucker@gmail.com)
  - [LinkedIn](https://www.linkedin.com/in/randy-hucker)

- **Sam Graler**
  - Major: Computer Science
  - Email: [gralersm@mail.uc.edu](mailto:gralersm@mail.uc.edu)
  - [LinkedIn](https://www.linkedin.com/in/sam-graler)

### Project Faculty/Industry Advisor

- **Dr. William Hawkins**  
  - Assistant Professor of Computer Science, University of Cincinnati  
  - Email: [hawkinwh@ucmail.uc.edu](mailto:hawkinwh@ucmail.uc.edu)
  - [LinkedIn](https://www.linkedin.com/in/whh3/)

---

### Project Topic Area

**Intelligent Food Ecosystem** - An AI/ML-driven platform that delivers nutrition insights, personalized food recommendations, smart grocery planning, and sustainability tracking.

---

### Project Abstract

**Problem Statement**: Modern consumers struggle to balance nutrition, affordability, and sustainability in their food choices. Information is scattered across recipes, grocery stores, and nutrition trackers leading to inconsistency and frustration.

**Abstract**: NutriFlow addresses the difficulty of planning healthy, affordable meals by unifying recipes, nutrition data, pantry inventory, pricing, and household coordination. Smart cart generation, pantry management, and our AI-assisted recommendation engine support a unique meal planning experience that reaches across the entire process, from gathering recipes to try to bringing groceries in from your doorstep.

---

### Inadequacy of Current Solutions

- **Nutrition Trackers** (e.g., MyFitnessPal) focus on logging, not proactive food guidance.
- **Meal Kits** provide convenience but are costly and don't reduce food waste.
- **Grocery Delivery Apps** solve logistics but ignore nutrition, substitutions, and sustainability.

There is **no integrated solution** connecting personal preferences, pantry inventory, pricing data, and AI recommendations.

---

### Technical Background

NutriFlow combines **data engineering, AI/ML, and user-centric design**:

- **Interactive UX** - Dashboards, recipe views, and meal planners.
- **Data Pipelines** - Web scraping + APIs for grocery pricing, availability, and nutrition data.
- **AI/ML Models** - Ingredient recognition, recipe generation, substitution suggestions.
- **Cloud Infrastructure** - GitHub repo, containerization, scalable backend services _(AWS **Lambda** & **Aurora**)_.

```mermaid
flowchart TD

A["Login / Sign-up"] --> B{"Onboarding?"}
B -->|Yes| C["Set Preferences - diet, allergens, goals"]
B -->|Skip| D["Dashboard"]

C --> H1["Join or Create Household"]
C --> D
H1 --> D

D --> E["Explore Features"]

E --> F["Search and Explore Foods / Recipes"]
E --> G["Upload Pantry or Receipt"]
E --> H["Scan Ingredient Barcode or Image"]
E --> P["Pantry Manager"]
E --> M["Meal Planner"]
E --> S["Grocery Cart"]
E --> X["Intake Log"]
E --> I["Nutrition Snapshot and Progress"]

G --> RCP["Receipt OCR and Parsing"]
RCP --> P

H --> ING["Ingredient Recognition"]
ING --> P

P --> F
P --> M
P --> S
P --> N["Notifications - expiry, low stock, reminders"]

F --> R["Recipe Detail View"]
R --> R1["See Nutrition Info and Substitutions"]
R --> R2["Add to Meal or Plan"]
R --> R3["Add Ingredients to Cart"]

R2 --> M
M --> M1["Auto-Generated Grocery List - Plan vs Pantry"]
M1 --> S
M --> X
M --> I

R3 --> S
S --> S1["Compare Prices Across Stores"]
S --> S3["Cart vs Plan Consistency Check"]
S3 --> M

S1 --> EXT["Store Integrations - Retail APIs"]
EXT --> S2["Checkout or Link to Retailer"]

S --> P
S2 --> I

X --> I
P --> I
M --> I

I --> Z1["Achievements and Badges"]
I --> Z2["Sustainability Stats - waste saved and money saved"]
I --> Z3["Community Recipes and Social Sharing"]
I --> D

D --> H2["Household Collaboration"]
H2 --> P
H2 --> M
H2 --> S

AI["AI and Recommendation Engine"]
F --> AI
M --> AI
P --> AI
S --> AI
AI --> R
AI --> M
AI --> S

N --> D
```

---

### Team Approach

- **Agile Iterations** to incrementally deliver scraping, recognition, and recommendation features.
- **Faculty Guidance** from Dr. Hawkins for technical depth and academic rigor.
- **Future Expansion**: Household collaboration, sustainability tracking, gamification, and premium features.