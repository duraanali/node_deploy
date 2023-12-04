# API Documentation

## Owner Sign Up

Create a new owner account.

### Endpoint

`POST /signup`

### Request Body

| Field   | Type   | Required | Description           |
|---------|--------|----------|-----------------------|
| name    | string | Yes      | Name of the owner     |
| email   | string | Yes      | Email of the owner    |
| password| string | Yes      | Password of the owner |

### Response

- **Success**: 201 Created
  ````json
  {
    "message": "Owner created successfully",
    "owner": {
      "name": "John Doe",
      "email": "john@example.com"
    }
  }
  

- **Error**: 409 Conflict
  ````json
  {
    "message": "Owner already exists"
  }
  

- **Error**: 500 Internal Server Error
  ````json
  {
    "message": "Something went wrong",
    "error": "Error message"
  }
  

## Owner Login

Authenticate an owner and generate an access token.

### Endpoint

`POST /login`

### Request Body

| Field   | Type   | Required | Description           |
|---------|--------|----------|-----------------------|
| email   | string | Yes      | Email of the owner    |
| password| string | Yes      | Password of the owner |

### Response

- **Success**: 200 OK
  ````json
  {
    "message": "Owner logged in successfully",
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MSwiZW1haWwiOiJqb2huQGV4YW1wbGUuY29tIiwiaWF0IjoxNTE2MjM5MDIyfQ.3vaHj7Jp9pccV-7T-nLkJJ8vOwHJc5IzjNoy4z-6ZJg"
  }
  

- **Error**: 404 Not Found
  ````json
  {
    "message": "Owner not found"
  }


- **Error**: 401 Unauthorized
  ````json
  {
    "message": "Invalid credentials"
  }
  

- **Error**: 500 Internal Server Error
  ````json
  {
    "message": "Something went wrong",
    "error": "Error message"
  }
  

Note: The access token returned in the response should be included in the `Authorization` header of subsequent requests as a bearer token for authentication.

# Ratings

## Get All Ratings

Retrieve all ratings.

### Endpoint

`GET /`

### Response

- **Success**: 200 OK
  ````json
  [
    {
      "id": 1,
      "rating": 4.5,
      "comment": "Great product"
    },
    {
      "id": 2,
      "rating": 3.8,
      "comment": "Average product"
    }
  ]
  

- **Error**: 404 Not Found
  ````json
  {
    "message": "ratings not found"
  }
  

- **Error**: 500 Internal Server Error
  ````json
  {
    "message": "Failed to get ratings"
  }
  

## Get Single Rating

Retrieve a single rating by ID.

### Endpoint

`GET /:id`

### Parameters

| Parameter | Type   | Description    |
|-----------|--------|----------------|
| id        | number | ID of the rating |

### Response

- **Success**: 200 OK
  ````json
  {
    "id": 1,
    "rating": 4.5,
    "comment": "Great product"
  }
  

- **Error**: 404 Not Found
  ````json
  {
    "message": "rating not found"
  }
  

- **Error**: 500 Internal Server Error
  ````json
  {
    "message": "Failed to get rating"
  }
  

## Add Rating

Add a new rating.

### Endpoint

`POST /`

### Request Body

| Field   | Type   | Required | Description            |
|---------|--------|----------|------------------------|
| rating  | number | Yes      | Rating value (1-5)     |
| comment | string | No       | Additional# API Documentation

## Get All Ratings

Retrieve all ratings.

### Endpoint

`GET /`

### Response

- **Success**: 200 OK
  ````json
  [
    {
      "id": 1,
      "rating": 4.5,
      "comment": "Great product"
    },
    {
      "id": 2,
      "rating": 3.8,
      "comment": "Average product"
    }
  ]
  

- **Error**: 404 Not Found
  ````json
  {
    "message": "ratings not found"
  }
  

- **Error**: 500 Internal Server Error
  ````json
  {
    "message": "Failed to get ratings"
  }
  

## Get Single Rating

Retrieve a single rating by ID.

### Endpoint

`GET /:id`

### Parameters

| Parameter | Type   | Description    |
|-----------|--------|----------------|
| id        | number | ID of the rating |

### Response

- **Success**: 200 OK
  ````json
  {
    "id": 1,
    "rating": 4.5,
    "comment": "Great product"
  }
  

- **Error**: 404 Not Found
  ````json
  {
    "message": "rating not found"
  }
  

- **Error**: 500 Internal Server Error
  ````json
  {
    "message": "Failed to get rating"
  }

## Add Rating

Add a new rating.

### Endpoint

`POST /`

### Request Body

| Field   | Type   | Required | Description            |
|---------|--------|----------|------------------------|
| rating  | number | Yes      | Rating value (1-5)     |
| comment | string | No       | Additional comments     |

### Response

- **Success**: 201 Created
  ````json
  {
    "id": 3,
    "rating": 4.2,
    "comment": "Good product"
  }
 

- **Error**: 404 Not Found
  ````json
  {
    "message": "rating not found"
  }
 

- **Error**: 500 Internal Server Error
  ````json
  {
    "message": "Failed to add rating"
  }
 

## Update Rating

Update an existing rating.

### Endpoint

`PUT /:id`

### Parameters

| Parameter | Type   | Description    |
|-----------|--------|----------------|
| id        | number | ID of the rating |

### Request Body

| Field   | Type   | Required | Description            |
|---------|--------|----------|------------------------|
| rating  | number | Yes      | Updated rating value   |
| comment | string | No       | Updated comments       |

### Response

- **Success**: 200 OK
  ````json
  {
    "id": 3,
    "rating": 4.0,
    "comment": "Updated rating"
  }
  

- **Error**: 404 Not Found
  ````json
  {
    "message": "rating not found"
  }
  

- **Error**: 500 Internal Server Error
  ````json
  {
    "message": "Failed to update rating"
  }
  

## Delete Rating

Delete a rating.

### Endpoint

`DELETE /:id`

### Parameters

| Parameter | Type   | Description    |
|-----------|--------|----------------|
| id        | number | ID of the rating |

### Response

- **Success**: 200 OK
  ````json
  {
    "message": "rating deleted"
  }
  

- **Error**: 404 Not Found
  ````json
  {
    "message": "rating not found"
  }
  

- **Error**: 500 Internal Server Error
  ````json
  {
    "message": "Failed to delete rating"
  }
  
  
# Restaurant  


## Endpoints

### Get All Restaurants

Retrieves a list of all restaurants.

- Method: GET
- URL: `/`
- Response:
  - Status: 200 OK
  - Body: JSON array containing a list of restaurants
- Error Responses:
  - Status: 404 Not Found
    - Body: `{ "message": "restaurants not found" }`
  - Status: 500 Internal Server Error
    - Body: `{ "message": "Failed to get restaurants" }`

### Get Single Restaurant

Retrieves a single restaurant by its ID.

- Method: GET
- URL: `/:id`
- Parameters:
  - `id` (number): ID of the restaurant
- Response:
  - Status: 200 OK
  - Body: JSON object representing the restaurant
- Error Responses:
  - Status: 404 Not Found
    - Body: `{ "message": "restaurant not found" }`
  - Status: 500 Internal Server Error
    - Body: `{ "message": "Failed to get restaurant" }`

### Get Restaurants by Owner ID

Retrieves a list of restaurants owned by a specific owner.

- Method: GET
- URL: `/owner/:id`
- Parameters:
  - `id` (number): ID of the owner
- Response:
  - Status: 200 OK
  - Body: JSON array containing a list of restaurants
- Error Responses:
  - Status: 404 Not Found
    - Body: `{ "message": "restaurant not found" }`
  - Status: 500 Internal Server Error
    - Body: `{ "message": "Failed to get restaurant" }`

### Add Restaurant

Adds a new restaurant.

- Method: POST
- URL: `/`
- Request Body: JSON object representing the restaurant
- Authentication Required: Yes (provide authentication token in the request headers)
- Response:
  - Status: 201 Created
  - Body: JSON object representing the added restaurant
- Error Responses:
  - Status: 404 Not Found
    - Body: `{ "message": "restaurant not found" }`
  - Status: 500 Internal Server Error
    - Body: `{ "message": "Failed to add restaurant" }`

### Update Restaurant

Updates an existing restaurant by its ID.

- Method: PUT
- URL: `/:id`
- Parameters:
  - `id` (number): ID of the restaurant
- Request Body: JSON object containing the updated restaurant data
- Authentication Required: Yes (provide authentication token in the request headers)
- Response:
  - Status: 200 OK
  - Body: JSON object representing the updated restaurant
- Error Responses:
  - Status: 404 Not Found
    - Body: `{ "message": "restaurant not found" }`
  - Status: 500 Internal Server Error
    - Body: `{ "message": "Failed to update restaurant" }`

### Delete Restaurant

Deletes a restaurant by its ID.

- Method: DELETE
- URL: `/:id`
- Parameters:
  - `id` (number): ID of the restaurant
- Authentication Required: Yes (provide authentication token in the request headers)
- Response:
  - Status: 200 OK
  - Body: `{ "message": "restaurant deleted" }`
- Error Responses:
  - Status: 404 Not Found
    - Body: `{ "message": "restaurant not found" }`
  - Status: 500 Internal Server Error
    - Body: `{ "message": "Failed to delete restaurant" }`

Note: Replace `authenticate` with your preferred authentication middleware or logic.

Please refer to the relevant API documentation for more details on making requests to these endpoints.
