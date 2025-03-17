# 👨‍🦱 User

This section provides details about the **User API endpoints** used to manage user and user profile.

#### Base URL <a href="#base-url" id="base-url"></a>

```
https://localhost:8000/api/v1/user
```

## Get User Profile

<mark style="color:purple;">GET</mark> `/my-profile`

This endpoint is used to get all the detail data of logged in user

**Headers**

| Name         | Value                                                                                     |
| ------------ | ----------------------------------------------------------------------------------------- |
| Content-Type | `application/json`                                                                        |
| cookie       | <p><code>accessToken=access-token;</code><br><code>refreshToken=refresh-token;</code></p> |

**Response**

{% tabs %}
{% tab title="200" %}
```json
{
    "status": "success",
    "data": {
        "id": "cm87lhqs20000li4qlzd5tcw9",
        "fullName": "Shankar Ghimire",
        "email": "ghimire.shankar1996@gmail.com",
        "phoneNumber": "977-986701566",
        "role": "customer",
        "isAuthenticated": true,
        "isVerified": true,
        "country": "Nepal",
        "address": "Imadol",
        "state": null,
        "dateOfBirth": null,
        "gender": "male",
        "profilePicture": "http://localhost:8000/uploads/1742193095341-91054300.webp",
        "bio": null
    }
}
```
{% endtab %}

{% tab title="401" %}
```json
{
  "status": "error",
  "message": "Unauthorized"
}
```
{% endtab %}
{% endtabs %}



## Get User details by UserId

<mark style="color:purple;">GET</mark> `/users/:userId`

**Authentication**:  **Protected Route** (only Super Admin and vendor can access)

**Headers**

| Name         | Value                                                                                                 |
| ------------ | ----------------------------------------------------------------------------------------------------- |
| Content-Type | `application/json`                                                                                    |
| cookie       | <p><code>accessToken=&#x3C;access-token></code><br><code>refreshToken=&#x3C;refresh-token></code></p> |

**Response**{

{% tabs %}
{% tab title="200" %}
```json
 {
   "status": "success",
    "data": {
        "id": "cm87lhqs20000li4qlzd5tcw9",
        "fullName": "Shankar Ghimire",
        "email": "ghimire.shankar1996@gmail.com",
        "phoneNumber": "977-986701566",
        "role": "customer",
        "isAuthenticated": true,
        "isVerified": true,
        "country": "Nepal",
        "address": "Imadol",
        "state": null,
        "dateOfBirth": null,
        "gender": "male",
        "profilePicture": "http://localhost:8000/uploads/1742193095341-91054300.webp",
        "bio": null
    }
}
```
{% endtab %}

{% tab title="401" %}
```json
{
    "status": "error",
    "message": "Unauthorized role"
}
```
{% endtab %}

{% tab title="404" %}
```json
{
    "status": "error",
    "message": "User not found"
}
```
{% endtab %}
{% endtabs %}



## Get All Users

<mark style="color:purple;">GET</mark> `/all-users`

This endpoint is used to get all the users detail.

**Authentication**:  **Protected Route** (only Super Admin can access)

**Headers**

| Name         | Value                                                                                                 |
| ------------ | ----------------------------------------------------------------------------------------------------- |
| Content-Type | `application/json`                                                                                    |
| cookie       | <p><code>accessToken=&#x3C;access-token></code><br><code>refreshToken=&#x3C;refresh-token></code></p> |

**Response**{

{% tabs %}
{% tab title="200" %}
```json
{
    "status": "success",
    "data": [
        {
            "id": "cm87lhqs20000li4qlzd5tcw9",
            "fullName": "Shankar Ghimire",
            "email": "ghimire.shankar1@gmail.com",
            "phoneNumber": "977-986701566",
            "role": "vendor",
            "createdAt": "2025-03-13T17:00:31.826Z",
            "isAuthenticated": true,
            "isVerified": true,
            "country": "Nepal",
            "state": null,
            "address": "Imadol",
            "dateOfBirth": null,
            "gender": "male",
            "profilePicture": "http://localhost:8000/uploads/1742193095341-91054300.webp",
            "bio": null
        }
    ]
}
```
{% endtab %}

{% tab title="401" %}
<pre class="language-json"><code class="lang-json"><strong>{
</strong><strong>    "status": "error",
</strong>    "message": "Unauthorized role"
}
</code></pre>
{% endtab %}
{% endtabs %}



## Update user profile

<mark style="color:blue;">`PUT`</mark> `/users`

This endpoint is used to update user.

**Authentication**:  **Protected Route** (all the logged in user can access this endpoint)

**Headers**

| Name         | Value                                                                                                 |
| ------------ | ----------------------------------------------------------------------------------------------------- |
| Content-Type | `multipart/form-data`                                                                                 |
| cookie       | <p><code>accessToken=&#x3C;access-token></code><br><code>refreshToken=&#x3C;refresh-token></code></p> |

**Body**

| Name           | Type                  | Description                                |
| -------------- | --------------------- | ------------------------------------------ |
| fullName       | string?[^1]           | Full Name of the user                      |
| email          | string?               | email of the user                          |
| phoneNumber    | string?               | Phone Number of the user                   |
| country        | string?               | Country of the user                        |
| address        | string?               | Address of the user                        |
| state          | string?               | State of the user where he lives           |
| dateOfBirth    | string?               | Date of the birth when he was born (Date)  |
| profilePicture | file(jpg, jpeg, png)? | Profile Picture of the user                |
| gender         | string?               | gender of the user                         |
| bio            | string?               | biography of the user                      |

[**NOTE:** If user want to change email and phone number, this endpoint will check if new email and new phone number is already used by other user or not. If used, user cannot change that.](#user-content-fn-2)[^2]

**Response**&#x20;

{% tabs %}
{% tab title="200" %}
```json
{
    "status": "success",
    "message": "Profile updated successfully",
    "data": {
        "id": "cm87lhqs20000li4qlzd5tcw9",
        "fullName": "Shankar",
        "email": "ghimire.shankar12@gmail.com",
        "phoneNumber": "977-986701566",
        "role": "vendor",
        "isAuthenticated": true,
        "isVerified": true,
        "country": "Nepal",
        "address": "Imadol",
        "state": null,
        "dateOfBirth": null,
        "gender": "male",
        "profilePicture": "http://localhost:8000/uploads/1742193095341-91054300.webp",
        "bio": null
    }
}
```
{% endtab %}

{% tab title="404" %}
```json
{
  "status": "error",
  "message": "User not found"
}
```
{% endtab %}

{% tab title="500" %}
```json
{
    "status": "error",
    "message": "Failed to process the image."
}
```
{% endtab %}

{% tab title="400" %}
```json
{
    "status": "error",
    "message": "userId is required while updating userProfile as superAdmin"
}
```
{% endtab %}
{% endtabs %}



## Delete User

<mark style="color:red;">DELETE</mark> `/:userId`

This endpoint is used to delete (remove) the user.

**Authentication**:  **Protected Route** (only Super Admin can access)

**Headers**

| Name         | Value                                                                                                 |
| ------------ | ----------------------------------------------------------------------------------------------------- |
| Content-Type | `application/json`                                                                                    |
| cookie       | <p><code>accessToken=&#x3C;access-token></code><br><code>refreshToken=&#x3C;refresh-token></code></p> |

**Response**

{% tabs %}
{% tab title="200" %}
```json
{
  "status": "success",
  "message": "User deleted successfully"
}
```
{% endtab %}

{% tab title="401" %}
```json
{
    "status": "error",
    "message": "Unauthorized role"
}
```
{% endtab %}

{% tab title="404" %}
```json
{
    "status": "error",
    "message": "User not found"
}
```
{% endtab %}

{% tab title="500" %}
```json
{
    "status": "error",
    "message": "An unknow error occured"
}
```
{% endtab %}
{% endtabs %}

[^1]: question mark (?) after data types represent that the field is optional.

[^2]: 
