# A9_Project_Thesis

#  A Web-Based Leave Management System

##  Overview 

**LMS** is a full-stack web application built with the **MERN stack** that automates the entire leave application and approval process in educational institutions. It replaces traditional paper-based leave management with a secure, role-based, and workflow-driven digital solution.

The platform serves **five distinct user roles** — Student, Faculty, HOD, Principal, and Admin — each with specialized dashboards and tools.

**Key features:** Multi-level approval workflow · Automated email & in-app notifications · Document upload support · Automatic attendance tracking

---

##  System Architecture

```
┌─────────────────────────────────────────────────────┐
│         PRESENTATION LAYER  (Frontend)              │
│   React.js 18 · React Router v6 · Axios            │
│   Custom CSS · AuthContext · Role-based Dashboards  │
└──────────────────────┬──────────────────────────────┘
                       │  HTTP / REST API + JWT Bearer Token
┌──────────────────────▼──────────────────────────────┐
│         APPLICATION LAYER  (Backend)                │
│   Node.js · Express.js · JWT Auth · Multer          │
│   Nodemailer (Gmail SMTP) · MVC Architecture        │
└──────────────────────┬──────────────────────────────┘
                       │  Mongoose ODM
┌──────────────────────▼──────────────────────────────┐
│         DATA LAYER  (Database)                      │
│   MongoDB 8.0 (Local / Atlas)                       │
│   Collections: Users · Leaves · Attendance         │
│                Departments · Notifications          │
└─────────────────────────────────────────────────────┘
```

---
## Implementation

Source Code
🔗 **https://github.com/Y22ACS591/A-Web-Based-Leave-Management-System**

Description

The implementation of the Leave Management System is available in the above GitHub repository, which includes frontend, backend, and database integration. The system supports role-based access, leave application workflows, and approval mechanisms.

##  User Roles & Modules

| Role | Level | Responsibilities |
|------|-------|-----------------|
| 🎓 **Student** | Applicant | Apply for Medical/OD leave, upload docs, track status, view attendance |
| 👨‍🏫 **Faculty** | Level 1 Approval | Review student leaves, mark daily attendance, apply for own leaves |
| 🏢 **HOD** | Level 2 Approval | Dept-wise reports, analytics, second-stage approval |
| 🎩 **Principal** | Final Authority | Institution-wide reports, final approval on all leaves |
| ⚙️ **Admin** | System Config | Manage accounts, configure departments, reset balances |

---

##  Multi-Level Approval Workflow

```
Student  →  Faculty  →  HOD  →  Principal
Faculty  →  HOD      →  Principal
HOD      →  Principal
```

Automated email notifications via **Nodemailer + Gmail SMTP** are sent at every stage.

---

##  Tech Stack

### Frontend
- **React.js 18** — Component-based UI library
- **React Router v6** — Client-side routing with protected routes
- **Axios** — HTTP client with JWT interceptors
- **React Hot Toast** — Toast notifications
- **Custom CSS** — No external framework dependency

### Backend
- **Node.js** — JavaScript runtime environment
- **Express.js** — Web application framework
- **MongoDB 8.0** — NoSQL document database
- **Mongoose** — MongoDB ODM
- **JWT (jsonwebtoken)** — Secure authentication (7-day expiry)
- **bcryptjs** — Password hashing (10 salt rounds)
- **Nodemailer** — Email notifications via Gmail SMTP
- **Multer** — File uploads (PDF, JPG, PNG · max 5MB)

---

##  Getting Started

### Prerequisites

- Node.js v18 or higher
- MongoDB 8.0 (local) or MongoDB Atlas (cloud)
- Gmail account with App Password for email notifications
- npm package manager

### Backend Setup

```bash
cd college-leave-management/backend
npm install
cp .env.example .env
```

**Backend `.env` configuration:**

```env
PORT=5000
MONGO_URI=mongodb://127.0.0.1:27017/college_leave_db
JWT_SECRET=your_super_secret_jwt_key_here
JWT_EXPIRE=7d
EMAIL_HOST=smtp.gmail.com
EMAIL_PORT=587
EMAIL_USER=your_gmail@gmail.com
EMAIL_PASS=your_gmail_app_password
CLIENT_URL=http://localhost:3000
NODE_ENV=development
```

### Frontend Setup

```bash
cd college-leave-management/frontend
npm install
cp .env.example .env
```

**Frontend `.env` configuration:**

```env
REACT_APP_API_URL=http://localhost:5000/api
```

### Seed Database (first time only)

```bash
cd college-leave-management/backend
npm run seed
```

### Run the Application

```bash
# Terminal 1 — Backend (Port 5000)
cd college-leave-management/backend
npm run dev

# Terminal 2 — Frontend (Port 3000)
cd college-leave-management/frontend
npm start
```

Open **http://localhost:3000** in your browser.

---

##  Demo Accounts

| Role | Email | Password |
|------|-------|----------|
| Admin | `admin@college.edu` | `admin123` |
| Principal | `principal@college.edu` | `principal123` |
| HOD | `hod.cse@college.edu` | `hod123` |
| Faculty | `faculty@college.edu` | `faculty123` |
| Student | `student1@college.edu` | `student123` |

---


##  Future Enhancements

- [ ] 📱 Mobile App — React Native for iOS & Android
- [ ] ☁️ Cloud Storage — AWS S3 / Cloudinary for documents
- [ ] ⚡ Real-Time Notifications — WebSocket / Firebase Cloud Messaging
- [ ] 🔬 Biometric Attendance — hardware device integration
- [ ] 📄 OD Certificate Generation — auto-generate PDF certificates
- [ ] 📅 Leave Calendar — department-level shared calendar
- [ ] 💬 SMS Notifications — Twilio gateway integration
- [ ] 🚀 Cloud Deployment — AWS / Render / Railway

---

## GitHub Repositories

🔗 **https://github.com/Y22ACS591/A-Web-Based-Leave-Management-System.git**

---

## 👨‍💻 Contributors

| V. Monika | Y22ACS591 |
| V. Hema Minakshi | Y22ACS583 |
| T. Manroosh | Y22ACS575 |
| H. Karthik Sonia | Y22ACS462 |

**Project Guide:** Mr. A. Gopinath, Assistant Professor, Dept. of CSE  
**Institution:** Bapatla Engineering College (Autonomous), Bapatla, Andhra Pradesh, India

---

##  Acknowledgements

- **Mr. A. Gopinath** — Project Guide
- **Dr. M. Rajesh Babu** — Head of Department, CSE
- **Bapatla Engineering College** — For infrastructure and support
- **MongoDB Atlas** — For database hosting
- **React.js Community** — For the open-source library

---

<div align="center">

Built with ❤️ by the CLMS Team &nbsp;·&nbsp; Bapatla Engineering College &nbsp;·&nbsp; 2025–2026

</div>
