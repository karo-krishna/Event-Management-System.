# ⚡ EventPro — Event Management System
### Full-Stack Web Application | React + PHP + MySQL

---

## 📋 Project Overview

EventPro is a **production-level Event Management System** built as a Final Year Web Technologies project. It features a modern glassmorphism UI, secure JWT authentication, full CRUD event management, a real-time ticketing system, and role-based admin/user dashboards.

---

## 🗂️ Project Structure

```
eventpro/
├── frontend/               ← React JS Application
│   ├── public/
│   │   └── index.html
│   ├── src/
│   │   ├── components/
│   │   │   ├── Navbar.jsx         ← Top navigation bar
│   │   │   ├── Sidebar.jsx        ← Role-based sidebar
│   │   │   ├── EventCard.jsx      ← Reusable event card
│   │   │   └── BookingModal.jsx   ← Ticket booking modal
│   │   ├── pages/
│   │   │   ├── HomePage.jsx       ← Hero, search, featured events
│   │   │   ├── EventsPage.jsx     ← Events listing with filters
│   │   │   ├── EventDetail.jsx    ← Single event + booking
│   │   │   ├── Dashboard.jsx      ← Admin & User dashboards
│   │   │   ├── CreateEvent.jsx    ← Admin: create event
│   │   │   ├── EditEvent.jsx      ← Admin: edit event
│   │   │   ├── AttendeesPage.jsx  ← Attendee management
│   │   │   ├── ReportsPage.jsx    ← Reports + CSV export
│   │   │   ├── LoginPage.jsx      ← Authentication
│   │   │   ├── RegisterPage.jsx   ← Registration
│   │   │   └── NotFound.jsx       ← 404 page
│   │   ├── context/
│   │   │   ├── AuthContext.jsx    ← JWT auth state
│   │   │   └── ThemeContext.jsx   ← Dark/Light mode
│   │   ├── App.jsx                ← Router + layout
│   │   ├── index.js               ← Entry point
│   │   └── index.css              ← Global design system
│   └── package.json
│
├── backend/                ← PHP REST API
│   ├── config.php          ← DB connection + JWT helpers
│   └── api/
│       ├── register.php    ← POST /api/register.php
│       ├── login.php       ← POST /api/login.php
│       ├── events.php      ← GET/POST/PUT/DELETE /api/events.php
│       ├── book_ticket.php ← GET/POST /api/book_ticket.php
│       ├── attendees.php   ← GET /api/attendees.php
│       ├── dashboard.php   ← GET /api/dashboard.php
│       ├── notifications.php ← GET/PUT /api/notifications.php
│       └── reports.php     ← GET /api/reports.php
│
└── database/
    └── schema.sql          ← Complete DB schema + sample data
```

---

## ✅ Features Implemented

| Feature | Status |
|---|---|
| User Registration & Login | ✅ |
| BCrypt Password Hashing | ✅ |
| JWT Token Authentication | ✅ |
| Admin / User Roles | ✅ |
| Create / Edit / Delete Events | ✅ |
| Event Image Upload | ✅ |
| Event Listing + Filters + Search | ✅ |
| Pagination | ✅ |
| Ticket Booking | ✅ |
| Capacity Limit + Sold Out | ✅ |
| Real-time Ticket Count | ✅ |
| Attendee Management | ✅ |
| Admin Dashboard with Stats | ✅ |
| User Dashboard | ✅ |
| Notifications System | ✅ |
| Reports (Events, Attendees, Revenue) | ✅ |
| CSV Export | ✅ |
| Dark / Light Mode | ✅ |
| Responsive Design | ✅ |
| Toast Notifications | ✅ |
| Form Validation (Frontend + Backend) | ✅ |
| 404 Error Page | ✅ |

---

## 🚀 Setup Instructions

### Prerequisites
- **XAMPP** (or any LAMP/WAMP stack)
  - Apache, MySQL, PHP 8.0+
- **Node.js** 18+ and npm
- A browser

---

### Step 1 — Clone / Extract the Project

Place the project folder so the structure is:
```
C:\xampp\htdocs\eventpro\      ← Windows
/var/www/html/eventpro/        ← Linux/Mac
```

---

### Step 2 — Import the Database

1. Start **MySQL** via XAMPP Control Panel
2. Open **phpMyAdmin**: http://localhost/phpmyadmin
3. Click **"New"** → create a database named `eventpro_db`
4. Select `eventpro_db` → click **"Import"**
5. Choose `database/schema.sql` → click **"Go"**

✅ This creates all tables and inserts sample data.

---

### Step 3 — Configure the Backend

Open `backend/config.php` and update if needed:
```php
define('DB_HOST', 'localhost');
define('DB_USER', 'root');   // your MySQL username
define('DB_PASS', '');       // your MySQL password (blank for XAMPP default)
define('DB_NAME', 'eventpro_db');
```

---

### Step 4 — Create Uploads Folder

```bash
mkdir -p backend/uploads
chmod 755 backend/uploads
```

On Windows, just create the folder `backend/uploads/` manually.

---

### Step 5 — Install & Run the React Frontend

```bash
cd frontend
npm install
npm start
```

The React app opens at: **http://localhost:3000**

> The `"proxy"` in `package.json` already points to `http://localhost/eventpro/backend`
> so all API calls will route correctly to your PHP files.

---

### Step 6 — Access the App

| URL | Page |
|---|---|
| http://localhost:3000 | Home Page |
| http://localhost:3000/events | Browse Events |
| http://localhost:3000/login | Login |
| http://localhost:3000/register | Register |
| http://localhost:3000/dashboard | Dashboard |

---

## 🔑 Demo Login Credentials

| Role | Email | Password |
|---|---|---|
| **Admin** | admin@eventpro.com | password |
| **User** | john@example.com | password |
| **User** | jane@example.com | password |

---

## 🗄️ Database Schema

```
users        → id, name, email, password(bcrypt), role, created_at
events       → id, title, description, date, time, venue, capacity, price, category, image, created_by
tickets      → id, event_id, user_id, quantity, total_price, status, booked_at
attendees    → id, event_id, user_id, name, email, phone, registered_at
notifications→ id, user_id, message, is_read, created_at
```

---

## 🔌 API Endpoints

| Method | Endpoint | Description | Auth |
|---|---|---|---|
| POST | /api/register.php | Register user | Public |
| POST | /api/login.php | Login | Public |
| GET | /api/events.php | List events (filterable) | Public |
| GET | /api/events.php?id=1 | Get single event | Public |
| POST | /api/events.php | Create event | Admin |
| PUT | /api/events.php?id=1 | Update event | Admin |
| DELETE | /api/events.php?id=1 | Delete event | Admin |
| GET | /api/book_ticket.php | My tickets | User |
| POST | /api/book_ticket.php | Book tickets | User |
| GET | /api/attendees.php | All/own attendees | User |
| GET | /api/dashboard.php | Dashboard stats | User |
| GET | /api/notifications.php | Notifications | User |
| PUT | /api/notifications.php | Mark read | User |
| GET | /api/reports.php?type=events | Reports | Admin |

---

## 🎨 Design Highlights

- **Glassmorphism** UI with `backdrop-filter: blur(20px)`
- **CSS Custom Properties** for instant theme switching
- **Syne** (display) + **DM Sans** (body) font pairing
- **Staggered animations** on page load
- **Mesh gradient** background orbs
- **Responsive** on mobile, tablet, desktop
- **Dark / Light mode** toggle persisted to localStorage

---

## 🛠️ Technologies Used

| Layer | Technology |
|---|---|
| Frontend | React 18, React Router v6, Axios |
| Styling | Pure CSS (custom design system) |
| Icons | Lucide React |
| Notifications | React Hot Toast |
| Date Handling | date-fns |
| Backend | PHP 8 (REST API, PDO) |
| Auth | Custom JWT (HMAC-SHA256) |
| Database | MySQL 8 |
| Server | Apache (XAMPP) |

---

## 📝 Key Implementation Notes

1. **JWT Auth**: Custom lightweight JWT implementation using `hash_hmac('sha256', ...)`. No external library needed.
2. **Password Security**: BCrypt hashing with `password_hash()` and `password_verify()`.
3. **SQL Injection Prevention**: All queries use PDO prepared statements.
4. **CORS**: Configured in `config.php` to allow React dev server.
5. **Image Upload**: Multipart form data sent from React, stored in `backend/uploads/`.
6. **Real-time tickets**: Ticket count recalculated from DB on each event fetch.

---

*Built for Final Year Web Technologies Project — EventPro v1.0*
