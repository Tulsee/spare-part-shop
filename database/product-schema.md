# Product Schema



| Field Name      | Data Types                                      | Description                                         |
| --------------- | ----------------------------------------------- | --------------------------------------------------- |
| name            | String                                          |                                                     |
| description     | String                                          |                                                     |
| sku             | String                                          | unique, (Parts-Number)                              |
| images          | String                                          | List of images of that product                      |
| isFeatured      | Boolean                                         |                                                     |
| category        | [Category](category-schema.md)                  | Category of that product                            |
| brand           | [Brand](brand-schema.md)                        | Brand of that product                               |
| productListing  | [ProductListing\[\]](product-listing-schema.md) | List of product listing that are register by vendor |
| vehicleCategory | [VehiclesCategory](vehicles-category-schema.md) | Vehicle Category of that product                    |



The **products** are added by the super admin.
