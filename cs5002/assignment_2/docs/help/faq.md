# FAQ

## What’s the difference between a Food and an Ingredient?
**Food** is user-defined (you create it).  
**Ingredient** is global/scraped (shared database).  
See: [Key Concepts](../reference/concepts.md)

## Why don’t my calories match my macros?
Common causes:
- Serving size mismatch (e.g., per 100g vs per serving)
- Unit conversion issues (ml ↔ g)
- Label rounding
- “Calories from macros” preference (if enabled)

## Can I share meal plans with my household?
Yes. Household members can view and subscribe to meal plans depending on permissions.

## Can multiple people edit the cart and pantry?
Yes, controlled by household permissions:
- can_modify_cart
- can_modify_pantry

## How does NutriFlow generate a cart from a meal plan?
NutriFlow estimates required ingredients/foods for the planned meals, subtracts pantry inventory (if enabled), and maps remaining needs to store items.

## Can I scan receipts?
Receipt import with basic OCR is an active goal. Accuracy and supported stores are TBD.

## Is there a “premium” tier?
The data model includes free/premium, but features are TBD.

## Where do recipe recommendations come from?
Planned:
- pantry-based recommendations
- cuisine exploration and personalization
