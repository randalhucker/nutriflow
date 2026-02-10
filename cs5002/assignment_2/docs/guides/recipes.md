# Recipes

A Recipe is a structured set of instructions for preparing a meal and typically includes:
- Ingredients and/or foods with quantities
- Step-by-step instructions
- Servings (used to scale nutrition)
- Optional: cuisine, difficulty, appliances

## Create a Recipe
1. Go to **Recipes**
2. Click **Create Recipe**
3. Fill in:
   - Name
   - Servings
   - Ingredient/Food list with quantities
   - Instructions (ordered steps)
   - Optional metadata (cuisine, difficulty, tags, appliances)
4. Save

> Screenshot placeholder: `docs/assets/recipes/create-recipe.png`

## Using recipes in Meals
A meal can reference one or more recipes (TBD) in two common patterns:
- **Meal as “the prepared recipe”** (1 recipe = 1 meal)
- **Meal as combination** (multiple recipes + add-ons)

Documented behavior is **TBD**:
- Whether meal nutrition is derived from recipe servings automatically
- Whether recipe scaling is supported in-meal

## Recipe scaling
If enabled, scaling adjusts:
- Ingredient amounts
- Nutrition totals

Potential constraints:
- rounding
- unit conversions
- density calculations

## Related
- [Meals](meals.md)
- [Meal Plans](meal-plans.md)
- [Search](search.md)
