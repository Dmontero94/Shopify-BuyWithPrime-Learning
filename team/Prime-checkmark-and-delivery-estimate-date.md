# 🔧 **Prime Checkmark and Delivery Estimate Date**

### Author: Daniela Montero

### Team: MCF and Buy with Prime

### Last Updated: October 2025

---

## 🧙‍♂️ **Overview**

This guide explains how to permanently add a **Buy with Prime checkmark** and a **dynamic delivery estimate date** (simplify version) inside a Shopify theme using only the Theme Editor.

The customization works with *modern Shopify Online Store 2.0* themes like **Dawn**, **Refresh**, and **Craft**, and requires **no external CSS**

---

## 🧢 **1. Identify the Target Section**

1. Open your store’s **home page** in Google Chrome.
2. Right-click the **product price area** → select **Inspect**.
3. Inside the **Elements** panel, look for this section:

   ```html
   <div class="card_content">
   ```
4. Scroll a few lines above that element. You should see:

   ```html
   <div class="card-information">
   ```

   This confirms that the price block is part of the **product card** component.

---

## 🗭 **2. Locate the Correct File in Shopify**

1. From your Shopify Admin, go to:
   **Online Store → Themes → (Your Current Theme) → Edit Code**
2. Open:

   ```
   snippets/card-product.liquid
   ```
3. Inside this file, search for:

   ```liquid
   class="card-information">
   ```
4. Place your custom code **just above** that line (not below).
   This ensures the Prime checkmark box appears *above the price section*.

---

## 💻 **3. Final Code Snippet (Inline Version)**

```liquid
<!-- Custom addition by Dani: Prime Checkmark and Delivery Estimate Date -->
<div style="display:flex; align-items:center; gap:6px; border:1px solid #e3e6e8; border-radius:6px; background-color:#dcdde1; padding:4px 8px; margin-top:6px; max-width:fit-content;">
  <img 
    src="https://cdn.shopify.com/shopifycloud/shopify/assets/branded_promises/prime-logo-3d34fb87e1de97edd7722680e7e61ec2c9dd5eb2b58abe6a268c6e47735dec44.svg"
    alt="Buy with Prime"
    width="60"
    height="20"
    style="width:60px; height:auto;">
  
  {% assign today = 'now' | date: "%s" %}
  {% assign delivery_date = today | plus: 172800 | date: "%a, %b %d" %}
  <span style="font-size:13px; color:#111; font-weight:500;">
    Get it as soon as <strong>{{ delivery_date }}</strong>
  </span>
</div>
<!-- End Custom addition by Dani -->
```

✅ This will render as:

> 🟦 *prime*  Get it as soon as **Fri, Dec 20**

---

## 🤓 **4. What the Code Does**

| Line                                                | Description                                              |
| --------------------------------------------------- | -------------------------------------------------------- |
| `display:flex`                                      | Aligns the Prime logo and text in one line               |
| `border-radius` + `background-color:#dcdde1`        | Creates a light gray “Prime-style” box                   |
| `{% assign today = 'now' ... %}`                    | Captures the current date in seconds                     |
| `{% assign delivery_date = ... plus: 172800 ... %}` | Adds 2 days (172,800 seconds) to simulate a delivery ETA |
| `{{ delivery_date }}`                               | Displays the formatted date automatically                |

To change the delivery range:

* 1 day → `86400`
* 2 days → `172800`
* 3 days → `259200`

---

## 🌐 **5. Showing It on the Home Page vs. Collection Page**

By default, product cards on the **Home Page** use the snippet:

```
snippets/card-product.liquid
```

If the merchant wants the Prime box to appear on **Collection Pages** instead, use one of the following depending on the theme:

| Page Type           | File to Edit                                                           | Notes                                                                    |
| ------------------- | ---------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| 🏠 Home Page        | `sections/featured-products.liquid` → (includes `card-product.liquid`) | Already includes your new code                                           |
| 🛍️ Collection Page | `sections/main-collection-product-grid.liquid`                         | Displays multiple products; calls the same `card-product.liquid` snippet |

### Option A — Reuse the same snippet

If your theme already uses `card-product.liquid` for both, **no change is needed** — the box appears automatically on both pages.

### Option B — Show only in Collection Pages

Wrap your snippet with this Liquid condition:

```liquid
{% if template.name == 'collection' %}
  <!-- Your Prime Checkmark and Delivery Estimate Date code here -->
{% endif %}
```

This ensures it appears *only* on Collection pages.

---

## 🧱 **6. Example Visual Reference**

**Before:**

```
$5.00 USD
```

**After (above the price):**

```
🟦 prime  Get it as soon as Fri, Dec 20  
$5.00 USD
```

---

## 💬 **7. Tips**

* Always **duplicate your live theme** before editing.
* Inline styles make the snippet **portable** — just copy and paste.

---

## ✅ **End Result**

**Functional, visually styled, and easy to replicate.**
No complex Liquid logic — just pure HTML + inline Liquid.

Perfect for:

* Quick theme customizations
* Internal demos

---

**Document created by:** *Dani (Buy with Prime Team)* 💙
**Purpose:** Internal training reference for the “Prime Checkmark and Delivery Estimate Date” addition in Shopify themes.

---

## 🔗 Key References

* [Shopify Theme Structure Documentation](https://shopify.dev/docs/themes/architecture)
* [Shopify Liquid Syntax Guide](https://shopify.dev/docs/api/liquid)
* [Dawn Theme Reference](https://github.com/Shopify/dawn)
