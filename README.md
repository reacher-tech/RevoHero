<<<<<<< HEAD
# Nuxt Starter Template

[![Nuxt UI](https://img.shields.io/badge/Made%20with-Nuxt%20UI-00DC82?logo=nuxt&labelColor=020420)](https://ui.nuxt.com)

Use this template to get started with [Nuxt UI](https://ui.nuxt.com) quickly.

- [Live demo](https://starter-template.nuxt.dev/)
- [Documentation](https://ui.nuxt.com/docs/getting-started/installation/nuxt)

<a href="https://starter-template.nuxt.dev/" target="_blank">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://ui.nuxt.com/assets/templates/nuxt/starter-dark.png">
    <source media="(prefers-color-scheme: light)" srcset="https://ui.nuxt.com/assets/templates/nuxt/starter-light.png">
    <img alt="Nuxt Starter Template" src="https://ui.nuxt.com/assets/templates/nuxt/starter-light.png" width="830" height="466">
  </picture>
</a>

> The starter template for Vue is on https://github.com/nuxt-ui-templates/starter-vue.

## Quick Start

```bash [Terminal]
npm create nuxt@latest -- -t github:nuxt-ui-templates/starter
```

## Deploy your own

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-name=starter&repository-url=https%3A%2F%2Fgithub.com%2Fnuxt-ui-templates%2Fstarter&demo-image=https%3A%2F%2Fui.nuxt.com%2Fassets%2Ftemplates%2Fnuxt%2Fstarter-dark.png&demo-url=https%3A%2F%2Fstarter-template.nuxt.dev%2F&demo-title=Nuxt%20Starter%20Template&demo-description=A%20minimal%20template%20to%20get%20started%20with%20Nuxt%20UI.)

## Setup

Make sure to install the dependencies:

```bash
pnpm install
```

## Development Server

Start the development server on `http://localhost:3000`:

```bash
pnpm dev
```

## Production

Build the application for production:

```bash
pnpm build
```

Locally preview production build:

```bash
pnpm preview
```

Check out the [deployment documentation](https://nuxt.com/docs/getting-started/deployment) for more information.
=======
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
>>>>>>> c89d69f8215aa52c1e1febfe7ea629df8b343a1d
