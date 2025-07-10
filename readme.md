
# .NET POC

A Proof of Concept (POC) project using the .NET framework, designed to demonstrate containerized deployment and integration with SQL Server. This repository showcases the essential components required for building, running, and connecting a .NET Core backend application with a SQL database using Docker.

## 🚀 Features

- ASP.NET Core Web API backend
- SQL Server integration
- Dockerized services with `Dockerfile`
- Easy environment configuration via `appsettings.json`
- Multi-container setup using Docker Compose

## 🛠️ Technologies Used

- [.NET 6+](https://dotnet.microsoft.com/)
- ASP.NET Core Web API
- SQL Server
- Docker & Docker Compose

## 📁 Project Structure

```plaintext
.NET_POC/
│
├── Backend/                 # .NET backend code
│   ├── Controllers/         # API controllers
│   ├── Models/              # Data models
│   ├── appsettings.json     # Configuration file
│   └── Dockerfile           # Backend Dockerfile
│
├── Database/                # SQL Server container config
│   └── init.sql             # Optional DB init script
│
├── docker-compose.yml       # Multi-container setup
└── README.md                # Project documentation
```

## 🐳 Getting Started with Docker

### Prerequisites

- [.NET SDK](https://dotnet.microsoft.com/download)
- [Docker](https://www.docker.com/products/docker-desktop)

### Build and Run with Docker Compose

```bash
docker-compose up --build
```

This will:
- Build the .NET backend container
- Start a SQL Server container
- Link both containers together

### Access the API

Once running, access the API at:  
```
http://localhost:5000
```

## ⚙️ Configuration

Edit `appsettings.json` to modify environment settings or update the SQL connection string as needed:

```json
"ConnectionStrings": {
  "DefaultConnection": "Server=sqlserver;Database=MyDb;User Id=sa;Password=YourStrongPassword;"
}
```

## 🧪 Testing the API

You can use tools like:

- [Postman](https://www.postman.com/)
- [curl](https://curl.se/)
- Browser (for simple GET endpoints)

## 📦 Building Without Docker

```bash
cd Backend
dotnet build
dotnet run
```

## 📌 Future Enhancements

- Add authentication/authorization
- Integrate Entity Framework Core
- Add unit/integration tests
- CI/CD pipeline integration (e.g., GitHub Actions)

## 🤝 Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you'd like to change.

---

**Author**: [@atharrvv](https://github.com/atharrvv)  
License: MIT
