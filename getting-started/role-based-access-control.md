# 👨‍🦱 Role-Based Access Control

In this project,  we have implemented **Role-Based Access Control (RBAC)** to manage user permissions and ensure that users only have access to the features relevant to their role. There are three primary roles:

* [**Customer**](role-based-access-control.md#id-1.-customer)
* [**Vendor**](role-based-access-control.md#id-2.-vendor)
* [**SuperAdmin**](role-based-access-control.md#id-3.-superadmin)

## Overview of Roles

### 1. Customer

**Description:** The **Customer** role represents regular users who can interact with the application but have limited access compared to vendors or administrators.\
\
**Permissions:**

* View products listing from different vendor
* Add to cart and wishlist
* Make orders
* Add multiple shipping address
* View Order history
* Make payment from esewa (for now)
* Update personal Profile and settings
* Access customer support (Proposed)
* Write product reviews

\
**Actions:**

* Customers cannot manage other users.
* Customers do not have access to vendor-specific features or administrative tools.



### 2. Vendor

**Description:** The **Vendor** role represents users who provide products or services on the platform.

Permissions:

* Add, edit, or remove their product-listing.
* View orders placed by the customers.
* Manage inventory and stock levels.
* Manage pricing for their products listing
* Access vendor-specific reports

**Actions:**

* Vendors cannot manage administrative functions or access the system's settings.
* Vendors cannot access customer information or manage customer profiles.

### 3. SuperAdmin

**Description**: The **SuperAdmin** role has full control over the application and can manage all aspects of the system.

**Permissions**:

* Manage users (Customers, Vendors)
* Manage roles and permissions
* Configure application settings
* Access system logs and reports
* Oversee all platform activities (orders, inventory, etc.)
* View and modify all data

**Actions**:

* SuperAdmin have unrestricted access to every part of the system.
* SuperAdmin can assign roles and permissions to other users.

## Conclusion

By implementing these role-based access controls, we ensure that users only have access to the features and data that are appropriate for their role. This structure helps maintain both security and ease of use across the platform.
