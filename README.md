# Horizon Aid — NGO Website Mockup

A multi-page frontend mockup for a fictional global humanitarian & environmental
aid NGO, built with **Nuxt 4**, **Vue 3** (`<script setup>`), and **Tailwind CSS v4**.

## Stack

- Nuxt 4 (`app/` srcDir convention, auto-imports, file-based routing)
- Vue 3 Composition API
- Tailwind CSS v4 (via `@tailwindcss/vite`)
- Custom `brand` / `leaf` / `sunset` color palette in `app/assets/css/main.css`

## Getting started

```bash
npm install
npm run dev
```

Then open http://localhost:3000.

## Structure

```
app/
├── app.vue                    # Root — mounts layout + page
├── assets/css/main.css        # Tailwind entry + theme tokens
├── layouts/default.vue        # Header + <slot/> + Footer
├── components/
│   ├── TheHeader.vue          # Sticky nav, mobile menu, Donate CTA
│   ├── TheFooter.vue          # Newsletter, link columns, socials
│   ├── HeroSection.vue        # Homepage hero
│   ├── ImpactMetrics.vue      # 3-col animated counters
│   ├── CampaignCard.vue       # Campaign card w/ progress bar
│   └── DonationForm.vue       # Tier selector + frequency toggle
└── pages/
    ├── index.vue              # Hero · Metrics · Campaigns · CTA
    ├── about.vue              # Stub — linked from nav
    ├── impact.vue             # Stub — linked from nav
    └── donate.vue             # Donation form page
```

## Notes

- All imagery is generated in-component with CSS gradients + SVG patterns,
  so the mockup runs with **zero external asset dependencies**.
- Forms (newsletter, donation) are mocked client-side — no backend wiring.
- Everything is fully responsive (mobile-first).
