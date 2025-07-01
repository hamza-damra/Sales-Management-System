# نظام إدارة المبيعات - Sales Management System

## نظرة عامة - Overview

نظام إدارة المبيعات هو تطبيق Windows Forms مطور باستخدام C# و DevExpress مع دعم كامل للغة العربية وتخطيط RTL. يوفر النظام إدارة شاملة للعملاء والمنتجات والفواتير والتقارير.

Sales Management System is a Windows Forms application developed using C# and DevExpress with full Arabic language support and RTL layout. The system provides comprehensive management for customers, products, invoices, and reports.

## المتطلبات التقنية - Technical Requirements

### البرمجيات المطلوبة - Required Software
- Visual Studio 2022 or later
- .NET 8.0 or later
- SQL Server 2019 or later (or SQL Server Express)
- DevExpress WinForms Controls v24.2.8

### قاعدة البيانات - Database
- SQL Server with Arabic collation support
- Connection String: `Data Source=DESKTOP-OBLI0EK\\SQLEXPRESS;Initial Catalog=FirstDB;Integrated Security=True;Encrypt=False;`

## التثبيت والإعداد - Installation and Setup

### 1. إعداد قاعدة البيانات - Database Setup

1. افتح SQL Server Management Studio
2. قم بتشغيل السكريبت الموجود في `Database/CreateDatabase.sql`
3. تأكد من إنشاء قاعدة البيانات `FirstDB` بنجاح

```sql
-- تشغيل السكريبت لإنشاء قاعدة البيانات والجداول
-- Run the script to create database and tables
USE master;
GO
-- ... (see Database/CreateDatabase.sql for full script)
```

### 2. إعداد المشروع - Project Setup

1. افتح الحل في Visual Studio 2022
2. استعادة حزم NuGet
3. تأكد من تثبيت DevExpress Controls
4. قم ببناء المشروع

```bash
# استعادة حزم NuGet - Restore NuGet packages
dotnet restore

# بناء المشروع - Build project
dotnet build
```

### 3. تشغيل التطبيق - Running the Application

1. اضغط F5 أو اختر Debug > Start Debugging
2. استخدم بيانات تسجيل الدخول الافتراضية:
   - اسم المستخدم: `admin`
   - كلمة المرور: `admin123`

## هيكل المشروع - Project Structure

```
DXApplication1/
├── BusinessLogicLayer/          # طبقة منطق الأعمال
│   ├── IUserService.cs
│   ├── UserService.cs
│   └── ICustomerService.cs
├── DataAccessLayer/             # طبقة الوصول للبيانات
│   ├── SalesDbContext.cs
│   ├── IRepository.cs
│   ├── Repository.cs
│   ├── IUnitOfWork.cs
│   ├── UnitOfWork.cs
│   ├── IUserRepository.cs
│   ├── UserRepository.cs
│   ├── ICustomerRepository.cs
│   └── CustomerRepository.cs
├── Models/                      # نماذج البيانات
│   ├── BaseEntity.cs
│   ├── User.cs
│   ├── Role.cs
│   ├── Customer.cs
│   ├── Category.cs
│   ├── Product.cs
│   ├── Invoice.cs
│   ├── InvoiceItem.cs
│   └── Payment.cs
├── PresentationLayer/           # طبقة العرض
│   ├── LoginForm.cs
│   ├── MainDashboardForm.cs
│   └── [Other Forms]
├── Utilities/                   # الأدوات المساعدة
│   ├── ConfigurationManager.cs
│   ├── SecurityHelper.cs
│   └── ArabicHelper.cs
├── Database/                    # سكريبتات قاعدة البيانات
│   └── CreateDatabase.sql
├── appsettings.json            # ملف الإعدادات
└── README.md                   # هذا الملف
```

## الميزات الرئيسية - Key Features

### 1. إدارة المستخدمين - User Management
- تسجيل الدخول الآمن مع تشفير كلمات المرور
- إدارة الأدوار والصلاحيات
- قفل المستخدمين بعد محاولات فاشلة

### 2. إدارة العملاء - Customer Management
- إضافة وتعديل وحذف العملاء
- تتبع أرصدة العملاء
- تاريخ المعاملات

### 3. إدارة المنتجات - Product Management
- تصنيف المنتجات
- تتبع المخزون
- إدارة الأسعار

### 4. نظام الفواتير - Invoice System
- إنشاء فواتير احترافية
- حساب الضرائب والخصومات
- طباعة وتصدير PDF

### 5. التقارير - Reports
- تقارير المبيعات
- تقارير العملاء
- تقارير المخزون

## الدعم العربي - Arabic Support

### خصائص RTL - RTL Features
- تخطيط من اليمين إلى اليسار
- دعم النصوص العربية
- تنسيق التواريخ والأرقام بالعربية
- واجهة مستخدم عربية كاملة

### الخطوط والتنسيق - Fonts and Formatting
- استخدام خط Tahoma للنصوص العربية
- تنسيق العملة بالريال السعودي
- تحويل الأرقام للعربية

## الأمان - Security

### تشفير كلمات المرور - Password Encryption
- استخدام BCrypt لتشفير كلمات المرور
- Salt عشوائي لكل كلمة مرور

### الصلاحيات - Permissions
- نظام أدوار متقدم
- تحكم دقيق في الصلاحيات
- منع الوصول غير المصرح به

## استكشاف الأخطاء - Troubleshooting

### مشاكل شائعة - Common Issues

1. **خطأ في الاتصال بقاعدة البيانات**
   - تأكد من تشغيل SQL Server
   - تحقق من صحة Connection String

2. **مشاكل DevExpress**
   - تأكد من تثبيت DevExpress Controls
   - تحقق من الترخيص

3. **مشاكل الترميز العربي**
   - تأكد من استخدام NVARCHAR في قاعدة البيانات
   - تحقق من إعدادات Collation

## المساهمة - Contributing

نرحب بالمساهمات لتحسين النظام. يرجى اتباع الإرشادات التالية:

1. Fork المشروع
2. إنشاء branch جديد للميزة
3. Commit التغييرات
4. Push إلى Branch
5. إنشاء Pull Request

## الترخيص - License

هذا المشروع مرخص تحت رخصة MIT. راجع ملف LICENSE للتفاصيل.

## الدعم - Support

للحصول على الدعم أو الإبلاغ عن مشاكل:
- إنشاء Issue في GitHub
- التواصل عبر البريد الإلكتروني

## معلومات الإصدار - Version Information

- الإصدار الحالي: 1.0.0
- تاريخ الإصدار: 2024-12-30
- متوافق مع: .NET 8.0, DevExpress 24.2.8

---

**ملاحظة**: هذا النظام في مرحلة التطوير. بعض الميزات قد تكون غير مكتملة.

**Note**: This system is under development. Some features may be incomplete.
