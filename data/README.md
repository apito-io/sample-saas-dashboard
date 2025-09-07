# SaaS Dashboard Sample Data

This folder contains realistic multi-tenant sample data for the SaaS Dashboard template:

## Organization-Based Multi-Tenancy Structure

```
data/
├── organization/       # 5 tenant organizations
│   ├── [uuid].json     # Individual organization files
│   └── relation.json   # Organization relationships
├── user/              # 20 users across organizations
│   ├── [uuid].json     # Individual user files
│   └── relation.json   # User relationships
├── analytics_event/   # 15 business intelligence events
│   ├── [uuid].json     # Individual event files
│   └── relation.json   # Event relationships
└── subscription/      # 15 subscription records
    ├── [uuid].json     # Individual subscription files
    └── relation.json   # Subscription relationships
```

## SaaS Multi-Tenancy Features

### Organization-Based Isolation
- **5 Organizations**: Different business types and sizes
- **Tenant Filtering**: All data properly isolated by organization_id
- **Cross-Tenant Security**: Complete data separation for compliance

### Sample Organizations
1. **Tech Startup** - Software development and analytics
2. **E-commerce Platform** - Online retail analytics
3. **Healthcare Services** - Patient and operational analytics
4. **Financial Services** - Investment and trading analytics
5. **Educational Institute** - Learning and enrollment analytics

## Sample Data Features

### Organizations (5 records - Tenant Model)
- Complete business profiles with industry classifications
- Various sizes: Startup, SMB, Enterprise
- Website and contact information
- Status tracking and creation dates
- Tenant isolation boundaries

### Users (20 records)
- User management within organizations
- Role-based access and permissions (Admin, Manager, Analyst, Viewer)
- Last login tracking and status monitoring
- Organization membership isolation
- Display names and authentication details

### Analytics Events (15 records)
- Business intelligence and event tracking
- Event types: page_view, user_action, conversion, error
- Structured event_data objects with flexible schemas
- Session tracking and IP address logging
- Timestamp-based analytics data
- Organization-based data isolation

### Subscriptions (15 records)
- SaaS subscription and billing management
- Plan types: Starter, Professional, Enterprise, Custom
- Billing cycles: monthly, annually, custom
- Status tracking: active, cancelled, past_due, trial
- Amount tracking and payment management
- Organization-based subscription isolation

## Relationship Format

### Organization Relations (Tenant)
```json
{
  "organization-uuid": {
    "user": {
      "relation_type": "has_many",
      "ids": ["user-uuid-1", "user-uuid-2"]
    },
    "analytics_event": {
      "relation_type": "has_many",
      "ids": ["event-uuid-1", "event-uuid-2"]
    },
    "subscription": {
      "relation_type": "has_many",
      "ids": ["subscription-uuid-1"]
    }
  }
}
```

### User Relations
```json
{
  "user-uuid": {
    "organization": {
      "relation_type": "has_one",
      "id": "organization-uuid"        // Tenant isolation
    },
    "analytics_event": {
      "relation_type": "has_many",
      "ids": ["event-uuid-1", "event-uuid-2"]
    }
  }
}
```

### Analytics Event Relations
```json
{
  "event-uuid": {
    "organization": {
      "relation_type": "has_one",
      "id": "organization-uuid"        // Tenant isolation
    },
    "user": {
      "relation_type": "has_one",
      "id": "user-uuid"               // Event attribution
    }
  }
}
```

## Multi-Tenant Data Patterns

### Tenant Isolation
- All models reference organization_id for data separation
- Cross-organization queries automatically filtered
- Secure tenant boundaries for compliance and privacy

### Business Intelligence
- Event-based analytics data collection
- User behavior tracking and analysis
- Organizational performance metrics
- Custom event data structures

### SaaS Management
- Subscription lifecycle management
- User role and permission management
- Organization onboarding and settings
- Usage analytics and reporting

### Object Fields (Analytics Events)
```json
{
  "event_data": {
    "page": "/dashboard",
    "user_agent": "Mozilla/5.0...",
    "referrer": "https://example.com",
    "custom_properties": {
      "feature": "analytics_view",
      "plan": "professional"
    }
  }
}
```

## Data Generation

This SaaS dashboard data was generated using the Apito Data Generator with multi-tenant support:

```bash
# Regenerate multi-tenant data
./apito-gen

# Verify tenant isolation
grep -r "organization_id" *.json
```

## Statistics

- **Total Files**: 59
- **Organizations**: 5 tenant entities (isolation boundaries)
- **Users**: 20 user profiles with role-based access
- **Analytics Events**: 15 business intelligence data points
- **Subscriptions**: 15 billing and plan management records
- **Relationships**: 100% tenant isolation maintained
- **UUID Format**: All files use UUID v4 naming
- **SaaS Architecture**: Proper multi-tenant data separation
- **Object Fields**: Flexible analytics data structures

## Import Instructions

### Via Apito Dashboard
1. Create new SaaS project with organization tenant model
2. Import schema.json with multi-tenant configuration
3. Upload data folder maintaining organization isolation
4. Verify tenant filtering and dashboard queries

### Via Apito CLI
```bash
apito import schema.json --saas --tenant-model=organization
apito import data/ --preserve-tenant-structure
```

## Use Cases Demonstrated

- **SaaS Analytics Platforms**: Multi-tenant dashboard systems
- **Business Intelligence**: Data-driven organizational insights
- **User Management**: Role-based access within organizations
- **Subscription Management**: SaaS billing and plan tracking
- **Event Tracking**: Business analytics and performance monitoring

---

**Note**: This demonstrates comprehensive SaaS dashboard architecture with organization-based multi-tenancy, business intelligence capabilities, and subscription management patterns suitable for analytics platforms and business dashboard applications.
