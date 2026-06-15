# 🛒 Market Flow API — Role-Based E-Commerce Backend

A RESTful API for managing users, roles, products, orders, and wallets. Built with NestJS, TypeORM, and PostgreSQL — designed with a clean role separation and a full order lifecycle out of the box.

---

## 📋 Table of Contents

- [About](#about)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Quick Start](#quick-start)
- [Docker](#docker)
- [Admin Seed](#admin-seed)
- [User Roles](#user-roles)
- [Testing](#testing)
- [Swagger](#swagger)
- [Environment Variables](#environment-variables)

---

## About

Mini Market is a backend platform that simulates a small marketplace — users can register, browse products, place orders, and manage their wallets. Sellers list products, admins oversee the platform.

### Key Features

- **Role System** — three distinct roles: `USER`, `SELLER`, `ADMIN`, each with scoped access
- **Product Management** — sellers can create and manage their listings
- **Order Lifecycle** — users place orders, track status, and manage purchases
- **Wallet System** — built-in balance management per user
- **JWT Authentication** — secure token-based auth with configurable expiry
- **Admin Seeding** — one-command admin account setup for initial configuration
- **Swagger Docs** — interactive API documentation included

---

## Tech Stack

| Technology | Purpose |
|---|---|
| NestJS | Backend framework |
| TypeORM | ORM and database interaction |
| PostgreSQL | Primary database |
| JWT | Authentication |
| Docker & Docker Compose | Containerization |
| Jest | Unit and E2E testing |

---

## Quick Start

### Requirements

- Docker and Docker Compose, or Node.js (for local development)
- PostgreSQL instance

### 1. Clone the Repository

```bash
git clone <repo_url>
cd mini_market
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Configure Environment Variables

```bash
cp .env.example .env
```

Fill in your values:

```env
PORT=3000
DB_HOST=localhost
DB_PORT=5432
DB_USERNAME=postgres
DB_PASSWORD=your_password
DB_NAME=mini_market
JWT_SECRET_KEY=your_secret_key
JWT_EXPIRE_IN=1d
```

---

## Docker

The recommended way to run the project:

```bash
docker-compose up -d
```

| Service | Port |
|---|---|
| API | 3000 |
| PostgreSQL | 5432 |

> ⚠️ If running locally, make sure no other process is occupying port 3000.

---

## Admin Seed

To bootstrap an admin account:

```bash
npm run seed:admin
```

This creates a user with the following credentials:

| Field | Value |
|---|---|
| Name | admin |
| Password | 123456 |
| Role | ADMIN |

> **Note:** Regular registration always defaults to the `USER` role. There is no way to self-assign `ADMIN` through the registration endpoint — this is intentional.

---

## User Roles

| Role | Description |
|---|---|
| `USER` | Regular customer — can browse products and place orders |
| `SELLER` | Can create and manage product listings |
| `ADMIN` | Full platform access and user management |

---

## Testing

Unit tests:

```bash
npm run test
```

End-to-end tests:

```bash
npm run test:e2e
```

---

## Swagger

Interactive API documentation is available at:

```
http://localhost:3000/api/docs
```

---

## Environment Variables

```env
PORT=3000
DB_HOST=localhost
DB_PORT=5432
DB_USERNAME=postgres
DB_PASSWORD=your_password
DB_NAME=mini_market
JWT_SECRET_KEY=your_secret_key
JWT_EXPIRE_IN=1d
```

> ⚠️ Never commit real credentials to `.env.example`. Keep secrets out of version control.

---

## Tips

- Admin seed only needs to run once — you can remove the script afterward or keep it for testing environments.
- Docker guarantees a consistent environment across all machines.
- JWT expiry is configurable via `JWT_EXPIRE_IN` — adjust based on your security requirements.

---

## License

MIT License
