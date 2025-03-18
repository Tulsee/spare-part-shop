# Cart Schema



| Field Name | Data Types                          | Description                           |
| ---------- | ----------------------------------- | ------------------------------------- |
| totalPrice | Float                               |                                       |
| user       | [User](user-schema.md)              | The user that cart belongs to         |
| item       | [CartItem\[\]](cart-item-schema.md) | List of item add by the specific user |
