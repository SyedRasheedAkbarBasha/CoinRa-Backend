# Wallet Management System Backend

A Node.js-based backend system for managing personal finances, transactions, and dream savings with secure PostgreSQL database integration using Neon.

## 📋 Overview

The Wallet Management System is a RESTful API backend designed to handle financial transactions, user savings goals, and account summaries. It ensures secure and reliable data management through rate limiting, cron jobs, and robust error handling.

## ✨ Features

- **Transaction Management**: Create, delete, and retrieve financial transactions
- **Dream Savings**: Set up and manage savings goals for specific purposes
- **Financial Summary**: Get balance, income, and expenses overview
- **Rate Limiting**: Protect API endpoints from abuse
- **Health Checks**: Automated system monitoring with cron jobs
- **Data Integrity**: PostgreSQL with proper transaction handling

## 🛠️ Technologies Used

- **Node.js** - Runtime environment
- **Express.js** - Web framework
- **PostgreSQL** - Database management system
- **Neon** - Serverless PostgreSQL platform
- **Redis** - Rate limiting and caching
- **Cron** - Scheduled task management
- **CORS** - Cross-origin resource sharing

## 🗄️ Database Schema

### Transactions Table

CREATE TABLE transactions(
    id SERIAL PRIMARY KEY,
    user_id VARCHAR(255) NOT NULL,
    title VARCHAR(255) NOT NULL,
    amount DECIMAL(10,2) NOT NULL,
    category VARCHAR(255) NOT NULL,
    created_at DATE NOT NULL DEFAULT CURRENT_DATE
);
## Dream Savings Table
sql
CREATE TABLE dream_savings (
    id SERIAL PRIMARY KEY,
    user_id VARCHAR(255) NOT NULL,
    title VARCHAR(255) NOT NULL,
    amount DECIMAL(10,2) NOT NULL,
    created_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
## Getting Started
Prerequisites
Node.js 16 or higher

- **PostgreSQL database**

- **Redis instance (for rate limiting)**

## Installation & Setup
Clone the repository


git clone https://github.com/yourusername/wallet-management-backend.git
cd wallet-management-backend

## Install dependencies

npm install
Set up environment variables

## Create a .env file with:

DATABASE_URL=your_neon_postgresql_connection_string
UPSTASH_REDIS_REST_URL=your_redis_url
UPSTASH_REDIS_REST_TOKEN=your_redis_token
PORT=5001
NODE_ENV=development
API_URL=your_deployment_url
Initialize the database
The server will automatically create required tables on startup

## Run the application
cd backend
npm start

## 📡 API Endpoints

Transactions
**GET /api/transactions/:userId** - Get user transactions

**POST /api/transactions** - Create new transaction

**DELETE /api/transactions/:id** - Delete transaction

**GET /api/transactions/summary/:userId** - Get financial summary

## Dream Savings
**GET /api/transactions/dream-savings/:userId** - Get dream savings

**POST /api/transactions/dream-savings/:userId** - Add dream saving

**DELETE /api/transactions/dream-savings/:userId** - Delete dream saving

## Health Check
**GET /health** - System health status

## 🔒 Security Features
- Rate limiting (100 requests per 60 seconds)

- Input validation and error handling

- CORS configuration

- SQL injection prevention with parameterized queries

## ⚙️ Configuration

 **Cron Job**
- Automatically pings health endpoint every 14 minutes in production


 **Rate Limiting**
 - Uses Redis for sliding window rate limiting


## 🚀 Deployment
- The application is configured for deployment on platforms on Render:

- Set environment variables in your deployment platform

- Ensure database connection is properly configured

- The system will auto-create tables on first run

## 🤝 Contributing
- Contributions are welcome! Please feel free to submit pull requests or open issues for suggestions.
