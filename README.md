CareerLink: AI-Powered Campus Placement Management System
Authors

Sk. Mohammad Ali (Y22ACS558)
M. Hema Bhuvaneswari (Y22ACS501)
V. Sravani (Y22ACS587)
S. Naga Goutham (Y22ACS564)


Overview
College Leave Management System (CLMS) is a full-stack web application developed using the MERN stack — MongoDB, Express.js, React.js, and Node.js — that automates the entire leave application and approval process in educational institutions. The system replaces traditional paper-based leave management with a secure, role-based, and workflow-driven digital solution.
The platform serves five distinct user roles — Student, Faculty, HOD, Principal, and Admin — providing each with specialized dashboards and tools to streamline college leave management.
Key features: Multi-level approval workflow, automated email and in-app notifications, document upload support, and automatic attendance tracking.

Implementation
Frontend Application
React-based responsive web application for all user roles.
🔗 GitHub: https://github.com/yourusername/college-leave-management-frontend
Backend Server
Node.js backend with Express.js and MongoDB.
🔗 GitHub: https://github.com/yourusername/college-leave-management-backend

Project Modules
1. Student Module

Apply for Medical Leave or OD Leave (workshops, hackathons, sports, quizzes)
Upload supporting documents (medical certificates, OD letters) — PDF, JPG, PNG up to 5MB
Track leave application status in real time
View leave balance and attendance calendar
Receive in-app and email notifications on status updates

2. Faculty Module

Apply for Casual, Medical, or OD Leave
Review and approve or reject student leave requests (Level 1 approval)
Mark daily attendance for department students
Receive in-app notifications for pending approvals

3. HOD Module

Review and approve or reject leave requests at Level 2
View department-wise leave reports and analytics
Receive in-app and email notifications for pending approvals

4. Principal Module

Final approval authority over all leave requests
View institution-wide reports and analytics
Receive notifications for pending approvals

5. Admin Module

Create and manage user accounts
Configure departments and assign HODs
Reset leave balances for all users
View comprehensive system reports

6. Multi-Level Approval Workflow

Dynamic approval chain based on applicant role
Student: Faculty → HOD → Principal
Faculty: HOD → Principal
HOD: Principal only
Automated email notifications at each stage via Nodemailer
In-app bell icon notifications with unread count badge

7. Attendance Tracking

Calendar-based attendance view for students
Faculty can mark daily attendance for department students
Attendance automatically updated to on_leave upon final leave approval


System Architecture
CLMS implements a three-tier architecture:
┌─────────────────────────────────────────────────────────┐
│           PRESENTATION LAYER (Frontend)                 │
│     React.js 18 + React Router v6 + Axios              │
│     Custom CSS + AuthContext + Role-based Dashboards   │
└────────────────────┬────────────────────────────────────┘
                     │ HTTP/REST API + JWT Bearer Token
┌────────────────────▼────────────────────────────────────┐
│          APPLICATION LAYER (Backend)                    │
│     Node.js + Express.js + JWT Auth + Multer           │
│     Nodemailer (Gmail SMTP) + MVC Architecture         │
└────────────────────┬────────────────────────────────────┘
                     │ Mongoose ODM
┌────────────────────▼────────────────────────────────────┐
│              DATA LAYER (Database)                      │
│     MongoDB 8.0 (Local / Atlas)                        │
│     5 Collections: Users, Leaves, Attendance,          │
│     Departments, Notifications                         │
└─────────────────────────────────────────────────────────┘

Technologies Used
Frontend

React.js 18 — Component-based UI library
React Router v6 — Client-side routing with protected routes
Axios — HTTP client with JWT interceptors
React Hot Toast — Toast notifications
Custom CSS — No external framework dependency

Backend

Node.js — JavaScript runtime environment
Express.js — Web application framework
MongoDB 8.0 — NoSQL document database
Mongoose — MongoDB ODM
JWT (jsonwebtoken) — Secure authentication tokens
bcryptjs — Password hashing (10 salt rounds)
Nodemailer — Email notifications via Gmail SMTP
Multer — File upload middleware (PDF, JPG, PNG, max 5MB)


Key Features
Multi-Level Approval

Dynamic approval chain based on applicant role
Embedded approval chain array in MongoDB leave document
Automatic routing to next approver upon approval

Notifications

Email notifications — Sent at each stage via Nodemailer + Gmail SMTP
In-app notifications — Bell icon with unread badge, dropdown panel
Polling mechanism — Frontend polls every 30 seconds for updates

Document Upload

Upload medical certificates and OD letters with leave requests
Multer middleware validates file type and size
Files served as static assets via Express.js

Security

JWT authentication — 7-day token expiry
bcrypt password hashing — 10 salt rounds
Role-based access control — Middleware on all protected routes
Axios interceptors — Auto-attach token + handle 401 responses

Attendance

Calendar-based monthly attendance view
Color-coded status: Present, Absent, On Leave, Holiday
Auto-update on leave approval via MongoDB upsert


Installation & Setup
Prerequisites

Node.js v18 or higher
MongoDB 8.0 (local) or MongoDB Atlas (cloud)
Gmail account with App Password for email notifications
npm package manager

Backend Setup
bash# Navigate to backend
cd college-leave-management/backend

# Install dependencies
npm install

# Create .env file
cp .env.example .env

# Edit .env with your credentials
Backend .env Configuration
envPORT=5000
MONGO_URI=mongodb://127.0.0.1:27017/college_leave_db
JWT_SECRET=your_super_secret_jwt_key_here
JWT_EXPIRE=7d
EMAIL_HOST=smtp.gmail.com
EMAIL_PORT=587
EMAIL_USER=your_gmail@gmail.com
EMAIL_PASS=your_gmail_app_password
CLIENT_URL=http://localhost:3000
NODE_ENV=development
Frontend Setup
bash# Navigate to frontend
cd college-leave-management/frontend

# Install dependencies
npm install

# Create .env file
cp .env.example .env
Frontend .env Configuration
envREACT_APP_API_URL=http://localhost:5000/api
Seed Database (First Time Only)
bashcd college-leave-management/backend
npm run seed
This creates the following demo accounts:
RoleEmailPasswordAdminadmin@college.eduadmin123Principalprincipal@college.eduprincipal123HODhod.cse@college.eduhod123Facultyfaculty@college.edufaculty123Studentstudent1@college.edustudent123
Run the Application
bash# Terminal 1 — Start Backend (Port 5000)
cd college-leave-management/backend
npm run dev

# Terminal 2 — Start Frontend (Port 3000)
cd college-leave-management/frontend
npm start
Open: http://localhost:3000

API Endpoints
Authentication
MethodEndpointDescriptionPOST/api/auth/loginUser loginGET/api/auth/meGet current userPUT/api/auth/profileUpdate profilePUT/api/auth/change-passwordChange password
Leaves
MethodEndpointDescriptionPOST/api/leavesApply for leave (with document)GET/api/leaves/myGet my leave applicationsGET/api/leaves/pendingGet pending approvalsGET/api/leavesGet all leaves (Admin/HOD/Principal)PUT/api/leaves/:id/statusApprove or reject leavePUT/api/leaves/:id/cancelCancel pending leave
Users & Departments
MethodEndpointDescriptionGET/api/usersGet all usersPOST/api/usersCreate new user (Admin)PUT/api/users/:idUpdate userPATCH/api/users/:id/toggleActivate / Deactivate userGET/api/departmentsGet all departmentsPOST/api/departmentsCreate department
Attendance & Notifications
MethodEndpointDescriptionPOST/api/attendance/markMark attendanceGET/api/attendance/myGet my attendanceGET/api/notificationsGet notificationsPUT/api/notifications/read-allMark all as readGET/api/reports/dashboardGet dashboard stats

Future Enhancements

Mobile Application — React Native app for iOS and Android
Cloud Storage — AWS S3 or Cloudinary for document storage
Real-Time Notifications — WebSocket / Firebase Cloud Messaging
Biometric Attendance — Integration with biometric devices
OD Certificate Generation — Auto-generate PDF certificates
Leave Calendar — Department-level shared leave calendar
SMS Notifications — Twilio SMS gateway integration
Cloud Deployment — AWS / Render / Railway deployment


Project Guide
Mr. A. Gopinath, Assistant Professor, Department of CSE
Bapatla Engineering College (Autonomous), Bapatla, Andhra Pradesh, India
Acknowledgements

Dr. M. Rajesh Babu — Head of Department, CSE
Bapatla Engineering College — For infrastructure and support
MongoDB Atlas — For database hosting
React.js Community — For open-source library


Built with ❤️ by CLMS Team | Bapatla Engineering College | 2025-2026
