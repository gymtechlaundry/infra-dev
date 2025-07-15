# Infra Dev Setup for Local Development

This repository manages Docker Compose orchestration for local development of the Devin Cooper portfolio ecosystem, including:

- ✅ `portfolio-frontend` (Angular)
- ✅ `portfolio-api` (Spring Boot + MyBatis)
- ✅ `db-migration` (Flyway for DB migrations)
- ✅ `mysql-portfolio` (MySQL 8)

---

## 🏗️ Folder Structure

```
Devin Cooper/
├── infra-dev/              # This repo
│   ├── docker-compose.yml
│   ├── .env
│   └── README.md
├── portfolio-frontend/     # Angular App Repo
├── portfolio-api/          # Spring Boot App Repo
└── db-migration/           # Flyway Migration Repo
```

---

## ⚙️ Getting Started

### 1. Clone All Repositories
Make sure all repos are cloned side-by-side under the `Devin Cooper/` directory.

```bash
git clone https://github.com/your-org/infra-dev.git
git clone https://github.com/your-org/portfolio-api.git
git clone https://github.com/your-org/db-migration.git
git clone https://github.com/your-org/portfolio-frontend.git
```

### 2. Create `.env` File

Create a `.env` file in `infra-dev/` with:

```env
MYSQL_ROOT_PASSWORD=securepassword
MYSQL_DATABASE=portfolio
MYSQL_USER=portfolio_user
MYSQL_PASSWORD=securepassword
```

### 3. Start Local Dev Environment

Run the stack using Docker Compose:

```bash
docker compose up --build
```

This will:
- Start a MySQL container
- Run Flyway DB migrations
- Launch the backend API
- Serve the frontend

---

## 🐳 Services

| Service             | Port | Notes                                |
|---------------------|------|--------------------------------------|
| MySQL               | 3306 | Access with `portfolio_user`         |
| Spring Boot API     | 8080 | REST API backend                     |
| Angular Frontend    | 4200 | Dev server for frontend UI           |

---

## 🧹 Cleaning Up

```bash
docker compose down -v
```

This will stop containers and remove volumes.

---

## ✅ Tips

- Update the `depends_on` order if needed during rebuilds.
- DB credentials are shared via `.env` to keep config consistent.
- Migrations are automatically triggered on startup by the `db-migration` service.

---

## 📌 Requirements

- Docker + Docker Compose
- Git
- Java 21 (for API + migration)
- Node.js + Angular CLI (for frontend dev if running manually)

---

## 📞 Need Help?

This repo is intended for local-only dev environments. If you're seeing connection issues:
- Ensure MySQL is listening on `mysql-portfolio` container (internal name)
- Check that `.env` values are correct and consistent

---
