# Product Listing Schema



| Field Name | Data Types   | Description                                        |
| ---------- | ------------ | -------------------------------------------------- |
| price      | Float        |                                                    |
| discount   | Float        |                                                    |
| stock      | Int          |                                                    |
| product    | Product      | The product of that listing                        |
| vendor     | Vendor       | The vendor who have register that product listing  |
| cartItem   | CartItem\[]  | The list of cart Item that have been added in cart |
| orderItem  | OrderItem\[] | The list of order items that has been order        |



In the **product listing**, each **product listing** represents a specific **product** under different vendor.
