# ACLED-Conflict-Data-API
A production-style backend REST API built with FastAPI, MySQL, and Docker to serve conflict analytics data. The API exposes analytics-ready endpoints designed for research, dashboards, and data-driven applications.  ⚠️ This project focuses on backend engineering and data access, not frontend UI development.

# Project Overview

This backend service provides structured access to conflict-related analytics data via RESTful endpoints.
It is designed to support:
- Research workflows
- Data science and analytics teams
- Dashboards (e.g., Tableau)
- Web or internal applications

The API connects to a MySQL database containing pre-aggregated analytical views and serves data as JSON.

# Architecture
Client (Tableau / Web App / API Consumer)
        ↓
FastAPI Backend (Python)
        ↓
MySQL Database (Analytics Views)

- FastAPI handles routing, validation, and OpenAPI documentation
- MySQL stores cleaned and aggregated conflict analytics
- Docker provides portable, reproducible deployment
- Swagger / OpenAPI is auto-generated for developer interaction

# API Endpoints
Global Conflict Trends
GET /api/conflict/trends
Returns yearly global totals of conflict-related deaths.

Example response
[
  { "year": 2000, "total_conflict_deaths": 91123 },
  { "year": 2001, "total_conflict_deaths": 34996 }
]

# Country-Level Summary
GET /api/conflict/countries

Returns total conflict deaths aggregated by country.

# Country Time-Series Detail

GET /api/conflict/country/{country_name}

Returns year-by-year conflict metrics for a selected country.

# OpenAPI Documentation (Not a Frontend)

The API automatically generates OpenAPI / Swagger documentation at:

http://localhost:8000/docs


This interface is:

- A developer tool, not a frontend application
- Used to explore, test, and validate backend endpoints
- Common in production backend systems

# Tech Stack
**Python** (FastAPI)
**MySQL**
**SQL analytics views**
**Docker**
**Swagger / OpenAPI**

# Running the API Locally (Without Docker)
pip install -r requirements.txt
uvicorn main:app --reload


## Access Swagger UI:

http://localhost:8000/docs

# Running the API with Docker
docker build -t acled-conflict-api .

docker run -d -p 8000:8000 --name acled-api acled-conflict-api

**Verify container**:

docker ps

# Environment Configuration

Sensitive configuration is managed via environment variables.

Create a .env file based on:

.env.example


Example:

DB_HOST=localhost
DB_USER=root
DB_PASSWORD=your_password
DB_NAME=conflict_analytics

# Intended Extensions
- Tableau dashboards consuming API or database views
- Additional filtering and query parameters
- Authentication and access control
- Cloud deployment (AWS / DigitalOcean)

# Why This Project

This project demonstrates:
- Backend API design
- SQL-driven analytics
- Clean data access layers
- Containerized deployment
- Production-style documentation

It is intentionally backend-focused and designed to integrate with downstream visualization and analytics tools.

# Screenshots

See docs/screenshots/ for:

Swagger UI

<img width="1304" height="624" alt="image" src="https://github.com/user-attachments/assets/e78e6bd6-841f-4b83-b9b8-6203e1a58114" />

# API responses
### GET/Country/Trends

<img width="1079" height="588" alt="image" src="https://github.com/user-attachments/assets/4fe73fb2-1391-4293-93f4-531f4d3a315d" />

### GET/Api/Conflict/Country
<img width="1050" height="590" alt="image" src="https://github.com/user-attachments/assets/b0f6b791-2b7e-47c3-96e0-315e4c5e8e7a" />

### GET/api/conflict/country/{country_name}
<img width="1071" height="586" alt="image" src="https://github.com/user-attachments/assets/551386b0-9cbe-4593-b523-71c36676e519" />

Docker container status

License

MIT
