API Documentation
Owner Sign Up
Create a new owner account.

Endpoint
POST /signup

Request Body
Field	Type	Required	Description
name	string	Yes	Name of the owner
email	string	Yes	Email of the owner
password	string	Yes	Password of the owner
Response
Success: 201 Created
json
Copy
{
  "message": "Owner created successfully",
  "owner": {
    "name": "John Doe",
    "email": "john@example.com"
  }
}
```

Error: 409 Conflict
json
Copy
{
  "message": "Owner already exists"
}
```

Error: 500 Internal Server Error
json
Copy
{
  "message": "Something went wrong",
  "error": "Error message"
}
```
Owner Login
Authenticate an owner and generate an access token.

Endpoint
POST /login

Request Body
Field	Type	Required	Description
email	string	Yes	Email of the owner
password	string	Yes	Password of the owner
Response
Success: 200 OK
json
Copy
{
  "message": "Owner logged in successfully",
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MSwiZW1haWwiOiJqb2huQGV4YW1wbGUuY29tIiwiaWF0IjoxNTE2MjM5MDIyfQ.3vaHj7Jp9pccV-7T-nLkJJ8vOwHJc5IzjNoy4z-6ZJg"
}
```

Error: 404 Not Found
json
Copy
{
  "message": "Owner not found"
}
```

Error: 401 Unauthorized
json
Copy
{
  "message": "Invalid credentials"
}
```

Error: 500 Internal Server Error
json
Copy
{
  "message": "Something went wrong",
  "error": "Error message"
}
```
Note: The access token returned in the response should be included in the Authorization header of subsequent requests as a bearer token for authentication.

