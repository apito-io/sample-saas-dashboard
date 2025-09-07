# SaaS Dashboard - Apito Engine Template

📊 **A comprehensive SaaS analytics dashboard with organization-based multi-tenancy and business intelligence features**

[![Apito Engine](https://img.shields.io/badge/Apito-Engine-blue?style=flat&logo=graphql)](https://apito.io)
[![Project Type](https://img.shields.io/badge/Project%20Type-SaaS-red?style=flat)](#project-type)
[![Tenant Model](https://img.shields.io/badge/Tenant%20Model-Organization-purple?style=flat)](#multi-tenancy)
[![Models](https://img.shields.io/badge/Models-4-orange?style=flat)](#data-models)
[![Sample Data](https://img.shields.io/badge/Sample%20Data-59%20Files-purple?style=flat)](#sample-data)

## 🚀 Quick Start

1. **Import Schema**: Use `schema.json` to set up your Apito Engine project
2. **Configure Multi-tenancy**: Reference `config.yml` for SaaS setup
3. **Load Sample Data**: Import the `data/` folder for realistic examples
4. **Set Up Organizations**: Configure tenant isolation
5. **Customize**: Add additional dashboard and analytics features

## 📋 Project Overview

- **Project Type**: SaaS (Multi-tenant)
- **Tenant Model**: Organization
- **Difficulty Level**: Advanced
- **Category**: Analytics & Business Intelligence

### **Key Features**

- ✅ Multi-tenant organization support
- ✅ User management and roles
- ✅ Analytics event tracking
- ✅ Subscription management
- ✅ Organization-based data isolation
- ✅ Business intelligence foundation
- ✅ Complete SaaS infrastructure
- ✅ Complete sample data with relationships

## 🏗️ Data Models

### **🏢 Organization Model** (5 records) - Tenant

Multi-tenant organization entity for complete data isolation.

**Key Fields:**

- `name`, `slug`, `description`
- `website`, `industry`, `size`
- `created_at`, `status`
- Tenant isolation for all related data

### **👤 User Model** (20 records)

User management within organizations.

**Key Fields:**

- `username`, `email`, `display_name`
- `role`, `status`, `last_login`
- `organization_id` (tenant relationship)

### **📈 Analytics Event Model** (15 records)

Business intelligence and event tracking.

**Key Fields:**

- `event_type`, `event_data` (object)
- `timestamp`, `user_id`
- `session_id`, `ip_address`
- `organization_id` (tenant isolation)

### **💳 Subscription Model** (15 records)

SaaS subscription and billing management.

**Key Fields:**

- `plan_type`, `status`, `amount`
- `start_date`, `end_date`, `billing_cycle`
- `organization_id` (tenant relationship)

## 🔒 Multi-Tenancy

Implements **organization-based multi-tenancy**:

### **Tenant Isolation**

- Each organization sees only their own data
- Automatic tenant-based filtering on all queries
- Secure data separation for compliance

### **Organization Structure**

```
Organization (Tenant)
├── Users (Team members and roles)
├── Analytics Events (Business intelligence)
└── Subscriptions (Billing and plans)
```

## 📊 Sample Data

**59 total files** with realistic SaaS dashboard content:

- **5 Organizations** - Different business types and sizes
- **20 Users** - Various roles and access levels
- **15 Analytics Events** - Business intelligence data
- **15 Subscriptions** - Different plans and billing cycles

## 🎯 Use Cases

Perfect for building:

- **SaaS Analytics Platforms** - Multi-tenant dashboards
- **Business Intelligence** - Data-driven insights
- **User Management Systems** - Organization-based access
- **Subscription Management** - SaaS billing and plans
- **Admin Dashboards** - Tenant management interfaces

## 🔧 Technical Highlights

- **Multi-tenant Architecture**: Organization-based isolation
- **Analytics Tracking**: Event-based data collection
- **User Management**: Role-based access control
- **Subscription Logic**: SaaS billing foundations
- **Object Fields**: Flexible event data storage

## 📦 Installation

```bash
# Clone repository
git clone https://github.com/apito-io/sample-saas-dashboard

# Import to Apito Engine (SaaS mode)
apito import schema.json --saas --tenant-model=organization
apito import data/
```

## 🏢 SaaS Configuration

```yaml
project_type: "saas"
tenant_model: "organization"
```

## 🙋‍♂️ Support

- **Documentation**: [Apito Engine Docs](https://docs.apito.io)
- **SaaS Guide**: [Multi-tenant Setup](https://docs.apito.io/saas)
- **Issues**: [GitHub Issues](https://github.com/apito-io/sample-saas-dashboard/issues)
- **Email**: support@apito.io

---

**Built with ❤️ using [Apito Engine](https://apito.io)**
