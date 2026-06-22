# StudySync – A Collaborative Study Platform

StudySync is a Full Stack MERN application designed to recreate the experience of studying together in a physical library. It provides students with collaborative study groups, real-time communication, shared resources, quizzes, and tutor booking in a single platform.

The application combines traditional web development with real-time technologies such as Socket.io and collaborative tools like a shared whiteboard, making it an advanced portfolio project.

---

# Features

## Authentication

- User Registration
- User Login
- JWT Authentication
- Password Encryption using bcrypt
- Protected Routes
- User Profile

---

## Study Groups

- Create Study Groups
- Edit Study Groups
- Delete Study Groups
- Join Groups using Invite Link
- Leave Groups
- View Joined Groups
- Manage Group Members

---

## Resource Repository

- Upload PDF Notes
- Upload Images
- View Shared Files
- Download Files
- Delete Uploaded Files
- Store Files in Firebase Storage
- Store File Metadata in MongoDB

---

## Real-Time Study Room

### Live Chat

- Real-time messaging
- Typing indicator (optional)
- Online users
- Message timestamps

---

### Collaborative Whiteboard

- Multiple users draw simultaneously
- Live synchronization
- Brush tool
- Eraser
- Clear canvas
- Different colors
- Adjustable brush size

---

## Quiz System

- Create Flashcards
- Create Multiple Choice Quizzes
- Attempt Quiz
- Automatic Score Calculation
- Quiz History
- Leaderboard

---

## Tutor Marketplace

- Tutor Profiles
- Subject Listings
- Hourly Pricing
- Availability Slots
- Student Booking
- Prevent Double Booking

---

## Dashboard

- Joined Groups
- Recent Activity
- Shared Resources
- Upcoming Bookings
- Leaderboard

---

# Tech Stack

## Frontend

- React.js
- React Router DOM
- Axios
- Socket.io Client
- HTML5 Canvas API
- CSS / Tailwind CSS (optional)

---

## Backend

- Node.js
- Express.js
- Socket.io

---

## Database

- MongoDB
- Mongoose

---

## Authentication

- JWT
- bcrypt

---

## File Storage

- Firebase Storage
- Multer

---

## Optional Video Calling

- PeerJS
or
- Agora SDK

---

## Deployment

Frontend

- Vercel

Backend

- Render / Railway

Database

- MongoDB Atlas

Storage

- Firebase Storage

---

# Project Architecture

```
                    React Frontend
                           │
                           │
                  REST API + Socket.io
                           │
                           ▼
                  Node.js + Express
                 /                  \
                /                    \
         MongoDB Atlas         Firebase Storage
                |
                |
            Application Data
```

---

# Folder Structure

```
StudySync/

│
├── frontend/
│
│   ├── public/
│
│   ├── src/
│   │
│   ├── assets/
│   ├── components/
│   ├── context/
│   ├── hooks/
│   ├── layouts/
│   ├── pages/
│   │
│   │   ├── Auth/
│   │   ├── Dashboard/
│   │   ├── Groups/
│   │   ├── StudyRoom/
│   │   ├── Marketplace/
│   │   ├── Quiz/
│   │
│   ├── services/
│   ├── socket/
│   ├── utils/
│   ├── App.jsx
│   └── main.jsx
│
├── backend/
│
│   ├── config/
│   │
│   ├── controllers/
│   │
│   ├── middleware/
│   │
│   ├── models/
│   │
│   ├── routes/
│   │
│   ├── socket/
│   │
│   ├── services/
│   │
│   ├── utils/
│   │
│   ├── uploads/
│   ├── server.js
│   └── app.js
│
├── README.md
├── package.json
└── .gitignore
```

---

# Database Collections

## Users

```
_id

name

email

password

profilePicture

role

joinedGroups

createdAt
```

---

## Groups

```
_id

groupName

description

createdBy

inviteCode

members[]

createdAt
```

---

## Resources

```
_id

groupId

uploadedBy

fileName

fileType

fileSize

downloadURL

createdAt
```

---

## Messages

```
_id

groupId

sender

message

timestamp
```

---

## Quizzes

```
_id

groupId

title

questions[]

createdBy

createdAt
```

---

## Quiz Results

```
_id

quizId

userId

score

submittedAt
```

---

## Tutors

```
_id

userId

subjects

experience

hourlyRate

availability

verified
```

---

## Bookings

```
_id

studentId

tutorId

date

time

status
```

---

# Authentication Flow

```
Register

↓

Hash Password

↓

Save User

↓

Login

↓

Verify Password

↓

Generate JWT

↓

Protected Routes
```

---

# Study Group Flow

```
Create Group

↓

Generate Invite Code

↓

Share Invite Link

↓

Student Opens Link

↓

Backend Verifies Invite

↓

Join Group
```

---

# Resource Upload Flow

```
Select File

↓

React

↓

Express

↓

Multer

↓

Firebase Storage

↓

Download URL

↓

MongoDB

↓

Display to Group
```

---

# Chat Flow

```
User Sends Message

↓

Socket.emit()

↓

Server

↓

Broadcast

↓

All Connected Members Receive Message
```

---

# Whiteboard Flow

```
Mouse Down

↓

Canvas Coordinates

↓

Socket.io

↓

Broadcast Coordinates

↓

Other Users Draw Same Line
```

---

# Quiz Flow

```
Tutor

↓

Create Quiz

↓

Students Attempt Quiz

↓

Backend Calculates Score

↓

Save Result

↓

Update Leaderboard
```

---

# Tutor Booking Flow

```
Student Selects Tutor

↓

Choose Date

↓

Choose Time

↓

Backend Checks Availability

↓

Slot Available

↓

Booking Created
```

---

# REST API Endpoints

## Authentication

```
POST    /api/auth/register

POST    /api/auth/login

GET     /api/auth/profile
```

---

## Users

```
GET     /api/users

GET     /api/users/:id

PUT     /api/users/:id
```

---

## Groups

```
POST    /api/groups

GET     /api/groups

GET     /api/groups/:id

PUT     /api/groups/:id

DELETE  /api/groups/:id

POST    /api/groups/join
```

---

## Resources

```
POST    /api/resources/upload

GET     /api/resources/:groupId

DELETE  /api/resources/:id
```

---

## Chat

```
Socket Events

join-room

leave-room

send-message

receive-message
```

---

## Whiteboard

```
Socket Events

draw

clear-canvas

erase
```

---

## Quiz

```
POST    /api/quizzes

GET     /api/quizzes

GET     /api/quizzes/:id

POST    /api/quizzes/submit
```

---

## Tutor Marketplace

```
POST    /api/tutors

GET     /api/tutors

GET     /api/tutors/:id
```

---

## Booking

```
POST    /api/bookings

GET     /api/bookings

DELETE  /api/bookings/:id
```

---

# Environment Variables

## Backend

```
PORT=

MONGODB_URI=

JWT_SECRET=

FIREBASE_PROJECT_ID=

FIREBASE_PRIVATE_KEY=

FIREBASE_CLIENT_EMAIL=

FIREBASE_STORAGE_BUCKET=
```

---

## Frontend

```
VITE_API_URL=

VITE_SOCKET_URL=
```

---

# Installation

## Clone Repository

```bash
git clone https://github.com/yourusername/studysync.git
```

---

## Install Frontend

```bash
cd frontend

npm install
```

---

## Install Backend

```bash
cd backend

npm install
```

---

## Run Backend

```bash
npm run dev
```

---

## Run Frontend

```bash
npm run dev
```

---

# Future Improvements

- Voice Chat
- AI Study Assistant
- AI Quiz Generator
- AI Note Summarizer
- Screen Sharing
- Collaborative Code Editor
- Push Notifications
- Email Notifications
- Mobile Application
- Dark Mode
- Attendance Tracking
- Calendar Integration
- Reminder System
- Group Analytics
- Study Time Tracking

---

# Learning Outcomes

This project demonstrates practical experience in:

- MERN Stack Development
- Authentication & Authorization
- REST API Development
- MongoDB Data Modeling
- Firebase Storage Integration
- Real-Time Communication with Socket.io
- HTML5 Canvas API
- File Upload Management
- State Management in React
- Backend Architecture
- Role-Based Access Control
- Deployment of Full Stack Applications
- Scalable Project Structure

---

# Project Timeline

## Week 1

- Authentication
- User Profiles
- Group CRUD
- Invite System
- Firebase Storage Integration

---

## Week 2

- Socket.io Setup
- Live Chat
- Whiteboard
- Group Study Room

---

## Week 3

- Flashcards
- Quiz Engine
- Leaderboard
- Score Tracking

---

## Week 4

- Tutor Marketplace
- Booking System
- Deployment
- Final Testing
- Demo Video

---

# Contributors

Developed as a Full Stack Web Development Project.

---

# License

This project is intended for educational and portfolio purposes.
