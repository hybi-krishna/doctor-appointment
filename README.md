## Overview

The **Doctor Appointment Booking System** is a MERN-stack application that streamlines healthcare appointment scheduling. It provides three distinct interfaces:

| Portal | Description |
|--------|-------------|
| **Patient (Frontend)** | Browse doctors by speciality, book appointments, manage profile & view appointment history |
| **Doctor (Admin Panel)** | View upcoming appointments, manage availability, update profile |
| **Admin (Admin Panel)** | Dashboard with analytics, manage doctors (add/remove), oversee all appointments |

---

## Features

### 👤 Patient Portal
- **User Authentication** — Secure signup & login with JWT tokens
- **Browse Doctors** — Filter and search doctors by speciality
- **Book Appointments** — Select available date & time slots
- **My Appointments** — View, track, and cancel booked appointments
- **Profile Management** — Update personal details and profile picture

### 🩻 Doctor Portal
- **Doctor Login** — Secure authentication for doctors
- **Dashboard** — Overview of earnings, appointments, and patient count
- **Appointment Management** — View, complete, or cancel appointments
- **Profile Settings** — Update fees, availability, and personal information

### 🔐 Admin Portal
- **Admin Dashboard** — Key metrics — total doctors, patients, appointments & latest bookings
- **Add Doctor** — Register new doctors with image upload (Cloudinary)
- **Manage Doctors** — View all doctors & toggle their availability
- **All Appointments** — Oversee and cancel appointments across the platform

---

## Tech Stack

### Frontend & Admin Panel
| Technology | Purpose |
|---|---|
| **React 18/19** | UI library |
| **React Router v7** | Client-side routing |
| **Tailwind CSS v4** | Utility-first styling |
| **Axios** | HTTP client for API calls |
| **React Toastify** | Toast notifications |
| **Vite** | Build tool & dev server |

### Backend
| Technology | Purpose |
|---|---|
| **Node.js** | Runtime environment |
| **Express.js** | Web framework |
| **MongoDB + Mongoose** | Database & ODM |
| **JWT** | Authentication tokens |
| **bcrypt** | Password hashing |
| **Cloudinary** | Image storage & CDN |
| **Multer** | File upload handling |
| **Validator** | Input validation |

---

## Project Structure

```
doctor-appointment/
├── frontend/                # Patient-facing React app
│   └── src/
│       ├── assets/          # Static assets (images, icons)
│       ├── components/      # Reusable UI components
│       │   ├── Navbar.jsx
│       │   ├── Footer.jsx
│       │   ├── Header.jsx
│       │   ├── Banner.jsx
│       │   ├── TopDoctors.jsx
│       │   ├── SpecialityMenu.jsx
│       │   └── RelatedDoctors.jsx
│       ├── context/         # React Context for state management
│       └── pages/           # Route-level page components
│           ├── Home.jsx
│           ├── Doctors.jsx
│           ├── Appointment.jsx
│           ├── MyAppointments.jsx
│           ├── MyProfile.jsx
│           ├── Login.jsx
│           ├── About.jsx
│           └── Contact.jsx
│
├── admin/                   # Admin & Doctor panel React app
│   └── src/
│       ├── components/      # Navbar, Sidebar
│       ├── context/         # Admin & Doctor context providers
│       └── pages/
│           ├── Login.jsx
│           ├── Admin/       # Admin-specific pages
│           │   ├── Dashboard.jsx
│           │   ├── AllAppointments.jsx
│           │   ├── AddDoctor.jsx
│           │   └── DoctorsList.jsx
│           └── Doctor/      # Doctor-specific pages
│               ├── DoctorDashboard.jsx
│               ├── DoctorAppointments.jsx
│               └── DoctorProfile.jsx
│
├── backend/                 # Express.js REST API
│   ├── config/              # DB & Cloudinary configuration
│   ├── controllers/         # Route handler logic
│   │   ├── adminController.js
│   │   ├── doctorController.js
│   │   └── userController.js
│   ├── middlewares/          # Auth & file upload middleware
│   │   ├── authAdmin.js
│   │   ├── authDoctor.js
│   │   ├── authUser.js
│   │   └── multer.js
│   ├── models/              # Mongoose schemas
│   │   ├── UserModel.js
│   │   ├── DoctorModel.js
│   │   └── AppointmentModel.js
│   ├── routes/              # API route definitions
│   │   ├── adminRoute.js
│   │   ├── doctorRoute.js
│   │   └── userRoute.js
│   └── server.js            # Entry point
│
└── README.md
```

---

## Getting Started

### Prerequisites

- **Node.js** ≥ 18.x
- **npm** ≥ 9.x
- **MongoDB** (local instance or [MongoDB Atlas](https://www.mongodb.com/atlas))
- **Cloudinary** account ([sign up free](https://cloudinary.com/))


MONGODB_URL=mongodb://localhost:27017
CLOUDINARY_NAME=your_cloudinary_name
CLOUDINARY_API_KEY=your_cloudinary_api_key
CLOUDINARY_SECRET_KEY=your_cloudinary_secret_key
JWT_SECRET=your_jwt_secret_key
PORT=5000
ADMIN_EMAIL=admin@example.com
ADMIN_PASSWORD=your_admin_password
```

```env
VITE_BACKEND_URL=http://localhost:5000
```

### Running the Application

Open **three terminal windows** and run each module:

```bash
# Terminal 1 — Backend (port 5000)
cd backend
npm run server

# Terminal 2 — Frontend (port 5173)
cd frontend
npm run dev

# Terminal 3 — Admin Panel (port 5174)
cd admin
npm run dev
```

| Module | URL |
|--------|-----|
| Frontend | `http://localhost:5173` |
| Admin Panel | `http://localhost:5174` |
| Backend API | `http://localhost:5000` |

---

## API Endpoints

### Admin Routes — `/api/admin`

| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/login` | Admin login |
| `POST` | `/add-doctor` | Add a new doctor (with image) |
| `GET` | `/all-doctors` | Get all doctors |
| `GET` | `/appointments` | Get all appointments |
| `POST` | `/cancel-appointment` | Cancel an appointment |
| `GET` | `/dashboard` | Get dashboard analytics |

### Doctor Routes — `/api/doctor`

| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/login` | Doctor login |
| `GET` | `/appointments` | Get doctor's appointments |
| `POST` | `/complete-appointment` | Mark appointment as completed |
| `POST` | `/cancel-appointment` | Cancel an appointment |
| `GET` | `/dashboard` | Get doctor dashboard data |
| `GET` | `/profile` | Get doctor profile |
| `POST` | `/update-profile` | Update doctor profile |

### User Routes — `/api/user`

| Method | Endpoint | Description |
|--------|----------|-------------|
| `POST` | `/register` | User registration |
| `POST` | `/login` | User login |
| `GET` | `/get-profile` | Get user profile |
| `POST` | `/update-profile` | Update user profile |
| `POST` | `/book-appointment` | Book an appointment |
| `GET` | `/appointments` | Get user's appointments |
| `POST` | `/cancel-appointment` | Cancel an appointment |

