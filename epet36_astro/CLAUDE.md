# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static website for EPET N°36, a technical school in Posadas, Misiones, Argentina. Built with Astro 6.x — no UI frameworks, no CSS libraries, no backend. All content is in Spanish.

## Commands

- `npm run dev` — Dev server at localhost:4321
- `npm run build` — Production build to `./dist/`
- `npm run preview` — Preview production build locally

## Architecture

**Pure Astro static site** with file-based routing. Pages live in `src/pages/`, components in `src/components/`. No integrations, no SSR, no external UI frameworks.

### Design System

CSS custom properties defined in `src/styles/colors.css` (teal/orange palette). Typography uses Google Fonts: Montserrat for headings, Roboto for body, Space Grotesk as secondary. Global styles in `src/styles/global.css`. All component styles are scoped within `.astro` files.

Responsive breakpoints: 968px (tablet), 768px (mobile).

### Pages

- `/` — Homepage: Hero, CTAAction, two SpecialtyCard components, Footer
- `/contacto` — Contact page with info cards, embedded Google Maps, FAQs, mini footer (does not use the shared Footer component)
- `/especialidades` — Specialties overview
- `/tecnologia-alimentos` and `/gestion-organizacional` — Individual specialty detail pages with learning outcomes and enrollment CTAs
- `/por-que-elegirnos` — Why choose us (renders the WhyChooseUs component)

### Key Components

- **Navigation.astro** — Sticky header with mobile hamburger menu and dropdown for "Oferta Educativa". Contains client-side JS for interactivity.
- **Footer.astro** — 2-column layout with embedded Google Maps and contact info. Uses glassmorphism styling.
- **SpecialtyCard.astro** — Reusable card accepting props: `title`, `content`, `backgroundImage`, `linkURL`, `useBackgroundImage`, `reverse`, `imageAlt`.

### External Services

- Google Forms for pre-enrollment (linked from specialty pages and CTAs)
- Google Maps embeds in Footer and contact page
- Google Fonts CDN
