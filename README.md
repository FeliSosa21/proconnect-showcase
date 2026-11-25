# ProConnect — Debt Collection CRM (showcase)

> This is a **showcase repository**. ProConnect is a private product built with Antonio Fontes, so the full source code is not public. This repo describes the system and my contribution. The code is available for review on request.

ProConnect is a multi-company CRM for debt collection teams. It manages debtor portfolios, phone collection activity, payment promises and payment plans, Excel imports, per-company commissions and reports.

## Features

- **Debtor portfolios** by company, with search and filters
- **Collection activity**: calls, interactions and their outcomes
- **Payment promises and plans**, with follow-up
- **Excel import pipeline** with templates for each file format
- **Commissions** calculated per company
- **Dashboard and reports**, with export to Excel
- **Users and roles** with JWT authentication

## Tech stack

| Layer | Technology |
|---|---|
| Frontend | React 18, Vite, Material UI, React Router, Axios, Recharts |
| Backend | Node.js, Express 5, TypeScript (strict) |
| Databases | MySQL 8 with Sequelize, and MongoDB with Mongoose for the import pipeline |
| Validation and auth | Zod, JWT, bcrypt |
| Testing | Jest and Supertest |
| Operations | Docker Compose, Caddy, AWS deployment, Winston and CloudWatch logging, Sentry, scheduled jobs with node-cron |

## Architecture

The backend uses strict layers, and dependencies only point inward:

```
Request → middleware (auth, roles, logging) → Route → Controller → Service → Repository → Model
```

- **Controllers** handle HTTP and validation. **Services** hold the business logic and transactions. **Repositories** build the queries.
- **Design patterns**: Repository; Strategy and Factory for the Excel importers, so each file format has its own parser.

## My contribution

I worked mainly on the **frontend** and on developer setup:

- API client wrappers for customers, debts, promises, interactions and users, with consistent naming
- Pages and forms: companies, payment promises, customer form, debtor list connected to the backend, and settings with password change
- Dashboard connected to the API; inline validation, loading skeletons and toast notifications
- Field mapping in the Excel importer
- Database seed script (`seed.ts`), `.env.example` and the project README

## Team

- Antonio Fontes
- Felipe Sosa
