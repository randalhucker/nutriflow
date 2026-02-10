# Data & Privacy

This page describes what data NutriFlow stores and how it is used.

> Implementation details are subject to change.

## Data stored
May include:
- Account info (name, email)
- Foods, meals, recipes, meal plans
- Intake logs
- Pantry and cart data
- Household membership and permissions
- Preferences (diet, allergens, goals)
- Receipt images (if receipt import enabled)

## Sharing
- Private items are only visible to the owner
- Household items are visible to household members
- Public items are visible to all users (TBD)

## Deletion
Behavior is TBD:
- Whether deleting an item removes it entirely
- Whether historical logs keep snapshots for integrity

## Security notes (TBD)
- Passwords stored as salted hash
- Transport encryption (HTTPS) in production
- Access control enforcement for household roles
