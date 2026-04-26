# PRD — Video Editor Portfolio One-Pager
**Framework**: Astro.build  
**Type**: Single-page static site  
**Goal**: Convert visitors into freelance clients

---

## 1. Overview

A minimal, clean one-page portfolio for a freelance video editor specialising in **Reels / Short-form** (Instagram, TikTok) and **YouTube / Content Creator** videos. The site targets potential clients who need social-media-first video content and should lead them clearly toward booking a call or sending a message.

---

## 2. Target Audience

| Persona | Need |
|---|---|
| Content Creators (YouTubers, Influencers) | Consistent, high-quality edits at speed |
| Brand / Business Owners | Reels & short-form ads that convert |
| Agencies | Reliable freelance editor to outsource to |

---

## 3. Design Direction

| Token | Decision |
|---|---|
| **Aesthetic** | Refined minimalism — lots of white space, tight typography, no clutter |
| **Theme** | Light base with one strong accent (e.g. warm off-black `#1a1a1a` + a single accent like `#e8ff47` or `#ff4d00`) |
| **Typography** | Display: editorial serif (e.g. *Playfair Display* or *DM Serif Display*) · Body: geometric sans (e.g. *DM Sans* or *Sora*) |
| **Motion** | Subtle scroll-triggered fade-ins, smooth section transitions, hover lift on project cards |
| **Layout** | Full-width sections, generous padding, asymmetric hero, grid-breaking project thumbnails |

> **The one thing visitors remember**: A hero with a punchy, confident tagline — not a job title, but an outcome statement (e.g. *"I make people stop scrolling."*)

---

## 4. Site Architecture (Single Page, Top → Bottom)

```
/
├── #hero
├── #about
├── #services
├── #work          ← featured projects
├── #testimonials
└── #contact
```

No sub-pages. All navigation anchors scroll within the same page.

---

## 5. Section Specs

### 5.1 Navigation (Sticky)
- Logo / name (left)
- Anchor links: Work · Services · Testimonials · Contact (right)
- CTA button: **"Book a Call"** → Calendly link (accent colour)
- Collapses to hamburger on mobile

---

### 5.2 Hero `#hero`
**80/20 priority: This section does the most conversion work.**

| Element | Content |
|---|---|
| **Headline** | Short, punchy outcome statement — e.g. *"I make people stop scrolling."* |
| **Sub-headline** | *Freelance Video Editor · Reels · YouTube · Short-form Content* |
| **Experience badge** | *1–2 years · Adobe Premiere Pro · After Effects* |
| **Primary CTA** | `Book a Call` → Calendly |
| **Secondary CTA** | `View My Work` → scrolls to #work |
| **Visual** | Full-width or split-layout hero; right side: auto-playing muted showreel loop OR a bold still frame with play button |

---

### 5.3 About `#about`
Keep it tight — 3–4 sentences max. Clients don't read walls of text.

- Who you are + what you do
- Your editing style / approach
- What makes you different (fast turnaround, creator-first communication, etc.)
- **No photo required** but optional; if included — candid, not corporate

---

### 5.4 Services `#services`
3 service cards (clean grid):

| Card | Title | Detail |
|---|---|---|
| 1 | Short-form & Reels | Instagram, TikTok, YouTube Shorts — hook-first editing for max retention |
| 2 | YouTube Long-form | Structured, engaging edits with pacing, graphics, and B-roll |
| 3 | Motion & Effects | After Effects animations, transitions, text overlays, and brand intros |

Each card: icon + title + 1–2 line description. No pricing (keeps it flexible for discovery calls).

---

### 5.5 Featured Work `#work`
**4–6 project cards in a masonry or asymmetric grid.**

Each card contains:
- Thumbnail (still from video or custom thumbnail)
- Project title
- Category tag (e.g. `Reel` · `YouTube` · `Short-form`)
- Short 1-line description
- Hover state: play icon overlay OR link to video (YouTube / Vimeo / Drive)

> **Note**: Video embeds should be lazy-loaded. Prefer thumbnail + external link over inline embeds for performance.

**Placeholder project data (to be replaced):**

| # | Title | Category | Platform |
|---|---|---|---|
| 1 | Creator Vlog Edit | YouTube | YouTube |
| 2 | Brand Reel — Product Drop | Reel | Instagram |
| 3 | Talking Head + B-roll Cut | YouTube | YouTube |
| 4 | TikTok Hook Series | Short-form | TikTok |
| 5 | Motion Intro Package | Motion | After Effects |
| 6 | Event Highlights Reel | Reel | Instagram |

---

### 5.6 Testimonials `#testimonials`
Horizontal scroll or 2–3 column grid of quote cards.

Each card:
- Quote text (2–4 lines)
- Client name + handle or role (e.g. *@username · Content Creator*)
- Optional: platform or project type

> Minimum 2 testimonials, ideal 3–4. Real names/handles massively improve trust.

---

### 5.7 Contact / CTA `#contact`
**80/20 priority: Second most important conversion section.**

- Big headline: *"Ready to level up your content?"* (or similar)
- Sub-text: *"Let's talk about your next project."*
- Two action buttons side by side:
  - `📅 Book a Call` → Calendly URL
  - `💬 Message on WhatsApp` → `https://wa.me/<number>`
- Below buttons: email address as plain text (optional fallback)

---

### 5.8 Footer
- Name / logo
- Repeat anchor nav links
- Social icons: Instagram · TikTok · YouTube (if applicable)
- Copyright line: `© 2026 [Name]. All rights reserved.`

---

## 6. Technical Spec

### Astro Setup

```
src/
├── components/
│   ├── Nav.astro
│   ├── Hero.astro
│   ├── About.astro
│   ├── Services.astro
│   ├── Work.astro
│   ├── ProjectCard.astro
│   ├── Testimonials.astro
│   ├── Contact.astro
│   └── Footer.astro
├── layouts/
│   └── BaseLayout.astro
├── pages/
│   └── index.astro
└── styles/
    └── global.css
```

### Key Astro Decisions

| Decision | Choice | Reason |
|---|---|---|
| Rendering | Static (`output: 'static'`) | No server needed; faster, cheaper to host |
| Styling | Plain CSS with CSS custom properties | Zero JS overhead; full design control |
| Animations | CSS `@keyframes` + `IntersectionObserver` (vanilla JS island) | Lightweight scroll-triggered reveals |
| Images | Astro `<Image />` component | Auto-optimised WebP, lazy loading |
| Fonts | Google Fonts via `<link>` in `<head>` | Simple, no build step needed |
| Deployment | Vercel / Netlify (static adapter) | Free tier, instant deploys |

### Performance Targets

| Metric | Target |
|---|---|
| Lighthouse Performance | ≥ 95 |
| LCP | < 2.5s |
| Total JS (client) | < 20KB |
| Images | WebP, max 200KB each |

---

## 7. Content Checklist (Fill Before Building)

- [ ] Your name / brand name
- [ ] Hero tagline (outcome-focused, not a job title)
- [ ] Short bio (3–4 sentences)
- [ ] 4–6 project thumbnails + video links
- [ ] 2–4 testimonial quotes + client names
- [ ] Calendly booking link
- [ ] WhatsApp number
- [ ] Social media handles
- [ ] Favicon / logo (even just initials in a box)

---

## 8. Out of Scope (v1)

- Blog / case studies page
- Client login / portal
- Payment integration
- CMS (Contentful, Sanity, etc.)
- Dark mode toggle
- Multi-language support

> Add these only if a real client need justifies the complexity.

---

## 9. Success Metrics

| Metric | Goal |
|---|---|
| Calendly booking clicks | Primary conversion event |
| WhatsApp clicks | Secondary conversion event |
| Bounce rate | < 60% |
| Time on page | > 1 min 30 sec |

---

*PRD version 1.0 — April 2026*
