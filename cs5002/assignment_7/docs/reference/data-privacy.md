# Data & Privacy

This page describes what data NutriFlow stores and how it is handled.

## Data Stored

NutriFlow stores the following information:

- **Account information** — first name, last name, email, hashed password
- **Nutrition goals** — daily calorie, protein, carb, and fat targets
- **Dietary preferences** — diet type, allergens, food category preferences
- **Recipes** — user-created recipes with ingredients, instructions, and metadata
- **Meal plans** — scheduled meals on a weekly calendar
- **Intake logs** — daily food intake records with calorie and macro data
- **Pantry items** — ingredient inventory with quantities, storage types, and expiration dates
- **Cart items** — grocery list items linked to Kroger products
- **Household data** — membership, roles, permissions, shared plans, appliances, and receipts
- **Kroger OAuth tokens** — used to fetch product data and prices (stored securely)

## Data Sharing

- **Private by default** — your data is only visible to you.
- **Household sharing** — if you belong to a household (Premium), meal plans, pantry, and cart data are shared with household members based on role permissions.
- **Third-party data** — recipe data from Spoonacular and product data from Kroger are fetched on demand and not stored permanently.

## Security

- Passwords are stored as salted hashes (never in plaintext).
- Authentication tokens are stored securely (Expo SecureStore on mobile, localStorage on web).
- All API communication uses HTTPS in production.
- Household role-based access control ensures members can only perform actions they are authorized for.

## Account Deletion

You can sign out at any time from the Profile page. For full account deletion, contact the development team.
