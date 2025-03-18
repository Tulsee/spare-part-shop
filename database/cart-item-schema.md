# Cart Item Schema



| Field Name     | Data Types                                  | Description                                        |
| -------------- | ------------------------------------------- | -------------------------------------------------- |
| quantity       | Int                                         | The number of quantity that has been added in cart |
| price          | Float                                       | The price of specific product                      |
| cart           | [Cart](cart-schema.md)                      | The cart to which specific cart item belong to.    |
| productListing | [ProductListing](product-listing-schema.md) |                                                    |
