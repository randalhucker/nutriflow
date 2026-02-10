# Key Concepts

This page explains NutriFlow’s core mental model.

## Objects
- **Ingredient**: global/scraped item with nutrition facts (not user-defined)
- **Food**: user-defined nutrition entry (may be private/household/public)
- **Recipe**: instructions + ingredient/food list + servings
- **Meal**: reusable “thing you eat” made from foods/ingredients/recipes
- **Meal Plan**: scheduled meals over time
- **Pantry Item**: inventory on-hand (servings left + storage + expiration)
- **Cart**: procurement list (possibly multi-store)
- **Household**: shared collaboration space

## Common workflows
- Plan → Generate Cart → Shop → Update Pantry → Cook → Log Intake

## Units & conversions (TBD)
Supported units:
- g, ml, lb, oz, unit

Known conversion challenges:
- volume ↔ weight conversions require density
