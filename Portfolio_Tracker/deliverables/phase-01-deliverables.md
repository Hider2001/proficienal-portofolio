# Phase 01 Deliverables

## Task 1: Portfolio Positioning Statement ✅

### English
**"I build clean, scalable web solutions that bridge technical excellence with business impact—from SQL-powered dashboards to cross-platform applications, delivered with precision and purpose."**

### Arabic (العربية)
**"أبني حلول ويب نظيفة وقابلة للتوسع تجمع بين التميز التقني والأثر العملي—من لوحات المعلومات المدعومة بـ SQL إلى التطبيقات متعددة المنصات، بدقة وهدف واضح."**

---

## Task 2: Dual-Audience User Journeys ✅

### Journey A: Technical Reviewers (Companies/Recruiters)

```
[Land on Portfolio] → [See Hero: Name + Role + Tech Stack badges]
        ↓
[Scroll to Case Cards] → [Click project: "Harvey Delivery App"]
        ↓
[View: Architecture diagram, Tech decisions, Code snippets]
        ↓
[See: GitHub link, Live demo, Performance metrics]
        ↓
[Navigate to: Skills breakdown with proficiency levels]
        ↓
[Action: Download CV / Contact via form]
```

**Key Expectations:**
- Code quality evidence (clean architecture)
- Tech stack clarity (React, Flutter, Node.js, SQL Server)
- Problem-solving narrative
- GitHub activity / contributions

---

### Journey B: Clients (Non-Technical)

```
[Land on Portfolio] → [See Hero: Clear value proposition in their language]
        ↓
[Scroll to Case Cards] → [See visual outcomes, not code]
        ↓
[Click project] → [View: Before/After, Business impact, Testimonial]
        ↓
[See: Timeline, Budget-friendly messaging, Process clarity]
        ↓
[Navigate to: "How I Work" section]
        ↓
[Action: WhatsApp / Quick contact form]
```

**Key Expectations:**
- Visual quality (does it look professional?)
- Trust signals (experience, testimonials)
- Clear pricing/process hints
- Easy communication (WhatsApp for Yemen/MENA market)

---

### Language Preference Touchpoints

| Touchpoint | EN Audience | AR Audience |
|------------|-------------|-------------|
| Default Language | Browser detection | Browser detection |
| Switcher Location | Header (top-right in LTR) | Header (top-left in RTL) |
| Content Depth | More technical detail | More business-focused |
| Contact Preference | Email / LinkedIn | WhatsApp / Direct call |

---

## Task 3: Visual Identity System (RTL-Aware) ✅

### Color Palette

| Token | Value | Usage |
|-------|-------|-------|
| `--color-primary` | `#0A2540` | Headers, dark backgrounds, text |
| `--color-accent` | `#38BDF8` | Links, highlights, CTAs, icons |
| `--color-background` | `#FFFFFF` | Main background |
| `--color-text` | `#1E293B` | Body text |
| `--color-surface` | `#CBD5E1` | Cards, badges, secondary bg |
| `--color-muted` | `#64748B` | Secondary text, captions |

### Typography Scale

| Level | Size | Weight | Usage |
|-------|------|--------|-------|
| h1 | 36px / 2.25rem | 700 | Hero headline |
| h2 | 24px / 1.5rem | 700 | Section titles |
| h3 | 18px / 1.125rem | 600 | Card titles, job titles |
| body | 16px / 1rem | 400 | Paragraphs |
| small | 14px / 0.875rem | 400 | Captions, dates |

### Spacing System (8px base)

| Token | Value | Usage |
|-------|-------|-------|
| `--space-1` | 4px | Tight gaps |
| `--space-2` | 8px | Icon gaps, inline |
| `--space-3` | 16px | Component padding |
| `--space-4` | 24px | Section gaps |
| `--space-5` | 32px | Large sections |
| `--space-6` | 48px | Page sections |

### RTL Considerations

```css
/* Use logical properties */
margin-inline-start: var(--space-3);  /* Not margin-left */
padding-inline-end: var(--space-2);   /* Not padding-right */
text-align: start;                    /* Not text-align: left */

/* Direction-aware transforms */
[dir="rtl"] .slide-in {
  transform: translateX(20px);  /* Opposite of LTR */
}
```

---

## Task 4: Success Metrics (KPIs) ✅

| # | Metric | Target | Tracking Method |
|---|--------|--------|-----------------|
| 1 | Time to First Meaningful Interaction | < 5 seconds | Analytics event on scroll/click |
| 2 | Bounce Rate | < 40% | Analytics |
| 3 | Contact Form Submissions | 5+ per month | Supabase count |
| 4 | Language Distribution | Track EN vs AR | Custom dimension |
| 5 | Project Card Click-Through Rate | > 30% | Click events / page views |
| 6 | CV Downloads | 10+ per month | Download event tracking |
| 7 | Average Session Duration | > 2 minutes | Analytics |

### Language-Specific Tracking

- Track bounce rate per language (AR may differ from EN)
- Monitor which projects resonate with which audience
- A/B test positioning copy per language

---

## Task 5: Content Inventory (EN/AR) ✅

| Content Type | EN Status | AR Status | Priority | Notes |
|--------------|-----------|-----------|----------|-------|
| **Hero Section** | | | | |
| Headline | ⬜ Needed | ⬜ Needed | High | Use positioning statement |
| Subheadline | ⬜ Needed | ⬜ Needed | High | Brief intro |
| CTA Button | ⬜ Needed | ⬜ Needed | High | "View Work" / "شاهد أعمالي" |
| **About Section** | | | | |
| Bio paragraph | ⬜ Needed | ✅ Exists (CV) | High | Adapt from CV summary |
| Profile photo | ⬜ Needed | ⬜ Needed | High | Professional headshot |
| **Projects (Placeholder)** | | | | |
| Project 1: Harvey App | ⬜ | ⬜ | High | Delivery app case study |
| Project 2: Dashboard System | ⬜ | ⬜ | High | SQL reporting system |
| Project 3: Web Application | ⬜ | ⬜ | Medium | TBD by user |
| Project 4: Portfolio Template | ⬜ | ⬜ | Low | This portfolio itself |
| **Skills Section** | | | | |
| Tech skills list | ⬜ | ✅ Exists (CV) | Medium | From CV |
| Skill categories | ⬜ | ⬜ | Medium | Need icons/grouping |
| **Contact Section** | | | | |
| Form labels | ⬜ | ⬜ | High | Name, Email, Message |
| Success/error messages | ⬜ | ⬜ | Medium | Confirmation text |
| Contact info | ✅ | ✅ | High | From CV |
| **Footer** | | | | |
| Copyright text | ⬜ | ⬜ | Low | © 2026 Hamza Hajeb |
| Social links | ⬜ | ⬜ | Medium | GitHub, LinkedIn, WhatsApp |

---

## Task 6: Language Strategy & Switching UX ✅

### URL Strategy

**Recommended: Path-based routing**
```
https://hamzahajeb.com/en/          → English version
https://hamzahajeb.com/ar/          → Arabic version
https://hamzahajeb.com/             → Redirect based on detection
```

### Detection Logic (Priority Order)

1. **URL path** – If `/ar/` or `/en/` in URL, use that
2. **localStorage** – If user previously selected a language
3. **Browser language** – `navigator.language` starts with `ar` → Arabic
4. **Default** – English (broader reach for international clients)

### Switching UX

```
┌─────────────────────────────────────────────────┐
│  [🌐 EN ▼]                          Header      │
│   ├── English                                   │
│   └── العربية                                   │
└─────────────────────────────────────────────────┘
```

**Behavior:**
- Toggle updates URL (`/en/` ↔ `/ar/`)
- Stores preference in `localStorage`
- Updates `<html dir="rtl/ltr" lang="ar/en">`
- Content refreshes without full page reload (React i18n)

### Implementation Notes

```javascript
// Persist language choice
localStorage.setItem('preferredLanguage', 'ar');

// Apply direction
document.documentElement.dir = lang === 'ar' ? 'rtl' : 'ltr';
document.documentElement.lang = lang;
```

---

## Task 7: Arabic Typography & Font Selection ✅

### Font Pairing

| Role | English | Arabic | Google Fonts |
|------|---------|--------|--------------|
| **Display** (Headlines) | Outfit | Cairo | Yes |
| **Body** (Text) | Inter | Tajawal | Yes |

### CSS Implementation

```css
:root {
  --font-display-en: 'Outfit', sans-serif;
  --font-display-ar: 'Cairo', sans-serif;
  --font-body-en: 'Inter', sans-serif;
  --font-body-ar: 'Tajawal', sans-serif;
}

/* Apply based on language */
[lang="en"] body {
  font-family: var(--font-body-en);
}

[lang="ar"] body {
  font-family: var(--font-body-ar);
}

[lang="en"] h1, [lang="en"] h2, [lang="en"] h3 {
  font-family: var(--font-display-en);
}

[lang="ar"] h1, [lang="ar"] h2, [lang="ar"] h3 {
  font-family: var(--font-display-ar);
}
```

### Google Fonts Import

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;500;600;700&family=Inter:wght@400;500;600;700&family=Outfit:wght@400;500;600;700&family=Tajawal:wght@400;500;700&display=swap" rel="stylesheet">
```

### Arabic Typography Notes

- **Cairo** – Premium feel, clear at all sizes, matches your existing CV
- **Tajawal** – Highly readable body text, modern Arabic sans-serif
- **Line-height** – Arabic may need slightly more (`1.7` vs `1.6`)
- **Letter-spacing** – Avoid on Arabic (breaks ligatures)

---

## Phase 01 Complete ✅

All 7 tasks have deliverables documented. Ready for Phase 02.
