# Silvercore — Senior C# Developer Portfolio

![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)
![License](https://img.shields.io/badge/license-All%20Rights%20Reserved-lightgrey.svg)
![Status](https://img.shields.io/badge/status-Active-brightgreen.svg)

## Overview

**Silvercore** is a professional, high-performance portfolio website showcasing **Jimmy Welkenhuysen**, a senior freelance C# and .NET developer specializing in robust backend architecture, API development, and cloud solutions.

Built as a zero-dependency, static HTML/CSS/JavaScript site, Silvercore demonstrates modern web practices including responsive design, accessibility compliance, smooth interactive experiences, and optimized performance—all hosted on GitHub Pages at [silvercore.be](https://silvercore.be).

**Key Value**: Serves as both a live production portfolio and a reference implementation for building elegant, performant static sites without frameworks or build tools.

---

## Table of Contents

- [Quick Start](#quick-start)
- [Getting Started](#getting-started)
- [Architecture Overview](#architecture-overview)
- [Features](#features)
- [Theme System](#theme-system)
- [Customization Guide](#customization-guide)
- [Development Workflow](#development-workflow)
- [Project Structure](#project-structure)
- [Technology Stack](#technology-stack)
- [Deployment](#deployment)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [License](#license)

---

## Quick Start

### Option 1: Local Preview with Python

```bash
python -m http.server 8080
```

### Option 2: Local Preview with Node.js

```bash
npx serve .
```

Then open `http://localhost:8080` in your browser.

### Option 3: Direct File Preview

Simply open `index.html` directly in any modern web browser.

---

## Getting Started

### Prerequisites

- **Browser**: Any modern browser (Chrome, Firefox, Safari, Edge)
- **Editor**: VS Code, Sublime Text, or any text editor
- **Local Server** (optional): Python 3+ or Node.js + npx for local development
- **Git**: For version control and GitHub Pages deployment

### Installation

1. **Clone the repository**:

   ```bash
   git clone https://github.com/yourusername/silvercore.be.git
   cd silvercore.be
   ```

2. **Start a local development server**:

   ```bash
   # Using Python
   python -m http.server 8080
   
   # Or using Node.js
   npx serve .
   ```

3. **Open in browser**:

   Navigate to `http://localhost:8080` (or the URL shown by your server)

4. **Explore the site**:

   - Click navigation links to scroll through sections
   - Use the theme toggle to switch between design variants
   - Test responsive behavior by resizing your browser

### Modifying Content

All content is directly editable in [index.html](index.html):

- **Hero section**: Update headline, description, and call-to-action buttons
- **Services section**: Modify service offerings and descriptions
- **About section**: Edit personal description and statistics
- **Contact section**: Update contact information and links
- **Footer**: Modify copyright and footer links

Simply edit the HTML, save the file, and refresh your browser to see changes instantly.

---

## Architecture Overview

### Single-Page Application (SPA) Pattern

Silvercore implements a lightweight, accessible single-page application without frameworks or routers:

```
┌─────────────────────────────────────────┐
│          index.html (Entry Point)       │
├─────────────────────────────────────────┤
│ • Semantic HTML5 structure              │
│ • Accessibility attributes (ARIA)       │
│ • Responsive meta tags                  │
│ • Font preloading (Plus Jakarta Sans)   │
└─────────────────────────────────────────┘
         ↓              ↓               ↓
    ┌────────┐    ┌───────────┐   ┌─────────┐
    │ css/   │    │ js/       │   │ CNAME   │
    │styles  │    │main.js    │   │(GitHub) │
    │.css    │    │(200 lines)│   │Pages    │
    └────────┘    └───────────┘   └─────────┘
```

### Key Architectural Decisions

| Aspect | Choice | Rationale |
|--------|--------|-----------|
| Framework | None | Minimal dependencies; maximum performance |
| Build Tool | None | Serve directly; reduce complexity |
| JavaScript | Vanilla | No runtime overhead; full control |
| Styling | CSS Variables | Theme switching without processing |
| Hosting | GitHub Pages | Free, reliable, automatic HTTPS |
| Storage | Browser Storage | Theme persistence without backend |

### Data Flow

1. **Page Load** → HTML parses, stylesheets cascade, JS initializes
2. **User Interaction** → Navigation, scroll events, theme toggle
3. **Local Storage** → Theme preference persisted across sessions
4. **Visual Update** → CSS variables updated; components re-render instantly

---

## Features

### Visual & Interaction Design

- **Responsive Design** — Optimized layouts for desktop (1140px), tablet (960px), and mobile (480px+) with fluid typography and spacing
- **Stripe-Inspired Theme** — Vibrant gradient hero section with layered silk swoosh animations (default theme)
- **Silver Theme Variant** — Cool, minimalist alternative theme for subdued aesthetics
- **Theme Persistence** — User preference saved to browser storage; remembered across sessions
- **Smooth Scroll Behavior** — Native CSS scroll-behavior with offset for sticky header
- **Active Link Navigation** — Underline indicators follow scroll position in real-time
- **Mobile-Optimized Menu** — Hamburger navigation with animated transitions and touch-friendly targets

### Accessibility & Performance

- **WCAG 2.1 Compliance** — Semantic HTML, ARIA labels, keyboard navigation
- **Reduced Motion Support** — Respects `prefers-reduced-motion` system preference
- **Focus Management** — Visible outline styling; skip links for keyboard users
- **Backdrop Blur Optimization** — GPU-accelerated sticky header with smooth performance
- **Font Preloading** — Eliminates layout shift with Plus Jakarta Sans preconnect
- **Zero Dependencies** — No external libraries; 100% first-party code

### Interactive Elements

- **Smooth Anchor Linking** — All section links animate smoothly
- **Dynamic Footer Year** — Automatically updates copyright year
- **Mobile Menu Toggle** — Three-line hamburger button with animated state transitions
- **Keyboard Support** — ESC closes mobile menu; Tab navigation works throughout

---

## Theme System

### How Themes Work

Silvercore uses **CSS custom properties (variables)** to implement theme switching with zero JavaScript complexity:

1. **Default Theme**: `:root[data-theme="stripe"]` or `:root` (implicit default)
2. **Alternative Theme**: `:root[data-theme="silver"]`
3. **All components** reference variables like `--bg`, `--text`, `--accent`
4. **Changing theme**: Toggle `data-theme` attribute on `<html>` element
5. **Browser storage**: Preference persists via `localStorage.theme`

### Stripe Theme (Default)

The default theme draws inspiration from [Stripe's](https://stripe.com) modern design language:

| Variable | Value | Usage |
|----------|-------|-------|
| `--bg` | `#ffffff` | Page background |
| `--text` | `#0a2540` | Primary text (high contrast) |
| `--accent` | `#635bff` | Buttons, links, highlights |
| `--gradient-hero` | Multi-stop | Hero section background |

**Gradient** (Stripe Silk Swoosh):
```
135deg: #635bff (purple) → #7c3aed (violet) → #06b6d4 (cyan) 
        → #10b981 (teal) → #f59e0b (amber)
```

Color palettes with semantic scale:
- **Text**: `--text`, `--text-muted`, `--text-subtle`
- **Background**: `--bg`, `--bg-subtle`, `--bg-muted`
- **Interaction**: `--accent`, `--accent-hover`, `--accent-soft`

### Silver Theme (Alternative)

The Silver theme provides a cooler, more subdued aesthetic:

- **Cooler neutral palette** — Grays with blue undertones
- **Reduced saturation** — Accents with less vibrancy
- **Minimalist gradient** — Subtle geometric patterns instead of colorful swoosh
- **Optimized for accessibility** — Higher contrast ratios for WCAG AA+

### Customizing Themes

To modify a theme, edit the CSS variables in [styles.css](css/styles.css):

```css
/* Stripe theme: change primary color */
:root[data-theme="stripe"] {
  --accent: #7c3aed;  /* Change from purple to violet */
  --accent-hover: #6d28d9;
  --accent-soft: rgba(124, 58, 237, 0.1);
}
```

All dependent components automatically adopt the new colors—no individual edits needed.

---

## Customization Guide

### Updating Personal Information

Edit [index.html](index.html) to customize content:

#### Hero Section
```html
<!-- Line ~50 -->
<p class="hero-eyebrow">Senior freelance C# developer <span>Jimmy Welkenhuysen</span></p>
<h1 class="hero-heading">
  Robust backends. Scalable APIs. <span class="text-gradient">Cloud solutions.</span>
</h1>
```

#### Services Section
```html
<!-- Lines ~100-150 -->
<div class="card">
  <h3>Backend Development</h3>
  <p>Description of your service...</p>
</div>
```

#### About Section
```html
<!-- Lines ~160-200 -->
<div class="about-content">
  <h2>About Me</h2>
  <p>Your biography...</p>
</div>
```

#### Contact Section
```html
<!-- Lines ~240-260 -->
<h2>Ready to work together?</h2>
<p>Let's discuss your project...</p>
<a href="mailto:your@email.com" class="btn btn-primary">Get in touch</a>
```

### Modifying Colors & Styling

#### Change Primary Accent Color

Edit [css/styles.css](css/styles.css), lines 22-48 (Stripe theme):

```css
:root[data-theme="stripe"] {
  --accent: #YOUR_COLOR;        /* Change button, link, highlight color */
  --accent-hover: #DARKER_COLOR; /* Hover state */
  --accent-soft: rgba(YOUR_RGB, 0.1); /* Soft backgrounds */
}
```

#### Change Typography

```css
:root {
  --font-sans: "Your Font", system-ui, sans-serif; /* Update font family */
}
```

Add new font via Google Fonts preload:
```html
<!-- In <head> -->
<link href="https://fonts.googleapis.com/css2?family=Your+Font:wght@400;600;800&display=swap" rel="stylesheet">
```

#### Adjust Spacing & Sizing

```css
:root {
  --container-max: 1140px;      /* Max content width */
  --header-height: 72px;        /* Sticky header height */
  --radius-lg: 16px;            /* Border radius for cards */
}
```

### Adding New Sections

1. Add HTML section with unique `id`:
   ```html
   <section id="new-section" class="section">
     <div class="container">
       <!-- Content -->
     </div>
   </section>
   ```

2. Add navigation link (in `<nav>`):
   ```html
   <li><a href="#new-section" class="nav-link">New Section</a></li>
   ```

3. Style in [styles.css](css/styles.css) following existing patterns

4. Test responsive behavior at breakpoints (960px, 768px, 480px)

### Customizing Theme Switching

To add theme toggle UI, create a button in `nav-actions`:

```html
<button id="theme-toggle" class="btn btn-sm" aria-label="Toggle theme">
  🌓 Theme
</button>
```

Then add to [js/main.js](js/main.js):
```javascript
const themeToggle = document.getElementById('theme-toggle');
themeToggle.addEventListener('click', function () {
  const current = document.documentElement.getAttribute('data-theme') || 'stripe';
  const next = current === 'stripe' ? 'silver' : 'stripe';
  document.documentElement.setAttribute('data-theme', next);
  localStorage.setItem('theme', next);
});
```

---

## Development Workflow

### Local Development Setup

1. **Clone and navigate**:
   ```bash
   git clone https://github.com/yourusername/silvercore.be.git
   cd silvercore.be
   ```

2. **Start dev server**:
   ```bash
   python -m http.server 8080
   # or: npx serve .
   ```

3. **Open browser**:
   ```
   http://localhost:8080
   ```

4. **Edit files** in your editor; browser auto-refreshes (with Live Server extension) or refresh manually

### Testing Checklist

Before committing, verify:

- [ ] **Visual**: All sections render correctly on desktop/tablet/mobile
- [ ] **Interactions**: 
  - [ ] Navigation links scroll smoothly
  - [ ] Active nav indicator follows scroll
  - [ ] Mobile menu opens/closes correctly
  - [ ] ESC key closes mobile menu
- [ ] **Themes**: 
  - [ ] Switch between Stripe and Silver themes
  - [ ] Theme persists after page reload
- [ ] **Accessibility**:
  - [ ] All images have alt text (if added)
  - [ ] Tab navigation works throughout
  - [ ] Keyboard focus is visible
  - [ ] Screen reader announces semantic structure
- [ ] **Performance**:
  - [ ] Page loads under 2 seconds on 4G
  - [ ] Smooth 60fps scrolling
  - [ ] No console errors

### Browser Support

| Browser | Minimum Version | Status |
|---------|-----------------|--------|
| Chrome | 90+ | ✅ Fully supported |
| Firefox | 88+ | ✅ Fully supported |
| Safari | 14+ | ✅ Fully supported |
| Edge | 90+ | ✅ Fully supported |
| IE 11 | N/A | ❌ Not supported |

**CSS Features Used**: Custom properties, Grid, Flexbox, Backdrop filter, CSS animations

### Common Development Tasks

#### Update a service description
→ Find the service card in [index.html](index.html) and edit the text directly

#### Add a new section
→ Follow the "Adding New Sections" guide in [Customization Guide](#customization-guide)

#### Change the color scheme
→ Edit CSS variables in [styles.css](css/styles.css); see [Theme System](#theme-system)

#### Fix mobile layout issue
→ Check responsive breakpoints: 960px (tablet), 768px (mobile), 480px (small mobile)

#### Debug JavaScript interaction
→ Open DevTools (F12), check Console for errors, and inspect `localStorage.theme`

---

## Project Structure

```
silvercore.be/
├── index.html              # Single-page application (entry point)
│                          # • Semantic HTML5 structure
│                          # • Accessibility metadata (ARIA)
│                          # • Responsive viewport configuration
│                          # • Font preloading
│
├── css/
│   └── styles.css         # Complete styling system (~900 lines)
│                          # • CSS custom properties (theming)
│                          # • Component styles (header, hero, cards, etc.)
│                          # • Responsive breakpoints (960px, 768px, 480px)
│                          # • Accessibility features (reduced motion, focus)
│                          # • Stripe + Silver theme variants
│
├── js/
│   └── main.js            # Client-side interactivity (~150 lines)
│                          # • Mobile navigation toggle
│                          # • Active link highlighting on scroll
│                          # • Smooth anchor link navigation
│                          # • Dynamic footer year update
│                          # • Theme persistence via localStorage
│
├── CNAME                  # GitHub Pages custom domain
│                          # Contains: silvercore.be
│
└── README.md              # This documentation file
```

### File Dependencies

```
index.html
├── css/styles.css (linked in <head>)
├── js/main.js (linked before </body>)
└── Google Fonts API (for Plus Jakarta Sans)

styles.css
└── (no external dependencies; self-contained)

main.js
└── (no external dependencies; vanilla JavaScript)
```

### Key Sections in index.html

| Line Range | Section | Purpose |
|------------|---------|---------|
| 1-20 | Head / Metadata | Document structure, SEO, fonts |
| 20-50 | Header / Navigation | Sticky nav, mobile toggle, links |
| 50-100 | Hero Section | Main headline, gradient background, CTA |
| 100-150 | Services Section | Service cards / offerings |
| 150-200 | About Section | Personal bio, stats, image |
| 200-240 | Contact Section | Call-to-action, contact form |
| 240-250 | Footer | Copyright, links, year auto-update |

---

## Technology Stack

### Frontend

| Technology | Purpose | Version | Rationale |
|-----------|---------|---------|-----------|
| **HTML5** | Markup & Semantics | Evergreen | Native standards; no build needed |
| **CSS3** | Styling & Layout | Evergreen | Custom properties for theming |
| **Vanilla JS** | Interactivity | ES6+ | No framework overhead; full control |
| **Plus Jakarta Sans** | Typography | Latest | Google Fonts; modern, friendly typeface |

### Hosting & Deployment

| Service | Purpose | Free Tier | Notes |
|---------|---------|-----------|-------|
| **GitHub Pages** | Web Hosting | Yes | Automatic deploys from `main` branch |
| **GitHub Domains** | Version Control | Yes | Repository storage & collaboration |
| **Registrar** | Custom Domain | $10-15/yr | Any registrar (namecheap, GoDaddy, etc.) |

### Development Tools (Optional)

| Tool | Purpose | Command |
|------|---------|---------|
| **Python HTTP Server** | Local preview | `python -m http.server 8080` |
| **Node.js `serve`** | Alternative server | `npx serve .` |
| **VS Code Live Server** | Auto-reload | Install extension; right-click → Open with Live Server |
| **Browser DevTools** | Debugging | F12 in any browser |

### Browser APIs Used

- **`localStorage`** → Theme persistence
- **`window.scrollY`** → Active link detection
- **`Element.scrollIntoView()`** → Smooth scroll navigation
- **`Date`** → Dynamic footer year
- **`window.addEventListener()`** → Scroll & resize handling

---

## Deployment

### Deploy to GitHub Pages

#### Step 1: Push to GitHub

```bash
git add .
git commit -m "Deploy Silvercore website"
git push origin main
```

#### Step 2: Enable GitHub Pages

1. Go to your repository on GitHub
2. Navigate to **Settings** → **Pages**
3. Under **Build and deployment**:
   - **Source**: Select "Deploy from a branch"
   - **Branch**: Select `main` and `/ (root)`
4. Click **Save**

The site will be live at `https://yourusername.github.io/silvercore.be/` within 2–3 minutes.

#### Step 3: Add Custom Domain (silvercore.be)

1. In **Settings** → **Pages**, under **Custom domain**, enter `silvercore.be`
2. Click **Save**
3. GitHub will create a [CNAME](CNAME) file automatically (or verify the existing one)

#### Step 4: Configure DNS Records

At your domain registrar (Namecheap, GoDaddy, Route 53, etc.), configure these DNS records:

This routes `silvercore.be` directly to GitHub Pages.

**Option B: www Subdomain**

| Type | Name | Value |
|------|------|-------|
| CNAME | `www` | `yourusername.github.io` |

This routes `www.silvercore.be` to your GitHub Pages site.

**Recommended**: Use **Option A** (apex A records) for the primary domain.

#### Step 5: Enable HTTPS

1. Return to **Settings** → **Pages**
2. Once DNS is verified (typically 5–30 minutes), check **Enforce HTTPS**
3. This forces all traffic to use encrypted connections

**DNS Propagation**: Changes may take 24–48 hours to propagate globally, but usually appear within 5–15 minutes.

### Verifying Deployment

After DNS propagates, test:

```bash
# Check DNS resolution
nslookup silvercore.be

# Verify HTTPS
curl -I https://silvercore.be
# Should return: 200 OK
```

### Updating the Live Site

After deployment, updates are simple:

1. Edit files locally
2. Test with local server
3. Commit and push:
   ```bash
   git add .
   git commit -m "Update [section]"
   git push origin main
   ```
4. Changes deploy automatically (usually within 30 seconds)

---

## Troubleshooting

### Local Development Issues

#### Site doesn't load locally
- **Problem**: "Connection refused" error
- **Solution**: Ensure your dev server is running; check port 8080 is not in use
  ```bash
  # Try a different port
  python -m http.server 9000
  ```

#### Styles not loading
- **Problem**: CSS file is blank or not found
- **Solution**: Check that `css/styles.css` exists in the project root; verify file path in HTML

#### JavaScript errors in console
- **Problem**: "Uncaught ReferenceError" or "Cannot read property"
- **Solution**: 
  - Verify `js/main.js` is linked before `</body>` in HTML
  - Check browser console (F12) for specific errors
  - Ensure JavaScript file isn't minified unexpectedly

#### Theme toggle not persisting
- **Problem**: Theme resets after page reload
- **Solution**: Check that `localStorage` is enabled; test in browser console:
  ```javascript
  localStorage.setItem('test', 'value');
  console.log(localStorage.getItem('test')); // Should return 'value'
  ```

### Deployment Issues

#### Domain not connecting to GitHub Pages
- **Problem**: DNS error or timeout
- **Solution**:
  - Verify A records are correctly set in DNS registrar
  - Wait for DNS propagation (can take up to 48 hours)
  - Use `nslookup silvercore.be` to verify records
  - Check CNAME file exists: [CNAME](CNAME)

#### HTTPS certificate not issuing
- **Problem**: "Enforce HTTPS" option is grayed out
- **Solution**:
  - Wait for DNS to fully propagate first
  - Ensure custom domain is correctly configured in GitHub Pages settings
  - Retry after 30 minutes

#### GitHub Pages shows 404
- **Problem**: Page not found error
- **Solution**:
  - Verify repository is public (private repos need GitHub Pro for Pages)
  - Ensure default branch is set to `main`
  - Check Pages settings point to root (`/`) not a subdirectory
  - Verify `index.html` exists in repository root

#### Theme not visible on live site
- **Problem**: Stripe or Silver theme colors don't appear
- **Solution**:
  - Force hard refresh: `Ctrl+Shift+R` (Chrome/Firefox) or `Cmd+Shift+R` (Mac)
  - Clear browser cache and cookies for the domain
  - Check that CSS file is loading (Network tab in DevTools)

### Mobile Issues

#### Mobile menu doesn't open
- **Problem**: Hamburger button unresponsive
- **Solution**:
  - Check JavaScript is enabled in mobile browser
  - Verify touch events aren't blocked
  - Test on different browser (Chrome, Safari)
  - Check viewport meta tag is present: `<meta name="viewport" content="width=device-width, initial-scale=1.0">`

#### Layout breaks on small screens
- **Problem**: Content overlaps or text is too small
- **Solution**:
  - Test responsive breakpoints: resize to 768px and 480px widths
  - Check mobile-specific styles in CSS (lines ~700–800)
  - Verify container padding and font sizes scale properly

#### Slow performance on mobile
- **Problem**: Page feels sluggish; scrolling is janky
- **Solution**:
  - Disable unnecessary animations: check `prefers-reduced-motion` support
  - Test on slower 4G connection (DevTools → Network throttling)
  - Minimize JavaScript execution during scroll
  - Ensure images are optimized (if any added)

### Browser Compatibility

#### CSS not working in older browsers
- **Problem**: Colors, layout broken in IE 11 or old Safari
- **Solution**: Silvercore requires modern browsers (Chrome 90+, Safari 14+)
  - CSS custom properties require CSS4 support
  - Provide fallbacks for older browsers if needed:
    ```css
    --accent: #635bff; /* CSS4 custom property */
    color: #635bff;    /* IE 11 fallback */
    color: var(--accent);
    ```

#### Smooth scroll not working
- **Problem**: Anchor links jump instantly
- **Solution**:
  - Check `scroll-behavior: smooth` is in CSS
  - Verify browser supports smooth scroll (most modern browsers do)
  - Fallback is instant scroll (acceptable UX)

---

## Contributing

Contributions and feedback are welcome! Whether you're reporting issues, suggesting improvements, or forking the project for your own use, we appreciate your involvement.

### How to Contribute

1. **Report Issues**: Found a bug or design inconsistency?
   - Open an issue on GitHub describing the problem
   - Include steps to reproduce and your browser/device info
   - Provide screenshots if applicable

2. **Suggest Improvements**: Have ideas for new features or better UX?
   - Open a discussion or issue with your suggestion
   - Explain the benefit and how it aligns with the site's goals
   - Include mockups or design concepts if possible

3. **Submit Pull Requests**: Want to contribute code?
   - Fork the repository
   - Create a feature branch: `git checkout -b feature/your-idea`
   - Make changes following the project's style and structure
   - Test thoroughly on desktop and mobile
   - Submit a pull request with a clear description

### Contribution Guidelines

- **Code Style**: Follow existing patterns in HTML, CSS, and JavaScript
- **Accessibility**: Ensure changes don't reduce accessibility; test with keyboard and screen readers
- **Performance**: Avoid adding heavy dependencies; prioritize small footprint
- **Testing**: Test across browsers (Chrome, Firefox, Safari, Edge) and devices (desktop, tablet, mobile)
- **Documentation**: Update README if adding new features or changing functionality

### Areas for Contribution

- **Themes**: Create new theme variants (design systems)
- **Animations**: Enhance scroll or interaction animations
- **Accessibility**: Improve WCAG compliance and screen reader support
- **Performance**: Optimize load times, reduce CSS/JS size
- **Localization**: Support for multiple languages
- **Documentation**: Improve guides and troubleshooting sections

### Code of Conduct

This project is maintained with professionalism and respect. Contributors are expected to:
- Communicate respectfully and constructively
- Respect intellectual property and licensing
- Focus on improvements that benefit the project's goals
- Avoid spam, self-promotion, or malicious activity

---

## License

**All Rights Reserved**

© 2024 Silvercore. All rights reserved.

The content, design, code, and materials in this repository are the intellectual property of **Jimmy Welkenhuysen** and **Silvercore**. Unauthorized copying, modification, or redistribution is prohibited without explicit written permission.

### Permitted Use

- **Personal Study**: You may view and study this code as a reference implementation
- **Portfolio**: You may fork this project as a template for your own portfolio (with substantial modifications)
- **Open Source Contributions**: Contributing improvements via pull requests is encouraged

### Not Permitted

- Commercial reproduction or sale
- Hosting or serving the site as your own without modification
- Trademark or brand reproduction
- Mass distribution or licensing to third parties

---

## Questions & Support

For questions about the site, deployment issues, or feature suggestions:

- **Email**: [your-email@example.com]
- **Website**: [silvercore.be](https://silvercore.be)
- **GitHub Issues**: [Report an issue](https://github.com/yourusername/silvercore.be/issues)

---

**Thank you for visiting Silvercore! If you found this project helpful, please consider starring the repository. 🌟**
- **No Dependencies** — Pure HTML, CSS, and JavaScript—zero build tools required
- **Fast & Lightweight** — Static files only; instant load times and ideal for GitHub Pages
- **Professional Branding** — Clean, modern layout emphasizing expertise and accessibility

## Technology Stack

| Layer | Technology |
|-------|-----------|
| **Markup** | HTML5 |
| **Styling** | CSS3 (custom themes, responsive) |
| **Interactivity** | Vanilla JavaScript (theme toggle, navigation) |
| **Hosting** | GitHub Pages + custom domain |

## License

© Silvercore. All rights reserved.
