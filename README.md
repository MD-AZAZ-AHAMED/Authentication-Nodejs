# Authentication-Nodejs


A clean and minimal Node.js authentication starter built with Express, MongoDB, JWT, and secure cookie handling.

## 🚀 Project Overview

This repository demonstrates a simple backend authentication flow with:
- User registration
- JWT token generation
- Cookie-based session handling
- Protected route access for authenticated users
- MongoDB integration via Mongoose

It is ideal for learning authentication fundamentals and building a lightweight auth API.

## 🧩 Key Features

- `POST /api/auth/register` — create a new user and issue a JWT cookie
- `POST /api/posts/create` — protected endpoint that validates the JWT cookie
- Passwords stored directly in MongoDB (demo scaffold)
- Environment-based configuration using `dotenv`
- Structured Express routing for clean project organization

## 🛠️ Tech Stack

- Node.js
- Express
- MongoDB / Mongoose
- JSON Web Tokens (`jsonwebtoken`)
- Cookie Parser (`cookie-parser`)
- dotenv

## 📁 Project Structure

- `server.js` — entry point that loads environment settings, connects to MongoDB, and starts the server
- `src/app.js` — Express app setup, middleware, and route registration
- `src/db/db.js` — MongoDB connection helper
- `src/models/user.model.js` — Mongoose user model
- `src/controllers/auth.controller.js` — authentication controller logic
- `src/routes/auth.routes.js` — auth route definitions
- `src/routes/post.routes.js` — protected post route definitions

## ⚙️ Setup Instructions

1. Install dependencies

```bash
npm install
```

2. Create a `.env` file at the repository root with the following values:

```env
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
```

3. Start the server

```bash
node server.js
```

4. Open the app at:

```text
http://localhost:3000
```

## 🔌 API Endpoints

### Register a user

- Method: `POST`
- URL: `/api/auth/register`
- Body:
  - `username` (string)
  - `email` (string)
  - `password` (string)

Example request:

```bash
curl -X POST http://localhost:3000/api/auth/register \
  -H "Content-Type: application/json" \
  -d '{"username":"john","email":"john@example.com","password":"secret"}'
```

Successful response returns:
- a `201` status
- `token` cookie set in the browser
- newly created user data

### Create a protected post

- Method: `POST`
- URL: `/api/posts/create`
- Requires `token` cookie issued during registration

Example request using browser / client cookie support:

```bash
curl -X POST http://localhost:3000/api/posts/create --cookie "token=<your_token_here>"
```

If the token is missing or invalid, the endpoint responds with `401 Unauthorized`.

## 💡 Notes

- This code is intended as an authentication learning exercise and not a production-ready solution.
- For production, add password hashing, input validation, refresh tokens, secure cookie flags, and better error handling.
- The current implementation stores plain text passwords in MongoDB for demo purposes only.

## ✅ Improvements

If you want to extend this project, consider adding:
- Login route with password verification
- Password hashing with `bcrypt`
- Role-based access control
- Refresh tokens and logout support
- Frontend integration with React or Vue

---

Built as a concise authentication backend example for practical learning and fast prototyping.
