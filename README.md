# Restuarant API

This is a new api for restuarants, you can login, sign up and create resturants. 

## API DOCUMENTATION

### Authentication

Do we need authentication, do we need token.

Sure, here's a Markdown documentation for the provided code:

# User Authentication API Documentation

This documentation outlines the endpoints and functionality of a user authentication API. The API allows users to sign up and log in as owners.

## Table of Contents

1. [**Sign Up**](#sign-up)
2. [**Log In**](#log-in)

---

## Sign Up

### Endpoint

- `POST /signup`

### Description

This endpoint allows a user to sign up as an owner by providing their name, email, and password. It checks if the email is unique, hashes the password for security, and creates a new owner in the system if all checks pass.

### Request Body

- `name` (string): The name of the owner.
- `email` (string): The email address of the owner.
- `password` (string): The password for the owner's account.

### Success Response

- **HTTP Status Code:** 201 Created
- **Response Body:**

  ```json
  {
    "message": "Owner created successfully",
    "owner": {
      // Owner object containing details
    }
  }
  ```

### Error Responses

- **HTTP Status Code:** 409 Conflict

  ```json
  {
    "message": "Owner already exists"
  }
  ```

- **HTTP Status Code:** 500 Internal Server Error

  ```json
  {
    "message": "Something went wrong",
    "error": "Error message details"
  }
  ```

---

## Log In

### Endpoint

- `POST /login`

### Description

This endpoint allows a user to log in as an owner by providing their email and password. It verifies the email's existence, checks if the provided password matches the stored hashed password, and issues a JWT token for authenticated access.

### Request Body

- `email` (string): The email address of the owner.
- `password` (string): The password for the owner's account.

### Success Response

- **HTTP Status Code:** 200 OK
- **Response Body:**

  ```json
  {
    "message": "Owner logged in successfully",
    "token": "JWT Token"
  }
  ```

### Error Responses

- **HTTP Status Code:** 404 Not Found

  ```json
  {
    "message": "Owner not found"
  }
  ```

- **HTTP Status Code:** 401 Unauthorized

  ```json
  {
    "message": "Invalid credentials"
  }
  ```

- **HTTP Status Code:** 500 Internal Server Error

  ```json
  {
    "message": "Something went wrong",
    "error": "Error message details"
  }
  ```
