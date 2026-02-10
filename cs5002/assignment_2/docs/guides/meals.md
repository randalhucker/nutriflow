# Meals

A Meal represents something you eat as a unit (e.g., “Breakfast Bowl”, “Chicken + Rice”). A meal can include:
- Foods (user-defined)
- Ingredients (global/scraped) — *if enabled*
- Recipes (optional linkage)

Meals are reusable in:
- Meal Plans
- Intake Logs
- Household-shared planning (if shared)

## Create a Meal
1. Go to **Meals**
2. Click **Create Meal**
3. Add one or more components:
   - Foods + quantities
   - Ingredients + quantities (optional / TBD)
   - Recipes (optional / TBD)
4. Save

> Screenshot placeholder: `docs/assets/meals/create-meal.png`

## Edit / Delete a Meal
- Same pattern as foods.

## Meal nutrition totals
NutriFlow computes totals by summing:
- Nutrition facts for foods/ingredients used
- Multiplying by entered quantities

Known edge cases (TBD):
- Unit conversions (g ↔ ml ↔ oz ↔ “unit”)
- Density conversions for volume-based items

## Visibility & sharing
Meals can be private, household, or public (TBD). See:
- [Visibility & Sharing](visibility-and-sharing.md)

## Related
- [Foods](food.md)
- [Recipes](recipes.md)
- [Meal Plans](meal-plans.md)
