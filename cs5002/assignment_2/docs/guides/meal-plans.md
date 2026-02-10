# Meal Plans

Meal Plans schedule meals over time (e.g., “Week of Feb 10”). A plan contains entries:
- A Meal
- A timestamp/date
- Optional: “locked” flag to prevent changes

Meal plans can be:
- Yours
- Household-shared (if enabled)
- Subscribed from household members

## Create a Meal Plan
1. Go to **Meal Plans**
2. Click **Create Meal Plan**
3. Name the plan
4. Add entries:
   - Select a meal
   - Choose date/time (or day slot)
   - Optionally lock
5. Save

> Screenshot placeholder: `docs/assets/mealplans/create-mealplan.png`

## Subscribe to a plan (Household)
If enabled:
- View household plans
- Subscribe to one or more plans
- NutriFlow uses active plans to build pantry/cart recommendations

> Behavior detail TBD:
- How conflicts are handled (multiple meal plans active)
- Whether subscriptions copy entries or reference them live

## From meal plan to cart
NutriFlow can generate a cart based on:
- Meals in the plan date range
- Pantry items on-hand
- Store item mappings (TBD)

See: [Cart](cart.md) and [Pantry](pantry.md)

## Related
- [Meals](meals.md)
- [Cart](cart.md)
- [Households](households.md)
