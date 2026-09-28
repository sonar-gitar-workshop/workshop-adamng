# Cross-repo dependencies

The order API in this repository has a separate caller,
sonar-gitar-workshop/workshop-storefront. It is deployed on its own and calls
this service over HTTP, so its tests do not run against changes here.

- `GET /products/<sku>`: the storefront reads `sku`, `name` and `price_cents`
  in `shop_client.py` and `product_page.py`.
- `POST /orders`: the storefront sends `items[].sku` and `items[].quantity`,
  and reads `id`, `items[].unit_price_cents` and `total_cents` in
  `shop_client.py` and `receipt.py`.
- `GET /orders/<order_id>`: the storefront reads `id` and `total_cents` in
  `shop_client.py` and `order_status.py`.

Any change to a route, request field or response field above must be checked
against workshop-storefront.
