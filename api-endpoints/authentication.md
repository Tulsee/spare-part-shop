# 🕵️ Authentication

This section provides details about the **Authentication API endpoints** used to manage user access, including registration, login, logout, and password management.

### Base URL

```arduino
https://localhost:8000/api/v1/auth
```



## Create a new user

<mark style="color:green;">`POST`</mark> `/register`

This endpoint is used to register user in the Spare Parts Shop website

**Headers**

| Name         | Value              |
| ------------ | ------------------ |
| Content-Type | `application/json` |

**Body**

| Name        | Type   | Description                     |
| ----------- | ------ | ------------------------------- |
| fullName    | string | Name of the user                |
| email       | string | Email of the user               |
| password    | string | password for the authentication |
| phoneNumber | string | Phone Number of the user        |

**Response**

{% tabs %}
{% tab title="201" %}
```json
{
    "status": "success",
    "message": "User registered successfully. OTP sent via SMS & email.",
    "data": {
        "id": "cm8bhuxol0000fvqabul3rxjd",
        "fullName": "Shankar Ghimire",
        "email": "ghimire.shankar1996@gmail.com",
        "role": "customer",
        "isAuthenticated": false,
        "isVerified": false,
        "otpCodeExpiry": "2025-03-16T10:39:53.318Z",
        "createdAt": "2025-03-16T10:29:53.541Z",
        "updatedAt": "2025-03-16T10:29:53.541Z"
    }
}
```
{% endtab %}

{% tab title="400" %}
```json
{
  "error": "Invalid request"
}
```
{% endtab %}

{% tab title="409" %}
```json
{
    "status": "error",
    "message": "User already exists with this phone number or email"
}
```

If the provided **email** or **phone number** already exists in the system, the following error will be returned:
{% endtab %}
{% endtabs %}



## User Login

<mark style="color:green;">`POST`</mark> `/login`

This endpoint is used to login all the users (customer, vendor and superAdmin) in the Spare Parts Shop website

Users can log in only after [verifying](authentication.md#verify-otp) the OTP sent to their email or phone number.

**Headers**

| Name         | Value              |
| ------------ | ------------------ |
| Content-Type | `application/json` |

**Body**

| Name     | Type   | Description                      |
| -------- | ------ | -------------------------------- |
| email    | string | Email used while registration    |
| password | number | Password used while registration |

**Response**

{% tabs %}
{% tab title="200" %}
```json
{
    "status": "success",
    "message": "Logged in successfully",
    "data": {
        "id": "cm87lhqs20000li4qlzd5tcw9",
        "fullName": "Shankar Ghimire",
        "email": "ghimire.shankar1996@gmail.com",
        "role": "customer",
        "isAuthenticated": true,
        "isVerified": true,
        "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VySWQiOiJjbTg3bGhxczIwMDAwbGk0cWx6ZDV0Y3c5IiwiZnVsbE5hbWUiOiJTaGFua2FyIEdoaW1pcmUiLCJlbWFpbCI6ImdoaW1pcmUuc2hhbmthcjFAZ21haWwuY29tIiwicm9sZSI6InZlbmRvciIsImlhdCI6MTc0MjEyMTQ4MiwiZXhwIjoxNzQyNzI2MjgyfQ._3SqAhickQTfoUBmeduEwcrEZkfHfAbZSxxJrJivI24",
        "refreshToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VySWQiOiJjbTg3bGhxczIwMDAwbGk0cWx6ZDV0Y3c5IiwiZnVsbE5hbWUiOiJTaGFua2FyIEdoaW1pcmUiLCJlbWFpbCI6ImdoaW1pcmUuc2hhbmthcjFAZ21haWwuY29tIiwicm9sZSI6InZlbmRvciIsImlhdCI6MTc0MjEyMTQ4MiwiZXhwIjoxNzQ0NzEzNDgyfQ.byLj_wykJOTaI4nufMkRBSLSMLOZEZWT19mtYEI4R5E"
    }
}
```

If the user logs in successfully, the `accessToken` and `refreshToken` are saved in cookies and also included in the response body.
{% endtab %}

{% tab title="403" %}
```json
{
    "status": "error",
    "message": "Invalid credentials."
}
```
{% endtab %}
{% endtabs %}



## Verify OTP

<mark style="color:green;">`POST`</mark> `/verify-otp`

This endpoint is used to verify the OTP sent to the user during registration.

**Headers**

| Name         | Value              |
| ------------ | ------------------ |
| Content-Type | `application/json` |

**Body**

| Name    | Type   | Description                              |
| ------- | ------ | ---------------------------------------- |
| email   | string | Email used while registration            |
| otpCode | string | OTP code sent via. email or phone number |

**Response**

{% tabs %}
{% tab title="200" %}
```json
{
 "status":"success",
 "message":"Your account has been verified successfully. You can now login with your email and password"
}
```
{% endtab %}

{% tab title="404" %}
```json
{
  "status":"error",
  "message":"No user found with this email address"
}
```
{% endtab %}

{% tab title="400" %}
```json
{
    "status":"error",
    "message":"OTP has expired. Pleased request a new OTP"
}

OR

{
    "status":"error",
    "message":"Invalid OTP code. Please check and try again"
}
```
{% endtab %}
{% endtabs %}



## Resend OTP

<mark style="color:green;">`POST`</mark> `/resend-otp`

This endpoint is used to resend otp. User can used this endpoint to resend otp if previous otp is expired before verifying their account.

**Headers**

| Name         | Value              |
| ------------ | ------------------ |
| Content-Type | `application/json` |

**Body**

| Name  | Type   | Description                                  |
| ----- | ------ | -------------------------------------------- |
| email | string | E-mail address of user for resending the otp |

**Response**

{% tabs %}
{% tab title="200" %}
```json
{
  "status":"success",
  "message":"OTP has been resent to your email and phone number.",
  "data":{
     "id": "cm8bhuxol0000fvqabul3rxjd",
     "fullName": "Shankar Ghimire",
     "email": "ghimire.shankar1996@gmail.com",
     "otpCodeExpiry": "2025-03-16T10:39:53.318Z"
  }
}
```
{% endtab %}

{% tab title="404" %}
```json
{
  "status": "error",
  "message": "No user found with this email address"
}
```
{% endtab %}

{% tab title="409" %}
```json
{
  "status": "error",
  "message": "Account is already verified."
}
```
{% endtab %}

{% tab title="429" %}
```json
{
  "status": "error",
  "message": "OTP is still valid. Please check your email fo the OTP."
}
```
{% endtab %}
{% endtabs %}



## Forgot Password

<mark style="color:green;">`POST`</mark> `/forgot-password`

This endpoint is used  to resend OTP for the forgot password.

If the user forgot their password, they can resent otp for changing password.

**Headers**

| Name         | Value              |
| ------------ | ------------------ |
| Content-Type | `application/json` |

**Body**

| Name  | Type   | Description        |
| ----- | ------ | ------------------ |
| email | string | E-mail of the user |

**Response**

{% tabs %}
{% tab title="200" %}
```json
{
  "status": "success",
  "message": "OTP has been sent to your registered email address",
  "data": {
    "email": "ghimire.shankar1996@gmail.com",
    "otpForgotPasswordExpiry": "2025-03-16T10:39:53.318Z"
  }
}
```
{% endtab %}

{% tab title="404" %}
```json
{
  "status": "error",
  "message": "No user found with this email address"
}
```
{% endtab %}
{% endtabs %}



## Reset Password

<mark style="color:green;">`POST`</mark> `/reset-password`

This endpoint is used to reset the user password.

If the user forget their password they get new opt by [`forgot-password`](authentication.md#forgot-password) endpoint, and reset password by this endpoint.

**Headers**

| Name         | Value              |
| ------------ | ------------------ |
| Content-Type | `application/json` |

**Body**

| Name        | Type   | Description                                                 |
| ----------- | ------ | ----------------------------------------------------------- |
| email       | string | E-mail of the user                                          |
| otp         | string | OTP received in phone number or email from forgot-password  |
| newPassword | string | New password for logging                                    |

**Response**

{% tabs %}
{% tab title="200" %}
```json
{
  "id": 1,
  "name": "John",
  "age": 30
}
```
{% endtab %}

{% tab title="400" %}
```json
{
  "error": "Invalid request"
}
```
{% endtab %}
{% endtabs %}
