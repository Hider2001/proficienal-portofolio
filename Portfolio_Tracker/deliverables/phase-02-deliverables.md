# Phase 02 Deliverables

## Task 1: Primary Navigation Structure (EN/AR) ✅

### Navigation Hierarchy (Max 5 Top-Level Items)

| # | EN Label | AR Label | Route | Notes |
|---|----------|----------|-------|-------|
| 1 | Home | الرئيسية | `/` | Hero + intro |
| 2 | Work | أعمالي | `/#work` | Project case cards |
| 3 | About | عني | `/#about` | Bio + skills |
| 4 | Contact | تواصل | `/#contact` | Form + info |
| — | 🌐 EN/AR | 🌐 EN/AR | — | Language toggle |

### Navigation Behavior

- **Desktop:** Horizontal nav in header, sticky on scroll
- **Mobile:** Hamburger menu with slide-in drawer (from right in RTL)
- **Scroll:** Smooth scroll to sections with hash routing
- **Active State:** Highlight current section based on scroll position

---

## Task 2: Section Hierarchy ✅

### Page Sections (Top to Bottom)

| Order | Section | Content Density | Purpose |
|-------|---------|-----------------|---------|
| 1 | **Hero** | Low | Immediate impact, positioning |
| 2 | **Work/Projects** | Medium | Showcase best projects |
| 3 | **About** | Medium | Personal story + credibility |
| 4 | **Skills** | Low-Medium | Technical competencies |
| 5 | **Contact** | Low | Convert visitor to lead |
| 6 | **Footer** | Low | Secondary links, copyright |

### Visibility Priority

```
Hero       ████████████████████  (100% - Always visible first)
Work       ██████████████████    (90% - Primary showcase)
About      ████████████████      (80% - Trust building)
Skills     ██████████████        (70% - Technical proof)
Contact    ████████████          (60% - Action point)
Footer     ██████████            (50% - Closure)
```

---

## Task 3: Project Taxonomy (Bilingual Labels) ✅

### Categories

| Key | EN Label | AR Label | Description |
|-----|----------|----------|-------------|
| `web` | Web Development | تطوير الويب | Websites, web apps |
| `mobile` | Mobile Apps | تطبيقات الجوال | Flutter, cross-platform |
| `desktop` | Desktop Apps | تطبيقات سطح المكتب | Electron apps |
| `dashboard` | Dashboards | لوحات المعلومات | Admin panels, analytics |
| `api` | Backend / API | الخوادم والـ API | Server-side, databases |

### Tags

| Key | EN Label | AR Label |
|-----|----------|----------|
| `react` | React | React |
| `flutter` | Flutter | Flutter |
| `nodejs` | Node.js | Node.js |
| `sql` | SQL Server | SQL Server |
| `firebase` | Firebase | Firebase |
| `electron` | Electron | Electron |

### Database Storage

```sql
-- Store key, display translations in code or translations table
categories (id, key, created_at)
-- Example: { id: 1, key: 'web' }

-- UI fetches translations from i18n files
// en.json: { "categories.web": "Web Development" }
// ar.json: { "categories.web": "تطوير الويب" }
```

---

## Task 4: Content-to-Component Relationships ✅

### Component Tree

```
App
├── LanguageProvider (i18n context)
│   ├── Header
│   │   ├── Logo
│   │   ├── NavLinks
│   │   ├── LanguageSwitcher
│   │   └── MobileMenu
│   │
│   ├── Main
│   │   ├── HeroSection
│   │   │   ├── Headline (i18n)
│   │   │   ├── Subheadline (i18n)
│   │   │   └── CTAButton (i18n)
│   │   │
│   │   ├── WorkSection
│   │   │   ├── SectionTitle (i18n)
│   │   │   ├── CategoryFilter
│   │   │   │   └── FilterButton[] (i18n labels)
│   │   │   └── ProjectGrid
│   │   │       └── ProjectCard[] (dynamic content)
│   │   │           ├── CardImage
│   │   │           ├── CardTitle (i18n or API)
│   │   │           ├── CardDescription (i18n or API)
│   │   │           └── CardTags
│   │   │
│   │   ├── AboutSection
│   │   │   ├── SectionTitle (i18n)
│   │   │   ├── ProfileImage
│   │   │   └── BioText (i18n)
│   │   │
│   │   ├── SkillsSection
│   │   │   ├── SectionTitle (i18n)
│   │   │   └── SkillCategory[]
│   │   │       └── SkillItem[]
│   │   │
│   │   └── ContactSection
│   │       ├── SectionTitle (i18n)
│   │       ├── ContactForm
│   │       │   ├── InputField[] (i18n labels)
│   │       │   └── SubmitButton (i18n)
│   │       └── ContactInfo
│   │
│   └── Footer
│       ├── SocialLinks
│       ├── Copyright (i18n)
│       └── LegalLinks (i18n)
```

### Shared Components

| Component | Usage | i18n |
|-----------|-------|------|
| `SectionTitle` | All sections | Yes |
| `Button` | CTA, form submit | Yes |
| `Card` | Projects, skills | Partial |
| `RevealOnScroll` | All sections | No |
| `LanguageSwitcher` | Header | Yes |

---

## Task 5: Footer & Secondary Content (EN/AR) ✅

### Footer Structure

```
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│  [Logo]                                                     │
│                                                             │
│  Connect                    Quick Links                     │
│  ─────────                  ───────────                     │
│  📧 hamzafuad2001@gmail.com   Home                          │
│  📱 +967 776645280            Work                          │
│  📍 Sana'a, Yemen             About                         │
│                               Contact                       │
│                                                             │
│  [GitHub] [LinkedIn] [WhatsApp]                             │
│                                                             │
│  ─────────────────────────────────────────────────────────  │
│  © 2026 Hamza Hajeb. All rights reserved.                   │
│  Privacy Policy  •  Terms of Service                        │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### Footer Content (EN/AR)

| Element | EN | AR |
|---------|----|----|
| Connect heading | Connect | تواصل |
| Quick Links heading | Quick Links | روابط سريعة |
| Copyright | © 2026 Hamza Hajeb | © 2026 حمزة حاجب |
| All rights | All rights reserved | جميع الحقوق محفوظة |
| Privacy | Privacy Policy | سياسة الخصوصية |
| Terms | Terms of Service | شروط الخدمة |

---

## Task 6: Bilingual URL Strategy ✅

### URL Structure

**Pattern: Path-based prefix**

| Page | English URL | Arabic URL |
|------|-------------|------------|
| Home | `/en/` | `/ar/` |
| Projects | `/en/#work` | `/ar/#work` |
| Project Detail | `/en/project/harvey-app` | `/ar/project/harvey-app` |
| About | `/en/#about` | `/ar/#about` |
| Contact | `/en/#contact` | `/ar/#contact` |

### Root URL Behavior

```
https://hamzahajeb.com/
        ↓
[Detect Language]
        ↓
┌─────────────────────────────────┐
│ 1. Check localStorage           │
│ 2. Check browser Accept-Language│
│ 3. Default to English           │
└─────────────────────────────────┘
        ↓
Redirect to /en/ or /ar/
```

### React Router Configuration

```jsx
<Routes>
  <Route path="/" element={<LanguageRedirect />} />
  <Route path="/:lang" element={<Layout />}>
    <Route index element={<Home />} />
    <Route path="project/:slug" element={<ProjectDetail />} />
  </Route>
</Routes>
```

### SEO Considerations

```html
<!-- On /en/ page -->
<link rel="alternate" hreflang="en" href="https://hamzahajeb.com/en/" />
<link rel="alternate" hreflang="ar" href="https://hamzahajeb.com/ar/" />
<link rel="canonical" href="https://hamzahajeb.com/en/" />

<!-- On /ar/ page -->
<html lang="ar" dir="rtl">
<link rel="canonical" href="https://hamzahajeb.com/ar/" />
```

---

## Phase 02 Complete ✅

All 6 tasks have deliverables documented. Ready for Phase 03.
