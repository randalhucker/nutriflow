# Troubleshooting

## Authentication Issues

### I can't log in
- Double-check your email and password for typos.
- If you signed up with Google, use the **Continue with Google** button instead of the email/password form.
- Clear your browser cache and try again.
- If all else fails, create a new account with **Sign Up**.

### The app redirects me to the sign-in page repeatedly
- Your authentication session may have expired. Sign in again.
- Check that cookies / localStorage are not being blocked by your browser.

---

## Recipe Issues

### Search returns no results
- Try fewer or broader keywords.
- Check which source filter is active — **My Recipes** only shows recipes you created, while **Discover** searches the Spoonacular catalog.
- If the "From My Pantry" filter is on, it will only show recipes matching your pantry inventory. Toggle it off for broader results.

### A recipe has incorrect nutritional information
- Nutritional data for Spoonacular recipes comes from their database and may be approximate.
- For user-created recipes, verify that ingredient quantities and serving counts are set correctly.

---

## Shopping & Cart Issues

### Cart doesn't match my meal plan
- Make sure you have meals scheduled in the current week on the **Meal Plan** page.
- Tap **Regenerate** on the Shopping page to rebuild the cart from the latest plan.
- Pantry subtraction may remove items you expected to buy — check your pantry inventory to confirm.

### Prices are not showing or seem outdated
- Tap **Update Prices** on the Shopping page to refresh product pricing from Kroger.
- Confirm your Kroger account is still connected (check **Profile > Kroger**).

### I can't find a specific product
- The product search uses the Kroger catalog. Try different keywords, brand names, or generic terms.
- Some products may not be available at your selected store location.

---

## Pantry Issues

### Expiration dates seem wrong
- Expiration dates are entered manually. Open the item and verify the date you entered.
- The badge shows time relative to today (e.g., "Expired 6d ago" means the expiration date was 6 days before today).

### Items are not subtracting from cart generation
- Make sure the pantry item name closely matches the recipe ingredient.
- Verify the pantry item has sufficient quantity remaining.

---

## Household Issues

### I see an "Upgrade to Premium" prompt on the Household page
- Household features require a Premium account. Free-tier users cannot create or join households.

### A household member can't edit the pantry or cart
- The household admin needs to enable permissions for that member.
- Go to **Profile > Household > Members** and check the **Cart: Edit** and **Pantry: Edit** permission tags.

---

## Display & Performance Issues

### The page looks broken or elements overlap
- Try refreshing the page (Ctrl+R / Cmd+R).
- NutriFlow is optimized for screens 500px wide or larger. On very narrow screens, some layouts may not display correctly.
- Clear your browser cache if styles look outdated.

### Animations are janky or slow
- NutriFlow uses scroll-reveal animations. On lower-powered devices, these may appear less smooth.
- Ensure your browser is up to date (Chrome, Firefox, Safari, or Edge).

---

## Report a Bug or Request a Feature

If you encounter a problem not covered here:

1. File an issue on the [NutriFlow GitHub repository](https://github.com/randalhucker/nutriflow_expo/issues).
2. Include:
   - Steps to reproduce the issue
   - What you expected to happen vs. what actually happened
   - Screenshots or browser console logs if available
   - Your browser and operating system
