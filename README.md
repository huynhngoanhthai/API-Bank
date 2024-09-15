
# API-Bank

This repository contains the API endpoints for a banking application. Below are the main API routes and their descriptions.

## Table of Contents

1. [Authentication](#authentication)
2. [Users](#users)
3. [Transactions](#transactions)
4. [Accounts](#accounts)
5. [Goals](#goals)
6. [Budgets](#budgets)
7. [Reports](#reports)

## Authentication

### Google Authentication

- **Endpoint**: `/auth-google`
- **Method**: POST
- **Description**: Authenticates a user using Google Sign-In.
- **Required Fields**: `id_token`

Example request:
```json
{
  "id_token": "eyJhbGciOiJSUzI1NiIsImtpZCI6IjFiZDY4NWY1ZThmYzYyZDc3ZTAyZjE3NTJjNDM0NDM3OWZiYjA3NDMiLCJ0eXAiOiJKV1QifQ..."
}
```

Example response:
```json
{
  "result": 1,
  "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "data": {
    "id": 1,
    "email": "user@example.com",
    "firstname": "John",
    "lastname": "Doe"
  },
  "msg": "Login is success!"
}
```

## Users

### Get All Users

- **Endpoint**: `/users`
- **Method**: GET
- **Description**: Retrieves all users (Admin only).

Example response:
```json
{
  "result": 1,
  "data": [
    {
      "id": 1,
      "email": "user1@example.com",
      "firstname": "John",
      "lastname": "Doe",
      "account_type": "regular",
      "is_active": true,
      "date": "2023-05-20 10:00:00"
    },
    {
      "id": 2,
      "email": "user2@example.com",
      "firstname": "Jane",
      "lastname": "Smith",
      "account_type": "admin",
      "is_active": true,
      "date": "2023-05-21 11:00:00"
    }
  ]
}
```

### Create New User

- **Endpoint**: `/users`
- **Method**: POST
- **Description**: Creates a new user (Admin only).
- **Required Fields**: `email`, `firstname`, `lastname`, `account_type`

Example request:
```json
{
  "email": "newuser@example.com",
  "firstname": "New",
  "lastname": "User",
  "account_type": "regular"
}
```

Example response:
```json
{
  "result": 1,
  "msg": "User added successfully! Please refresh the page."
}
```

### Get User by ID

- **Endpoint**: `/user/{id}`
- **Method**: GET
- **Description**: Retrieves a specific user by ID (Admin only).

Example response:
```json
{
  "result": 1,
  "data": {
    "id": 1,
    "email": "user@example.com",
    "firstname": "John",
    "lastname": "Doe",
    "account_type": "regular",
    "is_active": true,
    "date": "2023-05-20 10:00:00"
  }
}
```

### Update User

- **Endpoint**: `/user/{id}`
- **Method**: PUT
- **Description**: Updates a specific user (Admin only).
- **Required Fields**: `firstname`, `lastname`, `account_type`

Example request:
```json
{
  "firstname": "John",
  "lastname": "Updated",
  "account_type": "admin",
  "is_active": true
}
```

Example response:
```json
{
  "result": 1,
  "msg": "User updated successfully!"
}
```

### Delete User

- **Endpoint**: `/user/{id}`
- **Method**: DELETE
- **Description**: Deactivates a specific user (Admin only).

Example response:
```json
{
  "result": 1,
  "user": 1,
  "msg": "This user is deactivated!"
}
```

## Transactions

### Get All Transactions

- **Endpoint**: `/transactions`
- **Method**: GET
- **Description**: Retrieves all transactions for the authenticated user.

Example response:
```json
{
  "result": 1,
  "data": [
    {
      "id": 1,
      "account_id": 1,
      "category_id": 2,
      "amount": 100.00,
      "type": 1,
      "name": "Salary",
      "description": "Monthly salary",
      "transactiondate": "2023-05-01",
      "account": {
        "id": 1,
        "name": "Main Account"
      },
      "category": {
        "id": 2,
        "name": "Income",
        "type": 1,
        "color": "#00FF00",
        "description": "Income category"
      }
    }
  ]
}
```

### Create New Transaction

- **Endpoint**: `/transactions`
- **Method**: POST
- **Description**: Creates a new transaction.
- **Required Fields**: `category_id`, `account_id`, `amount`, `type`, `transactiondate`

Example request:
```json
{
  "category_id": 2,
  "account_id": 1,
  "amount": 100.00,
  "type": 1,
  "name": "Salary",
  "description": "Monthly salary",
  "transactiondate": "2023-05-01"
}
```

Example response:
```json
{
  "result": 1,
  "msg": "Transaction added successfully!"
}
```

### Get Transaction by ID

- **Endpoint**: `/transaction/{id}`
- **Method**: GET
- **Description**: Retrieves a specific transaction by ID.

Example response:
```json
{
  "result": 1,
  "data": {
    "id": 1,
    "account_id": 1,
    "category_id": 2,
    "amount": 100.00,
    "type": 1,
    "name": "Salary",
    "description": "Monthly salary",
    "transactiondate": "2023-05-01",
    "account": {
      "id": 1,
      "name": "Main Account"
    },
    "category": {
      "id": 2,
      "name": "Income",
      "type": 1,
      "color": "#00FF00",
      "description": "Income category"
    }
  }
}
```

### Update Transaction

- **Endpoint**: `/transaction/{id}`
- **Method**: PUT
- **Description**: Updates a specific transaction.
- **Required Fields**: `category_id`, `account_id`, `amount`, `type`, `transactiondate`

Example request:
```json
{
  "category_id": 2,
  "account_id": 1,
  "amount": 150.00,
  "type": 1,
  "name": "Updated Salary",
  "description": "Updated monthly salary",
  "transactiondate": "2023-05-01"
}
```

Example response:
```json
{
  "result": 1,
  "msg": "Transaction updated successfully!"
}
```

### Delete Transaction

- **Endpoint**: `/transaction/{id}`
- **Method**: DELETE
- **Description**: Deletes a specific transaction.

Example response:
```json
{
  "result": 1,
  "msg": "Transaction deleted successfully!"
}
```

## Accounts

(Similar structure to Transactions, detailing endpoints for GET all, POST new, GET by ID, PUT update, and DELETE)

## Goals

(Similar structure to Transactions, detailing endpoints for GET all, POST new, GET by ID, PUT update, and DELETE)

## Budgets

(Similar structure to Transactions, detailing endpoints for GET all, POST new, GET by ID, PUT update, and DELETE)

## Reports

### Get Category Monthly Report

- **Endpoint**: `/report/category-monthly`
- **Method**: GET
- **Description**: Retrieves monthly report grouped by categories.

Example response:
```json
{
  "result": 1,
  "data": {
    "total": 1000.00,
    "categories": [
      {
        "id": 1,
        "name": "Food",
        "color": "#FF0000",
        "total": 300.00
      },
      {
        "id": 2,
        "name": "Transportation",
        "color": "#00FF00",
        "total": 200.00
      }
    ],
    "monthly": [
      {
        "month": "2023-05",
        "categories": [
          {
            "id": 1,
            "total": 150.00
          },
          {
            "id": 2,
            "total": 100.00
          }
        ]
      }
    ]
  }
}
```

### Get Account Transactions Report

- **Endpoint**: `/report/account-transactions`
- **Method**: GET
- **Description**: Retrieves transactions report for a specific account.
- **Query Parameters**: `account`, `fromdate`, `todate`

Example request:
```
GET /report/account-transactions?account=1&fromdate=2023-05-01&todate=2023-05-31
```

Example response:
```json
{
  "result": 1,
  "data": [
    {
      "id": 1,
      "account_id": 1,
      "category_id": 2,
      "amount": 100.00,
      "type": 1,
      "name": "Salary",
      "description": "Monthly salary",
      "transactiondate": "2023-05-01",
      "category": {
        "id": 2,
        "name": "Income",
        "type": 1,
        "color": "#00FF00",
        "description": "Income category"
      }
    }
  ]
}
```

This README provides an overview of the main API endpoints in your banking application. You may want to add more details, such as authentication requirements, error responses, and any specific business logic or constraints for each endpoint.

This README.md file provides a comprehensive overview of the API endpoints in your banking application. It includes sections for Authentication, Users, Transactions, Accounts, Goals, Budgets, and Reports. Each section describes the available endpoints, their methods, required fields, and provides example requests and responses.

You can further customize this README by adding more specific details about your application, such as:

1. Installation instructions
2. Environment setup
3. Database schema
4. Authentication and authorization details
5. Rate limiting information
6. Error handling and common error codes
7. Versioning strategy
8. Changelog

Remember to keep this documentation up-to-date as you make changes to your API.
