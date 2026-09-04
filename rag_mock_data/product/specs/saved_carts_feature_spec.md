# Feature Spec: Saved Carts

**Status:** Approved for development
**Owner:** Product — Growth Team
**Target Release:** Q1 2026

## Problem Statement

User research shows that 34% of users who add items to their cart do not complete checkout in the same session, and of those, only 12% return to complete the purchase later because their cart was cleared after 24 hours of inactivity. This represents significant recoverable revenue.

## Goals

- Allow users to save their current cart for later, either automatically or manually
- Allow users to maintain multiple named saved carts (e.g., "Birthday gift", "Office supplies")
- Send a reminder notification 48 hours after a cart is abandoned, if the user has opted into marketing notifications
- Increase cart recovery rate from 12% to a target of 25% within two quarters of launch

## Non Goals

- This feature does not include price drop alerts for saved cart items (tracked separately in the Price Watch spec)
- This feature does not support sharing a saved cart with another user (tracked in the future Collaborative Carts spec)

## User Flows

### Automatic Save
When a signed in user leaves the site with items in their cart, the cart is automatically saved under "My Cart" and persists indefinitely, or until checked out or manually cleared.

### Manual Save As
From the cart page, a signed in user can select "Save cart as..." and provide a custom name. This creates a new named saved cart, separate from their active cart, and clears the active cart.

### Restoring a Saved Cart
From the "Saved Carts" section of the account page, a user can view all saved carts, see item availability status (in stock, low stock, out of stock, price changed), and restore any saved cart to become their active cart with one click.

## Edge Cases

- If an item in a saved cart is later marked out of stock, it is displayed with a clear "Out of Stock" badge and excluded from bulk restore, but the user can still view it.
- If an item's price has changed since saving, the new price is shown along with the original saved price, so the user is not surprised at checkout.
- Guest users (not signed in) do not get persistent saved carts; their cart is only session based, consistent with current behavior.

## Success Metrics

- Cart recovery rate (primary metric)
- Saved cart creation rate (secondary)
- Notification click through rate for the 48 hour reminder
- No regression in checkout conversion rate for users who do not use this feature

## Open Questions

- Should there be a limit on the number of named saved carts per user? Current proposal is a cap of 10, pending engineering feasibility review.
