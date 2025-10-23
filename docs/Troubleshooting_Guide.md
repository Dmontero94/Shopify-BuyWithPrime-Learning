# 🧩 Troubleshooting Guide – Buy with Prime Integration

> **Purpose:** Document recurring issues during Buy with Prime installation and provide tested solutions or workarounds.

---

## 🔍 Common Issues

| Issue | Platform | Cause | Solution / Workaround | Notes |
|--------|-----------|--------|------------------------|-------|
| BwP button not visible on product page | Shopify | Snippet not inserted or conflicting theme | Reinsert BwP snippet manually using Theme Editor (`theme.liquid`). | Test with Dawn theme as reference. |
| Checkout not completing | Shopify | Misconfigured API credentials | Reconnect Buy with Prime app → Settings → API setup. | Check error logs for “403 Forbidden.” |
| Inventory mismatch | Shopify | Sync delay with Seller Central | Trigger manual sync from Buy with Prime dashboard. | Usually resolves in 5–10 min. |
| Styling issues on product pages | Shopify | CSS conflict with existing theme | Add inline CSS override for BwP button. | Document which theme caused it. |

---

## 🧠 Additional Notes

- Always confirm **Shopify plan supports third-party checkouts** before installation.  
- Encourage merchants to **backup their theme** before editing Liquid files.  
- Most visual or rendering issues are solved by **clearing cache** or **checking the theme preview** instead of live view.

---

## 🧾 Log Format (for new cases)

```text
Date:
Merchant:
Platform:
Issue Summary:
Root Cause:
Resolution:
Follow-up Needed: Yes / No
