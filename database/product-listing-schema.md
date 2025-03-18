# Product Listing Schema



| Field Name | Data Types                            | Description                                        |
| ---------- | ------------------------------------- | -------------------------------------------------- |
| price      | Float                                 |                                                    |
| discount   | Float                                 |                                                    |
| stock      | Int                                   |                                                    |
| product    | [Product](product-schema.md)          | The product of that listing                        |
| vendor     | [Vendor](vendor-schema.md)            | The vendor who have register that product listing  |
| cartItem   | [CartItem\[\]](cart-item-schema.md)   | The list of cart Item that have been added in cart |
| orderItem  | [OrderItem\[\]](order-item-schema.md) | The list of order items that has been order        |



In the **product listing**, each **product listing** represents a specific **product** under different vendor.
