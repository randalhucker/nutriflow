# Pantry

The Pantry tracks what your household has on hand so NutriFlow can:
- Reduce waste
- Warn about expiring items
- Recommend recipes based on inventory
- Avoid adding already-owned items to a cart

Pantry items can be sourced from:
- Store items (preferred when available)
- Ingredients
- Foods (user-defined)

## Add items to Pantry
1. Go to **Pantry**
2. Click **Add Item**
3. Choose item type:
   - Store item / Ingredient / Food
4. Enter:
   - Servings left
   - Storage (dry/refrigerated/frozen)
   - Opened (yes/no)
   - Optional expiration date
5. Save

> Screenshot placeholder: `docs/assets/pantry/add-item.png`

## Update Pantry after shopping
Supported workflow (TBD):
- Manually increment servings left after purchase
- Optionally import a receipt image for OCR-assisted updates (basic OCR)

Receipt import status states:
- uploaded → parsed → applied
- error

> Screenshot placeholder: `docs/assets/pantry/receipt-import.png`

## Expiry warnings
NutriFlow can warn when items are:
- stale / freezer burned / rotten (heuristic rules TBD)
- past expiration date

## Related
- [Cart](cart.md)
- [Households](households.md)
- [FAQ](../help/faq.md)
