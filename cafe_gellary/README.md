

# Gellary Cafe
---

## Screenshots

Below are some example screenshots of the application:

| Home Page | Admin Dashboard | Customer Dashboard |
|-----------|----------------|-------------------|
| ![Home](images/Home.png) | ![Admin](admin dash1.avif) | ![Customer](specialitems1.jpeg) |

> _Replace or add more screenshots as needed for your deployment._

---

## API Documentation

### Database Connection
All PHP files use `connection.php` to connect to the MySQL database:

```php
$conn = new mysqli($servername, $username, $password, $dbname);
```

### Example: Fetching Menu Items

```php
// menu.php
$sql = "SELECT * FROM menu_items";
$result = $conn->query($sql);
while ($row = $result->fetch_assoc()) {
   // process $row
}
```

### Example: Inserting a Reservation

```php
$sql = "INSERT INTO reservations (date, time, party_size, table_id, status) VALUES (?, ?, ?, ?, ?)";
$stmt = $conn->prepare($sql);
$stmt->bind_param("ssiss", $date, $time, $party_size, $table_id, $status);
$stmt->execute();
```

### Example: User Authentication

```php
// login-customer.php
$sql = "SELECT * FROM users WHERE email=? AND password=?";
$stmt = $conn->prepare($sql);
$stmt->bind_param("ss", $email, $password);
$stmt->execute();
$result = $stmt->get_result();
```

---

## Usage Examples

### 1. Customer: Place an Order
1. Login as a customer.
2. Go to the [Menu](menu.php) page.
3. Click "Order Now" on your desired item.
4. Complete the order form and submit.

### 2. Admin: Add a Menu Item
1. Login as admin.
2. Go to [Manage Menu](manage-menu.php).
3. Click "Add Item", fill in details, and upload an image.
4. Save to update the menu.

### 3. Make a Reservation
1. Login as a customer.
2. Go to [Make Reservation](make-reservation.php).
3. Fill in the reservation form and submit.
4. View your upcoming reservations in the dashboard.

---

A web-based management and customer portal for Gellary Cafe. This project includes admin, staff, and customer dashboards, menu and order management, reservation system, and promotional features.

---

## Table of Contents
- [Features](#features)
- [Project Structure](#project-structure)
- [User Roles](#user-roles)
- [Database Schema](#database-schema)
- [Technologies Used](#technologies-used)
- [Getting Started](#getting-started)
- [Usage Guide](#usage-guide)
- [Security Notes](#security-notes)
- [License](#license)
- [Author](#author)

---

## Features
- **Admin dashboard**: Manage users, menu, orders, reservations, and promotions
- **Customer dashboard**: View menu, make reservations, place preorders, and view order history
- **Staff dashboard**: Manage parking and assist with orders/reservations
- **Menu management**: Add, edit, and display menu items with images
- **Reservation system**: Book, view, and manage table reservations
- **Order management**: Place and track food orders
- **Promotions**: View and manage special offers
- **Contact/About pages**: Informational pages for users
- **Image/file uploads**: (uploads/ directory, not tracked in git)

---

## Project Structure

```
cafe_gellary/
├── admin-dashboard.php         # Admin dashboard
├── customer-dashboard.php      # Customer dashboard
├── staff.php                   # Staff dashboard
├── menu.php                    # Menu display
├── order.php                   # Order placement
├── make-reservation.php        # Reservation form
├── manage-menu.php             # Admin menu management
├── manage-users.php            # Admin user management
├── manage-promotion.php        # Admin promotion management
├── connection.php              # Database connection
├── cafe (1).sql                # Database schema
├── uploads/                    # Uploaded files (not tracked)
├── images/                     # Images for menu/items
├── ...                         # Other PHP, HTML, and asset files
```

---

## User Roles

- **Admin**: Full access to all management features (users, menu, orders, reservations, promotions, parking)
- **Customer**: Can view menu, make reservations, place orders, and view their own history
- **Staff**: Can manage parking and assist with order/reservation fulfillment

---

## Database Schema

See `cafe (1).sql` for full details. Key tables:

- `users`: Stores user accounts (admin, customer, staff)
- `menu_items`: Menu items with name, price, category, image
- `orders`: Customer orders
- `reservations`: Table reservations
- `adminorders`, `adminreservation`: Admin-level order/reservation tracking
- `parking_slots`: Parking management
- `promotions`: Promotional offers

---

## Technologies Used
- PHP (backend logic)
- HTML, CSS, JavaScript (frontend)
- MySQL (database)

---

## Getting Started

1. **Clone the repository:**
   ```sh
   git clone https://github.com/MohamedKaamil/Gellary_Cafe.git
   ```
2. **Set up a local web server:** (e.g., XAMPP, WAMP, or similar)
3. **Import the database:**
   - Open phpMyAdmin or MySQL CLI
   - Import `cafe (1).sql` to create tables and sample data
4. **Configure database connection:**
   - Edit `connection.php` with your MySQL credentials
5. **Place files in web root:**
   - Copy all files to your web server's root directory (e.g., `htdocs`)
6. **Access the site:**
   - Open your browser and go to `http://localhost/cafe_gellary/`

---

## Usage Guide

- **Admin Login:** Go to `login-admin.php` and use admin credentials
- **Customer Login/Signup:** Use `login-customer.php` or `Signup.php`
- **Menu:** View menu at `menu.php`
- **Order:** Place orders via `order.php`
- **Reservation:** Book tables via `make-reservation.php`
- **Promotions:** View current offers at `promotion.php`
- **Parking:** Staff/admin can manage parking via `parking-admin management.php` and `staff-parking.php`

---

## Security Notes

- Do **not** commit real database credentials or sensitive data
- The `uploads/` directory is ignored by git for privacy and storage reasons
- Large binary files (installers, etc.) are not included due to GitHub's file size limits
- Always validate and sanitize user input in production

---

## License

Specify your license here (e.g., MIT, GPL, etc.)

---

## Author

Mohamed Kaamil
