# Res2Ran Server

This project is a comprehensive restaurant management platform built on Node.js and Express. It integrates MongoDB for data storage, Stripe for payment processing, and JWT for user authentication. The system facilitates user and admin functionalities such as user management, menu control, reviews, carts, payments, and admin analytics.

### Installation Process:

To install and run the project locally, follow these steps:

1.  Clone the repository.
2.  Run `npm install` to install dependencies.
3.  Set up environment variables in a `.env` file with necessary configurations (e.g., PORT, DB_USER, DB_PASSWORD, PAYMENT_SECRET_KEY, ACCESS_TOKEN).
4.  Ensure MongoDB is running and accessible.
5.  Run `npm start` to start the server.
6.  Access the endpoints using a tool like Postman or integrate them into your front-end application.

### API Documentation:


### Authentication

#### Generate JWT Token

-   **POST /jwt**
    -   **Description:** Generates a JSON Web Token (JWT) for user authentication.
    -   **Request Body:** Expects user details to create a token.
        
        
        `{
          "email": "user@example.com",
          "password": "securepassword"
        }` 
        
    -   **Response:** Returns a JWT token for authorized access.

### User Management

#### Retrieve All Users

-   **GET /users**
    -   **Description:** Retrieves all users registered in the system. (_Admin access required_)

#### Register New User

-   **POST /users**
    -   **Description:** Registers a new user in the system.
    -   **Request Body:** Requires user details for registration.
        
        
        `{
          "email": "newuser@example.com",
          "password": "newuserpassword",
          "name": "New User",
          "role": "customer"
        }` 
        
    -   **Response:** Returns the registration status.

#### Check Admin Status

-   **GET /users/admin/:email**
    -   **Description:** Checks if the specified user has admin privileges.
    -   **Request:** Requires the email of the user to be checked.
    -   **Response:** Returns whether the user has admin access.

#### Upgrade User to Admin

-   **PATCH /users/admin/:id**
    -   **Description:** Upgrades a user to admin status.
    -   **Request:** Requires the user ID to perform the upgrade.
    -   **Response:** Returns the status of the admin upgrade.

### Menu Management

#### Get Entire Menu

-   **GET /menu**
    -   **Description:** Retrieves the complete menu of available items.

#### Add Item to Menu

-   **POST /menu**
    -   **Description:** Adds a new item to the menu. (_Admin access required_)
    -   **Request Body:** Expects details of the new menu item.
        
        
        `{
          "name": "New Item",
          "category": "Main Course",
          "price": 15.99,
          "description": "Description of the new menu item"
        }` 
        
    -   **Response:** Returns the status of the item addition.

#### Remove Item from Menu

-   **DELETE /menu/:id**
    -   **Description:** Removes a menu item by its ID. (_Admin access required_)
    -   **Request:** Requires the ID of the item to be deleted.
    -   **Response:** Returns the status of the item deletion.

### Reviews

#### Get All Reviews

-   **GET /reviews**
    -   **Description:** Retrieves all reviews available in the system.

### Cart Operations

#### Get User's Cart

-   **GET /carts**
    -   **Description:** Retrieves items in the user's cart. (_Authenticated user access required_)

#### Add Item to Cart

-   **POST /carts**
    -   **Description:** Adds an item to the user's cart.
    -   **Request Body:** Requires the details of the item to be added.
        
        
        `{
          "itemId": "itemID",
          "quantity": 2
        }` 
        
    -   **Response:** Returns the status of the item addition to the cart.

#### Remove Item from Cart

-   **DELETE /carts/:id**
    -   **Description:** Removes an item from the user's cart by its ID.
    -   **Request:** Requires the ID of the item to be removed.
    -   **Response:** Returns the status of the item removal from the cart.

### Payments

#### Create Payment Intent

-   **POST /create-payment-intent**
    -   **Description:** Creates a payment intent for a transaction.
    -   **Request Body:** Requires details for the payment intent.
        
        
        `{
          "price": 50.99
        }` 
        
    -   **Response:** Returns the client secret for payment processing.

#### Record Payment and Clear Cart

-   **POST /payments**
    -   **Description:** Records payment details and clears cart items.
    -   **Request Body:** Expects payment and cart information.
        
        
        `{
          "paymentId": "paymentID",
          "cartItems": ["itemID1", "itemID2"],
          "price": 50.99
        }` 
        
    -   **Response:** Returns the status of payment recording and cart clearance.

### Admin Analytics

#### Get Admin Statistics

-   **GET /admin-stats**
    -   **Description:** Retrieves statistics on users, products, orders, and revenue. (_Admin access required_)

#### Aggregate Order Statistics

-   **GET /order-stats**
    -   **Description:** Aggregates data on orders categorized by menu item types. (_Admin access required_)

Ensure proper authentication headers are included for protected routes and appropriate role permissions are granted for accessing admin functionalities. The server runs on the specified port and connects to MongoDB for data management.
