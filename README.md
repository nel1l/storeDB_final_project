# storeDB_final_project
here my final project is located for adb

# Backend Project: E-Commerce API

## Table of Contents
- [Project Overview](#project-overview)
- [Features](#features)
- [Technologies Used](#technologies-used)
- [Database Schema](#database-schema)
- [Setup and Installation](#setup-and-installation)
- [API Endpoints](#api-endpoints)
- [Authentication & Authorization](#authentication--authorization)
- [Indexes & Query Optimization](#indexes--query-optimization)
- [Future Improvements](#future-improvements)

## Project Overview
This project is a backend API for an e-commerce platform that allows users to register, browse products, and place orders. Admin users can manage products and view all orders.

## Features
- User authentication with JWT
- Role-based authorization (Admin & User)
- Product management (CRUD operations)
- Order management
- Secure password storage (bcrypt)
- MongoDB indexing for optimized queries

## Technologies Used
- **Node.js** & **Express.js** for backend logic
- **MongoDB & Mongoose** for database operations
- **JWT** for authentication
- **bcrypt** for password hashing
- **dotenv** for environment variables
- **Postman** for API testing

## Database Schema
The application consists of three main collections:
1. **Users**
   ```json
   {
      "_id": "ObjectId",
      "name": "string",
      "email": "string",
      "password": "string",
      "isAdmin": "True | False"
   }
   ```
2. **Products**
   ```json
   {
      "_id": "ObjectId",
      "name": "string",
      "url": "string",
      "price": "number",
      "color": "string",
      "details": "string"
   }
   ```
3. **Orders**
   ```json
   {
      "_id": "ObjectId",
      "userId": "ObjectId",
      "products": [{ "productId": "ObjectId", "quantity": "number" }],
      "status": "pending | shipped | delivered"
   }
   ```

## Setup and Installation
### Prerequisites
- Node.js installed
- MongoDB running locally or using a cloud database (MongoDB Atlas)

### Installation Steps
1. Clone the repository:
   ```sh
   git clone <repository-url>
   ```
2. Navigate into the project directory:
   ```sh
   cd backend-project
   ```
3. Install dependencies:
   ```sh
   npm install
   ```
4. Create a `.env` file and configure environment variables:
   ```sh
   MONGO_URI=<your-mongodb-uri>
   JWT_SECRET=<your-secret-key>
   ```
5. Start the server:
   ```sh
   npm start
   ```

Also, to check API endpoints, I used the Postman program. Below are all the commands that can be run when using Postman.

## API Endpoints
### Authentication
- **Register a new user**: `POST /api/auth/register`
- **Login user**: `POST /api/auth/login`

### Products
- **Create a product (Admin only)**: `POST /api/products`
- **Get all products**: `GET /api/products`
- **Update a product (Admin only)**: `PUT /api/products/:id`
- **Delete a product (Admin only)**: `DELETE /api/products/:id`

### Orders
- **Create an order**: `POST /api/orders`
- **Get all orders (Admin only)**: `GET /api/orders`
- **Get user orders (Admin only)**: `GET /api/orders/user`
- **Delete an order (Admin only)**: `DELETE /api/orders/:id`

## Authentication & Authorization
- JWT-based authentication is used.
- Admin routes are protected with role-based access control.

## Indexes & Query Optimization
Indexes were added to optimize database queries:
- `UserSchema.index({ email: 1 }, { unique: true });` (Fast email lookup)
- `ProductSchema.index({ name: 1 });` (Quick search by product name)
- `OrderSchema.index({ userId: 1 });` (Faster retrieval of user orders)

## Future Improvements
- Implement order history tracking
- Add payment gateway integration
- Enhance product search with filtering and sorting

