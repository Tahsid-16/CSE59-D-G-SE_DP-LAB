# Software Requirements Specification (SRS)

# EasyBuy Grocery Shopping System

---

# Preface

This document provides the Software Requirements Specification (SRS) for the **EasyBuy Grocery Shopping System**. It defines the system functionalities, database structure, user requirements, and overall architecture required for development and deployment.

---

# Version History

- **Version 1.0** – Initial Draft
- **Version 1.1** – Added database and ER diagram section
- **Version 1.2** – Refined functional and non-functional requirements

---

# 1. Introduction

## Purpose

The **EasyBuy Grocery Shopping System** is a desktop-based shopping application designed to simplify online grocery purchasing. The system allows users to browse products, manage carts, place orders, and track purchases efficiently.

The application also provides secure user authentication and order management using a MySQL database backend connected through JDBC.

---

## Document Conventions

This document follows IEEE SRS conventions:

- **Must** – Mandatory requirement
- **Should** – Recommended requirement
- **May** – Optional enhancement

---

## Intended Audience and Reading Suggestions

- **Developers** – For implementation guidance
- **Database Designers** – For database and ER design
- **Testers** – For requirement validation
- **Course Instructor** – For project evaluation

---

## Scope

The EasyBuy system provides:

- User registration and login
- Product browsing
- Shopping cart management
- Wishlist functionality
- Order placement
- Order history tracking
- Database integration using JDBC and MySQL

---

## References

- IEEE SRS Documentation Standard
- Java Swing Documentation
- JDBC API Documentation
- MySQL Documentation

---

# 2. Overall Description

## Product Perspective

EasyBuy is a standalone Java desktop application developed using:

- Java Swing (Frontend UI)
- JDBC (Database Connectivity)
- MySQL/XAMPP (Backend Database)

---

## Product Functions

### User Management

- Register new users
- Secure login authentication
- Edit profile information
- Update phone number

### Product Management

- Display available grocery products
- Show product images and prices
- Search products

### Cart Management

- Add products to cart
- Remove products from cart
- Update product quantity

### Wishlist Management

- Add/remove products to wishlist

### Order Management

- Checkout products
- Store order history
- View previous orders

---

## User Classes and Characteristics

### Admin

- Manages products and database

### Customer/User

- Purchases products
- Manages cart and wishlist
- Views order history

---

## Operating Environment

- Windows Operating System
- Java JDK
- Apache NetBeans IDE
- XAMPP MySQL Server

---

## Design and Implementation Constraints

- Requires MySQL database connection
- Requires JDBC driver dependency
- Desktop-only implementation

---

## Assumptions and Dependencies

- XAMPP MySQL server must be running
- JDBC driver must be included
- Product images must exist in resources folder

---

# 3. System Requirements Specification

# Functional Requirements

## User Authentication

- The system must allow users to register
- The system must allow secure login using email and password
- Passwords must be stored as hashed values

---

## Product Browsing

- Users must be able to view all products
- Users must be able to search products by name

---

## Shopping Cart

- Users must be able to add products to cart
- Users must be able to remove products
- The system must calculate total price automatically

---

## Wishlist

- Users must be able to add products to wishlist
- Users must be able to remove wishlist items

---

## Order Management

- Users must be able to place orders
- The system must store order details in database
- Users must be able to view previous orders

---

# Non-Functional Requirements

## Performance Requirements

- Product loading should occur within 2 seconds
- Database operations should be efficient

---

## Security Requirements

- Passwords must be encrypted using SHA-256 hashing
- SQL Injection must be prevented using PreparedStatement

---

## Usability Requirements

- The interface should be simple and user-friendly
- The application should support dark theme UI

---

## Reliability and Availability

- Database transactions must maintain consistency
- Orders must not be lost during checkout

---

## Maintainability

- Code should follow modular design
- Separate MVC architecture should be maintained

---

## Portability

- The system should run on all systems supporting Java

---

# 4. System Models

## CONTEXT DIAGRAM

The EasyBuy system interacts with:

- Users
- MySQL Database
- Product Storage

---

## USE CASES

### User Use Cases

- Register
- Login
- Browse Products
- Add to Cart
- Add to Wishlist
- Checkout
- View Orders

---

# ENTITY RELATIONSHIP (ER) DIAGRAM

## Entities

### USERS

| Attribute | Description |
|---|---|
| id | Primary Key |
| name | User name |
| email | User email |
| password_hash | Encrypted password |
| payment_method | Payment type |
| phone_number | User phone number |

---

### PRODUCTS

| Attribute | Description |
|---|---|
| id | Primary Key |
| name | Product name |
| price | Product price |
| image_path | Product image |

---

### ORDERS

| Attribute | Description |
|---|---|
| id | Primary Key |
| user_id | Foreign Key from users |
| order_date | Order timestamp |
| total_amount | Total order price |
| status | Order status |

---

### ORDER_ITEMS

| Attribute | Description |
|---|---|
| id | Primary Key |
| order_id | Foreign Key from orders |
| product_id | Foreign Key from products |
| quantity | Product quantity |
| unit_price | Product price during purchase |

---

## Relationships

- One User can place many Orders
- One Order can contain many Products
- One Product can exist in many Order Items

---

## ER Diagram Structure

```text
USERS
  |
  | 1 ---- ∞
  |
ORDERS
  |
  | 1 ---- ∞
  |
ORDER_ITEMS
  |
  | ∞ ---- 1
  |
PRODUCTS
