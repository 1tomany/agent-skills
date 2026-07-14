---
name: web-design
description: Use when writing HTML and CSS for simple web pages or complex applications. This skill outlines standards and important conventions.
license: MIT
---

# Web Design Skill

## Mission

Create distinctive, production grade frontend interfaces that feel authored by a human designer, not averaged from template patterns.

## Success criteria

- Performant landing, marketing, and application pages
- Distinct visual identity with a clear narrative and signature element
- Production grade functionality with complete states and responsive behavior
- Accessibility by default with WCAG AA intent
- Token driven design system rather than one off styling
- Avoid relying on recognizable AI tropes or cliches

## Before writing code

Spend time understanding the answers to the following questions before writing any code. Ask as many questions as you need to ensure you confidently understand the problem being solved.

### Purpose

**Goal:** Answer: What problem does this interface solve and who uses it?

## Design tokens

Define tokens before layout.

```css
:root {
  /* Color */
  --color-bg:;
  --color-surface:;
  --color-text:;
  --color-muted:;
  --color-accent:;
  --color-focus:;
  --color-success:;
  --color-warning:;
  --color-danger:;

  /* Typography */
  --font-display:;
  --font-body:;
  --font-mono:;
  --text-xs:;
  --leading-xs:;
  --text-sm:;
  --leading-sm:;
  --text-base:;
  --leading-base:;
  --text-lg:;
  --leading-lg:;
  --text-xl:;
  --leading-xl:;
  --text-2xl:;
  --leading-2xl:;

  /* Spacing */
  --space-1:;
  --space-2:;
  --space-3:;
  --space-4:;
  --space-6:;
  --space-8:;

  /* Radius and Shadow */
  --radius-sm:;
  --radius-md:;
  --radius-lg:;
  --shadow-sm:;
  --shadow-md:;
  --shadow-lg:;

  /* Motion */
  --duration-fast:;
  --duration-base:;
  --duration-slow:;
  --ease-out:;
  --ease-spring:;
}
```

## Aesthetics Rules

### Typography

- When building landing pages, avoid the following fonts: Inter, Roboto, Arial, Helvetica, and system defaults
- When building application or administrative pages, prefer system default fonts
- Tune letter spacing and line height intentionally

### Color and palette

- No emojis or emoticon icons anywhere on the site
- No default purple gradient on white SaaS aesthetic
- One dominant hue plus one to three accents with defined roles
- Contrast and focus colors must be functional

### Layout and composition

- No predictable center hero followed by three cards and icon row
- Use consistent grid logic plus at least one intentional grid break
- Asymmetry encouraged when it clarifies hierarchy
- Responsive design must preserve narrative and rhythm

### Motion

- Performance is the top priority. Unless explicitly told, avoid unnecessary motion and animation at all costs, especially on non-landing or non-marketing pages
- Do **NOT** interfere with the scrolling settings the user has configured on their computer
- Animation on interactive elements should never cause unassociated elements to redraw: hovering over a link shouldn't cause text around it to wrap when it previously didn't, for example
- Prefer transform and opacity for performance
- Never reveal elements as a user scrolls; all elements should be rendered as they are specified

### Texture and material

- Avoid glass or transparent effects
- Use flat backgrounds for application pages
- Use textured or non-sterile backgrounds on landing or marketing pages if you feel they are performant and fit the design theme
- Preferred landing or marketing page techniques: Subtle grain overlay, SVG parametric patterns, noise driven gradients, paper fold shadows, CRT scanlines for retro themes

### Interaction states

Every interactive element must implement:

- Default state
- Hover state
- Active or pressed state
- Disabled state
- Loading state (if applicable)
- Error state (if applicable)

## Production Requirements

### Accessibility

- Semantic HTML structure
- ARIA rarely and only where necessary
- Keyboard navigation for all interactive elements
- Form validation messaging where forms exist

### Responsive

- Minimum three breakpoints
- Narrative and hierarchy preserved across sizes
- Touch targets at least 44 pixels on mobile

### Performance

- Your top priority is to prefer highly performant design: avoid heavy effects by default
- Canvas, WebGL, particles require reduced mode and lazy initialization
- GPU friendly animation patterns preferred

### Failure handling

Every design must account for failure paths, especially for application UI:

- Network failure or offline state
- Partial or delayed data
- User error and recovery flows

Failure states must be:

- Visually intentional
- On brand
- Informative without verbosity
- Silent failures are not permitted
- Default browser error states are not permitted

## Narrative consistency enforcement

Reject output if any are true:

- Typography, motion, layout, and copy feel authored by different systems
- Components are visually polished but conceptually disconnected
- Microcopy tone contradicts the chosen direction

**Goal:** Every element must reinforce the same story, mood, and intent.

## Abomination Checklist

Reject output if any are true:

- Inter plus purple gradient plus rounded cards plus generic icons
- Generic chatbot bubbles with no branded concept
- Default Tailwind appearance with minimal tokenization
- Missing focus states or keyboard access
- No error or loading states
- Marketplace template resemblance
- Visual polish without usability completeness
- Convergence on common AI aesthetic patterns

## Code

- Complete runnable code matching the requested scope
- Implementation complexity must match the aesthetic vision

## Final quality checks

Before delivery, verify all are true:

- Signature element exists and is functional
- Tokens drive styling decisions
- Accessibility requirements met
- All interaction states implemented
- Failure and recovery states designed
- Narrative consistency holds
- Responsive rhythm preserved
- No AI trope patterns appear

If any check fails, the output is invalid.

## Remember

You are capable of extraordinary creative work. Don't hold back. Show what can truly be created when thinking outside the box and committing fully to a distinctive vision. Every interface should feel like it was crafted by a designer with a clear point of view—not generated by an algorithm averaging templates.
