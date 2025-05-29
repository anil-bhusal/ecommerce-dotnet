
### 🛒 EcommerceApp (.NET 8 + PostgreSQL + JWT Authentication)

A simple backend API for an e-commerce platform built using ASP.NET Core 8, Entity Framework Core, PostgreSQL, and secured with JWT-based authentication. It supports user registration, login, and role-based authorization.


### ✅ Features

- Register new users with roles (`admin` or `user`)
- Login with email and password
- JWT Token-based authentication
- Secure routes using role-based authorization
- PostgreSQL database with Entity Framework Core
- API documentation via Swagger


### 💻 Technologies

- ASP.NET Core 8
- Entity Framework Core
- PostgreSQL
- JWT (JSON Web Tokens)
- Swagger for API documentation


### 🚀 Getting Started

### 1. Prerequisites

- [.NET 8 SDK](https://dotnet.microsoft.com/en-us/download/dotnet/8.0)
- [PostgreSQL](https://www.postgresql.org/download/)
- (Optional) [pgAdmin](https://www.pgadmin.org/) for DB management


### 2. Clone the Repository

```bash
git clone https://github.com/anil-bhusal/ecommerce-dotnet.git
cd ecommerce-dotnet
````

### 3. Configure the Database

Create a new PostgreSQL database:

```sql
CREATE DATABASE ecommerce;
```

---

### 4. Update `appsettings.json`

```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Host=localhost;Port=5432;Database=ecommerce;Username=postgres;Password=your_password"
  },
  "Jwt": {
    "Key": "this_is_a_secure_jwt_key_with_32_chars",
    "Issuer": "EcommerceApp",
    "Audience": "EcommerceApp"
  },
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning"
    }
  },
  "AllowedHosts": "*"
}
```

---

### 5. Apply Migrations

```bash
dotnet ef migrations add InitialCreate
dotnet ef database update
```

If `dotnet ef` is not available:

```bash
dotnet tool install --global dotnet-ef
```

---

### 6. Run the Application

```bash
dotnet run
```

Visit Swagger UI at:

```
http://localhost:5064/swagger
```

---

## 🔐 API Endpoints

### 📝 Register

`POST /api/Auth/register`

```json
{
  "username": "admin",
  "email": "admin@example.com",
  "password": "admin123",
  "role": "admin"
}
```

### 🔑 Login

`POST /api/Auth/login`

```json
{
  "email": "admin@example.com",
  "password": "admin123"
}
```

Response:

```json
{
  "token": "eyJhbGciOi..."
}
```

Use the token as:

```
Authorization: Bearer <your-token>
```

---

## 📂 Project Structure

```
EcommerceApp/
│
├── Controllers/
│   └── AuthController.cs
│
├── Data/
│   └── AppDbContext.cs
│
├── DTOs/
│   ├── RegisterDto.cs
│   └── LoginDto.cs
│
├── Interfaces/
│   └── ITokenService.cs
│
├── Models/
│   └── User.cs
│
├── Services/
│   └── TokenService.cs
│
├── Program.cs
├── appsettings.json
└── EcommerceApp.csproj
```

---

## 🧪 Testing

You can test APIs using Swagger UI or with tools like:

* [Postman](https://www.postman.com/)
* [Insomnia](https://insomnia.rest/)

---

## 📄 License

This project is licensed under the MIT License.
See the [LICENSE](LICENSE) file for details.