# Lost and Found System – Backend (Spring Boot)


---

## 🚀 Technologies Used

- Java 21
- Spring Data JPA (Hibernate)
- Spring Security (JWT)
- MySQL
- Maven
- Spring Boot


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




## 📦 Deployment (Optional)

You can deploy the app on:
- Render / Railway (Java support)
- Docker + Cloud MySQL
- AWS / Azure Spring services

---
