# Vendor Schema



| Field Name                | Data Type                                       | Description                                |
| ------------------------- | ----------------------------------------------- | ------------------------------------------ |
| companyName               | String                                          |                                            |
| location                  | String                                          |                                            |
| companyRegistrationNumber | String                                          | Unique                                     |
| companyRegistrationPhoto  | String                                          |                                            |
| ownerCitizenshipNumber    | String                                          |                                            |
| ownerCitizenshipPhoto     | String                                          |                                            |
| shopPhoto                 | String                                          |                                            |
| openingTime               | String                                          |                                            |
| closingTime               | String                                          |                                            |
| phoneNumber               | String                                          |                                            |
| promoCode                 | String                                          |                                            |
| verified                  | Boolean                                         |                                            |
| vendorAdmin               | [User](user-schema.md)                          |                                            |
| productListing            | [ProductListing\[\]](product-listing-schema.md) | List of products vendor have in their shop |
