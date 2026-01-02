# ⚛️ Stage 2: Next.js & React Implementation Workflow (v2026.1)

## 🎯 Primary Objective

To transform high-fidelity Figma designs into performant, accessible, and beautifully animated React applications. This document governs the Implementation and Validation phases for frontend development [cite: Copilot Phase 4-5].

## 🚦 Rule of Engagement: The "Frontend Investigation"

Before writing any JSX/TSX, you must perform a Deep Investigation of:

Design Specs: Review Figma/design layouts for spacing, typography, and color tokens.

Existing Component Library: Identify reusable atoms/molecules to prevent duplication (DRY) [cite: AGENTS Rule 7].

State Architecture: Determine if the task requires local state (useState), shared state (Context), or server-side data fetching.

Tailwind Configuration: Verify available design tokens in tailwind.config.js.

## 🏗 Next.js & React Implementation Standards

### 1. Component Architecture & Patterns

Server Components (RSC) by Default: Fetch data and render logic on the server to minimize client-side bundle size.

Client Component Isolation: Use 'use client' only for interactive elements or hooks (animations, state, effects).

Atomic Design Principles: Structure components into atoms, molecules, and organisms where appropriate for scalability.

### 2. Styling & Layout (The Visual Code)

Tailwind CSS Excellence: Use utility classes for styling. Avoid arbitrary values; stick to the theme.

Responsive-First Design: Always build for mobile first using Tailwind's sm:, md:, and lg: prefixes [cite: Universal 3.1].

Accessibility (a11y): Use semantic HTML (e.g., <main>, <section>, <nav>) and ARIA labels.

### 3. Animation & Interaction (Framer Motion / GSAP)

Declarative Animations: Use Framer Motion for layout transitions and simple interactions.

Complex Timelines: Use GSAP for high-performance, complex scroll-based or multi-step animations.

Reduced Motion: Always respect prefers-reduced-motion settings for accessibility.

## 🧱 Atomic Task Specification (Frontend)

For every UI task, generate a spec including:

Visual Goal: Describe the design-to-code target.

Component Signature: Define props (interfaces) and whether it's an RSC or Client Component.

Animation Strategy: Define the triggers (e.g., whileInView, layoutId) and easing.

Validation: Specify the visual check and the unit test file.

## 🧪 Validation & Testing (The Frontend Pyramid)

Component Tests: Use React Testing Library to verify user interactions and accessibility.

Visual Regression: Perform manual/automated checks against Figma designs.

Performance Audit: Check Lighthouse scores, focusing on LCP (Largest Contentful Paint) and CLS (Cumulative Layout Shift).

🏷 Git & Documentation Discipline

Commit Format: feat(ui): <summary> or fix(animation): <summary> [cite: git 3.1].

TSDoc: Document every public prop and complex hook using TSDoc/JSDoc format.

Project Log: Update /docs/logs/init_log.txt after visual validation [cite: git 5.1].

## ✅ Completion Checklist (Rule 66)

[ ] No Tailwind arbitrary values (unless absolutely necessary).

[ ] Accessibility audit passed (no broken tabIndex or missing alt tags).

[ ] Animations are fluid (60fps) and non-blocking.

[ ] Types are strict (no any).

[ ] Clean up all console.log and debug fragments.

Quick Start: "Next.js & React Workflow initialized. Architecture and Design are approved. Please provide the Figma spec or Component ID we are building. I will investigate the existing theme and component tree before proposing Task 1.1."