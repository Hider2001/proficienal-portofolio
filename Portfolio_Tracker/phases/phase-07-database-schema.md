# Phase 07: Database Schema Design (PostgreSQL)

**Status:** ⬜ Not Started  
**Progress:** 0/6 Tasks  
**Assignee:** _________________  
**Target Completion:** _________________

---

## Phase Overview

Designs the PostgreSQL schema with **multilingual content storage**—separate translation tables or JSON columns for EN/AR content.

---

## Progress Tracker

| # | Status | Task Name |
|---|--------|-----------|
| 1 | ⬜ | Design Projects Table (Multilingual) |
| 2 | ⬜ | Design Categories & Tags Tables (i18n) |
| 3 | ⬜ | Design Media Assets Table |
| 4 | ⬜ | Design Contact Submissions Table |
| 5 | ⬜ | Design UI Translations Table |
| 6 | ⬜ | Create Database Seed Script (EN/AR) |

**Legend:** ⬜ Not Started | 🔄 In Progress | ✅ Complete | ⏸️ Blocked

---

## Task Details

### Task 1: Design Projects Table (Multilingual)

| Property | Details |
|----------|---------|
| **UX / Product Purpose** | Stores project content in both languages |
| **Technical Notes** | Option A: `title_en`, `title_ar` columns. Option B: `translations` JSONB |
| **Definition of Done** | DDL script with multilingual content strategy |
| **Status** | ⬜ Not Started |
| **Notes** | |

**Schema Reference (Option A - Separate Columns):**
```sql
projects (
  id UUID PRIMARY KEY,
  slug VARCHAR(255) UNIQUE,
  title_en VARCHAR(255),
  title_ar VARCHAR(255),
  summary_en TEXT,
  summary_ar TEXT,
  description_en TEXT,
  description_ar TEXT,
  thumbnail_url TEXT,
  featured BOOLEAN DEFAULT false,
  created_at TIMESTAMPTZ DEFAULT NOW()
)
```

**Schema Reference (Option B - JSONB):**
```sql
projects (
  id UUID PRIMARY KEY,
  slug VARCHAR(255) UNIQUE,
  translations JSONB, -- {"en": {...}, "ar": {...}}
  thumbnail_url TEXT,
  featured BOOLEAN DEFAULT false,
  created_at TIMESTAMPTZ DEFAULT NOW()
)
```

---

### Task 2: Design Categories & Tags Tables (i18n)

| Property | Details |
|----------|---------|
| **UX / Product Purpose** | Category names display in user's language |
| **Technical Notes** | `name_en`, `name_ar` or translations JSONB |
| **Definition of Done** | Category schema with bilingual labels |
| **Status** | ⬜ Not Started |
| **Notes** | |

---

### Task 3: Design Media Assets Table

| Property | Details |
|----------|---------|
| **UX / Product Purpose** | Manages images, videos, documents |
| **Technical Notes** | Alt text needs EN/AR versions for accessibility |
| **Definition of Done** | Asset table with bilingual alt text |
| **Status** | ⬜ Not Started |
| **Notes** | |

---

### Task 4: Design Contact Submissions Table

| Property | Details |
|----------|---------|
| **UX / Product Purpose** | Captures leads without external services |
| **Technical Notes** | Store which language form was submitted in |
| **Definition of Done** | Submissions table with language field |
| **Status** | ⬜ Not Started |
| **Notes** | |

---

### Task 5: Design UI Translations Table

| Property | Details |
|----------|---------|
| **UX / Product Purpose** | Stores UI strings for dynamic loading |
| **Technical Notes** | Key-value with locale: `{"key": "nav.home", "en": "Home", "ar": "الرئيسية"}` |
| **Definition of Done** | UI translations table schema |
| **Status** | ⬜ Not Started |
| **Notes** | |

**Schema Reference:**
```sql
ui_translations (
  id UUID PRIMARY KEY,
  key VARCHAR(255) UNIQUE NOT NULL,
  en TEXT NOT NULL,
  ar TEXT NOT NULL,
  context VARCHAR(255) -- e.g., "navigation", "buttons", "errors"
)
```

---

### Task 6: Create Database Seed Script (EN/AR)

| Property | Details |
|----------|---------|
| **UX / Product Purpose** | Enables rapid environment setup with bilingual content |
| **Technical Notes** | Include sample projects with EN and AR content |
| **Definition of Done** | Seed script with realistic bilingual sample data |
| **Status** | ⬜ Not Started |
| **Notes** | |

---

## Phase Deliverables Checklist

- [ ] Projects table DDL (multilingual)
- [ ] Categories table DDL (i18n)
- [ ] Media assets table (bilingual alt text)
- [ ] Contact submissions table
- [ ] UI translations table
- [ ] Bilingual seed script

---

## Sign-Off

| Role | Name | Date | Signature |
|------|------|------|-----------|
| Phase Lead | | | |
| Reviewer | | | |
