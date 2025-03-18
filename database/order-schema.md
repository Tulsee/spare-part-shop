# Order Schema



| Field Name  | Data Types   | Description                          |
| ----------- | ------------ | ------------------------------------ |
| totalAmount | Float        | Total Amount of specific order       |
| status      | string       | Status of product delivery           |
| user        | User         | User to which specific order belongs |
| items       | OrderItem\[] | List of items that were order        |
| payment     | Payment\[]   |                                      |
