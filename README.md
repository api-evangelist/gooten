# Gooten (gooten)

Gooten is a print-on-demand and global manufacturing and fulfillment platform for custom products - apparel, wall art, drinkware, home goods, and more. Its public REST API is hosted at `api.print.io` (the Print.io platform Gooten was built on) and lets ecommerce brands and developers browse the catalog and per-region SKUs, retrieve print templates, create print-ready products from artwork, quote shipping and order prices, and submit and manage manufacturing orders routed across Gooten's distributed vendor network.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/gooten/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/gooten/refs/heads/main/apis.yml)

## Access Model

The Gooten API is open to partners and merchants - there is no application review gate documented, but you do need a Gooten account to obtain credentials.

- **Authentication.** Every request carries a public `RecipeID` (from the Gooten Admin) as a query parameter. Order-writing and billing endpoints additionally require a private `PartnerBillingKey`, which must be URL-encoded and must never be exposed client-side.
- **Transport.** REST over HTTPS only; plain HTTP calls fail. CORS is enabled for client-side catalog reads. Responses use a Gooten error envelope with a `HadError` flag and detailed error objects.
- **Base URLs.** Most catalog, order, shipping, and billing endpoints live under `https://api.print.io/api/v/5/source/api`. Print-ready product (PRP) management lives under `https://api.print.io/api/v2/recipes/{recipeId}`.
- **Pricing.** No setup or monthly fees. You pay the per-order production and shipping cost only when an item is manufactured and shipped, and set your own retail margin. High-volume merchants can negotiate custom rates with the Gooten enterprise team. See `plans/gooten-plans-pricing.yml`.
- **Async.** Order-status updates are delivered via configurable outbound webhooks (Gooten POSTs to a URL you provide). There is no public WebSocket or SSE API - see `review.yml`.

This entry was assembled by API Evangelist from Gooten's public API documentation. Field-level request/response shapes in the OpenAPI are modeled from the documented examples and are approximate; confirm exact payloads against the Gooten docs.

## Tags

- Print on Demand
- Fulfillment
- Manufacturing
- Ecommerce
- Dropshipping
- Custom Products

## Timestamps

- **Created:** 2026-07-11
- **Modified:** 2026-07-11

## APIs

### Gooten Products API

Browse the Gooten catalog. A product is a category (for example "Canvas Wraps"); each product has region-specific SKUs (variants) available per shipping country. List products, list variants and pricing for a product by country and currency, and look up supported shipping countries and currencies used across the rest of the API.

- **Human URL:** [https://www.gooten.com/api-documentation/product-variants-skus-for-a-product/](https://www.gooten.com/api-documentation/product-variants-skus-for-a-product/)
- **Base URL:** `https://api.print.io/api/v/5/source/api`

#### Tags

- Products
- Catalog
- SKUs
- Variants

#### Properties

- [Documentation](https://www.gooten.com/api-documentation/getting-started/)
- [API Reference](https://www.gooten.com/api-documentation/product-variants-skus-for-a-product/)
- [OpenAPI](openapi/gooten-openapi.yml)
- [Postman Collection](collections/gooten.postman_collection.json)
- [Open Collection](collections/gooten.opencollection.json)

### Gooten Orders API

Submit manufacturing orders with ship-to and billing addresses, line items (SKU, quantity, artwork images, ship method), and a Payment object carrying the PartnerBillingKey. Retrieve an order by its Safe Order ID or search orders by name, email, postal code, and date range, get full billing breakdowns, and update the shipping address or method on in-flight orders.

- **Human URL:** [https://www.gooten.com/api-documentation/submitting-an-order/](https://www.gooten.com/api-documentation/submitting-an-order/)
- **Base URL:** `https://api.print.io/api/v/5/source/api`

#### Tags

- Orders
- Fulfillment
- Billing

#### Properties

- [Documentation](https://www.gooten.com/api-documentation/submitting-an-order/)
- [API Reference](https://www.gooten.com/api-documentation/get-order-by-id/)
- [OpenAPI](openapi/gooten-openapi.yml)
- [Postman Collection](collections/gooten.postman_collection.json)
- [Open Collection](collections/gooten.opencollection.json)

### Gooten Shipping API

Quote a cart before you submit it. Post ship-to location and line items to retrieve available shipping options and their costs, and post a full cart to estimate the total order price - product cost, shipping, surcharges, taxes, and fees - in a chosen currency.

- **Human URL:** [https://www.gooten.com/api-documentation/shipping-options-for-a-cart/](https://www.gooten.com/api-documentation/shipping-options-for-a-cart/)
- **Base URL:** `https://api.print.io/api/v/5/source/api`

#### Tags

- Shipping
- Pricing
- Estimates

#### Properties

- [Documentation](https://www.gooten.com/api-documentation/shipping-options-for-a-cart/)
- [API Reference](https://www.gooten.com/api-documentation/getting-price-estimate-for-an-order/)
- [OpenAPI](openapi/gooten-openapi.yml)
- [Postman Collection](collections/gooten.postman_collection.json)
- [Open Collection](collections/gooten.opencollection.json)

### Gooten Print Assets API

Manage the artwork and print data behind a SKU. Retrieve the product template for a SKU - the image spaces, required sizes, and coordinates that describe how to build print-ready art - then create, list, update, and delete print-ready products (PRPs) that bind a Gooten SKU to your artwork so it can be ordered directly. The PRP endpoints live under the `/api/v2/recipes/{recipeId}` base.

- **Human URL:** [https://www.gooten.com/api-documentation/print-ready-products/](https://www.gooten.com/api-documentation/print-ready-products/)
- **Base URL:** `https://api.print.io`

#### Tags

- Print Assets
- Templates
- Artwork

#### Properties

- [Documentation](https://www.gooten.com/api-documentation/listing-product-templates-for-a-sku/)
- [API Reference](https://www.gooten.com/api-documentation/print-ready-products/)
- [OpenAPI](openapi/gooten-openapi.yml)
- [Postman Collection](collections/gooten.postman_collection.json)
- [Open Collection](collections/gooten.opencollection.json)

## Common Properties

- [Website](https://www.gooten.com)
- [LinkedIn](https://www.linkedin.com/company/gooten)
- [Documentation](https://www.gooten.com/api-documentation/getting-started/)
- [Support Center](https://help.gooten.com/hc/en-us)
- [Plans](plans/gooten-plans-pricing.yml)
- [Rate Limits](rate-limits/gooten-rate-limits.yml)
- [Fin Ops](finops/gooten-finops.yml)
- [Blog](https://www.gooten.com/blog/)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
