# Key Concepts

This page explains NutriFlow's core data model and how the pieces fit together.

## Core Objects

| Object | Description |
|---|---|
| **Recipe** | A structured set of instructions with ingredients, quantities, cook time, servings, and nutritional information. Recipes come from two sources: user-created (local) or discovered via Spoonacular. |
| **Meal Plan** | A weekly calendar of scheduled meals. Each day has four slots: Breakfast, Lunch, Dinner, Snack. Plans can be saved as templates and shared with households. |
| **Pantry Item** | An ingredient you have at home, tracked with quantity, storage type (Fridge / Frozen / Dry), and optional expiration date. |
| **Cart** | A grocery list of real Kroger products with prices, quantities, and substitution preferences. Carts can be auto-generated from meal plans. |
| **Household** | A shared group (Premium) where members collaborate on meal plans, pantry, cart, and spending. |
| **Intake Log Entry** | A record of food consumed on a specific day, used to track calories and macros against daily goals. |
| **Nutrition Goals** | Your daily calorie, protein, carb, and fat targets — set in the Profile screen. |
| **Dietary Preferences** | Your diet type, allergens, and food category interests — used to filter and recommend recipes. |

## The NutriFlow Workflow

The core loop in NutriFlow follows this progression:

```
Set Goals → Browse Recipes → Plan Meals → Generate Cart → Shop → Stock Pantry → Cook → Log Intake → Review Insights
```

1. **Set Goals** — Define your daily calorie and macro targets in Profile. Set dietary preferences.
2. **Browse Recipes** — Search and filter recipes, optionally filtered by what you already have in your pantry.
3. **Plan Meals** — Drag recipes and meals onto your weekly calendar.
4. **Generate Cart** — Auto-build a Kroger shopping cart from your meal plan, minus pantry items.
5. **Shop** — Use the cart at the store.
6. **Stock Pantry** — Add purchased items to your pantry (manually or from the cart).
7. **Cook & Eat** — Follow recipe instructions.
8. **Log Intake** — Record what you ate on the Home Dashboard.
9. **Review Insights** — Check weekly trends, streaks, and spending on the Insights page.

## Account Tiers

| Tier | Features |
|---|---|
| **Free** | Full access to meal planning, recipes, pantry, cart, intake logging, and insights |
| **Premium** | Everything in Free, plus: Household collaboration, shared meal plans, receipt uploads, and advanced features |

## Units

NutriFlow uses servings as the primary unit for pantry and intake tracking. Recipes specify ingredient quantities in standard cooking units (grams, cups, tablespoons, etc.).
