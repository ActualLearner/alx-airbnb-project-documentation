## Features and Functionalities

### 1. User Management

* **User Registration**
  Users can sign up as guests or hosts.
  Authentication uses secure methods such as JWT (JSON Web Tokens).

* **User Login and Authentication**
  Users can log in via email and password.
  OAuth support (e.g., Google, Facebook) can be included for social logins.

* **Profile Management**
  Users can update profile details such as name, profile photo, contact info, and preferences.

---

### 2. Property Listings Management

* **Add Listings**
  Hosts can create listings with title, description, location, price, amenities, and availability.

* **Edit/Delete Listings**
  Hosts have the ability to update or remove their listings.

---

### 3. Search and Filtering

* Search functionality includes filters for:

  * Location
  * Price range
  * Number of guests
  * Amenities (e.g., Wi-Fi, pool, pet-friendly)
* Pagination is included for navigating large result sets.

---

### 4. Booking Management

* **Booking Creation**
  Guests can book properties for specified dates.
  The system validates dates to prevent double bookings.

* **Booking Cancellation**
  Both guests and hosts can cancel bookings according to the cancellation policy.

* **Booking Status**
  Tracks the state of bookings: `pending`, `confirmed`, `canceled`, or `completed`.

---

### 5. Payment Integration

* Secure payment gateways (e.g., Stripe, PayPal) handle:

  * Guest payments at booking time
  * Automated host payouts after completion
* Supports multi-currency transactions.

---

### 6. Reviews and Ratings

* Guests can leave reviews and 1–5 star ratings for properties.
* Hosts may respond to reviews.
* Reviews are tied to bookings to prevent misuse or spam.

---

### 7. Notifications System

* Sends email and/or in-app notifications for:

  * Booking confirmations
  * Cancellations
  * Payment updates

---

### 8. Admin Dashboard

* Admins can manage:

  * Users
  * Listings
  * Bookings
  * Payments
* Enables oversight and moderation for the platform.
