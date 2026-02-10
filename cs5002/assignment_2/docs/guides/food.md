# Foods

Foods are **user-defined nutrition entries** (e.g., “2% Milk”, “Whey Protein Scoop”). Foods can be:
- Private (only you)
- Household-shared (members of your household)
- Public (available to everyone) — this can not be changed once enabled

## When to create a Food
Create a Food when:
- You regularly eat a packaged item with known macros that you don't see in our current database
- You want a consistent entry for intake logging
- You want to reuse it inside Meals and Recipes

## Create a Food
1. Go to **Foods**
2. Click **Create Food**
3. Enter:
   - Name
   - Serving size (amount + unit)
   - Nutrition facts (calories, protein, carbs, fat, fiber, sugar, micros if available)
   - Category/subcategory (optional)
   - Allergens (optional)
   - Visibility (private/household/public)

> Screenshot placeholder: `docs/assets/foods/create-food.png`

## Edit a Food
- Open the food details page
- Click **Edit**
- Save changes

## Delete a Food
- Open the food details page
- Click **Delete**
- Confirm

> Warning: Deleting a food may affect meals/recipes/log entries that reference it. Behavior is **TBD**:
- Option A: block deletion if referenced
- Option B: allow deletion and preserve historical log snapshots

## Tips
- Use consistent naming (brand + size) to avoid duplicates
- Use grams (g) for highest accuracy when possible
- Decide whether to trust “label calories” vs “macro-derived calories” (see [Preferences](preferences-and-goals.md))

## Related
- [Meals](meals.md)
- [Recipes](recipes.md)
- [Intake Log](intake-log.md)
- [Glossary](../reference/glossary.md)
