# Shopify Wishlist

A set of files used to implement a simple customer wishlist on a Shopify store.

## Installation

To begin using **Shopify Wishlist**, you must copy some of the files in this repo into your Shopify theme code.

_Note_: This setup assumes that you have a snippet for displaying a product card.

**Files to copy:**
|Repo File|Shopify Theme Location|
|:--:|:--:|
|[`button-wishlist.liquid`]()|`snippets/`|
|[`icon-wishlist.liquid`]()| `snippets/`|
|[`page.wishlist.liquid`]()|`templates/`|
|[`poduct.card.liquid`]()|`templates/`|
|[`wishlist.js`]()|`assets/`|

1. Place the `button-wishlist.liquid` snippet inside your existing product card snippet, or on the `product.liquid` template
   - `{%- render 'button-wishlist', product: product -%}`
   - This will allow customer's to add/remove items to/from their wishlist
2. Replace the snippet in the `product.card.liquid` template with you existing product card snippet
   - Same snippet from step 1
3. Create a new page in the Shopify admin:
   - Admin > Online Store > Pages > Add Page
   - Set the new page's `template` to `page.wishlist`
   - This page will display a customer's saved wishlist items
4. Place the script in `theme.liquid` before the closing `</head>` tag
   - `<script src="{{ 'wishlist.js' | asset_url }}" defer="defer"></script>`

That's it! When viewing you Shopify store, you should see the wishlist buttons inside your product cards (likely on collections pages) or on the product template. A click on the wishlist button will add/remove the item from the customer's wishlist and trigger active styling on the button. After adding wishlist items, you can view your wishlist by navigating to the page created in step 3.

[Demo Shopify Store](https://lerman-labs.myshopify.com/collections/all)

## Notes

- This wishlist uses Javascript and localStorage to save the customer's wishlist on their browser. The localStorage will not persist if the user clears browser storage or browses in incognito mode.
- As customers browser products and add them to their wishlist, the script will automatically set any wishlist buttons to active state if the corresponding product is already included in the wishlist.
- These files come with no styling or structure so that you can customize as needed. This is intended to bring you the base functionality of a wishlist with no frills.
