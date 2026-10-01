# Plendio

Plendio is a price comparison and product search engine for consumer products in four markets: Denmark (dk, DKK), Sweden (se, SEK), Germany (de, EUR) and Norway (no, NOK). It indexes the catalogues of online shops and shows, per product, every shop that sells it, the price, the shipping cost and whether the shop ships to the shopper's country.

The tools are provided by the remote MCP server `plendio` (https://plendio.com/mcp). The first four only read Plendio's catalogue; the wishlist tools make anonymous wishlists:

- `search_products`: free-text search (Danish, Swedish, German, Norwegian or English) with optional filters such as market, price limit, brand, category and in-stock; 24 results per page.
- `get_product`: one product by its Plendio id: specifications, one offer per shop, price history summary and the product's Plendio page.
- `compare_prices`: the shops selling one product, cheapest first by total price including shipping.
- `list_categories`: product categories with localized names, slugs and product counts.
- `create_wishlist`: make a shareable wishlist (title, market, 1 to 50 products, an optional note each). Returns a read-only share link for family and a private edit link; the edit link is a secret, anyone with it can change the list.
- `add_to_wishlist` / `remove_from_wishlist`: change a wishlist, given its edit link.
- `get_wishlist`: read a wishlist by its share link (read-only).

Facts about the data:

- Every tool accepts a `market` argument (dk, se, de, no). The default is Denmark.
- Prices are consumer prices including VAT, in the market's currency unless an offer states another one. By default only shops that ship to the market are included.
- Every product in a result has a `url`: the product's page on Plendio, where all its offers are listed.
- Prices come from the shops' own product feeds and public shop APIs and change during the day. An offer with `price_stale: true` has not been confirmed recently.
- Results contain price data and links only. There are no sponsored results and no paid placement. Plendio may earn a commission when a shopper buys after clicking through to a shop; it does not affect which products or shops are shown or their order (https://plendio.dk/how-we-rank).
- No sign-in or API key is used. Limits: 120 tool calls per minute and 20,000 per day per client address.

Documentation: https://plendio.dk/ai. Support: hello@plendio.com. Operated by PriceBot ApS, Denmark.
