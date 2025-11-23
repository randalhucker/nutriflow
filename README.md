# NutriFlow Final Design Report

> NOTE: all individual CS-5001 assignment documents can be found under cs5001/assignment_`#`/ where `#` is the assignment number

## Table of Contents

### 1. [Team Names](#team-members) & [Project Abstract](#project-abstract) (in README below)

### 2. [Project Description (Assignment #2)](cs5001/assignment_2/Project-Description.md)

### 3. [User Stories](cs5001/assignment_4/User_Stories.md) & [Design Diagrams](cs5001/assignment_4/Design_Diagram.md)  (Assignment #4)

### 4. [Project Tasks](cs5001/assignment_5/Tasklist.md) & [Timeline + Effort Matrix](cs5001/assignment_6/Milestones_Timeline_Effort.md) (Assignment #5-6)

### 5. [ABET Concerns Essay](cs5001/assignment_7/Project_Constraints_Essay.md) (Assignment #7)

### 6. [PPT Slideshow](cs5001/assignment_8/Fall_Design_Presentation.pdf) & [Video Presentation](https://drive.google.com/drive/folders/1aOjDmqiDJpHrK66QeJYEoNwFCOIy_Z2V?usp=sharing) (Assignment #8)

### 7. Self-Assessment Essays (Assignment #3)
- [Self-Assessment Essay — Sam](cs5001/assignment_3/Assignment%203%20-%20Individual%20Capstone%20Assessment%20-%20gralersm.pdf)
- [Self-Assessment Essay — Randy](cs5001/assignment_3/Assignment%203%20-%20Individual%20Capstone%20Assessment%20-%20huckerre.pdf)

### 8. Professional Biographies (Assignment #1)
- [Professional Biography — Sam](cs5001/assignment_1/gralersm_assignment_1_professional_biography.md)
- [Professional Biography — Randy](cs5001/assignment_1/huckerre_assignment_1_professional_biography.md)

### 9. [Budget](cs5001/assignment_10/Budget.md)

### 10. Appendix
- [Link to NutriFlow Code Repository](https://github.com/randalhucker/nutriflow_expo)
- [NutriFlow Design Document](cs5001/assignment_10/appendix%20documents/NutriFlow_Design.pdf)
- [Semester Meeting Notes](cs5001/assignment_10/appendix%20documents/NutriFlow_Meeting_Notes.md)
- [Preliminary UI Mocks](cs5001/assignment_10/appendix%20documents/ASN_10_Mocks.pdf)

## Final Design Document Assignment Revision Notes

For the Final Design Document, several assignments (1, 3, 5, 6, 7) were left largely unmodified for one of two reasons: 
1. The assignment's content did not depend on the progress of the project (assignments #1 and #3) and 
2. Our progress on the project did not necessitate updating the assignment's content (assignments #5, #6, and #7). 

The first case is self-explanatory, as it is clear that professional biographies (1) and preliminary personal assessments (3) would not be affected by the projects progression. To elaborate further on the second case, our work has not revealed significant issues in the work distribution/timeline (5/6), nor has it exposed any previously unconsidered constraints (7). We expect that this will not always be the case, but in the context of the final design document that is the reason those assignments were not revised.

Please reach out if more explanation is needed!

## NutriFlow CS5001 Project Description (README)

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

A[Login / Sign-up] --> B{Onboarding?}
B -->|Yes| C[Set Preferences - diet, allergens, goals]
B -->|Skip| D[Dashboard]

C --> H1[Join or Create Household]
C --> D
H1 --> D

D --> E[Explore Features]

%% Core feature entry points from Dashboard
E --> F[Search & Explore Foods/Recipes]
E --> G[Upload Pantry / Receipt]
E --> H[Scan Ingredient Barcode/Image]
E --> P[Pantry Manager]
E --> M[Meal Planner]
E --> S[Grocery Cart]
E --> X[Intake Log]
E --> I[Nutrition Snapshot & Progress]

%% Pantry ingestion & recognition
G --> RCP[Receipt OCR & Parsing]
RCP --> P

H --> ING[Ingredient Recognition]
ING --> P

%% Pantry-driven flows
P --> F
P --> M
P --> S
P --> N[Notifications - expiry, low stock, reminders]

%% Search & recipes
F --> R[Recipe Detail View]
R --> R1[See Nutrition Info & Substitutions]
R --> R2[Add to Meal / Plan]
R --> R3[Add Ingredients to Cart]

%% Meal planning & grocery list
R2 --> M
M --> M1[Auto-Generated Grocery List (Plan − Pantry)]
M1 --> S
M --> X
M --> I

%% Cart engine & price comparison
R3 --> S
S --> S1[Compare Prices Across Stores]
S --> S3[Cart vs Plan Consistency Check]
S3 --> M

S1 --> EXT[Store Integrations (APIs / E-commerce)]
EXT --> S2[Checkout / Link to Retailer]

S --> P
S2 --> I

%% Intake logging & analytics
X --> I
P --> I
M --> I

%% Insights, sustainability, and feedback loops
I --> Z1[Achievements & Badges]
I --> Z2[Sustainability Stats - waste saved, $ saved]
I --> Z3[Community Recipes & Social Sharing]
I --> D

%% Household collaboration
D --> H2[Household Collaboration]
H2 --> P
H2 --> M
H2 --> S

%% AI / recommendation engine touching multiple features
AI[AI / Recommendation Engine]
F --> AI
M --> AI
P --> AI
S --> AI
AI --> R
AI --> M
AI --> S

%% Notifications return user to app
N --> D
```

---

### Team Approach

- **Agile Iterations** to incrementally deliver scraping, recognition, and recommendation features.
- **Faculty Guidance** from Dr. Hawkins for technical depth and academic rigor.
- **Future Expansion**: Household collaboration, sustainability tracking, gamification, and premium features.

---