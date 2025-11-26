# Website Redesign: Complete Design Document
## Martin Lukac – AI Practitioner-Researcher

**Document Version:** 1.0  
**Date:** November 19, 2025  
**Status:** Ready for Development

---

## Table of Contents

1. [Executive Summary](#executive-summary)
2. [Design Philosophy](#design-philosophy)
3. [Visual Direction](#visual-direction)
4. [Color System](#color-system)
5. [Typography](#typography)
6. [Layout & Spacing](#layout--spacing)
7. [Component Specifications](#component-specifications)
8. [Page Structure](#page-structure)
9. [Interaction Design](#interaction-design)
10. [Content Strategy](#content-strategy)
11. [Technical Implementation](#technical-implementation)
12. [Success Metrics](#success-metrics)
13. [Deliverables Checklist](#deliverables-checklist)

---

## Executive Summary

### Current State
- Outdated portfolio mentioning closed ventures (Koios)
- Missing current work (Flank, Sentra, PsySafe)
- Generic academic layout
- No clear practitioner identity

### Target State
A modern, purpose-driven personal site that positions Martin at the intersection of deployment and ethics—credible to practitioners, accessible to stakeholders, and memorable to anyone building AI in high-stakes domains.

### Design Philosophy
**"Deployed Clarity"** – Clean, confident, technically grounded without being corporate. The site should feel like Martin's work: rigorous but not academic, real-world but not reckless.

---

## Design Philosophy

### Core Principles

1. **Credibility through clarity** – No jargon fog. If someone reads a sentence, they understand what you actually do.

2. **Deployment-first framing** – Lead with messy real-world problems (legal doc review, crisis chatbots) not the technology stack.

3. **Ethical tension made visible** – Don't hide the hard parts. Show that you work where AI capability meets human vulnerability.

4. **Academic rigor without academic dress** – PhD credibility, practitioner language.

5. **Open by default** – PsySafe, methods, lessons learned—if you're building openly, the site should breathe that ethos.

### Reference Sites Analysis

#### Hume.ai - Technical Confidence
- Dark mode foundation creates focus
- High contrast text for readability
- Purposeful animation that demonstrates
- Minimal ornamentation

**Key takeaway:** Technical credibility through restraint. Let the work speak.

#### Sian Brooke - Academic Authority Without Baggage
- Bold typography as primary hierarchy
- Text-forward design (ideas > decoration)
- Simple, clear sections
- Personal but professional voice

**Key takeaway:** Bio should feel like a well-edited personal statement, not a LinkedIn scrape.

#### ElevenLabs - Premium Polish
- Subtle gradients add depth
- Safety/ethics prominently featured
- Professional production value
- Clear product differentiation

**Key takeaway:** Serious work deserves matching gravitas without feeling cold.

---

## Visual Direction

### Core Aesthetic: "Workshop at 2AM"

Think focused, well-organized workshop late at night:
- **Intentional lighting** – Dark bg, high contrast text
- **Tools clearly laid out** – Nav, cards, clear structure
- **Work in progress visible** – Active projects, status
- **Still warm coffee** – Maintained, active, real

**NOT:**
- Sterile lab (too clinical)
- Chaotic notebook (too informal)
- Slick showroom (too corporate)

---

## Color System

### Foundation (Dark Mode Primary)

```css
/* Base Colors */
--color-bg-primary: #0A0E14;          /* Deep charcoal background */
--color-bg-surface: #131820;          /* Elevated elements */
--color-bg-surface-accent: #1C2433;   /* Cards, sections */
--color-bg-elevated: #242D3F;         /* Hover states */

/* Text Colors */
--color-text-primary: #E8EEF2;        /* Off-white, main text */
--color-text-secondary: #9BA5B4;      /* Hierarchy, meta */
--color-text-tertiary: #6B7785;       /* Timestamps, tags */

/* Project Accents */
--color-flank: #4A90E2;               /* Legal/Enterprise - Blue */
--color-sentra: #E27B7B;              /* Mental Health - Coral */
--color-psysafe: #7EC699;             /* Open Source - Green */

/* Interactive States */
--color-border: rgba(255, 255, 255, 0.08);
--color-border-hover: rgba(255, 255, 255, 0.16);
--color-focus: #4A90E2;
--color-selection-bg: rgba(74, 144, 226, 0.2);
```

### Light Mode Alternative (Optional)

```css
/* Base Colors */
--color-bg-primary: #FAFBFC;
--color-bg-surface: #FFFFFF;
--color-bg-surface-accent: #F4F6F8;

/* Text Colors */
--color-text-primary: #1A1F2C;
--color-text-secondary: #4A5568;
--color-text-tertiary: #718096;

/* Project Accents remain the same */
--color-flank: #4A90E2;
--color-sentra: #E27B7B;
--color-psysafe: #7EC699;
```

### Color Usage Guide

**Project Color-Coding:**
- **Flank (Blue):** Trust, precision, enterprise
- **Sentra (Coral):** Empathetic, human-centered
- **PsySafe (Green):** Open, safe, growth

**Application:**
- 4px top border on project cards
- Hover glow effects in project color
- CTA buttons inherit project identity
- Inline links use Flank blue as default

---

## Typography

### Font Stack

```css
/* Primary Font - Inter Variable */
@import url('https://rsms.me/inter/inter.css');

--font-primary: 'Inter', -apple-system, BlinkMacSystemFont, 
                'Segoe UI', 'Helvetica Neue', Arial, sans-serif;

/* Code Font - JetBrains Mono */
@import url('https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;500;600&display=swap');

--font-code: 'JetBrains Mono', 'SF Mono', Monaco, 
             'Cascadia Code', monospace;
```

### Type Scale

```css
/* Hero / H1 */
--text-hero-size: clamp(48px, 8vw, 72px);
--text-hero-weight: 700;
--text-hero-line-height: 1.1;
--text-hero-letter-spacing: -0.02em;

/* H2 */
--text-h2-size: clamp(32px, 5vw, 48px);
--text-h2-weight: 600;
--text-h2-line-height: 1.2;
--text-h2-letter-spacing: -0.01em;

/* H3 */
--text-h3-size: clamp(24px, 3vw, 32px);
--text-h3-weight: 600;
--text-h3-line-height: 1.3;

/* H4 */
--text-h4-size: clamp(20px, 2.5vw, 24px);
--text-h4-weight: 600;
--text-h4-line-height: 1.4;

/* Body Large */
--text-body-large-size: 20px;
--text-body-large-weight: 400;
--text-body-large-line-height: 1.7;

/* Body */
--text-body-size: 18px;
--text-body-weight: 400;
--text-body-line-height: 1.6;

/* Meta / Caption */
--text-meta-size: 14px;
--text-meta-weight: 500;
--text-meta-line-height: 1.4;
--text-meta-letter-spacing: 0.02em;
--text-meta-text-transform: uppercase;
```

### Typography Examples

**Hero Section:**
```
Martin Lukac
    ↑ 72px, weight 700, #E8EEF2

AI Practitioner–Researcher
    ↑ 24px, weight 400, #9BA5B4

Deployment · Ethics · Safety
    ↑ 18px, weight 500, #7BA3E2
```

**Body Text:**
```
I lead AI at Flank, building agentic legal workflows...
    ↑ 20px, weight 400, line-height 1.7
    ↑ Max width 800px for readability
```

---

## Layout & Spacing

### Grid System

```css
/* 12-Column Grid */
.grid-container {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  gap: var(--space-6);
  max-width: var(--container-standard);
  margin: 0 auto;
  padding: 0 var(--space-4);
}

/* Mobile: 4-column */
@media (max-width: 768px) {
  .grid-container {
    grid-template-columns: repeat(4, 1fr);
    gap: var(--space-4);
  }
}
```

### Container Widths

```css
--container-narrow: 800px;    /* Reading optimal */
--container-standard: 1200px; /* Content sections */
--container-wide: 1400px;     /* Project showcases */
```

### Spacing System (8px Base)

```css
--space-1: 8px;
--space-2: 16px;
--space-3: 24px;
--space-4: 32px;
--space-5: 40px;
--space-6: 48px;
--space-8: 64px;
--space-10: 80px;
--space-12: 96px;
--space-16: 128px;

/* Section spacing */
--section-spacing-small: 64px;
--section-spacing-medium: 96px;
--section-spacing-large: 128px;

/* Component spacing */
--card-padding: 32px;
--card-gap: 24px;
--nav-height: 80px;
```

### Breakpoints

```css
--breakpoint-mobile: 480px;
--breakpoint-tablet: 768px;
--breakpoint-desktop: 1024px;
--breakpoint-wide: 1440px;
```

---

## Component Specifications

### Navigation (Fixed Header)

```css
.nav-container {
  position: fixed;
  top: 0;
  width: 100%;
  height: 80px;
  background: rgba(10, 14, 20, 0.95);
  backdrop-filter: blur(8px);
  border-bottom: 1px solid var(--color-border);
  z-index: 1000;
}

.nav-content {
  max-width: 1400px;
  margin: 0 auto;
  padding: 0 32px;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
```

**Structure:**
```
[Martin Lukac]           [Work] [Writing] [About] [Contact]    [PsySafe Toolkit]
     ↑ Logo                    ↑ Nav links                      ↑ CTA button
```

**States:**
- Default links: `color: #9BA5B4`
- Hover: `color: #E8EEF2` + underline animation
- Active page: 2px bottom border in blue
- Scroll: Background opacity increases

### Buttons

```css
/* Primary Button */
.btn-primary {
  background: var(--color-flank);
  color: var(--color-text-primary);
  padding: 12px 24px;
  border-radius: 8px;
  font-size: 16px;
  font-weight: 600;
  border: none;
  cursor: pointer;
  transition: all 200ms ease-out;
}

.btn-primary:hover {
  background: #5CA0F2;
  transform: translateY(-2px);
  box-shadow: 0 8px 16px rgba(74, 144, 226, 0.2);
}

/* Secondary Button (Ghost) */
.btn-secondary {
  background: transparent;
  color: var(--color-text-primary);
  padding: 12px 24px;
  border-radius: 8px;
  font-size: 16px;
  font-weight: 600;
  border: 1px solid var(--color-border);
  cursor: pointer;
  transition: all 200ms ease-out;
}

.btn-secondary:hover {
  border-color: var(--color-border-hover);
  background: var(--color-bg-surface-accent);
}

/* Project-specific buttons */
.btn-psysafe {
  background: var(--color-psysafe);
  color: var(--color-bg-primary);
}
```

### Project Cards

**Visual Structure:**
```
┌─────────────────────────────────────────┐  ← 4px accent top border
│ [Icon]                     [Arrow →]    │
│                                          │
│ Flank                                    │  ← H3, 32px
│ Agentic legal workflows for law firms   │  ← Tagline, 18px
│                                          │
│ • Design document review agents          │
│ • Build evaluation systems               │
│ • Create guardrails                      │
│                                          │
│ Status: In production                    │  ← Meta, 14px
│                                          │
│ [Learn more →]                           │  ← Ghost button
└─────────────────────────────────────────┘
```

```css
.card {
  background: var(--color-bg-surface);
  border: 1px solid var(--color-border);
  border-radius: 12px;
  padding: 32px;
  transition: all 300ms ease-out;
}

.card:hover {
  border-color: var(--color-border-hover);
  transform: translateY(-4px);
  box-shadow: 0 16px 32px rgba(0, 0, 0, 0.2);
}

/* Project-specific accent borders */
.card-flank {
  border-top: 4px solid var(--color-flank);
}

.card-sentra {
  border-top: 4px solid var(--color-sentra);
}

.card-psysafe {
  border-top: 4px solid var(--color-psysafe);
}

/* Hover glow effects */
.card-flank:hover {
  box-shadow: 0 16px 32px rgba(74, 144, 226, 0.2);
}
```

### Links

```css
.link {
  color: var(--color-flank);
  text-decoration: none;
  position: relative;
  transition: color 200ms ease-out;
}

.link:hover {
  color: #5CA0F2;
}

/* Underline animation */
.link-underline {
  text-decoration: none;
  position: relative;
}

.link-underline::after {
  content: '';
  position: absolute;
  bottom: -2px;
  left: 0;
  width: 0;
  height: 2px;
  background: currentColor;
  transition: width 200ms ease-out;
}

.link-underline:hover::after {
  width: 100%;
}

/* Arrow links (→) */
.link-arrow::after {
  content: ' →';
  transition: transform 200ms ease-out;
  display: inline-block;
}

.link-arrow:hover::after {
  transform: translateX(4px);
}
```

---

## Page Structure

### Homepage (/)

#### Section 1: Hero (Full Height)

**Layout:** Centered, full viewport height

**Content:**
```html
<section class="hero">
  <h1>Martin Lukac</h1>
  <p class="subtitle">AI Practitioner–Researcher</p>
  <p class="keywords">Deployment · Ethics · Safety</p>
  <p class="current">
    Currently: <span class="flank">AI Lead at Flank</span> | 
    <span class="sentra">Co-founder, Sentra</span> | 
    <span class="psysafe">Maintainer, PsySafe</span>
  </p>
  <div class="scroll-indicator">↓</div>
</section>
```

**Styling:**
- H1: 72px, weight 700, color primary
- Subtitle: 24px, weight 400, color secondary
- Keywords: 18px, weight 500, spaced with middots
- Current roles: 16px, color-coded spans
- Scroll indicator: Subtle bounce animation

---

#### Section 2: What I Do (Introduction)

**Layout:** Single column, max 800px, centered

**Content:**
```
I lead AI at Flank, building agentic legal workflows with the 
evaluation and guardrail systems that keep them reliable and 
auditable in high-stakes documentation environments.

Beyond legal AI, I work on the frontlines of mental-health-sensitive 
deployments. I co-founded Sentra, an AI pilot for veterans and first 
responders, and maintain PsySafe—an open toolkit for risk detection 
and crisis response in chatbots.

My work turns real-world deployment lessons into shareable methods 
and patterns. PhD in computational social science. Based in Berlin 
and London.
```

**Styling:**
- 20px body text, line-height 1.7
- Key phrases linked: Flank (blue), Sentra (coral), PsySafe (green)
- 128px margin-top, 96px margin-bottom

---

#### Section 3: Current Work (Three Cards)

**Layout:** Grid, 3 columns desktop, 1 column mobile

**Card Content Structure:**

**Flank Card:**
```
[Blue Icon]
Flank
Agentic legal workflows for law firms and in-house teams

• Design document review and redlining agents
• Build evaluation systems for accuracy and auditability
• Create guardrails that align with professional standards

Status: In production, serving major law firms
[Learn more →]
```

**Sentra Card:**
```
[Coral Icon]
Sentra
AI mental health support for veterans and first responders

• Co-founded to explore AI in crisis-adjacent populations
• Design conversational systems that respect clinical boundaries
• Partner with Wounded Warrior Project, UK MoD

Status: Pilot serving ~100 users
[Learn more →]
```

**PsySafe Card:**
```
[Green Icon]
PsySafe
Open toolkit for mental health crisis response in chatbots

• Risk detection patterns and escalation protocols
• Policy templates for harm reduction and refusal behaviors
• Used by practitioners building crisis-sensitive AI

Status: Open source, actively maintained
[View toolkit →]
```

**Styling:**
- 24px gap between cards
- Each card: 4px top border in project color
- Icons: 32px, matching project color
- H3: 32px, weight 600
- Tagline: 18px, line-height 1.5
- Bullets: 16px, color secondary
- Status: 14px, uppercase, project color
- Button: Ghost style

---

#### Section 4: Approach / Philosophy (Optional)

**Layout:** Centered, max 800px

**Content:**
```
Deployment Lessons, Not Lab Promises

Across legal AI, mental health support, and open tooling, I work 
where advanced models meet high-stakes realities. The goal is 
simple: lessons learned in the wild should not stay siloed.

I turn messy deployment experiences into shareable evaluations, 
guardrails, and patterns—raising the floor for anyone building AI 
in documentation-heavy, human-sensitive, or ethically complex 
domains.
```

**Styling:**
- First line: H3 (32px, weight 600)
- Body: 18px, line-height 1.6
- 96px margin top/bottom

---

#### Section 5: Recent Writing

**Layout:** List, max 800px

**Content Structure:**
```
[Title linked]
Platform · Date
One-line summary

---

[Title linked]
Platform · Date
One-line summary

[View all writing →]
```

**Example:**
```
"Why LLM Applications Fail in Production"
LinkedIn · Oct 2024
Most AI reliability problems aren't about the model—they're about 
unclear requirements and missing eval harnesses.
```

**Styling:**
- Title: 20px, weight 600, link color blue
- Meta: 14px, uppercase, color tertiary
- Summary: 16px, color secondary
- Dividers: 1px, subtle
- "View all" button at bottom

---

#### Section 6: About Preview

**Layout:** Two-column (desktop) or stacked (mobile)

**Content:**
```
[Photo: Round, 150px diameter]

PhD in computational social science from KU Leuven, published in 
Nature on personality prediction from voice analysis. Previously 
at QuantCo (machine learning for fraud detection, health insurance). 
Currently splitting time between Berlin and London.

[Full background →]
```

**Styling:**
- Photo: Border-radius 50%, subtle shadow
- Text: 18px, line-height 1.6
- Link: Underline on hover
- 96px margin top/bottom

---

#### Section 7: Contact / CTA

**Layout:** Centered, simple

**Content:**
```
Working on AI deployments in high-stakes domains?

Let's talk about evaluation, guardrails, or ethical 
deployment practices.

[Email Icon] [LinkedIn Icon] [GitHub Icon]
```

**Styling:**
- Heading: 24px, weight 600
- Body: 18px, color secondary
- Icons: 32px, color tertiary
- Icon hover: Color primary + scale 1.1
- 64px margin top/bottom

---

#### Section 8: Footer

**Content:**
```
© 2025 Martin Lukac

[Work] [Writing] [About] [PsySafe] [Sentra]

[GitHub] [LinkedIn] [Email]
```

**Styling:**
- Background: Color bg-surface
- Padding: 48px vertical
- Text: 14px, color tertiary
- Links: Color secondary, hover primary
- Center-aligned

---

### About Page (/about)

#### Section 1: Long Bio

**Layout:** Single column, max 800px

**Content:** 
Full 230-word bio with subheadings:
- Practitioner–Researcher
- Legal AI at Flank
- Mental Health AI
- Academic Background
- Core Philosophy

**Styling:**
- Subheadings: 24px, weight 600, accent color
- Body: 18px, line-height 1.7
- Links inline to Flank, Sentra, PsySafe

---

#### Section 2: Timeline (Optional)

**Content:**
```
2024 – Present: AI Lead, Flank (Berlin)
2023 – Present: Co-founder, Sentra
2022 – Present: Maintainer, PsySafe
2020 – 2023: QuantCo, Machine Learning
2019: PhD, KU Leuven (Computational Social Science)
2018: Nature publication, Voice & Personality
```

**Styling:**
- Left-aligned, date → role → description
- Subtle connecting line (vertical)
- 16px body text

---

#### Section 3: Values / Principles (Optional)

**Content (3 cards):**
```
Deployed, Not Demoed
Real-world lessons > lab benchmarks. I build for production 
environments where models meet messy reality.

Ethics Through Practice
Values aren't checkboxes. Safety and fairness emerge from how 
systems are built, monitored, and governed.

Open by Default
Methods, tools, and hard-won insights should be shareable. 
Raising the field's floor benefits everyone.
```

**Styling:**
- Grid: 3 columns desktop, 1 column mobile
- Each principle as card with icon
- 24px gap

---

### Writing Page (/writing)

**Layout:** List view with optional filters

**Each post card:**
```
[Title linked]
Date · Platform · Tags

[2-3 sentence excerpt]

---
```

**Features:**
- Filter by tags (Legal AI, Mental Health, Ethics, Open Source)
- Search bar at top
- Chronological order
- Pagination if needed

---

### Work/Projects Detail Pages (Optional)

**Template Structure:**

1. **Hero:** Project name, tagline, role, color-coded
2. **The Problem:** Context, why it matters
3. **The Approach:** Your solution, methods
4. **What I Built:** Specific contributions
5. **Impact:** Metrics, users, deployment status
6. **Lessons Learned:** Open reflections
7. **Links:** GitHub, docs, demo

**Styling:**
- Generous spacing (96px between sections)
- Code snippets in JetBrains Mono
- Screenshots with 2px border
- Pull quotes for key insights

---

## Interaction Design

### Animations & Transitions

**Duration:**
```css
--transition-fast: 150ms;
--transition-base: 200ms;
--transition-slow: 300ms;
--transition-slower: 500ms;
```

**Easing:**
```css
--ease-out: cubic-bezier(0, 0, 0.2, 1);
--ease-in-out: cubic-bezier(0.4, 0, 0.2, 1);
```

### Common Animations

```css
/* Fade in on scroll */
@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(16px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.fade-in {
  animation: fadeIn 300ms ease-out;
}

/* Scale on hover */
.scale-hover {
  transition: transform 200ms ease-out;
}

.scale-hover:hover {
  transform: scale(1.02);
}
```

### Micro-interactions

**Cards:**
- Hover: `translateY(-4px)` + border glow + shadow
- Transition: 300ms ease-out
- Active: No additional state

**Links:**
- Default: Blue, no underline
- Hover: Lighter blue, underline slide-in
- Transition: 200ms ease-out

**Buttons:**
- Hover: `translateY(-2px)` + shadow glow
- Active: `translateY(0)` (press effect)
- Transition: 200ms ease-out

**Scroll:**
- Smooth scroll: `scroll-behavior: smooth`
- Intersection observer for fade-in sections
- No parallax effects

### Accessibility

```css
/* Focus states */
*:focus {
  outline: 2px solid var(--color-focus);
  outline-offset: 2px;
}

/* Skip link */
.skip-link {
  position: absolute;
  top: -40px;
  left: 0;
  background: var(--color-bg-primary);
  padding: 8px 16px;
  z-index: 9999;
}

.skip-link:focus {
  top: 0;
}

/* Screen reader only */
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border-width: 0;
}
```

**Requirements:**
- WCAG AA minimum (4.5:1 contrast ratio)
- Keyboard navigation fully supported
- Focus states on all interactive elements
- Respect `prefers-reduced-motion`
- Alt text on all images
- Semantic HTML (proper heading hierarchy)

---

## Content Strategy

### Voice & Tone

**Characteristics:**
- **Direct, not academic:** "I build guardrails" not "My research focuses on..."
- **Honest about complexity:** Don't oversell, don't hide challenges
- **Practitioner-first:** Lead with problems, not credentials
- **Open by default:** Share methods, invite contributions

**Example transformations:**

❌ Bad: "My research focuses on the intersection of artificial intelligence and mental health support systems..."

✅ Good: "I co-founded Sentra, an AI pilot for veterans and first responders."

---

❌ Bad: "Leveraging state-of-the-art language models to revolutionize legal documentation..."

✅ Good: "I design agentic legal workflows with the evaluation systems that keep them auditable."

### Key Messages

1. **Deployment over demos** – Real-world focus
2. **Ethics through practice** – Not abstract principles
3. **High-stakes domains** – Legal, mental health = real consequences
4. **Open and shareable** – PsySafe, methods, lessons learned

### SEO Keywords (Natural Integration)

- AI deployment, AI ethics, AI safety
- Legal AI, document review AI, agentic workflows
- Mental health AI, crisis chatbots, PsySafe
- Guardrails, evaluation systems, responsible AI
- Computational social science, voice analysis

---

## Technical Implementation

### Recommended Stack

**Option 1: Astro (Recommended)**
```bash
npm create astro@latest
```
- Static site generation, blazing fast
- Markdown for blog posts
- Component-based (React, Vue, Svelte supported)
- Built-in image optimization
- Deploy to GitHub Pages, Vercel, or Netlify

**Option 2: Next.js (Static Export)**
```bash
npx create-next-app@latest
```
- React-based
- Static export: `next export`
- More flexibility for dynamic features
- Image optimization built-in

**Styling: Tailwind CSS**
```bash
npm install -D tailwindcss
```
- Use custom theme matching this spec
- Configure in `tailwind.config.js`

### File Structure

```
/src
  /components
    - Nav.jsx
    - Footer.jsx
    - ProjectCard.jsx
    - Button.jsx
  /pages
    - index.astro           (Homepage)
    - about.astro
    - work.astro
    - writing.astro
  /styles
    - globals.css           (CSS vars, resets)
    - typography.css
    - components.css
  /content
    /writing
      - post-1.md
      - post-2.md
  /public
    /fonts
    /images
```

### CSS Setup

**globals.css:**
```css
@import url('https://rsms.me/inter/inter.css');

:root {
  /* Color system */
  --color-bg-primary: #0A0E14;
  --color-bg-surface: #131820;
  /* ... rest of CSS variables from Color System section */
}

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: var(--font-primary);
  font-size: var(--text-body-size);
  line-height: var(--text-body-line-height);
  color: var(--color-text-primary);
  background: var(--color-bg-primary);
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

/* Enable smooth scrolling */
html {
  scroll-behavior: smooth;
}

/* Respect user's motion preference */
@media (prefers-reduced-motion: reduce) {
  * {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
}
```

### Performance Optimization

**Images:**
```html
<!-- Use Astro's Image component -->
<Image 
  src="/images/photo.jpg" 
  alt="Martin Lukac"
  width={300}
  height={300}
  loading="lazy"
/>
```

**Fonts:**
- Use `font-display: swap` to prevent FOUT
- Subset fonts to Latin characters only
- Self-host fonts for performance

**Critical CSS:**
- Inline critical CSS in `<head>`
- Load rest asynchronously

**Lazy Loading:**
- Images below fold: `loading="lazy"`
- Components: Use Intersection Observer

### Analytics (Privacy-Respecting)

**Option 1: Plausible**
```html
<script defer data-domain="mblukac.github.io" 
  src="https://plausible.io/js/script.js"></script>
```

**Option 2: Fathom**
```html
<script src="https://cdn.usefathom.com/script.js" 
  data-site="XXXXXX" defer></script>
```

Both are:
- GDPR-compliant
- No cookies
- Privacy-focused
- Lightweight

---

## Success Metrics

### Qualitative Goals

- ✅ Visitors immediately understand what you do (not just "AI researcher")
- ✅ Practitioners recognize you as someone who's shipped real systems
- ✅ Stakeholders (investors, partners) see credibility + vision
- ✅ Other researchers/builders want to engage with PsySafe or methods

### Quantitative Targets (Post-Launch)

**Traffic:**
- Bounce rate: <40% (high engagement)
- Avg. time on site: >2 minutes
- Pages per session: >2

**Engagement:**
- Click-through on project cards: >30%
- "Learn more" clicks on Flank/Sentra: >20%
- PsySafe toolkit clicks: Measure GitHub traffic from site
- Social share rate: >5%

**Technical:**
- Lighthouse score: 95+ (Performance, Accessibility, Best Practices, SEO)
- Page load time: <2 seconds (3G)
- First Contentful Paint: <1.5s
- Cumulative Layout Shift: <0.1

---

## Deliverables Checklist

### Phase 1: Design
- [ ] Visual style guide (colors, typography, spacing)
- [ ] Component library (cards, buttons, nav, footer)
- [ ] Wireframes (all pages)
- [ ] High-fidelity mockups (desktop + mobile)
- [ ] Interaction specifications

### Phase 2: Development
- [ ] Repository setup + tooling (Astro/Next.js + Tailwind)
- [ ] CSS setup (variables, reset, base styles)
- [ ] Component implementation
  - [ ] Navigation
  - [ ] Footer
  - [ ] Project cards
  - [ ] Buttons
  - [ ] Links
- [ ] Page builds
  - [ ] Homepage
  - [ ] About
  - [ ] Writing (with blog setup)
  - [ ] Work/Projects (if detail pages)
- [ ] Responsive breakpoints (mobile, tablet, desktop)
- [ ] Accessibility audit
- [ ] Performance optimization

### Phase 3: Content
- [ ] Bio rewrite (short + long)
- [ ] Project descriptions (Flank, Sentra, PsySafe)
- [ ] Blog post migration/formatting
- [ ] Professional photo (if update needed)
- [ ] Social links, contact info verified

### Phase 4: Launch
- [ ] Domain setup (custom domain or GitHub Pages)
- [ ] Analytics integration (Plausible/Fathom)
- [ ] SEO metadata (titles, descriptions, OG images)
- [ ] Favicon + manifest
- [ ] Cross-browser testing (Chrome, Firefox, Safari, Edge)
- [ ] Mobile device testing (iOS Safari, Chrome Android)
- [ ] Lighthouse audit (95+ target)
- [ ] Soft launch feedback (5-10 people)
- [ ] Public announcement (LinkedIn, Twitter)

---

## Design Rationale

### Why This Approach?

**For practitioners:**
"I've deployed this in production" is immediately visible through project cards, status indicators, and honest descriptions.

**For stakeholders:**
PhD credentials and Nature publication establish authority, while current roles (Flank, Sentra) show active engagement at frontier of deployment.

**For ethical AI community:**
PsySafe prominence, open reflections on lessons learned, and transparency about high-stakes work signal serious commitment to responsible practice.

### What This Communicates

**The site says:**
*"I've deployed AI in high-stakes environments. I've learned hard lessons. Here's what works—use it."*

**NOT:**
- "Hire me" (consultant portfolio)
- "Look at my papers" (academic CV)
- "Check out my startup" (founder landing page)

**BUT RATHER:**
- "This is where I work" (practitioner identity)
- "This is what I've learned" (open practice)
- "This is what I'm building" (active projects)

---

## Final Notes for Developer

### Priority Order

1. **Get homepage right** – This is 80% of the site's impact
2. **Nail the project cards** – They communicate current work
3. **Make it accessible** – WCAG AA, keyboard nav, focus states
4. **Optimize performance** – <2s load time, Lighthouse 95+
5. **Polish interactions** – Smooth hover states, no jank

### Common Pitfalls to Avoid

❌ **Don't:** Make it too corporate (no "Request Demo" vibes)  
✅ **Do:** Keep it personal and practitioner-focused

❌ **Don't:** Hide the real work behind buzzwords  
✅ **Do:** Lead with specific problems and solutions

❌ **Don't:** Over-animate (parallax, auto-play, infinite loops)  
✅ **Do:** Use subtle, purposeful animation

❌ **Don't:** Cram everything above fold  
✅ **Do:** Use generous spacing, let sections breathe

### Questions to Ask

Before considering any section "done":

1. **Clarity:** Can someone who knows nothing about Martin understand what he does in 10 seconds?
2. **Credibility:** Is there evidence of real deployment (not just research)?
3. **Accessibility:** Can this be navigated with keyboard only?
4. **Performance:** Does this load quickly on mobile 3G?
5. **Maintenance:** Can content be updated without touching code?

---

## Support & Resources

### Design References
- Hume.ai: https://www.hume.ai/conversational-voice
- Sian Brooke: https://www.sianbrooke.com/
- ElevenLabs: https://elevenlabs.io/

### Technical Resources
- Astro docs: https://docs.astro.build/
- Tailwind CSS: https://tailwindcss.com/docs
- Inter font: https://rsms.me/inter/
- WCAG guidelines: https://www.w3.org/WAI/WCAG21/quickref/

### Tools
- Figma (for mockups): https://figma.com
- Lighthouse (performance): Chrome DevTools
- WebAIM Contrast Checker: https://webaim.org/resources/contrastchecker/
- Plausible Analytics: https://plausible.io/

---

**End of Document**

This spec is implementation-ready. All color codes, spacing values, component structures, and content are provided. For questions or clarifications, refer back to specific sections or reach out.

**Document Version:** 1.0  
**Last Updated:** November 19, 2025  
**Status:** Ready for Development  
**Author:** Claude (for Martin Lukac)
