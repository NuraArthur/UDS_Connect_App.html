# UDS Connect

**A campus-exclusive social media platform for the University for Development Studies, Tamale, Ghana.**

Built as a Final Year Project — BSc Computer Science, UDS Faculty of Mathematical Sciences.

---

## Overview

UDS Connect is a web-based social networking platform designed exclusively for students and staff of the University for Development Studies (UDS). It replaces fragmented WhatsApp groups and notice boards with a single, verified, campus-specific platform where the entire UDS community can connect, collaborate, and stay informed.

Access is restricted to verified UDS identity holders — users must sign up with a valid UDS student/staff ID and an official UDS email address (`@st.uds.edu.gh` or `@uds.edu.gh`).

---

## Features

| Module | Description |
|---|---|
| **Authentication** | UDS ID + email verification with OTP, JWT-based sessions |
| **Social Feed** | Post campus updates, announcements, photos, and polls |
| **Campus Events** | Create and discover events, RSVP, get reminders |
| **Messaging** | Real-time direct messages and group chats |
| **Clubs & Communities** | Join or create student clubs and study groups |
| **Marketplace** | Buy and sell textbooks, electronics, and other items (GH₵) |
| **Lost & Found** | Report lost items and claim found ones on campus |
| **Student Profiles** | Faculty, level, bio, connections, and post history |

---

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | React.js, Tailwind CSS |
| Backend API | Node.js, Express.js |
| Database | PostgreSQL |
| Real-time | Socket.IO |
| Authentication | JWT, bcrypt, Nodemailer (OTP) |
| File Storage | Cloudinary |
| Cache / Sessions | Redis |
| Deployment | Netlify (frontend), Render (backend) |

---

## Project Structure

```
uds-connect/
├── client/                  # React frontend
│   ├── src/
│   │   ├── components/      # Reusable UI components
│   │   ├── pages/           # Feed, Events, Chat, Profile, etc.
│   │   ├── hooks/           # Custom React hooks
│   │   ├── context/         # Auth context, socket context
│   │   └── utils/           # ID validation, formatters
│   └── public/
├── server/                  # Node.js backend
│   ├── routes/              # API route handlers
│   │   ├── auth.js
│   │   ├── posts.js
│   │   ├── events.js
│   │   ├── messages.js
│   │   ├── clubs.js
│   │   ├── marketplace.js
│   │   └── lostfound.js
│   ├── models/              # Database models
│   ├── middleware/          # Auth middleware, validation
│   ├── socket/              # Socket.IO event handlers
│   └── config/              # DB config, environment setup
├── database/
│   └── schema.sql           # PostgreSQL schema
├── UDS_Connect_App.html     # Prototype / demo file
└── README.md
```

---

## Getting Started

### Prerequisites

- Node.js v18+
- PostgreSQL 14+
- Redis
- A Cloudinary account (free tier works)

### Installation

**1. Clone the repository**

```bash
git clone https://github.com/yourusername/uds-connect.git
cd uds-connect
```

**2. Install dependencies**

```bash
# Backend
cd server
npm install

# Frontend
cd ../client
npm install
```

**3. Set up environment variables**

Create a `.env` file in the `server/` directory:

```env
PORT=5000
DATABASE_URL=postgresql://user:password@localhost:5432/uds_connect
JWT_SECRET=your_jwt_secret_key
REDIS_URL=redis://localhost:6379
CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret
EMAIL_USER=your_uds_smtp_email
EMAIL_PASS=your_email_password
```

**4. Set up the database**

```bash
psql -U postgres -c "CREATE DATABASE uds_connect;"
psql -U postgres -d uds_connect -f database/schema.sql
```

**5. Run the app**

```bash
# Start backend (from server/)
npm run dev

# Start frontend (from client/)
npm start
```

The app will be running at `http://localhost:3000`.

---

## Demo (Prototype)

A static HTML prototype of the full UI is included as `UDS_Connect_App.html`. Open it directly in any browser — no server required.

To share it for user testing, drag and drop the file onto [netlify.com/drop](https://app.netlify.com/drop) to get an instant shareable link.

**Test credentials for the prototype:**
- Student ID: `UDS/CS/21/0042`
- Any password will work in the demo

---

## UDS Student ID Format

The platform validates student IDs against the official UDS format:

```
UDS / [FACULTY CODE] / [2-DIGIT YEAR] / [4-DIGIT NUMBER]

Examples:
  UDS/CS/21/0042   → Computer Science, enrolled 2021
  UDS/AGRIC/22/0117 → Agriculture, enrolled 2022
  UDS/LAW/20/0305  → Law, enrolled 2020
```

---

## Database Schema (Summary)

- `users` — student/staff accounts with UDS ID and verified email
- `posts` — feed posts with tags, likes, and comments
- `events` — campus events with RSVP tracking
- `messages` — real-time messages linked to conversations
- `clubs` — campus clubs with membership tracking
- `marketplace_items` — items for sale in GH₵
- `lost_found` — lost and found reports with resolution status
- `follows` — user follow relationships
- `club_members` — club membership with role (admin/member)

---

## API Endpoints (Summary)

```
POST   /api/auth/register       Register with UDS ID + email
POST   /api/auth/login          Login and receive JWT
POST   /api/auth/verify-otp     Verify email OTP code

GET    /api/posts               Get feed posts
POST   /api/posts               Create a new post
POST   /api/posts/:id/like      Like a post

GET    /api/events              List campus events
POST   /api/events              Create an event
POST   /api/events/:id/rsvp     RSVP to an event

GET    /api/messages/:userId    Get conversation history
POST   /api/messages            Send a message

GET    /api/clubs               List all clubs
POST   /api/clubs/:id/join      Join a club

GET    /api/marketplace         List items for sale
POST   /api/marketplace         Create a listing

GET    /api/lostfound           List lost & found reports
POST   /api/lostfound           Submit a report
```

---

## Roadmap

- [x] UI prototype (all 7 modules)
- [x] UDS ID validation logic
- [x] System architecture design
- [x] Database schema
- [ ] Backend API (Node.js + Express)
- [ ] PostgreSQL integration
- [ ] JWT authentication + OTP email
- [ ] Real-time messaging (Socket.IO)
- [ ] File uploads (Cloudinary)
- [ ] User testing with UDS students
- [ ] Deployment to production

---

## Author
Nura jallu Bayong  
BSc Computer Science, Level 400  
University for Development Studies, Tamale  
Student ID: UDS/CSC/22/0063  
Supervisor:HOD,MUBARICK
Academic Year: 2025/2026

---

## License

This project was developed as an academic final year project at the University for Development Studies. All rights reserved © 2025.
