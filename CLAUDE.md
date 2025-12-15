# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a static marketing website for RemodelaMiDepa, an interior design and home remodeling service based in Mexico City. The site is built with vanilla HTML, CSS, and JavaScript, using Tailwind CSS (via CDN) for styling.

## Architecture

### Tech Stack
- **HTML**: Vanilla HTML5, Spanish language (`lang="es"`)
- **CSS**: Tailwind CSS v3 (CDN) + custom CSS in `main.css`
- **JavaScript**: Vanilla JS for interactive components (accordion, tabs, mobile menu, Swiper carousel)
- **External Libraries**:
  - Swiper.js v11 (image carousel)
  - Font Awesome 5.15.3 (icons)
  - LinkDrip pixel tracking (analytics)

### Site Structure
- `index.html` - Main landing page with sections: hero, gallery, services, work process, featured project, testimonials, FAQ, contact
- `projects.html` - Featured project showcase page (family apartment renovation)
- `main.css` - Custom styles (Aeonik font, accordion, hero title, Swiper)
- `assets/` - Images, logos, fonts, SVG icons, project photos organized in subdirectories

### Key Components

**Mobile Menu** (Pure CSS + JS):
- Checkbox-based toggle using Tailwind's `peer` utilities
- Hamburger icon transforms to X when open
- Overlay menu with dark green background (`#214438`)
- JavaScript closes menu when contact link is clicked

**Accordion FAQ** (Vanilla JS):
- Multiple accordion instances across tabbed sections
- Click handler toggles `open`/`close` classes
- Auto-closes other accordions when one opens (single accordion open at a time)
- Located in FAQ section with 4 tabs

**Tabs System** (Vanilla JS):
- FAQ section has 4 categories: service details, coverage, pricing/timelines, getting started
- `showTab()` function handles visibility and active state styling
- Default tab shown on page load via DOMContentLoaded event

**Image Carousel** (Swiper.js):
- Auto-play carousel with 2.5s delay
- Centered slides with loop
- Pagination dots (custom color: `#294038`)

**WhatsApp Widget**:
- Fixed position button (bottom-right)
- Links to `https://link.remodelamidepa.com/Wl0On` (tracked URL)

### Design System

**Colors**:
- Primary dark green: `#294038` / `#214438`
- Light gray background: `#F4F4F4`
- Black text: `#201E1F`
- White for contrast

**Typography**:
- Primary font: Aeonik (custom font with Regular, Bold, Light weights)
- Hero title responsive sizing: 4.2rem (desktop) → 3rem (tablet) → 2.5rem (mobile)
- Section numbers format: `01/`, `02/`, etc.

**Responsive Breakpoints**:
- Mobile-first approach
- Tailwind's default breakpoints (sm: 640px, md: 768px, lg: 1024px, xl: 1280px)
- Desktop padding: `px-20`, Mobile padding: `px-6`

### External Integrations
- **LinkDrip**: Analytics pixel tracking (currently active on index.html, commented out on projects.html)
- **WhatsApp**: All contact CTAs link to tracked WhatsApp URL
- **Instagram**: Social media link to `@remodelamidepa`

## Development Workflow

### Viewing the Site
Open `index.html` or `projects.html` directly in a browser. No build process required.

### Making Changes
- HTML modifications: Edit `index.html` or `projects.html`
- Styling: Prefer Tailwind utility classes; add custom CSS to `main.css` only for complex components
- JavaScript: Inline scripts at bottom of HTML files (no separate JS files)
- Images: Add to `assets/` directory with appropriate subdirectories

### Git Workflow
- Main branch: `main`
- Current branch: `develop`
- Do not push to GitHub without explicit user approval

## Content Notes

- Site is entirely in Spanish
- Target audience: Families and homeowners in Mexico City looking for full-service interior design and remodeling
- Service model: Design + execution (not just design, not just construction)
- Featured project: Family apartment with custom furniture, storage solutions, and rooftop renovation
- Pricing/timeline info intentionally vague to drive WhatsApp consultations

## Common Patterns

**Section Structure**:
Most sections follow this pattern:
1. Section number (e.g., `01/`) positioned on left (mobile) or right (desktop)
2. Heading (h2 or h3, uppercase, large text)
3. Descriptive paragraph
4. Content grid or cards

**Two-Column Layouts**:
Common grid pattern: `grid grid-cols-2` with `col-span-2 lg:col-span-1` for responsive switching

**CTA Buttons**:
- Primary: Black background, white text, rounded
- Secondary: Black border, transparent/white background, black text, rounded
- All link to WhatsApp or anchor links (contact section)

## Technical Debt / TODOs

- Several commented-out sections in both HTML files (team section, videocall CTAs)
- Some inline TODO comments about changing enums and background colors when "Conoce al equipo" section is activated
- Commented-out LinkDrip tracking code in projects.html
- No build tooling (relies on CDN for Tailwind)
- No package.json or dependency management (all via CDN)
