# 🏢 Sales Management System

[![.NET](https://img.shields.io/badge/.NET-8.0-blue.svg)](https://dotnet.microsoft.com/)
[![DevExpress](https://img.shields.io/badge/DevExpress-24.2.8-orange.svg)](https://www.devexpress.com/)
[![SQL Server](https://img.shields.io/badge/SQL%20Server-2019+-red.svg)](https://www.microsoft.com/en-us/sql-server/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

A comprehensive **Sales Management System** built with **C# WinForms** and **DevExpress** controls, featuring a modern 3-tier architecture, Arabic RTL support, and advanced business management capabilities.

## 🌟 Features

### 🔐 **Authentication & Security**
- Secure login system with BCrypt password encryption
- Role-based access control (RBAC)
- User session management
- Account lockout after failed attempts

### 👥 **Customer Management**
- Complete customer lifecycle management
- Customer balance tracking
- Transaction history
- Advanced search and filtering

### 📦 **Product Management**
- Product categorization and inventory tracking
- Multi-level pricing (purchase, sale, minimum)
- Stock management with alerts
- Barcode support

### 🧾 **Invoice System**
- Professional invoice generation
- Tax calculation and discount management
- PDF export capabilities
- Payment tracking

### 📊 **Analytics & Reporting**
- Real-time dashboard with charts
- Sales performance analytics
- Inventory reports
- Customer insights

### 🌐 **Internationalization**
- Full Arabic language support
- Right-to-Left (RTL) layout
- Localized date and number formatting
- Multi-language ready architecture

## 🛠️ Technology Stack

| Component | Technology |
|-----------|------------|
| **Framework** | .NET 8.0 |
| **UI Library** | DevExpress WinForms v24.2.8 |
| **Database** | SQL Server 2019+ |
| **ORM** | Entity Framework Core 8.0 |
| **Security** | BCrypt.Net |
| **Logging** | Serilog |
| **Configuration** | Microsoft.Extensions.Configuration |

## 📋 Prerequisites

- **Visual Studio 2022** or later
- **.NET 8.0 SDK** or later
- **SQL Server 2019+** (Express edition supported)
- **DevExpress WinForms Controls** v24.2.8
- **Windows 10/11** (x64)

## 🚀 Quick Start

### 1. Clone the Repository
```bash
git clone https://github.com/hamza-damra/Sales-Management-System.git
cd Sales-Management-System
```

### 2. Database Setup
1. Open **SQL Server Management Studio**
2. Execute the script: `Database/CreateDatabase.sql`
3. Verify the `FirstDB` database is created successfully

```sql
-- Create database and tables
USE master;
GO
-- Execute the complete script from Database/CreateDatabase.sql
```

### 3. Configure Connection String
Update the connection string in `appsettings.json`:
```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Data Source=YOUR_SERVER;Initial Catalog=FirstDB;Integrated Security=True;Encrypt=False;"
  }
}
```

### 4. Build and Run
```bash
# Restore NuGet packages
dotnet restore

# Build the solution
dotnet build

# Run the application
dotnet run
```

### 5. Login
Use the default credentials:
- **Username:** `admin`
- **Password:** `admin123`

## 🏗️ Project Architecture

The application follows a **3-tier architecture** pattern for maintainability and scalability:

```
📁 Sales-Management-System/
├── 🧠 BusinessLogicLayer/           # Business Logic Layer
│   ├── 👤 UserService.cs            # User management logic
│   ├── 🏢 CustomerService.cs        # Customer operations
│   ├── 📦 ProductService.cs         # Product management
│   ├── 📊 DashboardService.cs       # Analytics & reporting
│   └── ✅ ProductValidationService.cs # Business rules validation
│
├── 💾 DataAccessLayer/              # Data Access Layer
│   ├── 🗄️ SalesDbContext.cs         # Entity Framework context
│   ├── 📋 IRepository.cs            # Generic repository interface
│   ├── 🔧 Repository.cs             # Generic repository implementation
│   ├── 🔄 IUnitOfWork.cs           # Unit of Work interface
│   ├── ⚙️ UnitOfWork.cs            # Unit of Work implementation
│   ├── 👥 UserRepository.cs         # User data operations
│   ├── 🏢 CustomerRepository.cs     # Customer data operations
│   └── 📦 ProductRepository.cs      # Product data operations
│
├── 📋 Models/                       # Data Models
│   ├── 🏷️ BaseEntity.cs            # Base entity with common properties
│   ├── 👤 User.cs                  # User entity
│   ├── 🎭 Role.cs                  # Role entity
│   ├── 🏢 Customer.cs              # Customer entity
│   ├── 📂 Category.cs              # Product category entity
│   ├── 📦 Product.cs               # Product entity
│   ├── 🧾 Invoice.cs               # Invoice entity
│   ├── 📄 InvoiceItem.cs           # Invoice line items
│   └── 💳 Payment.cs               # Payment entity
│
├── 🖥️ PresentationLayer/           # User Interface Layer
│   ├── 🔐 LoginForm.cs             # Authentication form
│   ├── 📊 MainDashboardForm.cs     # Main dashboard
│   ├── 👥 CustomersForm.cs         # Customer management
│   ├── 📦 ProductsForm.cs          # Product management
│   ├── 🎨 ProductTileViewForm.cs   # Product tile view
│   ├── ➕ ProductAddEditForm.cs    # Product add/edit form
│   ├── 📈 ProductAnalyticsForm.cs  # Product analytics
│   ├── 🧾 InvoicesForm.cs          # Invoice management
│   ├── 📊 ReportsForm.cs           # Reports and analytics
│   ├── ⚙️ SettingsForm.cs          # Application settings
│   └── 👥 UsersForm.cs             # User management
│
├── 🛠️ Utilities/                   # Helper Classes
│   ├── ⚙️ ConfigurationManager.cs  # Configuration management
│   ├── 🔒 SecurityHelper.cs        # Security utilities
│   └── 🌐 ArabicHelper.cs          # Arabic/RTL support
│
├── 🗄️ Database/                    # Database Scripts
│   ├── 📝 CreateDatabase.sql       # Database creation script
│   └── 🔧 ProductStoredProcedures.sql # Stored procedures
│
├── 📚 Documentation/               # Project Documentation
│   ├── 📖 ProductManagementSystem.md
│   ├── 🧪 ProductManagementTesting.md
│   └── 🚀 DeploymentGuide.md
│
├── ⚙️ appsettings.json             # Application configuration
├── 📄 DXApplication1.csproj        # Project file
└── 📖 README.md                    # This file
```

## 🎯 Core Modules

### 🔐 **Authentication Module**
- **Secure Login System** with session management
- **Password Encryption** using BCrypt with salt
- **Role-Based Access Control** (Admin, Manager, User)
- **Account Lockout** protection against brute force attacks
- **Password Policy** enforcement

### 👥 **Customer Management**
- **Complete CRUD Operations** for customer data
- **Customer Balance Tracking** with credit limits
- **Transaction History** with detailed audit trails
- **Advanced Search & Filtering** capabilities
- **Customer Analytics** and insights

### 📦 **Product Management**
- **Multi-Category Product Organization**
- **Inventory Tracking** with real-time stock levels
- **Multi-Tier Pricing** (Purchase, Sale, Minimum prices)
- **Barcode Support** for quick product identification
- **Stock Alerts** for low inventory warnings
- **Product Analytics** with sales performance metrics

### 🧾 **Invoice & Sales**
- **Professional Invoice Generation** with customizable templates
- **Tax Calculation** with configurable tax rates
- **Discount Management** (percentage and fixed amount)
- **Payment Tracking** with multiple payment methods
- **PDF Export** for invoices and receipts
- **Sales Analytics** with trend analysis

### 📊 **Dashboard & Analytics**
- **Real-Time Dashboard** with key performance indicators
- **Interactive Charts** using DevExpress Chart Controls
- **Sales Performance Metrics** with period comparisons
- **Inventory Reports** with stock movement analysis
- **Customer Insights** with purchase behavior analytics
- **Financial Reports** with profit/loss statements

### 🌐 **Internationalization**
- **Full Arabic Language Support** with proper RTL layout
- **Localized Date/Time Formatting** for Arabic regions
- **Currency Formatting** (Saudi Riyal, USD, etc.)
- **Number Localization** with Arabic numerals support
- **Multi-Language Architecture** ready for expansion

## 🔒 Security Features

### 🛡️ **Data Protection**
- **BCrypt Password Hashing** with individual salts
- **SQL Injection Prevention** through parameterized queries
- **Input Validation** and sanitization
- **Secure Session Management**
- **Audit Logging** for all critical operations

### 👤 **Access Control**
- **Role-Based Permissions** with granular control
- **Feature-Level Security** based on user roles
- **Session Timeout** management
- **Concurrent Login Prevention**
- **Activity Monitoring** and logging

## 🖼️ Screenshots

### 🔐 Login Screen
Modern authentication interface with Arabic RTL support.

### 📊 Main Dashboard
Real-time analytics dashboard with interactive charts and KPIs.

### 📦 Product Management
Advanced product management with tile view and detailed forms.

### 👥 Customer Management
Comprehensive customer management with search and filtering capabilities.

## 🐛 Troubleshooting

### Common Issues

#### 🔌 Database Connection Issues
```bash
# Check SQL Server service status
services.msc → SQL Server (SQLEXPRESS)

# Verify connection string in appsettings.json
"Data Source=YOUR_SERVER\\SQLEXPRESS;Initial Catalog=FirstDB;Integrated Security=True;"
```

#### 🎨 DevExpress Issues
- Ensure DevExpress WinForms Controls v24.2.8 are installed
- Verify DevExpress license is valid
- Check NuGet package references

#### 🌐 Arabic/RTL Issues
- Ensure database uses `NVARCHAR` for Arabic text fields
- Verify SQL Server collation supports Arabic: `Arabic_CI_AS`
- Check Windows regional settings

#### 🏗️ Build Issues
```bash
# Clean and rebuild solution
dotnet clean
dotnet restore
dotnet build
```

## 🤝 Contributing

We welcome contributions! Please follow these guidelines:

### 🔄 Development Workflow
1. **Fork** the repository
2. **Create** a feature branch: `git checkout -b feature/amazing-feature`
3. **Commit** your changes: `git commit -m 'Add amazing feature'`
4. **Push** to the branch: `git push origin feature/amazing-feature`
5. **Open** a Pull Request

### 📝 Code Standards
- Follow **C# coding conventions**
- Use **meaningful variable names**
- Add **XML documentation** for public methods
- Include **unit tests** for new features
- Ensure **Arabic RTL compatibility**

### 🧪 Testing
- Run existing tests: `dotnet test`
- Add tests for new features
- Test Arabic text input/display
- Verify RTL layout functionality

## 📄 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

## 🆘 Support

### 📞 Getting Help
- 🐛 **Bug Reports**: [Create an Issue](https://github.com/hamza-damra/Sales-Management-System/issues)
- 💡 **Feature Requests**: [Open a Discussion](https://github.com/hamza-damra/Sales-Management-System/discussions)
- 📧 **Email Support**: Contact the maintainers

### 📚 Documentation
- 📖 [User Manual](Documentation/ProductManagementSystem.md)
- 🧪 [Testing Guide](Documentation/ProductManagementTesting.md)
- 🚀 [Deployment Guide](Documentation/DeploymentGuide.md)

## 📊 Project Status

| Component | Status | Coverage |
|-----------|--------|----------|
| 🔐 Authentication | ✅ Complete | 95% |
| 👥 Customer Management | ✅ Complete | 90% |
| 📦 Product Management | ✅ Complete | 92% |
| 🧾 Invoice System | ✅ Complete | 88% |
| 📊 Analytics | ✅ Complete | 85% |
| 🌐 Arabic Support | ✅ Complete | 98% |
| 🧪 Unit Tests | 🔄 In Progress | 70% |

## 🗺️ Roadmap

### 🎯 Version 1.1.0 (Q1 2025)
- [ ] **Mobile App** companion (Xamarin/MAUI)
- [ ] **REST API** for external integrations
- [ ] **Advanced Reporting** with custom report builder
- [ ] **Multi-Currency** support

### 🎯 Version 1.2.0 (Q2 2025)
- [ ] **Cloud Deployment** (Azure/AWS)
- [ ] **Multi-Tenant** architecture
- [ ] **Advanced Analytics** with ML insights
- [ ] **Barcode Scanning** integration

## 📈 Version History

| Version | Date | Changes |
|---------|------|---------|
| **1.0.0** | 2024-12-30 | Initial release with core features |
| **0.9.0** | 2024-12-15 | Beta release for testing |
| **0.8.0** | 2024-12-01 | Alpha release with basic functionality |

---

<div align="center">

**⭐ Star this repository if you find it helpful!**

Made with ❤️ by [Hamza Damra](https://github.com/hamza-damra)

</div>
