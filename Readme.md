# 🛒 E-Commerce Backend API

## 📌 Overview

This project is a robust, secure, and scalable **E-Commerce Backend API** built with Django and PostgreSQL. It supports key features like product and category management, user authentication, filtering, sorting, and pagination. The system is designed for real-world deployment and integration with frontend applications.

This project is part of the **ALX ProDev Backend Graduation Project** and is also submitted under **Project Nexus** to demonstrate real-world backend development skills.

---

## 🚀 Features

### ✅ Core Functionality

- **User Authentication** (JWT-based)
  - Register, Login
  - Token-based secure access
- **CRUD for Products and Categories**
  - Create, Read, Update, Delete
- **API Filtering and Sorting**
  - Filter products by category
  - Sort products by price (ascending or descending)
- **Pagination**
  - Efficient pagination for large product datasets

---

## ⚙️ Tech Stack

| Layer       | Technology             |
|-------------|------------------------|
| Backend     | Django, Django REST Framework |
| Database    | PostgreSQL             |
| Auth        | JWT (`djangorestframework-simplejwt`) |
| Docs        | Swagger (`drf-yasg`)   |
| Deployment  | Render (or any cloud host) |
| Others      | CORS, Environment Variables, Postman |

---

## 🗃️ Database Models

### 🧍 User
- Uses Django default User model
- Secured with JWT authentication

### 🛍️ Product
- `id`, `name`, `description`, `price`, `image`, `stock`, `category` (FK), `created_at`

### 🏷️ Category
- `id`, `name`, `slug`, `created_at`

ERD link: [📄 View ERD Diagram](https://your-erd-link.com)

---

## 🔐 Authentication

- JWT-based login and access using `djangorestframework-simplejwt`
- Obtain and refresh tokens via:
  - `/api/token/`
  - `/api/token/refresh/`

---

## 📘 API Documentation

Auto-generated using **Swagger**.

> 📍 Hosted Swagger URL: [https://your-live-domain.com/swagger/](https://your-live-domain.com/swagger/)

You can interact with all API endpoints and view schema directly from this interface.

---

## 📂 API Endpoints

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/api/products/` | GET, POST | List or create products |
| `/api/products/<id>/` | GET, PUT, DELETE | Single product operations |
| `/api/categories/` | GET, POST | List or create categories |
| `/api/categories/<id>/` | GET, PUT, DELETE | Single category operations |
| `/api/token/` | POST | Obtain JWT token |
| `/api/token/refresh/` | POST | Refresh JWT token |

---

## 📊 Filtering, Sorting, Pagination

- **Filtering**: `/api/products/?category=electronics`
- **Sorting**: `/api/products/?ordering=price` or `?ordering=-price`
- **Pagination**: `/api/products/?limit=10&offset=20`

---

## 🧠 Best Practices Implemented

- ✅ Modular Django app structure
- ✅ Environment variables for configuration
- ✅ Token-based secure auth (JWT)
- ✅ DRF serializers and query optimization with `select_related()`
- ✅ Indexing on filter/sort fields for performance
- ✅ Pagination for scalable API delivery
- ✅ Swagger auto-docs and Postman collection
- ✅ PEP8-compliant, commented, and readable code
- ✅ Git-flow version control strategy with clear commits

---

## 📺 Demo & Presentation

- 🎬 Demo Video: [YouTube or Drive Link](https://your-demo-video-link.com)
- 📊 Slide Deck: [Google Slides](https://your-slide-deck-link.com)

---

## 🌐 Deployment

> Live API Base URL: [https://your-live-domain.com/api/](https://your-live-domain.com/api/)

Hosted on **Render** (or other service). Includes:
- Auto migrations on deploy
- Swagger docs
- Live CORS-enabled API

---

## 🛠️ Getting Started Locally

### 📥 Installation

```bash
git clone https://github.com/your-username/ecommerce-backend.git
cd ecommerce-backend
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```
---
## 👨‍💻 Author
# Tsigie Beyene

Backend Developer | ALX Fellow
GitHub: @Tsigie-beyene

---
