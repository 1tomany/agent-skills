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
- Focus on using standard Tailwind styles
- Avoid relying on recognizable AI tropes or cliches

## Before writing code

Spend time understanding the answers to the following questions before writing any code. Ask as many questions as you need to ensure you confidently understand the problem being solved.

### Purpose

**Goal:** Answer: What problem does this interface solve and who uses it?

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

Every interactive element should implement (if applicable):

- Default state
- Hover state
- Active or pressed state
- Loading state
- Error state

A focus state should only be added to form inputs and buttons. Avoid focus states on links and icons.

## Production Requirements

### Accessibility

- Semantic HTML structure
- ARIA used very sparingly only only where absolutely necessary
- Keyboard navigation for all interactive elements
- Form validation messaging where forms exist

### Responsive

- At least two breakpoints: one for mobile and one for desktop browsers
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

- Generic chatbot bubbles with no branded concept
- Default Tailwind appearance with minimal tokenization
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
