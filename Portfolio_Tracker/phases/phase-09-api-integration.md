# Phase 09: API ↔ UI Integration

**Status:** ⬜ Not Started  
**Progress:** 0/6 Tasks  
**Assignee:** _________________  
**Target Completion:** _________________

---

## Phase Overview

Connects frontend to backend with **language-aware data fetching**, ensuring content loads in the user's selected language.

---

## Progress Tracker

| # | Status | Task Name |
|---|--------|-----------|
| 1 | ⬜ | Create API Client Module (i18n-Aware) |
| 2 | ⬜ | Implement Projects Data Fetching (Multilingual) |
| 3 | ⬜ | Implement Category Filtering (Bilingual Labels) |
| 4 | ⬜ | Implement Contact Form Submission |
| 5 | ⬜ | Handle Image Loading from Supabase Storage |
| 6 | ⬜ | Implement UI Translation Loading |

**Legend:** ⬜ Not Started | 🔄 In Progress | ✅ Complete | ⏸️ Blocked

---

## Task Details

### Task 1: Create API Client Module (i18n-Aware)

| Property | Details |
|----------|---------|
| **UX / Product Purpose** | All API calls include current language |
| **Technical Notes** | Axios interceptor adds `lang` param from i18n context |
| **Definition of Done** | API client automatically includes language in requests |
| **Status** | ⬜ Not Started |
| **Notes** | |

---

### Task 2: Implement Projects Data Fetching (Multilingual)

| Property | Details |
|----------|---------|
| **UX / Product Purpose** | Projects load in user's language |
| **Technical Notes** | React Query/SWR with language in cache key |
| **Definition of Done** | Projects refetch when language changes |
| **Status** | ⬜ Not Started |
| **Notes** | |

---

### Task 3: Implement Category Filtering (Bilingual Labels)

| Property | Details |
|----------|---------|
| **UX / Product Purpose** | Filter buttons show translated category names |
| **Technical Notes** | Fetch categories with `lang` param |
| **Definition of Done** | Filters display in current language |
| **Status** | ⬜ Not Started |
| **Notes** | |

---

### Task 4: Implement Contact Form Submission

| Property | Details |
|----------|---------|
| **UX / Product Purpose** | Captures leads with language context |
| **Technical Notes** | Include `language` field in submission |
| **Definition of Done** | Form submits with language, shows localized confirmation |
| **Status** | ⬜ Not Started |
| **Notes** | |

---

### Task 5: Handle Image Loading from Supabase Storage

| Property | Details |
|----------|---------|
| **UX / Product Purpose** | Images load progressively |
| **Technical Notes** | Supabase storage URLs, responsive images, bilingual alt text |
| **Definition of Done** | Images load with correct alt text per language |
| **Status** | ⬜ Not Started |
| **Notes** | |

---

### Task 6: Implement UI Translation Loading

| Property | Details |
|----------|---------|
| **UX / Product Purpose** | UI strings load dynamically (optional) |
| **Technical Notes** | Fetch from `/api/translations/:locale` or use bundled JSON |
| **Definition of Done** | Translations load, fallback to bundled if API fails |
| **Status** | ⬜ Not Started |
| **Notes** | |

---

## Phase Deliverables Checklist

- [ ] i18n-aware API client
- [ ] Multilingual projects fetching
- [ ] Bilingual category filtering
- [ ] Contact form with language context
- [ ] Progressive image loading (bilingual alt)
- [ ] UI translation loading

---

## Sign-Off

| Role | Name | Date | Signature |
|------|------|------|-----------|
| Phase Lead | | | |
| Reviewer | | | |
