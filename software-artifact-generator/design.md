```
# AI Agent Design Directive: Bento UI System

> **INSTRUCTION TO AI AGENT:** This document contains mandatory design rules. You MUST follow these specifications when generating any UI component, layout, or styling code. Deviations are not permitted unless explicitly requested by the user.

---

## 1. Core Design Philosophy

You are implementing **Soft Minimalism** with **Bento Grid** architecture—a calm, breathable, yet high-density modular interface. Think "complexity contained within simplicity."

### 1.1. Visual Identity Mandates

| Principle | Implementation |
|-----------|----------------|
| **Style Reference** | Linear/Vercel aesthetic |
| **Surface Treatment** | Semi-transparent surfaces with subtle depth |
| **Background Base** | Ghost White (#F8F8FF), never pure white |
| **Interaction Model** | Optimistic UI, spring physics, touch-native |

---

## 2. Color System: The Ghost Palette

> **AI AGENT RULE:** Never use pure white (#FFFFFF) for application backgrounds. Never use pure black (#000000) for text.

### 2.1. Required CSS Custom Properties

```css
:root {
  /* Backgrounds */
  --bg-app: #F8F8FF;           /* Ghost White - Main canvas */
  --bg-panel: #FFFFFF;          /* Cards and Bento tiles */
  --bg-panel-transparent: rgba(255, 255, 255, 0.8);  /* Glassmorphism overlays (High legibility) */
  --bg-surface-subtle: #F0F8FF; /* Secondary interaction zones */
  
  /* Foreground/Text */
  --fg-primary: #171717;        /* Main text - almost black */
  --fg-secondary: #666666;      /* Subtitles, metadata */
  --fg-tertiary: #999999;       /* Placeholders, passive icons */
  
  /* Borders */
  --border-subtle: rgba(0, 0, 0, 0.08);   /* Standard card borders */
  --border-active: rgba(0, 0, 0, 0.16);   /* Hover/Focus states */
  --border-hairline: rgba(0, 0, 0, 0.06); /* Ultra-thin separators */
  
  /* Brand Accent - CUSTOMIZE THESE FOR YOUR PROJECT */
  --accent-brand: linear-gradient(135deg, #2B5F75, #1F746B, #B8737A);
  --accent-brand-start: #2B5F75;   /* Primary */
  --accent-brand-mid: #1F746B;     /* Secondary */
  --accent-brand-end: #B8737A;     /* Tertiary */
}
```

### 2.2. Brand Accent Gradient Usage Rules

You MUST use the brand gradient sparingly in these specific contexts only:

1. **Text Gradients:** For featured headlines and key CTAs (use `background-clip: text`)
2. **Border Gradients:** On Bento cards using `mask-image` techniques
3. **Spotlights:** Radial gradients following cursor/touch position

```css
/* Example: Brand Gradient Text */
.brand-heading {
  background: var(--accent-brand);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}
```

> **AI AGENT RULE:** For loading or "processing" states, use a living gradient animation.

```css
@keyframes living-gradient {
  0% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
  100% { background-position: 0% 50%; }
}

.loading-animated {
  background: linear-gradient(270deg, var(--accent-brand-start), var(--accent-brand-mid), var(--accent-brand-end));
  background-size: 200% 200%;
  animation: living-gradient 3s ease infinite;
}
```

---

## 3. Shadow System: Layered Depth

> **AI AGENT RULE:** Never use single-layer box-shadows. Always use multi-layer shadows for realistic ambient occlusion.

### 3.1. Required Shadow Variables

```css
:root {
  /* Rest state - subtle presence */
  --shadow-bento-rest: 
    0px 1px 2px rgba(0, 0, 0, 0.04),   /* Sharp edge */
    0px 4px 8px rgba(0, 0, 0, 0.02),   /* Mid-distance */
    0px 12px 24px rgba(0, 0, 0, 0.02); /* Ambient spread */
  
  /* Lifted state - hover/focus */
  --shadow-bento-lift: 
    0px 2px 4px rgba(0, 0, 0, 0.06),
    0px 8px 16px rgba(0, 0, 0, 0.04),
    0px 24px 48px rgba(0, 0, 0, 0.03);
  
  /* Glass blur effect */
  --glass-blur: blur(12px) saturate(180%);
}
```

### 3.2. Border Technique: Inset Shadow Method

> **AI AGENT RULE:** Prefer inset box-shadows over traditional borders to prevent layout shifts.

```css
/* CORRECT - Use this */
.bento-card {
  box-shadow: 
    inset 0 0 0 1px var(--border-subtle),
    var(--shadow-bento-rest);
}

/* INCORRECT - Avoid this */
.bento-card {
  border: 1px solid #E5E5E5; /* Causes layout shifts */
}
```

### 3.3. Hairline Border for Retina Displays

For high-DPI screens, implement 0.5px borders using pseudo-elements:

```css
.bento-card {
  position: relative;
}

.bento-card::after {
  content: '';
  position: absolute;
  inset: 0;
  border: 1px solid rgba(0, 0, 0, 0.1);
  pointer-events: none;
  border-radius: inherit;
}

@media (-webkit-min-device-pixel-ratio: 2) {
  .bento-card::after {
    border-width: 0.5px;
  }
}
```

---

## 4. Typography: Geist System

> **AI AGENT RULE:** Use Geist Sans for UI elements, Geist Mono for code and data values. Never use system fonts.

> **NOTE:** Geist Sans and Geist Mono are Vercel/Next.js ecosystem fonts. If your tech stack does not include Next.js, substitute with equivalent sans-serif and monospace fonts (e.g., Inter, Roboto for sans; Fira Code, JetBrains Mono for mono).

### 4.1. Font Family Setup

```css
:root {
  --font-sans: 'Geist Sans', -apple-system, BlinkMacSystemFont, sans-serif;
  --font-mono: 'Geist Mono', 'SF Mono', 'Fira Code', monospace;
}
```

### 4.2. Typography Scale with Tracking

| Element | Size | Tracking | Weight | Usage            |
| ------- | ---- | -------- | ------ | ---------------- |
| Display | 32px | -0.03em  | 600    | Hero headings    |
| H1      | 24px | -0.02em  | 500    | Section titles   |
| H2      | 20px | -0.01em  | 500    | Card headers     |
| Body    | 16px | 0        | 400    | Long-form text   |
| Caption | 13px | +0.01em  | 400    | Subtitles        |
| Label   | 11px | +0.05em  | 600    | Uppercase labels |

### 4.3. Required Typography CSS

```css
:root {
  /* Fluid Typography using clamp() for responsiveness */
  --text-display: 600 clamp(28px, 5vw, 32px)/1.2 var(--font-sans);
  --text-h1: 500 clamp(22px, 4vw, 24px)/1.3 var(--font-sans);
  --text-h2: 500 clamp(18px, 3vw, 20px)/1.4 var(--font-sans);
  --text-body: 400 16px/1.6 var(--font-sans);
  --text-caption: 400 13px/1.5 var(--font-sans);
  --text-label: 600 11px/1.4 var(--font-sans);
}

.display { 
  font: var(--text-display); 
  letter-spacing: -0.03em; 
}

.h1 { 
  font: var(--text-h1); 
  letter-spacing: -0.02em; 
}

.data-value {
  font-family: var(--font-mono);
  font-variant-numeric: tabular-nums; /* Mandated for data tables */
  letter-spacing: -0.01em;
}

.label { 
  font: var(--text-label); 
  letter-spacing: 0.05em; 
  text-transform: uppercase; 
}
```

> **CRITICAL:** Never set input font-size below 16px on mobile—iOS will auto-zoom the viewport.

---

## 5. Bento Grid Layout System

> **AI AGENT RULE:** Always use CSS Grid with `grid-auto-flow: dense`. Never stack all items in a single column on mobile.

### 5.1. Grid Architecture

```css
:root {
  --grid-gap-desktop: 24px;
  --grid-gap-mobile: 12px; /* Use 8px for very dense data grids */
  --container-padding-mobile: 16px;
  --radius-bento: 12px;
}

/* Mobile-first base */
.bento-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: var(--grid-gap-mobile);
  grid-auto-flow: dense; /* MANDATORY */
  padding: var(--container-padding-mobile);
}

/* Desktop expansion */
@media (min-width: 768px) {
  .bento-grid {
    grid-template-columns: repeat(12, 1fr);
    gap: var(--grid-gap-desktop);
  }
}
```

### 5.2. Tile Spanning Rules

| Tile Type      | Mobile (4-col)                         | Desktop (12-col)          |
| -------------- | -------------------------------------- | ------------------------- |
| Hero/Main Chat | `span 4` (full)                      | `span 8` or `span 12` |
| Standard Card  | `span 4` (full) or `span 2` (half) | `span 3` or `span 4`  |
| Metric Tile    | `span 2` (half)                      | `span 2` or `span 3`  |
| Icon Button    | `span 1` (quarter)                   | `span 1`                |

```css
/* Example spanning classes */
.tile-hero { grid-column: span 4; }
.tile-standard { grid-column: span 4; }
.tile-metric { grid-column: span 2; }
.tile-icon { grid-column: span 1; }

@media (min-width: 768px) {
  .tile-hero { grid-column: span 8; }
  .tile-standard { grid-column: span 4; }
  .tile-metric { grid-column: span 3; }
  .tile-icon { grid-column: span 1; }
}
```

### 5.3. Horizontal Scroll Lanes (Swimlanes)

For content like "Recent Projects", use horizontal scrolling on mobile:

```css
.swimlane {
  display: flex;
  gap: var(--grid-gap-mobile);
  overflow-x: auto;
  scroll-snap-type: x mandatory;
  scroll-padding-left: var(--container-padding-mobile);
  -webkit-overflow-scrolling: touch;
}

.swimlane > * {
  flex-shrink: 0;
  scroll-snap-align: start;
}
```

---

## 6. Animation & Motion Physics

> **AI AGENT RULE:** Use spring physics for all transitions. Never use linear or basic ease-in-out.

### 6.1. Motion Tokens

```css
:root {
  /* Spring easing with slight overshoot */
  --ease-spring: cubic-bezier(0.175, 0.885, 0.32, 1.275);
  --ease-smooth: cubic-bezier(0.4, 0, 0.2, 1);
  
  /* Duration scale */
  --duration-instant: 100ms;  /* Touch feedback */
  --duration-fast: 200ms;     /* Micro-interactions */
  --duration-medium: 350ms;   /* Panel transitions */
  --duration-slow: 500ms;     /* Page transitions */
}
```

### 6.2. Desktop Hover vs Mobile Active States

> **CRITICAL DISTINCTION:** Hover states do not exist on mobile. Implement `:active` for touch.

```css
/* Desktop: Lift on hover */
@media (hover: hover) {
  .bento-card:hover {
    transform: translateY(-2px);
    box-shadow: var(--shadow-bento-lift);
    transition: all var(--duration-fast) var(--ease-spring);
  }
}

/* Mobile: Press down on touch */
@media (hover: none) {
  .bento-card:active {
    transform: scale(0.98);
    transition: transform var(--duration-instant) var(--ease-smooth);
  }
}
```

### 6.3. Skeleton Loading (Optimistic UI)

> **AI AGENT RULE:** Never use spinners. Always show skeleton placeholders that match expected content dimensions to prevent Cumulative Layout Shift (CLS).

```css
.skeleton {
  background: linear-gradient(
    90deg,
    transparent 0%,
    rgba(255, 255, 255, 0.5) 50%,
    transparent 100%
  );
  background-size: 200% 100%;
  animation: shimmer 1.5s infinite;
  border-radius: 4px;
}

@keyframes shimmer {
  0% { background-position: 200% 0; }
  100% { background-position: -200% 0; }
}
```

---

## 7. Touch & Accessibility Requirements

> **AI AGENT RULE:** All interactive elements must meet minimum touch target sizes. Bottom 30% of viewport is reserved for primary actions.
> **AI AGENT RULE:** NEVER place primary actions (like "Submit" or "Generate") at the top of the screen on mobile. They must be in the "Thumb Zone".

### 7.1. Touch Target Specifications

| Element Type                | Visual Size | Actual Hit Area                 |
| --------------------------- | ----------- | ------------------------------- |
| Primary Actions (Nav, FAB)  | 48px        | 48px × 48px minimum            |
| Card Interactions           | Variable    | Entire card clickable           |
| Inline Actions (menu icons) | 24px        | 44px × 44px via pseudo-element |

```css
/* Expanded touch target technique */
.icon-button {
  position: relative;
  width: 24px;
  height: 24px;
}

.icon-button::before {
  content: '';
  position: absolute;
  inset: -10px; /* Expand to 44px */
}
```

### 7.2. Thumb Zone Placement

```css
/* Primary input MUST be bottom-positioned */
.primary-input-container {
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
  padding-bottom: env(safe-area-inset-bottom);
  background: var(--bg-panel-transparent);
  backdrop-filter: var(--glass-blur);
}
```

### 7.3. Safe Areas

```css
/* Respect device safe areas */
.app-container {
  padding-top: env(safe-area-inset-top);
  padding-bottom: env(safe-area-inset-bottom);
  padding-left: env(safe-area-inset-left);
  padding-right: env(safe-area-inset-right);
}
```

---

## 8. Glassmorphism Implementation

> **AI AGENT RULE:** Always include `saturate(180%)` with blur to prevent graying.

```css
.glass-panel {
  background: var(--bg-panel-transparent);
  backdrop-filter: blur(12px) saturate(180%);
  -webkit-backdrop-filter: blur(12px) saturate(180%);
  border: 1px solid var(--border-subtle);
}
```

---

## 9. Component Patterns

### 9.1. Bento Card Template

```css
.bento-card {
  background: var(--bg-panel);
  border-radius: var(--radius-bento);
  padding: 16px;
  position: relative;
  box-shadow: 
    inset 0 0 0 1px var(--border-subtle),
    var(--shadow-bento-rest);
  transition: all var(--duration-fast) var(--ease-spring);
}

/* Hairline overlay for Retina */
.bento-card::after {
  content: '';
  position: absolute;
  inset: 0;
  border-radius: inherit;
  border: 1px solid rgba(0, 0, 0, 0.08);
  pointer-events: none;
}

@media (-webkit-min-device-pixel-ratio: 2) {
  .bento-card::after {
    border-width: 0.5px;
  }
}
```

### 9.2. Chat/Input Interface

```css
.chat-input {
  position: sticky;
  bottom: 0;
  background: var(--bg-panel-transparent);
  backdrop-filter: var(--glass-blur);
  padding: 16px;
  padding-bottom: calc(16px + env(safe-area-inset-bottom));
}

.send-button {
  width: 48px;
  height: 48px;
  border-radius: 50%;
  background: var(--accent-brand);
}

/* Streaming/typing cursor effect */
.streaming-response::after {
  content: '▋';
  animation: blink 1s steps(1) infinite;
}

@keyframes blink {
  50% { opacity: 0; }
}
```

### 9.3. Code Block

```css
.code-block {
  font-family: var(--font-mono);
  font-size: 14px;
  line-height: 1.6;
  background: var(--bg-surface-subtle);
  border-radius: 8px;
  padding: 16px;
  overflow-x: auto;
  
  /* Fade indicator for horizontal overflow */
  mask-image: linear-gradient(
    to right,
    black calc(100% - 24px),
    transparent 100%
  );
}
```

---

## 10. Technical Stack Constraints

> **NOTE:** The specifications below are designed for Next.js projects. If your tech stack does not include Next.js, adapt the framework-specific items (Lucide React, `next/image`, Server/Client Components) to your equivalent stack.

| Requirement       | Specification                                |
| ----------------- | -------------------------------------------- |
| Framework         | Next.js (App Router)                         |
| Styling           | CSS Modules (`.module.css`) — class-based selectors only, no global CSS unless explicitly required |
| Icons             | Lucide React (stroke-width: 1.5) — substitute if not using Next.js |
| Images            | `next/image` with `placeholder="blur"` — substitute if not using Next.js |
| Server Components | Use for Bento Grid shell (data fetching)     |
| Client Components | Use for interactive tiles (`"use client"`) |

---

## 11. Checklist: Before Submitting Any Component

Before finalizing any UI component, verify:

- [ ] Background uses `#F8F8FF`, not pure white
- [ ] Text uses `#171717`, not pure black
- [ ] Shadows are multi-layered (minimum 2 layers)
- [ ] Grid uses `grid-auto-flow: dense`
- [ ] Touch targets are minimum 44px
- [ ] Primary actions are in bottom 30% of viewport
- [ ] Spring easing is used for animations
- [ ] Skeleton loaders are used instead of spinners
- [ ] Safe areas are respected
- [ ] Glassmorphism includes `saturate(180%)`
- [ ] Mobile uses `:active` not `:hover` for touch feedback
- [ ] No primary actions at the top of mobile screen
- [ ] Skeletons match final content size (No CLS)
- [ ] Data tables use `font-variant-numeric: tabular-nums`

---

## 12. Quick Reference: CSS Variables Template

Copy this complete set of variables to every project:

```css
:root {
  /* Color: Ghost Palette */
  --bg-app: #F8F8FF;
  --bg-panel: #FFFFFF;
  --bg-panel-transparent: rgba(255, 255, 255, 0.7);
  --bg-surface-subtle: #F0F8FF;
  --fg-primary: #171717;
  --fg-secondary: #666666;
  --fg-tertiary: #999999;
  --border-subtle: rgba(0, 0, 0, 0.08);
  --border-active: rgba(0, 0, 0, 0.16);
  
  /* Brand Accent - CUSTOMIZE FOR YOUR PROJECT */
  --accent-brand: linear-gradient(135deg, #2B5F75, #1F746B, #B8737A);
  
  /* Shadows */
  --shadow-bento-rest: 
    0px 1px 2px rgba(0, 0, 0, 0.04),
    0px 4px 8px rgba(0, 0, 0, 0.02),
    0px 12px 24px rgba(0, 0, 0, 0.02);
  --shadow-bento-lift: 
    0px 2px 4px rgba(0, 0, 0, 0.06),
    0px 8px 16px rgba(0, 0, 0, 0.04),
    0px 24px 48px rgba(0, 0, 0, 0.03);
  
  /* Glass */
  --glass-blur: blur(12px) saturate(180%);
  
  /* Typography */
  --font-sans: 'Geist Sans', -apple-system, BlinkMacSystemFont, sans-serif;
  --font-mono: 'Geist Mono', 'SF Mono', monospace;
  
  /* Spacing */
  --grid-gap-desktop: 24px;
  --grid-gap-mobile: 12px;
  --container-padding-mobile: 16px;
  --radius-bento: 12px;
  
  /* Motion */
  --ease-spring: cubic-bezier(0.175, 0.885, 0.32, 1.275);
  --ease-smooth: cubic-bezier(0.4, 0, 0.2, 1);
  --duration-instant: 100ms;
  --duration-fast: 200ms;
  --duration-medium: 350ms;
}
```

---

> **END OF DESIGN DIRECTIVE**
>
> AI Agent: You have read and understood all design rules. Apply them consistently to every component you generate. When in doubt, refer to this document.

```

```
