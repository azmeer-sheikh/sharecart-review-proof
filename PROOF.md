# ShareCart — App Store review proof of resolution

## 1. Create & share functionality (Uncategorized error)
**Issue:** Admin “Create & share” failed with an error toast (GraphQL inventory / lookup).
**Fix deployed:** Removed `inventoryQuantity` from product GraphQL (needs `read_inventory`); resilient cart create/lookup; storefront share no longer hangs on primary-domain sync.
**App:** https://sharecart-production.up.railway.app  
**How to verify:** In ShareCart admin → Create → add products → **Create & share**. Expect success toast and share link modal (no “Something went wrong”).

## 2. Pricing information (4.2.1)
**Issue:** Listing pricing / trial did not match in-app plans.
**Fix:** Shopify App Pricing + listing updated to:
- Free
- Starter **$9.99**/mo — **7-day** trial
- Growth **$29**/mo — **7-day** trial  
- Pro **$79**/mo — **7-day** trial

**Live listing:** https://apps.shopify.com/sharecart-1  
**Partner App Pricing index:** shows starter $9.99 + 7-day trial on all paid plans (screenshot attached).

## 3. Billing on reinstall (1.2.2)
**Issue:** Same paid plan reactivated on reinstall without charge approval.
**Fix:** On uninstall, shop resets to Free; unpaid paid plans are cleared; selecting a paid plan again creates a new charge for merchant approval (Shopify App Pricing / Billing).
**How to verify:** Uninstall ShareCart → reinstall → open Billing → select Starter/Growth/Pro → approve charge screen (plan not silently restored).
