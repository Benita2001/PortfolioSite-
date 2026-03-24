# 📄 FINAL PRD v2.0
## BigBeni — 100-Day AI Build Challenge Portfolio
### Claude Code Build Document

---

## 0. Non-Negotiable Rules (Read First)

**Build Rules — Never skip these:**
1. Prototype the hardest part first — validate before building features
2. 30-minute visual checkpoint after first build — compare to references
3. PRD must include actual screenshot references, not words only
4. Build in layers: visuals → navigation → data → features
5. Describe the approach before writing any code — get approval first
6. Validate the foundation before building the house

**Anti-Vibe-Code Rules — Enforce on every component:**
- No default purple gradients unless brand-appropriate
- No sparkles or emojis in hero headings
- No generic glowing hover effects
- Consistent type scale and weight hierarchy — define it first, stick to it
- Define exactly 3 border radius values — use nothing else
- Hover states: 2-4px lift max, cubic-bezier easing only
- Every animation serves a purpose — no decoration
- Loading states on all async actions
- No em-dash overuse in copy
- No vague phrases: "Build your dreams", "Launch faster", "Create without limits"
- No fake testimonials, no placeholder names
- **Core principle: Build the design system first. Every value references it. Inconsistency signals vibe-coding.**

---

## 1. Project Identity

| Field | Value |
|---|---|
| Site name | BigBeni — 100-Day AI Build Challenge |
| Owner | Ukachi Chidera Benita (BigBeni) |
| Role | TikTok & Instagram AI content creator |
| Builder | Builds with Claude and Claude Code. Zero coding background. |
| Deadline | Live before Wednesday March 26, 2026 |
| Note | This website is Day 1 of the challenge itself |

---

## 2. What This Site Does

Three jobs, one site:

1. **Public challenge tracker** — every build day logged and visible live
2. **Creator portfolio** — every project showcased as a portfolio piece
3. **Brand pitch document** — the link sent to AI companies for collab deals

It must impress a brand manager in under 10 seconds on a phone.

---

## 3. Design Direction: "Dark Dreamy Editorial"

Not generic dark mode. Not vibe-coded purple soup. A cinematic, intentional, premium dark editorial aesthetic — like a luxury art book that also happens to be a tracker.

**References analyzed (12 sites):**
- BentoGrids → Varied card sizes, editorial rhythm
- Wall of Art → Full-bleed dark, gallery-level confidence
- Dan Woodger → Big bold personality in hero typography
- Henry Hobson → Cinematic dark atmosphere, film-like
- Bertus Gerssen → Subtle breathing motion, nothing gratuitous
- Directed by Wes → Intentional grid structure
- The Marmalade → Warm color pops against dark
- Lundgren+Lindqvist → Text and grid coexisting beautifully
- Duotone → Minimal but rich, every element earns its place
- Dribbble Calendar UI → Clean day-number card typography
- Webflow Calendar → Navigation feel for the tracker
- BentoGrids glassmorphism shot → Frosted card surfaces, depth

**Mood in one sentence:** Walking into a dark luxury room with soft gold candlelight — premium, warm, faith-driven, human.

---

## 4. Design System (Define This Before Any Component)

Claude Code must output these as CSS custom properties at the top of the file. No hardcoded values anywhere in the CSS.

```css
:root {
  /* Spacing — 8pt grid */
  --space-1: 4px;
  --space-2: 8px;
  --space-3: 12px;
  --space-4: 16px;
  --space-5: 24px;
  --space-6: 32px;
  --space-7: 48px;
  --space-8: 64px;

  /* Colors */
  --color-bg:         #0a0a0f;
  --color-surface:    rgba(255, 255, 255, 0.04);
  --color-border:     rgba(255, 255, 255, 0.08);
  --color-text-primary:   #f4f4f5;
  --color-text-secondary: #a1a1aa;
  --color-accent:     #7c3aed;       /* used sparingly */
  --color-accent-alt: #06b6d4;       /* used sparingly */
  --color-rest:       #fbbf24;       /* rest days only */
  --color-rest-soft:  #c084fc;       /* rest day surface only */

  /* Border radius — exactly 3 values */
  --radius-sm:   6px;    /* tags, badges */
  --radius-md:   12px;   /* cards */
  --radius-lg:   999px;  /* pills, buttons */

  /* Typography scale */
  --text-xs:   12px;
  --text-sm:   14px;
  --text-base: 16px;
  --text-md:   20px;
  --text-lg:   24px;
  --text-xl:   32px;
  --text-2xl:  48px;

  /* Font weights */
  --weight-normal:  400;
  --weight-medium:  500;
  --weight-bold:    700;

  /* Line heights */
  --leading-body:    1.5;
  --leading-heading: 1.2;

  /* Animations */
  --ease-standard: cubic-bezier(0.25, 0.46, 0.45, 0.94);
  --duration-fast:   180ms;
  --duration-base:   260ms;
  --stagger-delay:   60ms;

  /* Hover */
  --hover-lift: translateY(-3px);
}
```

---

## 5. Pages

| Page | Purpose |
|---|---|
| Home / Hero | Name, specific brand hook, CTA to follow the challenge |
| The Challenge | Full bento grid — all 100 days, each clickable |
| About | Bio, story, why she's doing this |
| Contact / Collab | Brand deal inquiry — clean form, no fake testimonials |

---

## 6. The Bento Grid — Core Feature

This is the hardest part. Prototype this first.

### Layout

| Breakpoint | Grid |
|---|---|
| Mobile (< 640px) | 4-column grid. Mostly 1×1 cards. Occasional 2×1 wide cards for built days. |
| Desktop (≥ 1024px) | 10-column grid. Mixed 1×1, 2×1, 1×2. Today's card is always 2×2. |

Rest day cards (every 10th) are always wider than standard — visually distinct by size, not just color.

### Card States

| State | Visual Treatment |
|---|---|
| **Locked** | Dark glass surface, day number only, 40% opacity, no interaction |
| **Built** | Full opacity glass surface, project name visible, subtle accent border |
| **Rest Day** | Soft lavender-to-gold surface, moon glyph (not emoji), wider card |
| **Today** | 2×2 featured, solid accent border, scale(1.02) on load, "TODAY" badge |

### Interactions

**Built day tap:**
Smooth bottom sheet slides up on mobile / centered modal on desktop.
Contains: project name, one-line description, live link button, TikTok link button, date built.
No fake data. If empty, show nothing.

**Rest day tap:**
Full-screen overlay. Dreamy but typographically clean — no emoji soup.
Content:
- Quote: *"Benita is resting today. Even God rested on the 7th day. Excellence requires recovery."*
- Countdown to next build day (functional, live)
- Short section: the science of rest and performance
- Aesthetic: soft lavender and gold, floating particle animation (purposeful, subtle)

**Locked day tap:**
Subtle shimmer on the card. No modal. No content.

**Hover (desktop):**
`translateY(-3px)` + border opacity increase. `cubic-bezier(0.25, 0.46, 0.45, 0.94)`, `180ms`. Nothing more.

### Card entry animation
Cards stagger in on page load. 60ms delay between each. `cubic-bezier(0.25, 0.46, 0.45, 0.94)`. Fade + translateY(8px) → translateY(0).

---

## 7. Challenge Structure

| Field | Value |
|---|---|
| Total days | 100 |
| Build days | 90 |
| Rest days | 10 (days 10, 20, 30, 40, 50, 60, 70, 80, 90, 100) |
| Start date | Wednesday, March 26, 2026 |
| Schedule | Monday to Friday only. Weekends off. |
| End date | ~August 2026 |

Date calculation logic: Day 1 = March 26. Each subsequent day increments Mon–Fri only, skipping Sat and Sun. The code must calculate this automatically from the start date.

---

## 8. Data Structure

One JS array at the top of the file. BigBeni updates this herself with zero coding knowledge.

```js
const CHALLENGE_DATA = [
  {
    day: 1,
    name: "Portfolio Site",
    description: "The public tracker for the 100-Day AI Build Challenge.",
    liveLink: "https://...",
    tiktokLink: "https://...",
    date: "March 26, 2026"
  },
  {
    day: 2,
    locked: true
  },
  // Day 10, 20, 30... are auto-detected as rest days by the code
  // No manual tagging needed
];
```

Rest days are detected automatically: `if (day % 10 === 0) → rest day`.

---

## 9. Copy Rules

**Hero headline:** Specific, not vague.
- ❌ "Building the future with AI"
- ✅ "I'm building 90 AI projects in 100 days. Live."

**CTA:** Action-oriented, specific.
- ❌ "Get started"
- ✅ "Follow the challenge"

**About page:** Real story. Real reason. No buzzwords.

**Contact page:** Direct. Professional. No fake social proof.

---

## 10. Sound Design (Layer 4 only)

- Off by default. Small audio toggle in nav.
- Built day tap: soft chime (one note, under 1 second)
- Rest day tap: soft bell tone
- No ambient loops. No autoplay. Ever.

---

## 11. Tech Stack

| Item | Decision |
|---|---|
| Stack | Vanilla HTML + CSS + JS. Single `index.html` to start. |
| Font | Plus Jakarta Sans (Google Fonts) |
| Deploy | Vercel free tier — drag folder or GitHub connect |
| Data | JS array at top of file |
| Performance | No frameworks. Target: under 2s load on mobile 4G. |
| Mobile-first | Yes. Phone is primary device for BigBeni's audience. |

---

## 12. Build Layers — Strict Order, No Skipping

| Layer | What Gets Built | Approval Gate |
|---|---|---|
| **Layer 1** | Design system CSS vars + hero section + full bento grid with all 4 card states. No clicks. No data. Visual only. | Must be approved on mobile view before Layer 2 |
| **Layer 2** | Navigation. About page. Contact/Collab page. Smooth scroll. | Must be approved before Layer 3 |
| **Layer 3** | Data array wired up. Working modals. Rest day overlay. Live countdown. Date calculation logic. | Must be approved before Layer 4 |
| **Layer 4** | Live links. TikTok links. Sound toggle. Vercel deploy. | Ship |

---


---

