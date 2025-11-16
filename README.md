# 🪙 CoinRa Backend Code

A Node.js-based backend system for managing personal finances, transactions, and dream savings with secure PostgreSQL database integration using Neon.

---

## 📋 Overview

The CoinRa Backend is a RESTful API designed to handle financial transactions, user savings goals, and account summaries.  
It ensures secure and reliable data management through rate limiting, cron jobs, and robust error handling.

---

## ✨ Features

- **Transaction Management** — Create, delete, and retrieve financial transactions  
- **Dream Savings** — Manage custom savings goals  
- **Financial Summary** — Overview of balance, income, and expenses  
- **Rate Limiting** — Redis-based API protection  
- **Health Checks** — Automated monitoring via cron jobs  
- **Data Integrity** — PostgreSQL with safe query handling  

---

## 🛠️ Technologies Used

- **Node.js** – Runtime environment  
- **Express.js** – Web framework  
- **PostgreSQL** – Database  
- **Neon** – Serverless PostgreSQL host  
- **Redis** – Rate limiting and caching  
- **Cron** – Scheduled jobs  
- **CORS** – Cross-origin access  

---

## 🗄️ Database Schema

### 🧮 Transactions Table

```sql
CREATE TABLE transactions(
    id SERIAL PRIMARY KEY,
    user_id VARCHAR(255) NOT NULL,
    title VARCHAR(255) NOT NULL,
    amount DECIMAL(10,2) NOT NULL,
    category VARCHAR(255) NOT NULL,
    created_at DATE NOT NULL DEFAULT CURRENT_DATE
);
```

### 🎯 Dream Savings Table

```sql
CREATE TABLE dream_savings (
    id SERIAL PRIMARY KEY,
    user_id VARCHAR(255) NOT NULL,
    title VARCHAR(255) NOT NULL,
    amount DECIMAL(10,2) NOT NULL,
    created_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

---

## 🚀 Getting Started

### 📌 Prerequisites
- Node.js **16 or higher**
- **PostgreSQL database**
- **Redis instance (for rate limiting)**

---

## ⚙️ Installation & Setup

### 1️⃣ Clone the repository

```bash
git clone https://github.com/yourusername/wallet-management-backend.git
cd wallet-management-backend
```

### 2️⃣ Install dependencies

```bash
npm install
```

### 3️⃣ Create a `.env` file with:

```ini
DATABASE_URL=your_neon_postgresql_connection_string
UPSTASH_REDIS_REST_URL=your_redis_url
UPSTASH_REDIS_REST_TOKEN=your_redis_token
PORT=5001
NODE_ENV=development
API_URL=your_deployment_url
```

### 4️⃣ Initialize the database
The server will **automatically create required tables** on startup.

### 5️⃣ Run the application

```bash
cd backend
npm start
```

---

## 📡 API Endpoints

### Transaction Routes

```
GET    /api/transactions/:userId        → Get user transactions  
POST   /api/transactions                → Create new transaction  
DELETE /api/transactions/:id            → Delete transaction  
GET    /api/transactions/summary/:userId → Financial summary  
```

### Dream Savings Routes

```
GET    /api/transactions/dream-savings/:userId   → Get dream savings  
POST   /api/transactions/dream-savings/:userId   → Add dream saving  
DELETE /api/transactions/dream-savings/:userId   → Delete dream saving  
```

### Health Check

```
GET /health → System health status  
```

---

## 🔒 Security Features

- Redis rate limiting (100 requests / 60 seconds)  
- Input validation  
- CORS configuration  
- SQL injection prevention (parameterized queries)  

---

## ⚙️ Configuration

### Cron Job
- Automatically pings `/health` every **14 minutes** in production.

### Rate Limiting
- Uses Redis sliding window algorithm.

---

## 🚀 Deployment

- Optimized for platforms like **Render**, **Railway**, **Vercel**, etc.
- Set all required environment variables
- Ensure PostgreSQL (Neon) + Redis connections are active
- Backend auto-creates database tables on first run

---

## 🤝 Contributing

Contributions are welcome!  
Feel free to submit **pull requests** or open **issues** for improvements.

---
