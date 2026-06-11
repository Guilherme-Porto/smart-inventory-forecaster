<div align="center">

<img src="https://img.shields.io/badge/status-in%20development-yellow?style=for-the-badge" alt="Status"/>
<img src="https://img.shields.io/badge/license-proprietary-red?style=for-the-badge" alt="License"/>
<img src="https://img.shields.io/badge/python-3.11+-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python"/>
<img src="https://img.shields.io/badge/node.js-20+-339933?style=for-the-badge&logo=nodedotjs&logoColor=white" alt="Node.js"/>
<img src="https://img.shields.io/badge/React-18-61DAFB?style=for-the-badge&logo=react&logoColor=black" alt="React"/>

<br/><br/>

# 📦 Smart Inventory & Sales Forecaster

**An intelligent inventory management system powered by machine learning demand forecasting.**  
Built to eliminate stockouts and overstock losses for retail and small businesses.

> ⚠️ **This is a proprietary project.** Source code is shared for portfolio and educational viewing only.  
> Commercial use or redistribution requires explicit written permission. See [`LICENSE`](LICENSE) for details.

[Report a Bug](#) · [Request a Feature](#) · [Licensing Inquiries](#-contact)

</div>

---

## 🧩 The Problem

Every retail business faces the same silent killers:

| Problem | Business Impact |
|---|---|
| **Stockout** | Lost revenue, damaged customer trust |
| **Overstock** | Tied-up capital, storage costs, waste |
| **Gut-feel purchasing** | Inconsistent decisions, no data trail |

Traditional inventory systems tell you *what you have*. This system tells you *what you'll need*.

---

## ✨ What It Does

- **Tracks inventory in real time** — full CRUD for products and stock levels
- **Ingests historical sales data** via CSV upload
- **Generates 30-day demand forecasts** per product using time-series ML models
- **Flags risk automatically** — stockout and overstock alerts on the dashboard
- **Visualizes everything** — interactive charts so non-technical users can act fast

---

## 🏗️ Architecture

The system is built as a **decoupled microservices architecture**. The AI/ML forecasting module runs as an independent service so it can be upgraded or swapped without touching the core backend.

```
┌──────────────────────────────────────────────────────────┐
│                      React Frontend                       │
│         (Dashboard · Charts · Alerts · CSV Upload)        │
└──────────────────┬───────────────────────────────────────┘
                   │ REST / JSON
┌──────────────────▼───────────────────────────────────────┐
│                  Java Core API (spring Boot)              │
│       (Auth · Inventory CRUD · Business Logic)            │
└───────┬──────────────────────────────────┬───────────────┘
        │ SQL                              │ HTTP (internal)
┌───────▼────────┐             ┌───────────▼───────────────┐
│  PostgreSQL   │             │   Python Forecasting API   │
│  (Products ·  │             │  (Pandas · Scikit-Learn ·  │
│   Sales Logs) │             │   Time-Series Models)      │
└────────────────┘             └───────────────────────────┘
```

---

## 🛠️ Tech Stack

### Frontend
| Technology | Purpose |
|---|---|
| **React 18** | Component-based UI |
| **Tailwind CSS** | Utility-first responsive styling |
| **Chart.js** | Interactive forecast & inventory charts |

### Backend (Core API)
| Technology | Purpose |
|---|---|
| **Java 17+** | High-performance backend language |
| **Spring Boot 3+** | REST API framework and dependency injection |
| **Spring Security/JWT** |Robust and stateless authentication |
| **PostgreSQL** | Relational storage for inventory and sales logs |
| **Hibernate / JPA** | Object-Relational Mapping (ORM) |

### AI / Data Science Service
| Technology | Purpose |
|---|---|
| **Python 3.11+** | Forecasting microservice |
| **Pandas** | Data ingestion and time-series preprocessing |
| **Scikit-Learn** | Regression and forecasting models |
| **FastAPI** | Lightweight HTTP layer for the Python service |

---

## 📋 Functional Requirements

| ID | Requirement | Status |
|---|---|---|
| FR1 | Product and stock CRUD | 🔄 In Progress |
| FR2 | CSV historical data upload | 🔄 In Progress |
| FR3 | 30-day demand forecast per product | 🔄 In Progress |
| FR4 | Dashboard risk alerts (stockout / overstock) | 🔄 In Progress |

## ⚙️ Non-Functional Requirements

| ID | Requirement | Decision |
|---|---|---|
| NFR1 | Forecasting module must be independently deployable | Standalone FastAPI service |
| NFR2 | Interface must be usable by non-technical operators | Mobile-responsive, no jargon |

---

## 🚀 Getting Started

### Prerequisites

- Java 17+
- Maven or Gradle
- Python 3.11+
- Node.js 20+ (for Frontend)
- PostgreSQL 15+
- npm or yarn

### Installation

**1. Clone the repository**
```bash
git clone https://github.com/Guilherme-Porto/smart-inventory-forecaster.git
cd smart-inventory-forecaster
```

**2. Set up the Core API**
```bash
cd backend
cp .env.example .env        # Fill in your DB credentials
npm install
npm run dev
```

**3. Set up the Forecasting Service**
```bash
cd forecasting-service
pip install -r requirements.txt
uvicorn main:app --reload --port 8001
```

**4. Set up the Frontend**
```bash
cd frontend
npm install
npm run dev
```

**5. Run database migrations**
```bash
cd backend
npm run migrate
```

The app will be available at `http://localhost:5173`.

---

## 📁 Project Structure

```
smart-inventory-forecaster/
├── frontend/                  # React app
│   ├── src/
│   │   ├── components/        # UI components
│   │   ├── pages/             # Route-level pages
│   │   └── hooks/             # Custom React hooks
├── backend/                   # Java Spring Boot API
│   ├── src/main/java/.../
│   │   ├── controllers/       # REST endpoints
│   │   ├── services/          # Business logic
│   │   ├── models/            # JPA Entities
│   │   └── repositories/      # Data access layer
│   └── src/main/resources/    # Configs (application.yml)
├── forecasting-service/       # Python ML service
│   ├── models/                # Scikit-Learn pipeline
│   ├── routers/               # FastAPI endpoints
│   └── data/                  # Preprocessing utilities
└── docs/                      # Architecture diagrams
```

---

## 🗺️ Roadmap

- [x] Project setup and architecture design
- [ ] Database schema and migrations
- [ ] Core inventory CRUD API
- [ ] CSV upload and data ingestion pipeline
- [ ] ML forecasting model (baseline: Linear Regression)
- [ ] Dashboard with Chart.js visualizations
- [ ] Risk alert engine
- [ ] Authentication (JWT)
- [ ] Docker Compose setup
- [ ] Improve forecasting model (ARIMA / Prophet)

---

## 📬 Contact

This project is being actively developed for commercial deployment.  
For licensing inquiries, partnerships, or business opportunities:

**Guilhermelandim22@outlook.com**  
**https://www.linkedin.com/in/guilherme--landim/**

---

## 📄 License

Copyright (c) 2025 [Guilherme Landim Porto]

All rights reserved.

This source code is made publicly available for portfolio and educational viewing purposes only. Commercial use, redistribution, modification, or incorporation into other products or services — in whole or in part — is strictly prohibited without explicit written permission from the author.

See the full [`LICENSE`](LICENSE) file for details.

---

<div align="center">
  Built by <a href="https://github.com/your-username">Guilherme Landim Porto</a> · Actively developed · Not open for contribution
</div>
