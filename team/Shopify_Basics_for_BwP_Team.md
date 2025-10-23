# 🧱 Shopify Theme Editor Basics for Buy with Prime Team

> **Goal:** Help team members understand the basic structure of Shopify and how Buy with Prime integrates at the theme level.

---

## 🧭 1. What is the Shopify Theme Editor?

The **Theme Editor** is where merchants customize the look and feel of their online store.  
It controls the layout, sections, and styling of every page — from product listings to checkout.

For Buy with Prime (BwP), this is the main place where code snippets or app elements are added.

---

## 🧩 2. Key Theme Files

| File / Folder | Purpose |
|----------------|----------|
| `theme.liquid` | The main layout of the store (like the skeleton). Controls global structure. |
| `sections/` | Contains editable sections (e.g. product info, image gallery, footer). |
| `templates/` | Defines page types (product, collection, cart, etc.). |
| `snippets/` | Small pieces of reusable code, often used for app integrations. |

---

## 💻 3. How Buy with Prime Fits In

1. Merchant installs the **Buy with Prime app** via Shopify App Store.  
2. The app injects a **Liquid snippet** into product page templates.  
3. The snippet calls the **BwP button** and connects to Amazon Seller Central.  
4. Customers can then use their Amazon Prime account to complete checkout.

Example snippet (simplified):

```liquid
{% if product.available %}
  <div id="bwp-button">
    <button>Buy with Prime</button>
  </div>
{% endif %}

This means the button will only appear when the product is in stock.

⚙️ 4. Best Practices for Support

✅ Always back up the theme before editing code.

🔍 Confirm that the Shopify plan supports third-party checkout.

🧩 Insert snippets only in product-related templates or sections.

🔄 Test the integration using the Dawn theme (cleanest default theme).

🧠 If an issue appears, check:

Snippet placement in theme.liquid

App permissions

Inventory sync between Shopify and Amazon Seller Central

## 🔗 Key References

- [Shopify Developer Docs – Themes](https://shopify.dev/docs/themes)
- [Shopify Liquid Basics](https://shopify.dev/docs/api/liquid)
- [Buy with Prime – Official Site](https://buywithprime.amazon.com/)
- [Shopify Learn – Courses](https://www.shopify.com/learn)
- [Shopify Community Forums](https://community.shopify.com/)


This guide was created to help Buy with Prime team members better understand Shopify’s structure and provide faster, more effective support to merchants.
Author: Daniela Montero 💙