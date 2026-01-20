# Deployment Guide

**Repository:** HamzaHajib  
**Live URL:** https://hider2001.github.io/HamzaHajib/

---

## ✅ Completed Steps

1. ✅ Created GitHub repository: `HamzaHajib`
2. ✅ Added secrets:
   - `VITE_SUPABASE_URL`
   - `VITE_SUPABASE_ANON_KEY`
3. ✅ Pushed code to GitHub
4. ✅ Enabled GitHub Pages (Source: GitHub Actions)

---

## Verification Checklist

- [ ] Site loads at https://hider2001.github.io/HamzaHajib/
- [ ] Projects load from Supabase
- [ ] Contact form works
- [ ] Language switching works (EN ↔ AR)
- [ ] RTL layout correct in Arabic mode
- [ ] No console errors

---

## Troubleshooting

### Build fails
- Check GitHub Actions logs at: https://github.com/Hider2001/HamzaHajib/actions

### Page shows 404
- Verify workflow completed successfully
- Check `base` in `vite.config.ts` matches repo name

### Supabase connection fails
- Verify secrets match your Supabase project
- Check RLS policies allow public reads
