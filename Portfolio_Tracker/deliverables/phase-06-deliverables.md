# Phase 06 Deliverables

## Task 1: API Route Structure (i18n-Aware) ✅

### Route Map

| Method | Endpoint | Description | Auth |
|--------|----------|-------------|------|
| GET | `/api/projects?lang=en` | List projects | Public |
| GET | `/api/projects/:slug?lang=ar` | Single project | Public |
| POST | `/api/projects` | Create project | Admin |
| PUT | `/api/projects/:id` | Update project | Admin |
| DELETE | `/api/projects/:id` | Delete project | Admin |
| GET | `/api/categories?lang=en` | List categories | Public |
| POST | `/api/contact` | Submit contact form | Public |
| GET | `/api/translations/:locale` | UI translations | Public |
| POST | `/api/auth/login` | Admin login | Public |
| GET | `/api/auth/verify` | Verify token | Admin |

### Language Handling

```javascript
// Middleware: Extract language from query or header
const langMiddleware = (req, res, next) => {
  req.lang = req.query.lang || 
             req.headers['accept-language']?.split(',')[0]?.substring(0,2) || 
             'en';
  if (!['en', 'ar'].includes(req.lang)) req.lang = 'en';
  next();
};

app.use('/api', langMiddleware);
```

### Response Format

```json
{
  "success": true,
  "data": { ... },
  "meta": {
    "lang": "ar",
    "timestamp": "2026-01-17T00:00:00Z"
  }
}
```

---

## Task 2: Authentication Strategy ✅

### Flow Diagram

```
[Admin Login Page]
       ↓
[POST /api/auth/login {email, password}]
       ↓
[Supabase Auth → signInWithPassword]
       ↓
[Return JWT access_token + refresh_token]
       ↓
[Store in httpOnly cookie OR localStorage]
       ↓
[Protected requests: Authorization: Bearer <token>]
       ↓
[Middleware verifies JWT with Supabase]
```

### Express Middleware

```javascript
const { createClient } = require('@supabase/supabase-js');
const supabase = createClient(process.env.SUPABASE_URL, process.env.SUPABASE_KEY);

const authMiddleware = async (req, res, next) => {
  const token = req.headers.authorization?.replace('Bearer ', '');
  
  if (!token) {
    return res.status(401).json({ error: 'AUTH_REQUIRED', message_key: 'errors.auth_required' });
  }
  
  const { data: { user }, error } = await supabase.auth.getUser(token);
  
  if (error || !user) {
    return res.status(401).json({ error: 'INVALID_TOKEN', message_key: 'errors.invalid_token' });
  }
  
  req.user = user;
  next();
};
```

---

## Task 3: Content Management API (Multilingual) ✅

### Create Project

```javascript
// POST /api/projects
// Body:
{
  "slug": "harvey-app",
  "title_en": "Harvey Delivery App",
  "title_ar": "تطبيق هارفي للتوصيل",
  "summary_en": "Cross-platform delivery app...",
  "summary_ar": "تطبيق توصيل متعدد المنصات...",
  "description_en": "Full description...",
  "description_ar": "الوصف الكامل...",
  "thumbnail_url": "https://...",
  "category_id": "uuid",
  "tags": ["flutter", "firebase"],
  "featured": true
}
```

### Update Workflow

1. Admin updates EN content → saves
2. AR content shows "needs translation" badge
3. Admin updates AR content → saves
4. Both marked as synced

### API Endpoints

| Endpoint | Purpose |
|----------|---------|
| `POST /api/projects` | Create with both languages |
| `PUT /api/projects/:id` | Update specific fields |
| `PATCH /api/projects/:id/translate` | Update single language |
| `GET /api/projects/:id/status` | Check translation sync |

---

## Task 4: Error Handling Strategy (Localized) ✅

### Error Response Format

```json
{
  "success": false,
  "error": {
    "code": "VALIDATION_ERROR",
    "message_key": "errors.validation.email_invalid",
    "message": "Email format is invalid",
    "details": { "field": "email" }
  }
}
```

### Error Codes

| Code | EN Message | AR Message | HTTP |
|------|------------|------------|------|
| `AUTH_REQUIRED` | Authentication required | يجب تسجيل الدخول | 401 |
| `FORBIDDEN` | Access denied | غير مصرح | 403 |
| `NOT_FOUND` | Resource not found | غير موجود | 404 |
| `VALIDATION_ERROR` | Validation failed | فشل التحقق | 400 |
| `RATE_LIMITED` | Too many requests | طلبات كثيرة | 429 |
| `SERVER_ERROR` | Internal error | خطأ في الخادم | 500 |

### Express Error Handler

```javascript
app.use((err, req, res, next) => {
  const lang = req.lang || 'en';
  const messages = require(`./locales/${lang}/errors.json`);
  
  res.status(err.status || 500).json({
    success: false,
    error: {
      code: err.code || 'SERVER_ERROR',
      message_key: err.messageKey,
      message: messages[err.messageKey] || err.message
    }
  });
});
```

---

## Task 5: Rate Limiting & Security ✅

### Rate Limits

| Endpoint | Limit | Window |
|----------|-------|--------|
| Public API | 100 req | 15 min |
| Contact form | 5 req | 1 hour |
| Auth login | 5 req | 15 min |
| Admin API | 200 req | 15 min |

### Implementation

```javascript
const rateLimit = require('express-rate-limit');

const publicLimiter = rateLimit({
  windowMs: 15 * 60 * 1000,
  max: 100,
  message: { error: 'RATE_LIMITED', message_key: 'errors.rate_limited' }
});

const contactLimiter = rateLimit({
  windowMs: 60 * 60 * 1000,
  max: 5
});

app.use('/api', publicLimiter);
app.use('/api/contact', contactLimiter);
```

### CORS Configuration

```javascript
const cors = require('cors');

app.use(cors({
  origin: [
    'https://hamzahajeb.com',
    'https://hamzahajeb.github.io',
    process.env.NODE_ENV === 'development' && 'http://localhost:5173'
  ].filter(Boolean),
  methods: ['GET', 'POST', 'PUT', 'DELETE'],
  credentials: true
}));
```

### Security Checklist

- [x] Rate limiting on all endpoints
- [x] CORS whitelist (no wildcard in prod)
- [x] Helmet.js for security headers
- [x] Input validation (express-validator)
- [x] SQL injection prevention (parameterized queries via Supabase)
- [x] XSS prevention (sanitize inputs)
- [x] Environment variables for secrets

---

## Task 6: Translation Content API ✅

### Endpoint

```
GET /api/translations/:locale
```

### Response

```json
{
  "success": true,
  "data": {
    "nav.home": "Home",
    "nav.work": "Work",
    "nav.about": "About",
    "nav.contact": "Contact",
    "hero.headline": "Building digital experiences",
    "hero.cta": "View Work",
    "contact.name": "Your Name",
    "contact.email": "Email Address",
    "contact.message": "Message",
    "contact.submit": "Send Message",
    "errors.required": "This field is required"
  },
  "meta": {
    "locale": "en",
    "count": 12,
    "cached": true
  }
}
```

### Caching Strategy

```javascript
const cache = new Map();
const CACHE_TTL = 3600000; // 1 hour

app.get('/api/translations/:locale', async (req, res) => {
  const { locale } = req.params;
  const cacheKey = `translations_${locale}`;
  
  if (cache.has(cacheKey)) {
    const { data, timestamp } = cache.get(cacheKey);
    if (Date.now() - timestamp < CACHE_TTL) {
      return res.json({ success: true, data, meta: { cached: true } });
    }
  }
  
  const { data, error } = await supabase
    .from('ui_translations')
    .select('key, value')
    .eq('locale', locale);
  
  const translations = Object.fromEntries(data.map(t => [t.key, t.value]));
  cache.set(cacheKey, { data: translations, timestamp: Date.now() });
  
  res.json({ success: true, data: translations, meta: { cached: false } });
});
```

---

## Phase 06 Complete ✅

All 6 tasks have deliverables documented. Ready for Phase 07.
