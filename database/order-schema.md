# Order Schema



| Field Name  | Data Types                            | Description                          |
| ----------- | ------------------------------------- | ------------------------------------ |
| totalAmount | Float                                 | Total Amount of specific order       |
| status      | string                                | Status of product delivery           |
| user        | [User](user-schema.md)                | User to which specific order belongs |
| items       | [OrderItem\[\]](order-item-schema.md) | List of items that were order        |
| payment     | [Payment\[\]](payment-schema.md)      |                                      |
