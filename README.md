<div align="center">
  <img src="docs/logo.webp" alt="AfterTech Logo" width="180" />
  <h1>AfterTech</h1>
  <p>Boutique web agency landing page — Hebrew RTL, dark-mode, conversion-focused</p>

  <br />

  [![Live Site](https://img.shields.io/badge/Live%20Site-after--tech.co.il-10B981?style=for-the-badge)](https://www.after-tech.co.il/)

  <br /><br />

  <img src="https://img.shields.io/badge/Performance-90+-4ade80?style=flat-square&logo=lighthouse&logoColor=white" alt="Performance" />
  <img src="https://img.shields.io/badge/Accessibility-90+-4ade80?style=flat-square" alt="Accessibility" />
  <img src="https://img.shields.io/badge/Best%20Practices-90+-4ade80?style=flat-square" alt="Best Practices" />
  <img src="https://img.shields.io/badge/SEO-100-4ade80?style=flat-square" alt="SEO" />

  <br /><br />

  [![Astro](https://img.shields.io/badge/Astro-5-BC52EE?style=flat-square&logo=astro&logoColor=white)](https://astro.build/)
  [![React](https://img.shields.io/badge/React-19-61DAFB?style=flat-square&logo=react&logoColor=black)](https://react.dev/)
  [![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6?style=flat-square&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
  [![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-4-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white)](https://tailwindcss.com/)
  [![Vercel](https://img.shields.io/badge/Deployed_on-Vercel-000000?style=flat-square&logo=vercel&logoColor=white)](https://vercel.com/)

  <br /><br />

  > **Note:** This is a showcase repository. Source code is maintained in a private repository.
</div>

---

## Preview

<div align="center">

### Desktop

<img src="docs/screenshots/desktop.png" alt="AfterTech desktop view" width="800" />

### Mobile

<img src="docs/screenshots/mobile.png" alt="AfterTech mobile view" width="300" />

</div>

---

## About the Project

AfterTech is a single-page Hebrew (RTL) landing page for a boutique web agency serving Israeli small and medium-sized businesses. The site positions Shagee Menahem as a trusted technical partner — handling the complexity of modern web development so business owners can focus on running their business.

The page is built for conversion: it walks visitors through a clear narrative from the hero hook to transparent pricing, real client work, and a dual-form intake system. Every section is independently hydrated via Astro Islands Architecture, ensuring minimal JavaScript is delivered to the browser.

### Goals
- Establish credibility through technical depth and real portfolio work
- Drive leads through two contact flows: quick inquiry and detailed intake questionnaire
- Achieve 90+ Lighthouse scores across all four metrics
- Support full accessibility with a persistent accessibility menu

---

## Key Features

### Design and UX
- **Dark Mode Design System** — Single dark-mode-only theme with emerald green primary, cyan accent, and amber highlight palette built on CSS custom properties via Tailwind `@theme` block
- **RTL Hebrew-First** — All layouts built with Tailwind logical properties (`ps-`, `pe-`, `ms-`, `me-`) for correct right-to-left rendering across all breakpoints. Self-hosted Heebo (variable 300–900) and David Libre typefaces with no external font requests
- **Centralized Content** — All Hebrew copy, labels, and metadata live in `src/data/siteContent.ts`. No hardcoded strings in component files

### Animations and 3D
- **Aceternity-Style UI Library** — Custom animated primitives built in-house: bento grid, 3D pin, scroll-morph hero, card hover effects, tracing beam, focus cards, meteors, vortex background, and particle fields
- **Centralized Animation Presets** — All Framer Motion variants, easing curves, duration constants, spring configs, and viewport helpers exported from `src/lib/animations.ts`. Components import presets rather than defining motion values inline
- **Three.js 3D Elements** — Interactive 3D globe and procedural particle field via `@react-three/fiber` + `@react-three/drei`. Particle geometry uses simplex noise for organic movement. All 3D components guard against SSR with a mounted-state pattern

### Technical
- **Astro Islands Architecture** — Static HTML at build time with selective React hydration. Above-the-fold components use `client:load`; all remaining sections use `client:visible` and hydrate only on scroll into view
- **Structured Data and SEO** — JSON-LD schemas: `Organization`, `ProfessionalService`, `WebSite`, and `FAQPage`. Automated sitemap, Open Graph metadata, and canonical URLs throughout
- **Performance-First Build** — Explicit image dimensions preventing CLS, deferred hydration, CSS-only animations where possible, lazy-loading for all below-fold sections

### Forms and Accessibility
- **EmailJS Contact System** — Quick-inquiry form for general leads and a detailed intake questionnaire for project scoping. Both submit client-side via EmailJS with Israeli phone number validation — no backend required
- **Floating Accessibility Menu** — Five independently toggleable display modes: grayscale, high contrast, enlarged text, link highlighting, and reduced motion. Preferences applied via CSS class toggling on the document body

---

## Page Sections

The single-page layout consists of nine sections:

| # | Section | Description |
|---|---------|-------------|
| 1 | **Hero** | Animated scroll-morph headline with dual CTA |
| 2 | **Value Proposition** | Four-card bento grid showcasing core advantages |
| 3 | **Expert** | Credentials, background, and portrait |
| 4 | **Portfolio** | Client work showcase with device mockups |
| 5 | **Process** | Five-step workflow with icons and timeline |
| 6 | **Pricing** | Three tiers — Prime / Authority / Custom |
| 7 | **Maintenance** | Post-launch support options |
| 8 | **FAQ** | Nine accordion items addressing common objections |
| 9 | **CTA** | Dual intake form with WhatsApp fallback |

---

## Tech Stack

| Layer | Technology | Purpose |
|-------|-----------|---------|
| **Framework** | [Astro 5](https://astro.build/) | Static generation with partial hydration |
| **UI** | [React 19](https://react.dev/) | Interactive component islands |
| **Styling** | [Tailwind CSS 4](https://tailwindcss.com/) | Utility-first CSS with custom design tokens |
| **Animation** | [Framer Motion](https://www.framer.com/motion/) | Scroll animations and micro-interactions |
| **3D** | [Three.js](https://threejs.org/) + `@react-three/fiber` | 3D globe and particle effects |
| **Noise** | `simplex-noise` | Procedural particle movement |
| **Icons** | [Lucide React](https://lucide.dev/) | Consistent icon system |
| **Forms** | `@emailjs/browser` | Client-side email delivery |
| **Language** | [TypeScript 5](https://www.typescriptlang.org/) (strict) | Type-safe development |
| **Deployment** | [Vercel](https://vercel.com/) | Edge deployment via `@astrojs/vercel` adapter |
| **Sitemap** | `@astrojs/sitemap` | Automatic sitemap generation |

---

## Architecture Highlights

```
src/
├── data/siteContent.ts     <- Single source of truth for all Hebrew copy
├── lib/
│   ├── animations.ts       <- All Framer Motion presets (variants, easing, springs)
│   └── utils.ts            <- cn() class merger (clsx + tailwind-merge)
├── styles/global.css       <- @theme tokens, component utilities, keyframes
├── components/
│   ├── sections/           <- 9 page sections, barrel-exported
│   ├── ui/                 <- Animated primitive library
│   └── portfolio/          <- Portfolio detail components
└── pages/index.astro       <- Hydration directives for all sections
```

**Hydration strategy:**

| Strategy | Components |
|----------|-----------|
| `client:load` | Navbar, Hero, WhatsApp button, Scroll-to-top, Footer |
| `client:visible` | All remaining sections |
| `client:idle` | Floating accessibility button |

---

## Performance

| Metric | Score |
|--------|-------|
| Performance | 90+ |
| Accessibility | 90+ |
| Best Practices | 90+ |
| SEO | 100 |

_Google PageSpeed Insights_

---

## License

All Rights Reserved. This is a commercial project. Source code is not included in this repository.

---

## Author

**Sagi Menahem** — Full-Stack Developer

[![GitHub](https://img.shields.io/badge/GitHub-sagi--menahem-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/sagi-menahem)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/sagi-menahem/)

---

<div align="center">
  <strong>Interested in a similar project? <a href="https://www.linkedin.com/in/sagi-menahem/">Get in touch</a>.</strong>
</div>