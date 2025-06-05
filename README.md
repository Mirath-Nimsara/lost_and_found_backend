# Lost and Found System – Backend (Spring Boot)

This is the backend component of the **Lost and Found Management System** developed as part of the **CMJD coursework** (Batch 108/109). It provides RESTful APIs for authentication, item management, and claim processing, secured with JWT and role-based access.

---

## 🚀 Technologies Used

- Java 21
- Spring Boot
- Spring Data JPA (Hibernate)
- Spring Security (JWT)
- MySQL
- Maven

---

## 📁 Project Structure

```
src/main/java/com/lostandfound/demo/
├── controller/         # REST Controllers (Auth, Item, Request)
├── entity/             # JPA Entities: User, Item, Request
├── service/            # Business logic layer
├── repository/         # JPA repositories (UserRepo, ItemRepo, etc.)
├── security/           # JWT filter, utils, security config
└── config/             # CORS config, password encoder
```

---

## 🔐 Roles & Access Control

| Role   | Permissions |
|--------|-------------|
| USER   | Report lost items, claim found items, view own claims |
| STAFF  | Report found items, view & manage claims |
| ADMIN  | View & delete all items |

---

## 📦 Endpoints Overview

### 🔑 Authentication
- `POST /api/auth/signup` – Register a new user
- `POST /api/auth/signin` – Login and get JWT token

### 📦 Items
- `POST /api/items/lost` – Report lost item (USER)
- `POST /api/items/found` – Report found item (STAFF)
- `GET /api/items/lost` – View all lost items
- `GET /api/items/found` – View all found items
- `DELETE /api/items/{id}` – Delete item (ADMIN)

### 📨 Claims / Requests
- `POST /api/requests/{itemId}` – Claim a found item (USER)
- `GET /api/requests/my` – View my claims (USER)
- `GET /api/requests` – View all claims (STAFF, ADMIN)
- `PUT /api/requests/{id}?status=APPROVED|REJECTED` – Update claim (STAFF)
- `DELETE /api/requests/{id}` – Delete request (ADMIN)

---

## 🛠️ Setup Instructions

1. **Clone the Repository:**

```bash
git clone https://github.com/your-username/lost-and-found-backend.git
cd lost-and-found-backend
```

2. **Configure Database:**  
In `src/main/resources/application.properties`, update:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/lost_found_db
spring.datasource.username=your_mysql_username
spring.datasource.password=your_mysql_password

jwt.secret=your-encoded-secret-key
jwt.expiration=86400000
```

3. **Run the App:**

```bash
./mvnw spring-boot:run
```

> Server will run on: `http://localhost:8080`

---

## ✅ Completed Requirements

| Feature                               | Status |
|---------------------------------------|--------|
| Spring Boot REST API structure        | ✅ Done |
| JWT Authentication & Role Auth        | ✅ Done |
| CORS config for frontend              | ✅ Done |
| CRUD for Item & Request               | ✅ Done |
| Staff claim approval workflow         | ✅ Done |
| Secure endpoints by role              | ✅ Done |
| Entity relationships mapped           | ✅ Done |

---

## 📝 Coursework Reference

**Assignment**: Backend Development  
**Framework**: Spring Boot + MySQL  
**Course**: CMJD – Comprehensive Master Java Developer  
**Batch**: 108 / 109

---

## 🧪 Testing

Use Postman or your React frontend (`localhost:3000`) to test endpoints.  
All routes require a valid JWT in `Authorization: Bearer <token>` header.

---

## 📦 Deployment (Optional)

You can deploy the app on:
- Render / Railway (Java support)
- Docker + Cloud MySQL
- AWS / Azure Spring services

---
