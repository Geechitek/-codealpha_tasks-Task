 Zomato — Food Delivery & Restaurant Discovery Platform

![Zomato](https://img.shields.io/badge/Platform-Food%20Delivery-E23744?style=for-the-badge&logo=zomato&logoColor=white)
![React Native](https://img.shields.io/badge/React_Native-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazonaws&logoColor=white)

> **Discover restaurants, order food, and read reviews — all in one place.**  
> Zomato is India's leading food-tech platform connecting millions of users with restaurants across 1000+ cities worldwide.


##  Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Architecture](#architecture)
- [Getting Started](#getting-started)
- [Environment Variables](#environment-variables)
- [API Reference](#api-reference)
- [Contributing](#contributing)
- [License](#license)


##  Overview

Zomato was founded in 2008 and has grown into one of the world's largest food-tech companies, operating in **24 countries** with over **100 million monthly active users**. The platform offers:

-  **Restaurant Discovery** — Search and explore 1.5M+ listed restaurants
-  **Food Delivery** — Real-time order tracking with 30-minute average delivery
-  **Reviews & Ratings** — Verified user reviews, photos, and menus
-  **Zomato Gold / Pro** — Subscription for discounts and priority delivery
-  **Analytics Dashboard** — For restaurant partners to track orders and revenue



##  Features

### For Users
-  Location-based restaurant discovery with map view
-  Smart search with filters (cuisine, rating, price, dietary preferences)
-  Cart management with real-time price updates
-  Live order tracking with delivery partner location
-  Coupon and offer management
-  Multi-platform support (iOS, Android, Web)

### For Restaurant Partners
-  Menu management and real-time updates
-  Order management dashboard
-  Sales analytics and insights
-  Payment settlement tracking

### For Delivery Partners
-  Optimised route suggestions
-  Earnings tracker
-  Availability toggle



##  Tech Stack

| Layer | Technology |
| **Frontend (Mobile)** | React Native, Redux, TypeScript |
| **Frontend (Web)** | React.js, Next.js, Tailwind CSS |
| **Backend** | Node.js, Express, Go (microservices) |
| **Database** | PostgreSQL, MongoDB |
| **Cache** | Redis |
| **Search** | Elasticsearch |
| **Message Queue** | Apache Kafka |
| **Maps** | Google Maps API, MapmyIndia |
| **Payments** | Razorpay, Stripe, UPI |
| **Cloud** | AWS (EC2, S3, RDS, Lambda) |
| **CDN** | Cloudflare |
| **CI/CD** | GitHub Actions, Docker, Kubernetes |



## 🏗️ Architecture

┌──────────────────────────────────────────────────┐
│                   CLIENT LAYER                   │
│         iOS App │ Android App │ Web App          │
└─────────────────────┬────────────────────────────┘
                      │ HTTPS / WebSocket
┌─────────────────────▼────────────────────────────┐
│                  API GATEWAY                     │
│          (Rate Limiting, Auth, Routing)          │
└──────┬──────────┬──────────┬─────────────────────┘
       │          │          │
┌──────▼──┐  ┌───▼────┐  ┌──▼──────────┐
│  User   │  │ Order  │  │  Restaurant │
│ Service │  │Service │  │   Service   │
└──────┬──┘  └───┬────┘  └──┬──────────┘
       │          │          │
┌──────▼──────────▼──────────▼──────────┐
│           Message Bus (Kafka)          │
└──────────────────┬─────────────────────┘
                   │
┌──────────────────▼─────────────────────┐
│         Notification Service           │
│    (Push, SMS, Email, WhatsApp)        │
└────────────────────────────────────────┘



##  Getting Started

### Prerequisites

- Node.js >= 18.x
- PostgreSQL >= 14
- Redis >= 7.0
- Docker & Docker Compose

### Installation

```bash
# Clone the repository
git clone https://github.com/zomato/zomato-platform.git
cd zomato-platform

# Install dependencies
npm install

# Copy environment config
cp .env.example .env

# Start services with Docker
docker-compose up -d

# Run database migrations
npm run migrate

# Start development server
npm run dev
```

The app will be available at `http://localhost:3000`

---

## 🔐 Environment Variables

```env
# App
PORT=3000
NODE_ENV=development

# Database
DB_HOST=localhost
DB_PORT=5432
DB_NAME=zomato_db
DB_USER=postgres
DB_PASSWORD=your_password

# Redis
REDIS_URL=redis://localhost:6379

# Auth
JWT_SECRET=your_jwt_secret
JWT_EXPIRES_IN=7d

# Google Maps
GOOGLE_MAPS_API_KEY=your_api_key

# Payments
RAZORPAY_KEY_ID=your_key
RAZORPAY_KEY_SECRET=your_secret

# AWS
AWS_ACCESS_KEY_ID=your_key
AWS_SECRET_ACCESS_KEY=your_secret
AWS_S3_BUCKET=zomato-assets
```

---

##  API Reference

### Authentication
```
POST   /api/v1/auth/signup        — Register a new user
POST   /api/v1/auth/login         — Login with email/phone + OTP
POST   /api/v1/auth/refresh       — Refresh JWT token
```

### Restaurants
```
GET    /api/v1/restaurants        — List nearby restaurants
GET    /api/v1/restaurants/:id    — Get restaurant details
GET    /api/v1/restaurants/search — Search with filters
GET    /api/v1/restaurants/:id/menu — Get full menu
```

### Orders
```
POST   /api/v1/orders             — Place a new order
GET    /api/v1/orders/:id         — Get order details
GET    /api/v1/orders/:id/track   — Live tracking
PATCH  /api/v1/orders/:id/cancel  — Cancel an order
```

### Reviews
```
POST   /api/v1/reviews            — Submit a review
GET    /api/v1/reviews/:restaurantId — Get reviews for a restaurant
```

> Full API documentation: [docs.zomato.com/api](https://docs.zomato.com/api)

---

##  Contributing

We welcome contributions! Please read our [Contributing Guide](CONTRIBUTING.md) before submitting a pull request.

```bash
# Fork the repo, then:
git checkout -b feature/your-feature-name
git commit -m "feat: add your feature"
git push origin feature/your-feature-name
# Open a Pull Request
```

Please follow our [Code of Conduct](CODE_OF_CONDUCT.md) and ensure all tests pass before submitting.

---

##  License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

<p align="center">Made with ❤️ by the Zomato Engineering Team</p>
