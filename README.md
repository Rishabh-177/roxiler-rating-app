# Roxiler Store Rating

A local full-stack assessment project for store discovery, customer ratings, and role-based store management.

## Features

- JWT-based login with role-specific dashboards
- Normal user registration
- Admin dashboard with user, store, and rating counts
- Admin creation of users and stores
- Store listing with search, filters, and sorting
- Rating submission and modification by normal users
- Store owner dashboard with store averages and customer ratings
- Password updates
- Client-side and server-side form validation

## Tech Stack

- **Frontend:** React, Vite, React Router, Axios, React Feather, CSS
- **Backend:** Node.js, Express.js, JWT, bcryptjs
- **Database:** MySQL

## Project Structure

```text
roxiler-store-rating-177/
├── README.md
├── .gitignore
├── database/
│   └── schema.sql
├── backend/
│   ├── .env.example
│   ├── package.json
│   └── src/
└── frontend/
    ├── .env.example
    ├── index.html
    ├── package.json
    ├── vite.config.js
    └── src/
```

## Requirements

- Node.js 18 or later
- npm
- MySQL

## Database Setup

From the project root, execute the schema using a MySQL account that can create databases:

```bash
mysql -u your_mysql_user -p < database/schema.sql
```

The schema creates and selects the `roxiler_rating` database and creates its tables.

## Backend Setup

In PowerShell, from the project root:

```powershell
cd backend
npm install
Copy-Item .env.example .env
```

Update `backend/.env` with your local MySQL settings and a private JWT secret, then run:

```powershell
npm run seed
npm run dev
```

The seed command creates or resets the demo admin and store-owner accounts and adds a demo store if needed. The API listens on `http://localhost:5000` by default; `GET /health` checks the database connection.

## Frontend Setup

Open another terminal in the project root:

```powershell
cd frontend
npm install
Copy-Item .env.example .env
npm run dev
```

Vite prints the local frontend URL when its development server starts.

## Environment Variables

Backend variables in `backend/.env`:

| Variable | Purpose |
| --- | --- |
| `PORT` | API port; defaults to `5000` |
| `CLIENT_URL` | Allowed frontend origin; defaults to `http://localhost:5173` |
| `DB_HOST` | MySQL host |
| `DB_PORT` | MySQL port; defaults to `3306` |
| `DB_USER` | MySQL username |
| `DB_PASSWORD` | MySQL password |
| `DB_NAME` | MySQL database name |
| `JWT_SECRET` | Secret used to sign and verify login tokens |
| `JWT_EXPIRES_IN` | Token lifetime; defaults to `1d` |

The frontend accepts `VITE_API_URL` in `frontend/.env`; it defaults to `http://localhost:5000/api`.

The checked-in `.env.example` files contain placeholders only. Keep real `.env` files private.

## Demo Credentials

After running `npm run seed` in the backend:

- **Admin:** `admin@roxiler.com` / `Admin@123`
- **Store owner:** `owner@roxiler.com` / `Owner@123`

The seed command sets these demo passwords whenever it runs. Normal users can register through the frontend.

## Roles

- **ADMIN:** View dashboard totals and manage user and store records.
- **USER:** Register, discover stores, and submit or update ratings.
- **STORE_OWNER:** View assigned stores, their average ratings, and customer rating details.

## Assessment Features

The project implements role-based authentication, user and store administration, searchable and sortable store listings, 1–5 customer ratings that can be updated, store-owner rating summaries, and password changes. Name, email, address, and password validation is applied in the registration and user-creation flows.

## Notes

This is a local assessment project. It is not configured or claimed to be deployed.
