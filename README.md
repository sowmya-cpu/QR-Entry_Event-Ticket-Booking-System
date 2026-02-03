# QR-Entry---Event-Ticket-Booking-System & Attendance Management System  

> A full-stack web application that allows users to browse events, book tickets securely, and enables real-time QR-based attendance tracking for organizers.

 Built with **Django, MySQL, and React**, this project demonstrates real-world full-stack development, authentication, payment readiness, and real-time data handling.

---

##  Why This Project Stands Out

✅ Real-world **production-grade use case**  
✅ **End-to-end full-stack implementation**  
✅ **Secure authentication & authorization**  
✅ **QR-code based check-in system**  
✅ **Admin dashboard for organizers**  
✅ Designed with **scalability & performance in mind**

This is not just a CRUD app — it’s a **complete event-tech platform**.

---

##  Key Features

###  User Side
- Event browsing with detailed descriptions  
- Secure user authentication & authorization  
- Ticket booking system  
- Booking history & ticket management  
- QR code generation for each ticket  

###  Organizer / Admin Side
- Event creation & management  
- Real-time attendance tracking using QR scans  
- Dashboard with booking & attendance analytics  
- Duplicate entry prevention  

###  Security
- Password hashing  
- Auth-protected routes  
- Role-based access control  

---

##  Tech Stack

### Backend
- **Django (Python)**
- **MySQL**
- Django REST Framework
- JWT Authentication

### Frontend
- **React.js**
- Axios
- CSS / Tailwind

### Tools & Platforms
- Git & GitHub  
- VS Code  
- Postman (API testing)  

---

##  System Architecture

This project follows a **modern 3-tier full-stack architecture** ensuring scalability, security, and clean separation of concerns.


**Frontend Layer**
- Built using React.js  
- Handles UI, user interaction, and API calls  

**Backend Layer**
- Built using Django REST Framework  
- Handles authentication, business logic, ticket booking, QR validation, and attendance tracking  

**Database Layer**
- MySQL database  
- Stores users, events, bookings, and attendance records  

###  Data Flow

User → React Frontend → Django REST API → MySQL Database  
MySQL Database → Django REST API → React Frontend → User


---

##  Backend Architecture (Django)

The backend is built using **Django + Django REST Framework (DRF)** following a **modular app-based architecture**.

###  Core Django Apps

| App Name | Responsibility |
|----------|----------------|
| `users` | User registration, login, JWT auth, roles |
| `events` | Event creation, listing, filtering |
| `bookings` | Ticket booking, history, QR generation |
| `attendance` | QR validation & real-time attendance |
| `adminpanel` | Organizer dashboard & analytics |

Each app contains:
- `models.py` → Database schema  
- `serializers.py` → API data validation  
- `views.py` → Business logic  
- `urls.py` → API routing  

---

##  Authentication & Authorization Flow (JWT)

1. User registers or logs in
2. Django validates credentials
3. Server issues a **JWT Token**
4. Token is stored in browser (localStorage)
5. Django middleware verifies:
- Token validity
- User role (admin or user)
6. Unauthorized users are blocked automatically

✅ Protects against:
- Route tampering
- Unauthorized bookings
- Admin privilege abuse

---

##  Database Design (Relational Mapping)

### 🔹 Core Tables

| Table | Description |
|--------|-------------|
| `users` | Stores login credentials & roles |
| `events` | Stores event info (date, price, capacity) |
| `bookings` | Stores booked tickets |
| `attendance` | Stores QR scan & check-in logs |

---

##  Ticket Booking Flow (Full Internal Logic)

1. User selects an event from frontend
2. React sends `POST /api/book-ticket/`
3. Django checks:
   - User is authenticated
   - Event capacity is not exceeded
   - Duplicate booking prevention
4. Ticket is created in `bookings` table
5. Unique **QR Code is generated**
6. QR is linked with:
   - User ID
   - Event ID
   - Booking ID
7. QR image is returned to frontend

✅ Prevents:
- Duplicate bookings
- Over-booking
- Unauthorized bookings

---

##  QR Code Validation Flow (Real-Time Attendance)

1. Admin scans QR at event entry
2. Frontend sends scanned QR data to:POST /api/attendance/validate/
3. Django verifies:
- QR belongs to valid booking
- Booking is not already used
- Event is currently active
4. If valid:
- Attendance is marked ✅
- Entry allowed
5. If invalid:
- Entry rejected 
- Reason returned (duplicate, expired, fake)

✅ This ensures:
- No duplicate entry
- No fake ticket entry
- Real-time live attendance tracking

---

##  Organizer Dashboard Logic

The admin panel dynamically fetches:

- Total tickets sold
- Live attendance count
- No-show users
- Event revenue summary

All data is fetched using:GET /api/admin/analytics/


Aggregations are optimized using:
- Django ORM annotations
- Database indexing on foreign keys

---

##  Performance & Scalability Handling

- ✅ Pagination for event listings
- ✅ Indexed foreign keys for fast lookups
- ✅ Token-based stateless authentication
- ✅ Optimized QR validation queries
- ✅ Separation of concerns via app-based Django design

---

##  Security Measures Implemented

- Password hashing using Django’s built-in hashers
- JWT token expiration handling
- Input sanitization via serializers
- Role-based access control
- CSRF-safe API design

---

##  Production Readiness

This project is designed to be **deployment-ready** with support for:
- Cloud hosting (AWS / Railway / DigitalOcean)
- Persistent MySQL storage
- React production build
- Secure environment variables

---

##  Engineering Highlights

✅ Real-time QR-based attendance  
✅ Stateless JWT authentication  
✅ Clean backend architecture  
✅ Fully relational database design  
✅ Scalable REST APIs  
✅ Production-level system behavior  

---
