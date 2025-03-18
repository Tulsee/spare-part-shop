# Product Schema



| Field Name      | Data Types        | Description                                         |
| --------------- | ----------------- | --------------------------------------------------- |
| name            | String            |                                                     |
| description     | String            |                                                     |
| sku             | String            | unique, (Parts-Number)                              |
| images          | String            | List of images of that product                      |
| isFeatured      | Boolean           |                                                     |
| category        | Category          | Category of that product                            |
| brand           | Brand             | Brand of that product                               |
| productListing  | ProductListing\[] | List of product listing that are register by vendor |
| vehicleCategory | VehiclesCategory  | Vehicle Category of that product                    |



The **products** are added by the super admin.
