# LOOO Landing — Nuxt Drop-in Guide

## What goes where in your Nuxt project

```
YOUR-NUXT-PROJECT/
│
├── nuxt.config.ts          ← REPLACE or MERGE with the provided nuxt.config.ts
│
├── assets/
│   └── css/
│       └── main.css        ← ADD this file (or merge into your existing global CSS)
│
├── pages/
│   └── index.vue           ← ADD (or replace your existing index.vue)
│
└── components/
    ├── TheNavbar.vue       ← ADD
    ├── HeroSection.vue     ← ADD
    ├── TheDashboard.vue    ← ADD
    └── LogoCarousel.vue    ← ADD
```

---

## Step-by-step

### 1. Copy the component files
Copy all 4 files from `components/` into your project's `components/` folder.
Nuxt auto-imports them — no manual import statements needed.

### 2. Copy the page
Copy `pages/index.vue` into your project's `pages/` folder.
If you already have a `pages/index.vue`, replace it (or merge the template content).

### 3. Add global CSS
Copy `assets/css/main.css` into your project.

If you already have a global CSS file, paste the `:root {}` variables block
and the reset rules at the top of it instead.

### 4. Update nuxt.config.ts

**If you don't have a nuxt.config.ts yet**, just copy the provided one.

**If you already have one**, add these two sections:

```ts
export default defineNuxtConfig({
  // ... your existing config ...

  css: ['~/assets/css/main.css'],   // ← add this line

  app: {
    head: {
      link: [
        { rel: 'preconnect', href: 'https://fonts.googleapis.com' },
        { rel: 'preconnect', href: 'https://fonts.gstatic.com', crossorigin: '' },
        {
          rel: 'stylesheet',
          href: 'https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Sans:opsz,wght@9..40,300;9..40,400;9..40,500&display=swap',
        },
      ],
    },
  },
})
```

### 5. Run the dev server
```bash
npm run dev
```
Open http://localhost:3000 — you should see the full page.

---

## Adding real logo icons to the carousel

Open `components/LogoCarousel.vue`. Find the comment `TO ADD REAL ICONS` and:

1. Add a `src` field to each logo object:
```js
const logos = [
  { id: 1, name: 'Logoipsum', src: '/icons/logoipsum.svg' },
  // ...
]
```

2. Replace the `<span>{{ logo.name }}</span>` with:
```html
<img :src="logo.src" :alt="logo.name" />
```

Place your SVG/PNG files in `public/icons/`.

---

## Swapping text in the dashboard

All data (stats, integrations, todos, chart bars) lives in `components/TheDashboard.vue`
inside the `<script setup>` block. Edit the arrays there to update the displayed values.