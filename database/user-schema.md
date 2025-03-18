# User Schema



| Field Name              | Data Types                       | Description                                  |
| ----------------------- | -------------------------------- | -------------------------------------------- |
| fullName                | String                           |                                              |
| email                   | String                           | Unique                                       |
| phoneNumber             | String                           | Unique                                       |
| password                | String                           | Hashed Password                              |
| isVerified              | Boolean                          |                                              |
| isAuthenticated         | Boolean                          |                                              |
| role                    | Enum                             | vendor, customer, superAdmin                 |
| otpCode                 | String                           | OTP code generated while registration        |
| otpCodeExpiry           | DateTime                         |                                              |
| country                 | String                           |                                              |
| address                 | String                           |                                              |
| state                   | String                           |                                              |
| dateOfBirth             | String                           |                                              |
| gender                  | String                           |                                              |
| profilePicture          | String                           | Photo of user                                |
| bio                     | String                           |                                              |
| otpForgotPassword       | String                           | OTP send for forgot password                 |
| otpForgotPasswordExpiry | String                           |                                              |
| vendor                  | [Vendor\[\]](vendor-schema.md)   | List of vendor if register                   |
| review                  | Review\[]                        | List of reviews if given                     |
| cart                    | [Cart\[\]](cart-schema.md)       | List of cart if any product is added to cart |
| order                   | [Order\[\]](order-schema.md)     | List of Orders                               |
| payment                 | [Payment\[\]](payment-schema.md) | List of payment if any product was order     |

