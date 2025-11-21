Production-grade backend powering *Telemedicine Platform*, built for:

•⁠  ⁠*100,000+ daily consultations*
•⁠  ⁠*99.95% availability*
•⁠  ⁠*p95 < 200ms read latency*
•⁠  ⁠*Scalable, secure, modular architecture*

---

## 🎯 Project Overview

This repository provides a production-ready backend built using *NestJS, **PostgreSQL, **Redis, and **Docker*, following enterprise architecture guidelines for scalability, observability, and security.

---

## 🧱 Core Technologies

| Layer              | Technology              | Rationale                                          |
| ------------------ | ----------------------- | -------------------------------------------------- |
| *Backend*        | Node.js (NestJS)        | Modular DI-based architecture, guideline compliant |
| *Database*       | PostgreSQL              | Primary transactional database                     |
| *Caching*        | Redis                   | High-speed caching to meet latency SLAs            |
| *Infrastructure* | Docker / Docker Compose | Containerization & Infra-as-Code                   |
| *Security*       | JWT, bcrypt, RBAC       | Strong encryption & role-based access control      |

---

## 🚀 Getting Started

### Prerequisites

•⁠  ⁠*Docker* → required for Postgres & Redis
•⁠  ⁠*Node.js / npm* → required to run the NestJS backend

---

## 🔧 Installation & Setup

### 1️⃣ Clone the Repository

⁠ bash
git clone <your-ssh-or-https-url>
cd doctor-booking-system
 ⁠

---

### 2️⃣ Create Environment Variables File

Create a file named ⁠ .env ⁠ in the project root:

⁠ ini
# .env
POSTGRES_USER=amrutamuser
POSTGRES_PASSWORD=securepassword
POSTGRES_DB=amrutam_db
POSTGRES_PORT=5432

REDIS_HOST=redis
REDIS_PORT=6379

# IMPORTANT: JWT secret for signing tokens
JWT_SECRET=YOUR_SUPER_SECURE_TOKEN_FOR_SIGNING_JWTS
 ⁠

---

### 3️⃣ Launch Infrastructure (Postgres + Redis)

⁠ bash
docker-compose up -d
 ⁠

---

### 4️⃣ Install Dependencies & Start Backend

⁠ bash
npm install
npm run start:dev
 ⁠

Your application will start at:

👉 *[http://localhost:3000](http://localhost:3000)*

---

## ⚙️ Core Architecture & Modules

The backend follows a *clean Modular Service Architecture* with separate domain-driven modules.

---

## 🔐 Authentication Module (Auth)

### Endpoints

| Workflow         | Method | Endpoint           | Feature                               |
| ---------------- | ------ | ------------------ | ------------------------------------- |
| *Registration* | POST   | ⁠ /auth/register ⁠   | bcrypt password hashing & validation  |
| *Login*        | POST   | ⁠ /auth/login ⁠      | JWT-based authentication              |
| *Role Update*  | POST   | ⁠ /auth/admin/role ⁠ | Access controlled via ⁠ @Roles(ADMIN) ⁠ |

---

## 📅 Booking Module (High-Scale Slot Booking)

### Endpoints

| Workflow                  | Method | Endpoint                | Feature                                  |
| ------------------------- | ------ | ----------------------- | ---------------------------------------- |
| *Availability Search*   | GET    | ⁠ /booking/slots/search ⁠ | Redis Cache (Cache-Aside Pattern)        |
| *Transactional Booking* | POST   | ⁠ /booking/slots/book ⁠   | Pessimistic locking & concurrency safety |

---

## 🩺 Consultation Module

### Endpoints

| Workflow                | Method | Endpoint                         | Feature                    |
| ----------------------- | ------ | -------------------------------- | -------------------------- |
| *Upload Prescription* | POST   | ⁠ /consultation/:id/prescription ⁠ | Asynchronous audit logging |

---
