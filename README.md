# 🎯 MERN Goal Setter

> Personal goal tracker with JWT auth. Built with React, Redux Toolkit, Node and MongoDB.

![React](https://img.shields.io/badge/React-17-61DAFB?logo=react&logoColor=white)
![Redux Toolkit](https://img.shields.io/badge/Redux_Toolkit-1.7-764ABC?logo=redux&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-Express-339933?logo=node.js&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-Mongoose-47A248?logo=mongodb&logoColor=white)
![JWT](https://img.shields.io/badge/Auth-JWT-000000?logo=jsonwebtokens&logoColor=white)

A small full-stack MERN app where authenticated users can register, log in, and manage a private list of personal goals. Built in 2022 as a learning project to go through the full Redux Toolkit + Express + JWT flow.

## ✨ Features

- **JWT authentication**: register / login with hashed passwords (`bcryptjs`) and `Bearer` token sessions
- **Protected goal CRUD**: create, read, update, and delete goals scoped to the logged-in user
- **Redux Toolkit**: `authSlice` and `goalSlice` hold all client state via `createAsyncThunk`
- Protected routes on the React side with redirects for unauthenticated users
- Toast notifications via `react-toastify` for auth and CRUD feedback
- Centralized Express error handler with `express-async-handler`

## 🛠️ Tech Stack

- **Frontend**: React 17, Redux Toolkit, React Router v6, Axios, react-toastify
- **Backend**: Node.js, Express
- **Database**: MongoDB via Mongoose
- **Auth**: JWT (`jsonwebtoken`) + `bcryptjs`
- **Dev tooling**: `nodemon`, `concurrently`

## 📁 Project Structure

```
.
├── backend/
│   ├── config/         # Mongo connection
│   ├── controllers/    # goal + user controllers
│   ├── middleware/     # auth (protect) + error handler
│   ├── models/         # Mongoose models
│   ├── routes/         # /api/goals, /api/users
│   └── server.js
└── frontend/
    └── src/
        ├── app/        # Redux store
        ├── features/
        │   ├── auth/   # authSlice + authService
        │   └── goals/  # goalSlice + goalService
        ├── components/
        └── pages/
```

## 📖 Getting Started

### Prerequisites

- Node.js 14+
- A MongoDB connection string (local or Atlas)

### Install

```bash
# from the repo root
npm install
npm install --prefix frontend
```

### Environment variables

Create a `.env` file in the repo root:

```bash
NODE_ENV=development
PORT=5000
MONGO_URI=mongodb://localhost:27017/goalsetter
JWT_SECRET=your_jwt_secret_here
```

### Run

```bash
# run backend + frontend concurrently
npm start

# or run them separately
npm run server   # backend only (nodemon)
npm run client   # frontend only (CRA dev server on :3000)
```

The frontend is proxied to `http://localhost:5000`, so API calls hit Express directly in development.

## 🔌 API

All `/api/goals` routes require an `Authorization: Bearer <token>` header.

| Method | Endpoint              | Description                |
| ------ | --------------------- | -------------------------- |
| POST   | `/api/users`          | Register a new user        |
| POST   | `/api/users/login`    | Log in, returns JWT        |
| GET    | `/api/users/me`       | Current user (protected)   |
| GET    | `/api/goals`          | List the user's goals      |
| POST   | `/api/goals`          | Create a goal              |
| PUT    | `/api/goals/:id`      | Update a goal              |
| DELETE | `/api/goals/:id`      | Delete a goal              |

## 🙌 Credits

Built by [Mohamed Gado](https://mohamedgado.com).
