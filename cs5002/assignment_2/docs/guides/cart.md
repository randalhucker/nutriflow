# Cart

Carts support grocery planning and procurement. A cart can:
- Contain items from multiple stores
- Be generated from meal plans
- Be manually edited (add/modify/remove)

Cart status values:
- open
- submitted
- fulfilled
- canceled

## Create a Cart from a Meal Plan
1. Go to **Cart**
2. Click **Generate from Meal Plan**
3. Select a date range (or select an active meal plan)
4. NutriFlow will:
   - Compute required ingredients/foods
   - Subtract pantry items (if enabled)
   - Map remaining needs to store items from locations in your area
5. Review and save

> Screenshot placeholder: `docs/assets/cart/generate.png`

## Manual cart editing
- Search for store items
- Add to cart
- Adjust quantity
- Mark substitutable
- Add notes

## Cart mismatch warnings
NutriFlow may warn when:
- Your cart does not cover planned meals (missing items)
- You removed required items for a meal plan range

## Price comparison
If enabled, you can compare:
- Store item price and serving count
- Recipe total cost (estimated) — TBD rules

## Related
- [Pantry](pantry.md)
- [Meal Plans](meal-plans.md)
- [Search](search.md)
