# ⚛️ Stage 2: Next.js & React Implementation Workflow (v2026.2)

## 🎯 Primary Objective

To transform high-fidelity Figma designs into performant, accessible, and beautifully animated React applications. This document governs the Implementation and Validation phases for frontend development [cite: master_workflow 4].

## 🚦 Rule of Engagement: The "Frontend Investigation"

Before generating any JSX/TSX, you MUST perform a Deep Investigation of:

Design Specs: Review Figma/design tokens for spacing, typography, and color scales to ensure pixel-perfect fidelity.

Existing Component Library: Identify reusable atoms/molecules to prevent duplication (DRY) and maintain visual consistency [cite: AGENTS Rule 7].

State & Data Architecture: Determine if the task requires Server Components (RSC), local state (useState), or shared context/server actions.

Authoritative Invariants: Define frontend invariants (e.g., "The modal must never be open without an overlay", "Form validation must block submission") [cite: master_template Principle 0].

## 🏗️ Next.js & React Implementation Standards

1. Component Architecture (RSC & Client Isolation)

Server-First Design: Use React Server Components (RSC) for data fetching and static rendering to minimize client-side bundles.

Client Component Isolation: Mark components with 'use client' only when strictly necessary for interactivity, hooks, or animations.

Atomic Design: Organize the file structure into atoms, molecules, and organisms to maintain a scalable component hierarchy.

2. Styling & Layout (Responsive Excellence)

Tailwind CSS Tokens: Use utility classes derived from the theme. Avoid arbitrary values; if a custom value is needed, add it to tailwind.config.js.

Responsive-First: Always build for mobile-first using Tailwind's sm:, md:, and lg: prefixes [cite: Universal 3.1].

Accessibility (a11y): Use semantic HTML and ensure every interactive element is keyboard-navigable and screen-reader friendly (ARIA labels).

3. Animation & Interaction (Framer Motion / GSAP)

Declarative Animations: Use Framer Motion for layout transitions and simple interactive states (e.g., hover, tap).

Performance-Critical UI: Use GSAP for complex, timeline-based, or scroll-triggered animations that require high-performance rendering.

Reduced Motion: Always respect prefers-reduced-motion settings to ensure accessibility for all users.

## 🧱 Atomic Task Specification (Frontend)

For every approved task from Stage 1, generate a spec including:

Visual Goal: A clear description of the design-to-code target.

Component Signature: Define props (interfaces), state requirements, and whether it's an RSC or Client Component.

Animation Strategy: Define the triggers (e.g., whileInView, layoutId) and the easing/duration parameters.

Acceptance Criteria: Behavioral Given/When/Then contracts [cite: AGENTS Rule 15].

## 🧪 Implementation Discipline

Atomic Commits: feat(ui): <summary> – one logical change per commit [cite: git 3.3].

No Hallucinated Docs: Cite actual file paths and component names in all comments/logs [cite: docs.md].

Struggle Briefly: Use AI for boilerplate; keep ownership of component logic, accessibility contracts, and animation timing [cite: master_template Step 6].

### ✅ Completion Checklist (Rule 66)

[ ] Tailwind arbitrary values are used only where theme-extension is impossible.

[ ] Accessibility audit (e.g., axe-core) reports zero critical violations.

[ ] Animations are fluid (60fps) and do not cause Layout Shift (CLS).

[ ] TypeScript types are strict; no use of any or @ts-ignore.

[ ] All console.log and debug fragments are removed before commit.

Quick Start: "Next.js & React Workflow v2026.2 initialized. Architecture and Design are approved. Please provide the Figma spec or Component ID. I will investigate the existing theme and component tree before proposing Task 2.1."