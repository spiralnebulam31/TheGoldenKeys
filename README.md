# The Golden Keys (Τα Χρυσά Κλειδιά)

A multi-page, Greek-language website for **Τα Χρυσά Κλειδιά** (The Golden Keys), a small locksmith business in western Thessaloniki, Greece. The site presents the business's services, the areas it covers, a gallery of its work, customer reviews, opening hours and contact details.

**Live site:** [www.taxrysakleidia.gr](https://www.taxrysakleidia.gr/)

## Table of Contents

- [Overview](#overview)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Pages & Features](#pages--features)
- [Content Management](#content-management)
- [Getting Started](#getting-started)
- [Available Scripts](#available-scripts)
- [Deployment](#deployment)

## Overview

**The challenge:** give a small local business a professional online presence. Customers are often in an urgent situation, such as being locked out, so they need to see quickly what the business offers, check that it covers their area and get in touch.

**The solution:** a responsive React site. The landing page gives a short preview of every section, and dedicated pages go into more detail. Floating contact icons keep phone, mobile, email and Facebook one tap away on every page. An interactive map outlines the neighbourhoods the business serves.

## Tech Stack

| Area | Technology |
| --- | --- |
| Framework | React 18, Vite 5 |
| Routing | React Router 6 |
| Styling | Tailwind CSS 3 (custom gold/dark palette and font families) with PostCSS + Autoprefixer, plus a few page-level CSS files |
| Animation | Framer Motion, with variants organised in `src/motion/` |
| Maps | Leaflet + React Leaflet: service-area polygons and a custom shop marker |
| Galleries | PrimeReact: `Galleria` + `Paginator` for photos, `Carousel` for videos |
| Responsive helpers | `react-responsive` (`useMediaQuery`) |
| Modals | `react-responsive-modal` (Accessibility statement) |
| Fonts | EB Garamond (titles), Roboto (body) via Google Fonts |
| Hosting | Vercel |

## Project Structure

```
TheGoldenKeys/
└── the-golden-keys/
    ├── public/                   # Favicon
    ├── src/
    │   ├── assets/               # Images and videos grouped by section (hero, services, gallery, etc.)
    │   ├── components/
    │   │   ├── common/           # Header, Navbar + MobileMenu, Footer, floating contact icons, titles, contact cards
    │   │   ├── landing-page/     # Hero, About, Services, Areas, Gallery and Reviews sections
    │   │   ├── services/         # Small and large service cards
    │   │   ├── areas/            # Service-areas map and shop location map
    │   │   ├── gallery/          # ImageGallery and VideoGallery
    │   │   └── reviews/          # ReviewCard
    │   ├── data/                 # Site content: services, areas, reviews, opening times, nav, contact links
    │   ├── motion/               # Framer Motion variants
    │   ├── pages/                # LandingPage, ServicesPage, AreasPage, GalleryPage, ContactPage
    │   └── App.jsx               # Router + shared layout
    ├── tailwind.config.js
    ├── vite.config.js
    └── vercel.json               # SPA rewrites for client-side routing
```

## Pages & Features

| Route | Page | Contents |
| --- | --- | --- |
| `/` | Landing page | Hero, business profile, services, areas (with a shop location map), gallery preview and customer reviews, each with an animated section title |
| `/services` | Services | Detailed service cards: keys and spare keys, locks and padlocks, security locks, car and motorbike immobilizer keys, emergency unlocking |
| `/areas` | Areas | Map with polygons for Ampelokipoi, Stavroupoli, Evosmos and Polichni, plus the shop marker |
| `/gallery` | Gallery | Paginated photo gallery (21 per page) with a full-screen lightbox, and a video carousel |
| `/contact` | Contact | Animated contact cards (phone, mobile, email, Facebook) |

**Shared across all pages**

- Responsive header and navbar, with an animated mobile menu.
- Floating contact icons that stay vertically centred while the page scrolls.
- A footer with navigation, opening hours, contact details and an Accessibility statement modal.
- Smooth scrolling with scroll padding, so section anchors are not hidden under the header.

## Content Management

All text content lives in plain JS modules in `src/data/`, separate from the components:

- `services.js`: service titles, descriptions and images
- `areas.js`: polygon coordinates for each service area
- `location.js`: shop coordinates
- `reviews.js`: customer reviews
- `opening-times.js`: weekly opening hours
- `contact-icons.js`, `navbar.js`, `footer-nav.js`: links and navigation

Images and videos are exported from `index.js` files under `src/assets/<section>/`. To add a gallery photo, drop the file in the right folder and add it to that folder's export list.

## Getting Started

### Prerequisites

Node.js 18+ and npm.

### Installation

```bash
git clone https://github.com/spiralnebulam31/TheGoldenKeys.git
cd TheGoldenKeys/the-golden-keys
npm install
npm run dev
```

Then open the local URL printed in the terminal (usually [http://localhost:5173](http://localhost:5173)).

## Available Scripts

Run these from `the-golden-keys/`:

| Script | Description |
| --- | --- |
| `npm run dev` | Start the Vite dev server |
| `npm run build` | Create a production build in `dist/` |
| `npm run preview` | Preview the production build locally |
| `npm run lint` | Run ESLint |

## Deployment

The site is deployed on Vercel with `the-golden-keys/` as the project root. `vercel.json` rewrites every path to `/`, so client-side routes load correctly on a refresh or direct visit.
