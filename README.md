# netlab-store — SBD Module 6 Start Template

Next.js + Express + PostgreSQL monorepo for the SBD Module 6 case study. A simple store frontend + backend with PostgreSQL, seeded sample data, and Vercel deployment config.

## What's Here

| Directory | Description |
|---|---|
| `apps/frontend/` | Next.js 14 app router (app/ directory). Home page with product listings, auth flows. |
| `apps/backend/` | Express.js API server. PostgreSQL (knex/pg) with auth, items, users, transactions. Includes seed data and API routes. |
| `package.json` | Root workspace config (turbo). Scripts: `dev`, `build`, `lint`. |
| `vercel.json` | Vercel rewrites: `/api/*` → `apps/backend/server.js`, all other routes → `apps/frontend`. |
| `seed.sql` | PostgreSQL schema + sample users + items + transactions. |
| `README.md` | This file. |

## Prerequisites

- Node.js (v18+ or v20+)
- PostgreSQL
- npm (v11+) or pnpm

## Setup

```bash
# 1. Clone
git clone https://github.com/JoshRiang/next-redis-start-template.git
cd next-redis-start-template

# 2. Install
npm install

# 3. Environment
cp apps/backend/.env.example apps/backend/.env
# Fill in DATABASE_URL (postgres://...)

# 4. Seed the database
psql $DATABASE_URL -f apps/backend/seed.sql

# 5. Start development
npm run dev
# - Frontend: http://localhost:3000
# - Backend:  http://localhost:3000/api (proxied via vercel.json local dev)
```

## API Endpoints

| Method | Path | Description |
|---|---|---|
| `GET` | `/api/users` | List users |
| `POST` | `/api/users` | Create user |
| `GET` | `/api/items` | List items |
| `POST` | `/api/items` | Create item |
| `GET` | `/api/transactions` | List transactions |

See `apps/backend/src/routes/` for the full route map and request/response schemas.

## License

MIT

## How to Deploy to Vercel

1. Push this repo to GitHub.
2. Import the repo into Vercel.
3. Set the `DATABASE_URL` environment variable in the Vercel dashboard.
4. Vercel will auto-detect the `vercel.json` rewrites and deploy both the frontend and backend as a single service.