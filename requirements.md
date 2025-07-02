# Backend Requirements Specification – Airbnb Clone

This document defines the technical and functional specifications for core backend features of the Airbnb Clone project. Each section includes a feature overview, API design, input/output structure, validation logic, and performance considerations.

---

## 1. User Authentication

### 🎯 Objective
Allow users (Guests, Hosts, Admins) to register, log in, and authenticate via secure methods.

### 🔌 Endpoints

| Method | Endpoint         | Description           |
|--------|------------------|-----------------------|
| POST   | `/api/register`  | Register a new user   |
| POST   | `/api/login`     | Authenticate a user   |

### 📥 Input Specifications

#### `/api/register`

```json
{
  "first_name": "John",
  "last_name": "Doe",
  "email": "john@example.com",
  "password": "StrongPassword123",
  "phone_number": "555-1234",
  "role": "guest"
}
````

#### `/api/login`

```json
{
  "email": "john@example.com",
  "password": "StrongPassword123"
}
```

### 📤 Output Specifications

```json
{
  "token": "jwt-token-string",
  "user": {
    "user_id": "uuid-string",
    "first_name": "John",
    "role": "guest"
  }
}
```

### ✅ Validation Rules

* Email must be unique and valid.
* Password must meet complexity requirements (min 8 chars, 1 uppercase, 1 number).
* Role must be one of: `guest`, `host`, `admin`.

### ⚙️ Performance

* Token generation under 200ms.
* Use bcrypt for password hashing and JWT for session management.

---

## 2. Property Management

### 🎯 Objective

Enable hosts to list, update, and manage properties for booking.

### 🔌 Endpoints

| Method | Endpoint              | Description             |
| ------ | --------------------- | ----------------------- |
| POST   | `/api/properties`     | Create a new property   |
| GET    | `/api/properties`     | Retrieve all properties |
| GET    | `/api/properties/:id` | Retrieve property by ID |
| PUT    | `/api/properties/:id` | Update a property       |
| DELETE | `/api/properties/:id` | Delete a property       |

### 📥 Input Example (POST)

```json
{
  "name": "Seaside Villa",
  "description": "Beautiful beachside home.",
  "location": "Malibu",
  "pricepernight": 250.00
}
```

### 📤 Output Example

```json
{
  "property_id": "uuid-string",
  "name": "Seaside Villa",
  "host_id": "uuid-host-id",
  "created_at": "timestamp"
}
```

### ✅ Validation Rules

* All fields required except description.
* Price must be positive decimal.
* Only authenticated hosts can create/update/delete listings.

### ⚙️ Performance

* Listings retrieval with pagination (`limit`/`offset`).
* Indexed by `location`, `price`, `created_at`.

---

## 3. Booking System

### 🎯 Objective

Allow guests to book properties, view status, and manage bookings.

### 🔌 Endpoints

| Method | Endpoint            | Description              |
| ------ | ------------------- | ------------------------ |
| POST   | `/api/bookings`     | Create a new booking     |
| GET    | `/api/bookings`     | List bookings for user   |
| PUT    | `/api/bookings/:id` | Cancel or update booking |

### 📥 Input Example (POST)

```json
{
  "property_id": "uuid-string",
  "start_date": "2025-08-01",
  "end_date": "2025-08-05"
}
```

### 📤 Output Example

```json
{
  "booking_id": "uuid-string",
  "status": "pending",
  "total_price": 1000.00
}
```

### ✅ Validation Rules

* Dates must be in the future and not overlapping existing bookings.
* Total price = price per night × number of nights.
* Only authenticated users may book.

### ⚙️ Performance

* Use composite index on `property_id`, `start_date`, `end_date`.
* Booking creation time under 500ms with conflict validation.

---

## 📁 File Info

* **File name**: `requirements.md`
* **Directory**: `/` (project root)
* **Repository**: `alx-airbnb-project-documentation`

---

## 📌 Notes

* Future features (e.g., reviews, messaging, notifications) can be added using this same format.
* All endpoints assume token-based authentication using JWT.

```
