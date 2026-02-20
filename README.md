# Trempel Game - Portfolio & Design System

## Project Description

Trempel Game is an independent "High-End Indie" game studio founded by Nikita Donorkin (Nikitiya). 
This repository contains the production-ready static portfolio website for the studio, built with maximum SEO coverage, multi-language support (English & Russian), and a performance-oriented CSS-only animation approach.

The site uses a strict "OLED Noir" aesthetic without any JavaScript frameworks (no React, Vue, Tailwind, or npm build tools), hosted on GitHub Pages.

## File Structure

```text
/
├── index.html          # Main English version (lang="en")
├── privacy.html        # Privacy Policy EN (required for Google Play)
├── styles.css          # Global Design System & CSS-only Animations
├── sitemap.xml         # SEO sitemap with hreflang definitions
├── robots.txt          # Web crawler configuration
├── README.md           # Project documentation
└── ru/                 # Russian Localization
    ├── index.html      # Russian version
    └── privacy.html    # Privacy Policy RU
```

## CSS Tokens (OLED Noir Design System)

The global styling is driven by CSS variables located at the top of `styles.css`.

```css
:root {
  --bg-color: #050505;        /* Deep OLED Black */
  --bg-surface: #121212;      /* Elevated Surface */
  --accent-1: #03dac6;        /* Electric Teal - Primary Interactions */
  --accent-2: #bb86fc;        /* Soft Purple - Secondary Accents */
  --text-primary: #e8e8e8;    /* High Contrast Text */
  --text-secondary: #999999;  /* Muted Text */
  
  --font-main: 'Outfit', sans-serif;
  
  --glass-bg: rgba(18, 18, 18, 0.7);
  --glass-border: rgba(255, 255, 255, 0.05);
  
  --transition-smooth: 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
}
```

## Game Card Template

To add a new game, copy and paste the following HTML structure inside the `<div class="games-grid">` in both `index.html` and `ru/index.html`:

```html
<!-- ======= GAME CARD ======= -->
<article class="game-card fade-up" itemscope itemtype="https://schema.org/SoftwareApplication">
  <meta itemprop="applicationCategory" content="Game">
  <meta itemprop="operatingSystem" content="Android">
  <meta itemprop="author" content="Trempel Game">
  
  <div class="game-visual">
    <!-- Replace emoji with an <img> tag if you have an icon -->
    <div class="emoji">🎮</div> 
    <span class="platform-badge">Android</span>
  </div>
  
  <div class="game-info">
    <div class="game-genre" itemprop="genre">Genre Name</div>
    <h3 class="game-title" itemprop="name">Game Title</h3>
    <p class="game-desc" itemprop="description">Short description (1-2 sentences) about the game.</p>
    
    <a href="#" class="btn-primary" itemprop="downloadUrl">
      <!-- Google Play SVG Icon -->
      <svg width="24" height="24" viewBox="0 0 24 24" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
        <path d="M3 20.5V3.5C3 2.91 3.34 2.39 3.84 2.15L13.69 12L3.84 21.85C3.34 21.6 3 21.09 3 20.5ZM14.85 10.83L18.44 8.79C19.34 8.28 19.34 6.96 18.44 6.45L16.48 5.34L14.85 10.83ZM16.48 18.66L18.44 17.55C19.35 17.04 19.35 15.72 18.44 15.21L14.85 13.17L16.48 18.66ZM4.8 3.51L14.28 12.99L4.8 20.49V3.51Z"/>
      </svg>
      Get on Google Play
    </a>
  </div>
</article>
<!-- ======= END GAME CARD ======= -->
```

## 🚨 Critical Rules for AI Agents

1. **Do not break multilingual support.** Always ensure `hreflang` tags in the `<head>` are consistent across all versions.
2. **Use Relative Paths!** 
   * When linking from `index.html` to RU: use `ru/index.html`
   * When linking from `ru/index.html` to EN: use `../index.html`
   * From `ru/index.html`, CSS is referenced as `../styles.css`
   * This ensures the site functions properly offline and across different subfolder deployments (like GitHub Pages).
3. **No JavaScript.** Features like language switching must remain simple HTML relative `<a href="...">` links. Animations must be standard `@keyframes` and CSS `transition`.
4. **Maintain JSON-LD & Open Graph.** Every page must preserve its SEO tags and JSON-LD structured data.
5. **No build tools.** Do not introduce Webpack, Vite, npm, Tailwind, etc. This is a strictly pure HTML/CSS project.
