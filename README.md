
# Fullstack Application (Vue.js, NestJS, PostgreSQL)

This is a fullstack application using Vue.js for the frontend, NestJS for the backend, and PostgreSQL as the database. The project also includes Docker configuration to set up the environment for development , with optional PgAdmin for database management.

## Table of Contents

- [Technologies Used](#technologies-used)
- [Getting Started](#getting-started)
  - [Clone and Install Dependencies](#clone-and-install-dependencies)
  - [Using Docker](#using-docker)
- [Project Structure](#project-structure)
- [Available Scripts](#available-scripts)
- [Environment Variables](#environment-variables)
- [Docker Services](#docker-services)
- [Managing PostgreSQL with PgAdmin](#managing-postgresql-with-pgadmin)

## Technologies Used

- **Frontend**: Vue.js
- **Backend**: NestJS
- **Database**: PostgreSQL
- **Database Management**: PgAdmin
- **ORM**: Prisma
- **Docker**: For containerizing services

## Getting Started

### Clone and Install Dependencies

You can run this project either in a traditional way by cloning the repository and installing the dependencies or by using Docker for containerized development.

#### Step 1: Clone the repository

```bash
git clone <repository-url>
cd <project-directory>
git submodule update --init --recursive
```

#### Step 2: Install dependencies

**Frontend (Vue.js)**

```bash
cd Client
npm install
```

**Backend (NestJS)**

```bash
cd Server
npm install
```

## Available Scripts

### Backend (NestJS)

To run the NestJS backend locally (without Docker):

```bash
npm run dev
```

To build and run the backend:

```bash
npm run build
npm run start
```

### Frontend (Vue.js)

To run the Vue.js frontend locally:

```bash
npm run dev
```

To build the frontend for production:

```bash
npm run build
```

### Using Docker

You can run the entire application stack (**frontend**, **backend**, **PostgreSQL**, **PgAdmin**) using Docker Compose.

#### Step 1: Set up environment variables

Create a **.env** file in the root directory for both backend and frontend and define the required variables. Here’s an example for the backend:

```bash
POSTGRES_USER=postgres
POSTGRES_PASSWORD=yourpassword
POSTGRES_DB=yourdatabase
DATABASE_URL=postgresql://postgres:yourpassword@db:5432/yourdatabase
PGADMIN_DEFAULT_EMAIL=admin@admin.com
PGADMIN_DEFAULT_PASSWORD=admin
```

#### Step 2: Start Docker services

In the root directory of your project, run the following command to start all services:

```bash
docker-compose up --build
```

This will start the following services:
- **PostgreSQL** database
- **PgAdmin** (optional, for database management)
- **NestJS** backend (exposed on port **3000**)
- **Vue.js** frontend (exposed on port **5173**)

You can access the frontend by navigating to **http://localhost:5173**, the backend at **http://localhost:3000**, and PgAdmin at **http://localhost:5050**.

#### Step 3: Stop Docker services

To stop the running services, use:

```bash
docker-compose down
```

## Project Structure

```
├── Client               # Vue.js frontend
│   ├── src              # Frontend source code
│   ├── public           # Public files
│   ├── Dockerfile       # Frontend Dockerfile
│   └── package.json     # Frontend dependencies
├── Server               # NestJS backend
│   ├── src              # Backend source code
│   ├── prisma           # Prisma schema and migrations
│   ├── Dockerfile       # Backend Dockerfile
│   └── package.json     # Backend dependencies
├── docker-compose.yml   # Docker Compose configuration
└── README.md            # This file
```

## Docker Services

The following services are included in the **docker-compose.yml** file:

  1. **db** : PostgreSQL database service.
  2. **pgadmin** : PgAdmin service for managing the database.
  3. **backend** : NestJS backend service.
  4. **frontend** : Vue.js frontend service.

### Health Checks

PostgreSQL has a built-in health check using **pg_isready** to ensure the service is running correctly.

## Managing PostgreSQL with PgAdmin

If you prefer to manage the PostgreSQL database via a graphical interface, you can use **PgAdmin**. It is accessible at **http://localhost:5050** with the default credentials set in your **.env** file:

- **Email**: **admin@admin.com**
- **Password**: **admin**

You can add the PostgreSQL database to PgAdmin using the following credentials:

- **Host**:**db**
- **Port**:**5432**
- **Username**:**POSTGRES_USER** (from **.env**)
- **Password**:**POSTGRES_PASSWORD** (from **.env**)
