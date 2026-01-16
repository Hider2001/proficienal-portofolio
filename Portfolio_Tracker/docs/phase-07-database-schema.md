# Phase 07: Database Schema Design (PostgreSQL)

**Status:** ⬜ Not Started  
**Progress:** 0/5 Tasks  
**Assignee:** _________________  
**Target Completion:** _________________

---

## Phase Overview

Designs the PostgreSQL database schema for Supabase. Creates tables for projects, categories, media assets, and contact submissions with proper relationships and seed data.

---

## Progress Tracker

| # | Status | Task Name |
|---|--------|-----------|
| 1 | ⬜ | Design Projects Table |
| 2 | ⬜ | Design Categories & Tags Tables |
| 3 | ⬜ | Design Media Assets Table |
| 4 | ⬜ | Design Contact Submissions Table |
| 5 | ⬜ | Create Database Seed Script |

**Legend:** ⬜ Not Started | 🔄 In Progress | ✅ Complete | ⏸️ Blocked

---

## Task Details

### Task 1: Design Projects Table

| Property | Details |
|----------|---------|
| **UX / Product Purpose** | Stores core portfolio content |
| **Technical Notes** | PostgreSQL via Supabase, UUID primary keys |
| **Definition of Done** | DDL script + Supabase table configuration |
| **Status** | ⬜ Not Started |
| **Notes** | |

**Schema Reference:**
```sql
projects (
  id UUID PRIMARY KEY,
  title VARCHAR(255) NOT NULL,
  slug VARCHAR(255) UNIQUE,
  summary TEXT,
  description TEXT,
  thumbnail_url TEXT,
  featured BOOLEAN DEFAULT false,
  created_at TIMESTAMPTZ DEFAULT NOW()
)
```

---

### Task 2: Design Categories & Tags Tables

| Property | Details |
|----------|---------|
| **UX / Product Purpose** | Enables filtering and discovery |
| **Technical Notes** | Many-to-many junction table pattern |
| **Definition of Done** | Normalized schema with foreign key relationships |
| **Status** | ⬜ Not Started |
| **Notes** | |

**Schema Reference:**
```sql
categories (id, name, slug)
project_categories (project_id, category_id)
```

---

### Task 3: Design Media Assets Table

| Property | Details |
|----------|---------|
| **UX / Product Purpose** | Manages images, videos, documents |
| **Technical Notes** | References to Supabase Storage paths |
| **Definition of Done** | Asset table with metadata fields (dimensions, alt text) |
| **Status** | ⬜ Not Started |
| **Notes** | |

**Schema Reference:**
```sql
media (
  id UUID PRIMARY KEY,
  project_id UUID REFERENCES projects(id),
  url TEXT NOT NULL,
  type VARCHAR(50),
  alt_text TEXT,
  display_order INTEGER
)
```

---

### Task 4: Design Contact Submissions Table

| Property | Details |
|----------|---------|
| **UX / Product Purpose** | Captures leads without external services |
| **Technical Notes** | Timestamps, status enum, email reference |
| **Definition of Done** | Submissions table + RLS policies |
| **Status** | ⬜ Not Started |
| **Notes** | |

**Schema Reference:**
```sql
contact_submissions (
  id UUID PRIMARY KEY,
  name VARCHAR(255),
  email VARCHAR(255),
  message TEXT,
  status VARCHAR(50) DEFAULT 'new',
  created_at TIMESTAMPTZ DEFAULT NOW()
)
```

---

### Task 5: Create Database Seed Script

| Property | Details |
|----------|---------|
| **UX / Product Purpose** | Enables rapid environment setup |
| **Technical Notes** | SQL or Supabase CLI seeding |
| **Definition of Done** | Seed script with realistic sample data |
| **Status** | ⬜ Not Started |
| **Notes** | |

---

## Phase Deliverables Checklist

- [ ] Projects table DDL script
- [ ] Categories & junction table DDL
- [ ] Media assets table DDL
- [ ] Contact submissions table + RLS policies
- [ ] Complete seed script

---

## Sign-Off

| Role | Name | Date | Signature |
|------|------|------|-----------|
| Phase Lead | | | |
| Reviewer | | | |
