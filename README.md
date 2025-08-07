# Pet Project Plan: Marketplace

## Project Initialization

- Create a **Koa** application.
- Set up PostgreSQL connection using **TypeORM**.
- Create models for **Users**, **Transactions** and **Products**.

## Models Schema

### Users Model

| Field        | Type     | Description                     |
|--------------|----------|---------------------------------|
| id           | UUID     | Unique identifier               |
| email        | string   | User's email address            |
| password     | string   | Hashed password                 |
| transactions | UUID[]   | List of transaction IDs         |

### Products Model

| Field       | Type     | Description                      |
|-------------|----------|----------------------------------|
| id          | UUID     | Unique identifier                |
| name        | string   | Product name                     |
| description | string   | Product description              |
| price       | number   | Product price                    |
| fileKey     | string   | S3 file key or file reference    |

### Transactions Model

| Field          | Type     | Description                           |
|----------------|----------|---------------------------------------|
| transactionId  | UUID     | Unique transaction identifier         |
| userId         | UUID     | ID of the user who made the purchase  |
| userCardId     | string   | ID of the user's card used for payment|
| products       | UUID[]   | List of product IDs included          |
| date           | DateTime | Date and time of the transaction      |

## User Registration and Authentication

- Implement basic user registration and login (JWT can be used).

## Payment Processing

- Integrate **Stripe** as the payment processor.
- Handle payment flows for purchases within the marketplace.
- Use Stripe Connect if supporting multiple vendors.

## Working with Products

- Implement **CRUD** operations for products with the following fields:
  - Name
  - Description
  - Price
  - Link to file in **S3**

- Upload files using **pre-signed URLs**.

## Pre-signed URL Generation

- Create an endpoint that generates a temporary URL for direct file upload to **S3**.

## Displaying Products

- Create an endpoint to retrieve a list of products with download links.
