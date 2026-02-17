# TruBuild Astro Migration Plan

**Goal:** Refactor trubuildpenticton.ca from vanilla HTML to Astro to hit 90+ PageSpeed performance

**Current:** 72 performance, 2.0s LCP
**Target:** 90+ performance, <1.5s LCP

---

## Why Astro

1. **Static generation** - Zero JS by default, fastest possible load
2. **Built-in image optimization** - Automatic WebP, responsive images, lazy loading
3. **Component architecture** - Clean, maintainable code
4. **Tailwind integration** - Proper purge out of the box
5. **Production experience** - Learn modern stack for future clients

---

## Migration Strategy

### Phase 1: Setup & Structure (Checkpoint 1)
- [ ] Create new Astro project in separate branch
- [ ] Install dependencies: @astrojs/tailwind, @astrojs/image
- [ ] Set up basic project structure
- [ ] Copy over existing assets (images, favicon)
- [ ] Configure Tailwind with existing config

**Time estimate:** 30-45 min

### Phase 2: Core Layout & Components (Checkpoint 2)
- [ ] Create base Layout.astro with head/meta tags
- [ ] Build Header component (nav, logo)
- [ ] Build Hero component (background image, CTA)
- [ ] Build Footer component
- [ ] Test: Basic page structure loads

**Time estimate:** 45-60 min

### Phase 3: Content Sections (Checkpoint 3)
- [ ] Services section with cards
- [ ] About section
- [ ] Reviews section
- [ ] Contact form
- [ ] Test: All sections render correctly

**Time estimate:** 60-90 min

### Phase 4: Interactive Features (Checkpoint 4)
- [ ] Gallery/Photo slider - DECISION POINT: Replace Swiper or keep?
  - Option A: Use Swiper (familiar, but heavy)
  - Option B: Use lightweight alternative (Embla, Keen-slider)
  - Option C: Build vanilla JS solution (lightest, most work)
- [ ] Modal functionality
- [ ] Form validation/submission
- [ ] Smooth scroll, animations (AOS or replace?)
- [ ] Test: All interactions work

**Time estimate:** 60-90 min

### Phase 5: Image Optimization (Checkpoint 5)
- [ ] Use Astro Image component for all images
- [ ] Set up responsive images (srcset)
- [ ] Configure lazy loading
- [ ] Optimize hero images with proper formats
- [ ] Test: Images load fast, look good on all devices

**Time estimate:** 30-45 min

### Phase 6: Performance Tuning (Checkpoint 6)
- [ ] Inline critical CSS
- [ ] Defer non-critical JS
- [ ] Add preload hints for hero image
- [ ] Minify and purge unused CSS
- [ ] Test locally: Run Lighthouse, aim for 90+

**Time estimate:** 30-45 min

### Phase 7: Deployment (Checkpoint 7)
- [ ] Build production version
- [ ] Deploy to Netlify staging
- [ ] Run PageSpeed Insights on staging
- [ ] Fix any issues found
- [ ] Get approval from Dude
- [ ] Push to production
- [ ] Verify live site performance
- [ ] Document before/after metrics

**Time estimate:** 30-45 min

---

## Total Time Estimate: 5-7 hours across 2-3 work sessions

---

## Key Decisions To Make

### 1. Slider Library
**Current:** Swiper (78KB minified)
**Options:**
- Keep Swiper (familiar, works, but heavy)
- Embla Carousel (14KB, modern, lightweight)
- Keen-slider (5KB, very light)
- Vanilla JS (0KB library, custom code)

**Recommendation:** Embla or Keen-slider - balance of features and performance

### 2. Animation Library
**Current:** AOS (Animate On Scroll)
**Options:**
- Keep AOS (works, but adds weight)
- Replace with Intersection Observer API (vanilla, 0KB)
- Remove animations entirely (fastest)

**Recommendation:** Intersection Observer for simple fade-ins, drop fancy animations

### 3. Icon Library
**Current:** Font Awesome (via CDN)
**Options:**
- Keep Font Awesome kit
- Use Font Awesome SVG (only icons needed)
- Replace with Heroicons or Lucide (lighter)

**Recommendation:** Font Awesome SVG, only include icons actually used

---

## File Structure (Target)

```
Trubuild/
├── src/
│   ├── components/
│   │   ├── Header.astro
│   │   ├── Hero.astro
│   │   ├── Services.astro
│   │   ├── About.astro
│   │   ├── Reviews.astro
│   │   ├── Gallery.astro
│   │   ├── Contact.astro
│   │   └── Footer.astro
│   ├── layouts/
│   │   └── Layout.astro
│   ├── pages/
│   │   └── index.astro
│   └── styles/
│       └── global.css
├── public/
│   ├── images/
│   ├── favicon/
│   └── robots.txt
├── astro.config.mjs
├── tailwind.config.cjs
└── package.json
```

---

## Current Status

**Last updated:** 2026-01-12 14:25pm

**Current phase:** Planning
**Next action:** Review plan with Dude, get approval to start
**Blockers:** None

---

## Session Checkpoints (Save State Here)

### Session 1: 2026-01-12 (2:00pm-3:00pm)
**Phase 1: Setup & Structure - COMPLETE** (~45 min)
- Created migration plan
- Documented current performance: 72 score, 2.0s LCP
- ✅ Created astro-rebuild branch
- ✅ Upgraded Node.js v18.19 → v20.19.6 (via nvm)
- ✅ Installed Astro minimal template
- ✅ Added Tailwind v4 CSS integration via Vite
- ✅ Copied assets to public/ (images, favicon)
- ✅ Cleaned up logo files (keeping lightwoodlogo.png only)
- ✅ Created base Layout.astro with proper head/meta tags
- ✅ Created test index.astro page
- ✅ Dev server running successfully on localhost:4321

**Phase 2: Core Components - COMPLETE** (~60 min)
- ✅ Created Header.astro (contact bar + nav)
- ✅ Created Hero.astro (single optimized hero image)
- ✅ Added Font Awesome for icons
- ✅ Created Services.astro (6 service cards in grid)
- ✅ Created About.astro (company info + features)
- ✅ Created Reviews.astro (Google reviews image)
- ✅ Created Contact.astro (working form with formsubmit.co)
- ✅ Created Footer.astro (logo, contact, social links)
- ✅ Full page structure complete and loading in dev server

**Phase 3: Gallery & Production - COMPLETE** (~75 min)
- ✅ Installed Keen-slider (5KB library)
- ✅ Created Gallery.astro with 29 images
- ✅ Added fullscreen modal for images
- ✅ Fixed gallery image numbering (skips #13)
- ✅ Added smooth scroll behavior (native CSS)
- ✅ Fixed hero image rendering (img tag vs CSS background)
- ✅ Production build successful
- ✅ Tested production preview (localhost:4322)
- ✅ Created netlify.toml config
- ✅ Pushed to GitHub (astro-rebuild branch)
- ✅ Created deployment-guide.md

**Total Time:** ~3 hours (2:00pm-5:00pm)

**Status:** READY FOR STAGING DEPLOYMENT

### Session 2: [Date]
- [What was accomplished]
- [Current state]
- [Next steps]

### Session 3: [Date]
- [What was accomplished]
- [Current state]
- [Next steps]

---

## Notes & Discoveries

- Initial HTML has duplicate Font Awesome (fixed)
- Hero image compression q70 works well (236KB)
- Already have WebP images converted
- Contact form sends via [method to document]
- Google Reviews displayed as static images
- **REDESIGN:** Old site loads 3 hero images via CSS media queries (bad practice)
  - New approach: Single source hero, Astro Image component generates responsive srcset
  - Modern, automatic, optimized
- Logo: Using lightwoodlogo.png only (removed test logos)

---

## Before/After Metrics

### Before (Current Vanilla HTML)
- Performance: 72
- FCP: 1.8s
- LCP: 2.0s
- TBT: 0ms
- CLS: 1
- Speed Index: 2.1s

### After (Astro - Target)
- Performance: 90+
- FCP: <1.0s
- LCP: <1.5s
- TBT: 0ms
- CLS: 0
- Speed Index: <1.5s

### After (Astro - Actual)
- [To be filled after deployment]
