# Multi-Tenant Backend Database Schema

This repository contains a PostgreSQL database schema designed for a multi-tenant healthcare and e-commerce platform. The schema supports multiple tenants (brands) within a single database, with strict tenant isolation enforced at the database level.



## Main Domains Covered

### CMS / Content

* Pages and page sections for tenant-specific landing pages
* Media/file associations
* Slug-based routing (domain handled at tenant level)

### Forms \& Questionnaires

* Reusable, tenant-scoped forms
* Form submissions separated from answers
* Support for multiple submissions per user

### Healthcare

* Patients linked to tenant-scoped users
* Consultations and prescriptions with correct lifecycle modeling

### E-Commerce

* Products, categories, and product categorization
* Orders, order items, payments
* Shipping with address snapshotting



## Running the Schema

### Requirements

* PostgreSQL 14+
* psql

### Apply migrations

```
psql "$DATABASE\_URL" -f dbdiagram_docs/db_design.sql
```

Migrations are ordered to respect table dependencies.





## Notes \& Tradeoffs

* The schema favors explicit relational integrity over application-level guarantees.
* Address data is snapshotted in shipping records to preserve historical accuracy.
* Product variants, inventory, and payment event logs can be added in future iterations.





