# TruBuild Astro - Deployment Guide

**Branch:** `astro-rebuild`
**Status:** Ready to deploy to staging
**GitHub:** https://github.com/brycedipalo/Trubuild/tree/astro-rebuild

---

## What's Complete

✅ Full site rebuilt in Astro
✅ All components working (Header, Hero, About, Services, Gallery, Reviews, Contact, Footer)
✅ Keen-slider gallery (5KB, 29 images)
✅ Smooth scroll navigation
✅ Production build tested locally (localhost:4322)
✅ Netlify config created (netlify.toml)
✅ Branch pushed to GitHub

---

## Deploy to Netlify Staging

### Option 1: Netlify UI (Recommended)

1. Go to https://app.netlify.com/
2. Log in to your account
3. Click "Add new site" → "Import an existing project"
4. Choose GitHub, select `brycedipalo/Trubuild` repo
5. **Important:** Select branch `astro-rebuild` (not main)
6. Build settings (auto-detected from netlify.toml):
   - Build command: `npm run build`
   - Publish directory: `dist`
7. Click "Deploy site"
8. Wait 2-3 minutes for build to complete
9. Get staging URL (e.g., `random-name-12345.netlify.app`)
10. **Run PageSpeed Insights on staging URL**

### Option 2: Netlify CLI (Alternative)

```bash
cd /home/zerocool/projects/Trubuild
netlify login
netlify deploy --build --dir=dist
# Follow prompts to create new site or link existing
# Get draft URL for testing
```

---

## After Staging Tests Pass

### Run PageSpeed Insights

1. Go to https://pagespeed.web.dev/
2. Enter your staging URL
3. **Target:** 85-90+ performance score
4. **Current baseline:** 73 (old vanilla HTML site)
5. **Expected improvement:** 15-20 points

### If Performance is Good (85+)

**Update DNS to point to Netlify:**

1. Go to Porkbun DNS settings for trubuildpenticton.ca
2. Update A records to point to Netlify:
   - Delete existing A records
   - Add Netlify's load balancer IP: `75.2.60.5`
3. Add CNAME for www:
   - Name: `www`
   - Value: `your-site-name.netlify.app`
4. Wait for DNS propagation (15 min - 24 hours, usually <1 hour)
5. In Netlify, add custom domain: trubuildpenticton.ca
6. Enable HTTPS (automatic via Let's Encrypt)

### Merge to Main

Once live site is confirmed working:

```bash
git checkout main
git merge astro-rebuild
git push origin main
```

---

## Rollback Plan (If Issues)

If something breaks:

1. In Porkbun DNS: Revert A records to original Porkbun hosting IP
2. Original site on `main` branch still intact
3. DNS propagates back in 15-60 minutes

---

## Performance Comparison

| Metric | Old (Vanilla HTML) | Target (Astro) |
|--------|-------------------|----------------|
| Performance | 73 | 85-90+ |
| FCP | 1.8s | <1.0s |
| LCP | 2.0s | <1.5s |
| TBT | 0ms | 0ms |
| CLS | 1 | 0 |

---

## Tech Stack Changes

**Removed (Heavy):**
- Swiper library (78KB) → Keen-slider (5KB)
- Duplicate Font Awesome
- AOS animations (unnecessary)
- 3 separate hero images via CSS

**Added (Modern):**
- Astro static site generation
- Tailwind v4 (with purge)
- Keen-slider (lightweight)
- Single optimized hero image
- Smooth scroll (native CSS)

---

## Next Steps

1. Deploy to Netlify staging (Option 1 or 2 above)
2. Test staging site thoroughly
3. Run PageSpeed Insights
4. If 85-90+ performance: Update DNS and go live
5. If <85 performance: Identify bottlenecks and optimize
6. Merge to main once confirmed working

---

## Contact

Questions or issues: Check localhost:4322 for local preview or review code in astro-rebuild branch.
